---
type: solucao
cliente: Ebramed (Escola Brasileira de Medicina — Grupo Educar Mais)
papel: Engenheiro de IA — diagnóstico, arquitetura e migração
stack: [n8n, Supabase, pgvector, PostgreSQL, WhatsApp Cloud API (Meta), Uazapi, Google Vertex AI, OpenAI Whisper]
escala: 20 workflows · ~600 nós · 17 ativos
tags: [solucao, agente-ia, sdr, diagnostico, causa-raiz, migracao, compliance, portfolio]
analisado: 2026-08-29
fonte: revisão local de 28/07/2026 + leitura direta da instância n8n via MCP em 29/08/2026
---

# Ebramed — Isabela, do diagnóstico à migração

> Agente SDR de WhatsApp para captação de médicos em pós-graduação. **O case mais forte do portfólio** — não pela construção, mas porque é o único com o ciclo completo documentado: diagnóstico com evidência → decisão de arquitetura → migração → verificação do resultado.

## Por que este case vale mais que os outros

Os outros projetos mostram que ele **constrói**. Este mostra que ele **descobre por que algo está quebrado, prova, decide e verifica depois**. É a diferença entre um desenvolvedor e um engenheiro.

---

## Parte 1 — O diagnóstico (28/07/2026)

Revisão de 420 linhas sobre 5 workflows de agente com 121–122 nós cada.

### A metodologia veio antes dos achados
A revisão declara, no topo, como cada afirmação foi verificada:
- **[PROVADO]** — log de execução real do n8n, resposta HTTP medida, ou consulta SQL
- **[ANÁLISE]** — leitura estática do workflow: plausível e específico, mas não reproduzido

Essa separação é o que torna o documento utilizável. Sem ela, achado sério e palpite ficam no mesmo nível.

**O que foi inspecionado:** os 5 workflows normalizados e diffados entre si, 50 execuções com erro, schema e conteúdo do banco, o system prompt de 14.953 caracteres confrontado com os 10 documentos comerciais, e os 6 links que o prompt entrega ao lead.

### A causa-raiz — P0-1
Os três nós `Infos Manuais`, `Infos Manuais1` e `Infos Manuais2`, **em todos os 5 workflows**, derivavam o telefone assim:

```js
(n=>{ n=(n||'').toString().replace(/[^0-9]/g,'');
      if(n.substr(0,2)!=='55') n='55'+n;
      if(n.length===12) n=n.slice(0,4)+'9'+n.slice(4);
      return n; })( $('Webhook1').item.json.body.chat.phone )
```

**`body.chat` não existe no payload do provedor.** Verificado contra o payload real capturado do webhook de produção.

A cadeia de consequências:

```
body.chat.phone → undefined
   → telefone normalizado = "55"  (a função "conserta" o vazio)
      → sessionKey da memória = vazia
         → TODOS os leads compartilham a mesma conversa
         → busca de lead existente sempre falha  → duplicatas
         → lead novo grava com celular vazio
         → buffer de mensagens é compartilhado entre leads
```

**Uma causa explicando quatro sintomas.** É o tipo de achado que só aparece quando se procura a origem em vez de tratar sintoma.

### Os outros 17 achados
| Nível | Achados |
|---|---|
| **P0** — quebra o produto | Shard `Conversas 2` devolvendo 404 e descartando 100% das mensagens · tool de preço falhando com 401, funil nunca registrando preço apresentado |
| **P1** — grave | Vírgula do lead virando quebra de linha · `start_conversation` re-disparando · chunking do RAG quebrado na reingestão · sem fallback de modelo · corrida em follow-up gerando duplicata · registro de falha de envio que nunca registra |
| **P2** — dívida e risco | 4 clones sem fonte única de verdade · **segredos em texto puro nos nós** · **RLS desabilitado em 8 tabelas** · custo por turno sem teto · restos de outro projeto em produção |

### O harness de teste
`testes/harness.mjs` — **429 linhas, Node 18+, zero dependências.** Dispara payloads reais no webhook e verifica o estado resultante no banco.

- Códigos de saída distintos: `0` passou · `1` falhou · `2` falta configuração · `3` erro inesperado — para pendurar em CI ou cron.
- Configuração inteira por variável de ambiente, com default.
- Casos agrupados (`webhooks`, `links`, `rag`, `identidade`, `filtros`) para rodar só o necessário.
- Acompanhado de **1.049 linhas** de documentação de teste: matriz de casos de borda com taxonomia de severidade (**S1** perde ou vaza dado de lead · **S2** lead não atendido ou atendido errado · **S3** degrada qualidade · **S4** cosmético), roteiros conversacionais e payloads de integração.

---

## Parte 2 — A migração (agosto/2026)

A arquitetura de 4 números em **API não oficial**, com escoamento de volume entre eles para diluir risco de banimento, não se sustentou: os números foram bloqueados na prática. A decisão foi migrar para **um único número na API Oficial da Meta**.

### O que a instância mostra hoje

| 28/07/2026 | 29/08/2026 |
|---|---|
| `Conversas 01`, `2`, `3`, `4` + `Ensino` — 5 clones byte-a-byte | `Conversas 01` (legado) + `Agente SDR - API Oficial` (novo) |
| Identidade derivada em **3 nós** por workflow | Identidade em **1 nó** |
| Uazapi (não oficial) | Meta Cloud API + trilha legada em paralelo |
| — | `FUPS - API Oficial INBOUND` (115n) separado do `FUPs - Ebramed` (83n) |

**P0-2 e P2-12 resolvidos por eliminação:** o shard morto e os clones sem fonte única de verdade deixaram de existir.

### A trilha nova foi construída limpa
O `Agente SDR - API Oficial` (128 nós) deriva a identidade do lead assim:

```js
nome    = $('Webhook').item.json.contacts[0].profile.name
celular = $('Webhook').item.json.messages[0].from
```

Campos reais do payload da Meta Cloud API, lidos **uma vez**, num único nó. O bug não foi propagado para a arquitetura nova — e a duplicação de três nós de identidade, que era o que permitia a inconsistência, foi eliminada por desenho.

---

## ⚠️ Achado atual — 29/08/2026

> [!danger] O legado continua ativo e continua quebrado
> `Agente SDR - Ebramed - Conversas 01` está **ATIVO** e seus três nós `Infos Manuais*` ainda leem `$('Webhook1').item.json.body.chat.phone`. **20 nós** desse workflow ainda dependem desse caminho.
>
> A trilha nova está correta. A antiga não foi corrigida nem desligada — as duas rodam em paralelo. Todo lead que entrar pela trilha antiga cai na memória compartilhada.
>
> **Decisão a tomar:** corrigir o legado ou desativá-lo. Manter os dois ligados é o pior dos três cenários, porque o comportamento depende de por onde o lead entrou.

Outros pontos ainda abertos, que valem verificar contra a revisão de julho: os segredos em texto puro (P2-13) e o RLS desabilitado (P2-14) — nenhum dos dois é visível como resolvido pela estrutura dos workflows.

---

## Parte 3 — A engenharia de prompt

`PROMPT_ISABELA_v4.md`, **294 linhas**, estruturado em tags XML com precedência declarada: regras invioláveis > fluxo > pedido do lead.

**Compliance regulatório na camada de prompt.** Publicidade médica é regulada pelo CFM. O prompt proíbe explicitamente: promessa de renda, vaga, aprovação ou resultado; comparação com concorrente; superlativo vazio; urgência falsa. E proíbe afirmar ou sugerir que a pós concede **RQE ou título de especialista** — é lato sensu, não residência. Risco jurídico do cliente tratado como requisito de sistema.

**Grounding anti-alucinação.** "Nunca invente carga horária, módulos, coordenador, duração, valor, link, depoimento ou estatística." Regra separada e explícita proibindo **montar, adivinhar, traduzir ou adaptar uma URL**, mesmo quando o padrão parece óbvio — que é exatamente o modo de falha real de LLM com link.

**Orçamento de conteúdo.** Mecanismo próprio: o agente conta quantas mensagens já entregaram informação nova; depois da segunda, a próxima é obrigatoriamente de fechamento. O racional está escrito: *"excesso de conteúdo é tão ruim quanto conteúdo nenhum: mantém o lead confortável sem decidir."*

**Escada de ofertas** com degradação controlada, para o lead nunca sair da conversa sem alternativa. E **uma pergunta por mensagem**, com exemplo de certo e errado no próprio prompt.

**Corpus RAG curado à mão:** 25 programas de curso + 10 documentos comerciais convertidos para markdown estruturado.

---

## Competências que este projeto comprova

| Competência | Evidência |
|---|---|
| **Depuração de causa-raiz** | Uma causa provada explicando quatro sintomas, com payload de produção como evidência |
| **Disciplina de evidência** | Separação [PROVADO] / [ANÁLISE] declarada antes dos achados |
| **Engenharia de teste** | Harness de 429 linhas sem dependências + 1.049 linhas de documentação de caso |
| **Taxonomia de severidade** | S1–S4 ancorada em impacto no negócio, não em gosto técnico |
| **Decisão de arquitetura sob restrição** | Migração de API não oficial para oficial, com trade-off (custo e aprovação de template) assumido |
| **Não repetir o erro** | A trilha nova concentra identidade em um nó — o defeito não foi carregado adiante |
| **Compliance como requisito** | CFM implementado no prompt |
| **Segurança** | RLS ausente e segredos em texto puro identificados e classificados |

## Como contar isso

- **Recrutador (1 linha):** "Diagnostiquei em produção a causa-raiz que fazia todos os leads compartilharem a mesma sessão de conversa, e conduzi a migração de WhatsApp não oficial para API Oficial da Meta."
- **Cliente:** "Não trato sintoma. Provo a origem com log de produção antes de mexer."
- **Entrevista técnica:** este é o case para contar por inteiro. Tem hipótese, evidência, causa-raiz, decisão, execução e verificação posterior — inclusive a parte que ainda não foi resolvida. Contar o que ficou aberto aumenta a credibilidade, não diminui.

> [!question] Em aberto
> - `Conversas 01` ainda ativo com o bug: decisão consciente ou esquecimento?
> - Os P0-3, P1-4 a P1-11 foram corrigidos? A estrutura não deixa ver.
> - Resultado da primeira campanha (985 contatos, ~R$ 315): quantos responderam?

<!-- fonte: REVISAO_FLUXOS.md de 28/07/2026 + leitura da instância n8n via MCP em 29/08/2026, somente leitura. Nenhuma credencial, URL de instância ou endpoint registrado neste vault. -->
