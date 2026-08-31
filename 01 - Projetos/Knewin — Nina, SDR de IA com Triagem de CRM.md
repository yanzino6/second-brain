---
type: solucao
cliente: Knewin (gestão de reputação de marca — produtos Dino e Comunique-se)
papel: Engenheiro de IA — arquitetura, construção e operação
stack: [n8n, Supabase, pgvector, PostgreSQL, WhatsApp Cloud API, HubSpot, OpenAI, Google Vertex AI, Google Gemini, Azure OpenAI]
escala: 34 workflows · ~700 nós · 26 ativos em produção
tags: [solucao, agente-ia, sdr, rag, crm, hubspot, cadencia, portfolio]
analisado: 2026-08-29
fonte: leitura direta da instância n8n via MCP (somente leitura)
---

# Knewin — Nina, SDR de IA com Triagem de CRM

> Agente de qualificação inbound no WhatsApp, com **14 tools**, RAG segregado por propósito, triagem contra HubSpot antes de responder, e dois sistemas de cadência independentes.
> **34 workflows, ~700 nós, 26 ativos em produção.** É a solução mais madura das quatro.

## O problema

Lead preenche formulário e cai no WhatsApp. Antes de qualquer resposta é preciso saber: essa pessoa já é cliente? já tem vendedor vinculado? falou com a gente nos últimos 90 dias? Responder errado significa um SDR de IA abordando cliente da casa como se fosse lead frio, ou passando por cima do vendedor que já tem o relacionamento.

---

## Arquitetura

```
Formulário HubSpot → link WhatsApp
        │
        ▼
Agente Conversacional (137 nós)
   ├─ buffer + debounce 25s
   ├─ ingestão multimodal (áudio, imagem, PDF/XLS/XLSX)
   ├─ memória Postgres por lead
   ├─ 2 índices RAG separados
   └─ 14 tools
        │
        ├─ triagem_elegibilidade (54n) ── HubSpot: cliente? vendedor? <90d?
        ├─ qualificado / desqualificar_lead / interesse_dino
        ├─ realiza_agendamento + consulta_disponibilidade
        ├─ get_help (transbordo humano)
        └─ envia_cliente / salva_produto / salva_email / start_conversation

Cadências (independentes do agente)
   ├─ "Sem Mensagem"  → preencheu form, não escreveu em 5 min
   └─ "Perdidos"      → reativação da base, 6 templates + 3 e-mails em D1/D3/D5

FUPs (95 nós) → 4 agentes LLM paralelos, um por touchpoint
```

---

## As decisões que valem defender

### 1. RAG segregado por propósito, não um índice só
Duas tools de retrieval distintas, com vector stores separados:
- `consultar_base_produtos` — o que o produto é, faz e resolve
- `consultar_perguntas_produto` — o que perguntar para qualificar

Índice único misturaria "descrição do Dino" com "pergunta de descoberta sobre o Dino" e a busca semântica traria a coisa errada na hora errada. Separar os índices é decisão de arquitetura de retrieval, não detalhe de implementação.

Os dois workflows de ingestão são versionados e documentados dentro da plataforma, com o modelo de embedding declarado: `text-multilingual-embedding-002`, 768 dimensões, Google Vertex. Um recebe `.jsonl` de base de conhecimento, outro recebe `.md` e **infere o produto pelo nome do arquivo**.

### 2. A triagem roda antes da conversa, contra o CRM real
`tool - triagem_elegibilidade`, 54 nós, é a peça mais sofisticada da instância. A árvore de decisão:

1. **E-mail genérico ou corporativo?** `gmail.com` e afins entram por busca de contato por e-mail. Domínio corporativo entra por busca de empresa — porque o domínio identifica a organização, não a pessoa.
2. **Contato existe no HubSpot?** Se não: cria contato, cria negócio, **associa os dois** via API de associações v4, move para a etapa "Contato Realizado".
3. **Se existe:** navega as associações contato→negócios, itera os negócios e busca cada um.
4. **Já é cliente?** (`e_cliente` no negócio) → rota própria, o agente não trata como lead frio.
5. **Interagiu nos últimos 90 dias?** Compara `closedate` contra a janela. Se sim: registra a mensagem, atualiza a etapa, **desativa os follow-ups agendados**, e busca o **dono do negócio** na API de owners para entregar o lead direto ao vendedor que já tem o relacionamento.

Isso é regra de negócio comercial implementada com travessia real de grafo de CRM — não um `if` sobre um campo.

### 3. Follow-up gerado por LLM, com schema, não por template
O workflow `FUPs` (95 nós) tem **4 agentes de IA em paralelo**, um por touchpoint, cada um com:
- **memória Postgres própria** — o follow-up conhece a conversa que já aconteceu
- **Structured Output Parser** — a saída é validada contra schema antes de virar mensagem

Follow-up templatizado ignora o que o lead já disse. Este não.

### 4. Jitter aleatório entre toques
```js
Math.floor(Math.random() * (120 - 1 + 1)) + 1
```
Intervalo aleatório de 1 a 120 antes de cada touchpoint, em vez de espaçamento fixo. Cadência com intervalo constante tem assinatura de robô; essa não tem. Detalhe operacional que só aparece em quem já viu número ser bloqueado.

### 5. Duas cadências com propósitos separados, documentadas na plataforma
- **"Sem Mensagem"** — entrada e executor separados. Entrada: lead preencheu o formulário e não escreveu em 5 min; **busca o negócio existente no HubSpot em vez de criar** (evita duplicata) e inscreve na fila. Executor: roteia por quantidade de variáveis do template.
- **"Perdidos"** — reativação da base: 6 templates de WhatsApp + 3 gatilhos de e-mail via HubSpot, em três janelas (D1, D3, D5), reaproveitando o esqueleto do FUPs. Tem workflow de **handoff** próprio, para o lead que responde sair da cadência e entrar no fluxo normal.

Ambas têm descrição escrita **dentro do n8n**. Documentação onde o próximo operador vai olhar.

### 6. Tools de responsabilidade única
Cada tool é um workflow separado, quase todas entre 6 e 15 nós, com o mesmo formato: gatilho de execução → ação no CRM → registro no monitoramento. `tool - interesse_dino` (8 nós) atualiza a etapa, marca `oportunidade_principal` como DINO AVULSO e grava o resumo da conversa nas observações do negócio. Uma tool, uma transição de estado, um registro.

### 7. Observabilidade
Toda chamada de tool e toda mensagem passam por um backend de monitoramento dedicado, além do registro no CRM. Há workflow de erro global com `errorTrigger`.

---

## Achados técnicos (o lado crítico)

> [!warning] Coisas que eu apontaria numa revisão
> - **RLS desabilitado nas 7 tabelas** do Supabase do agente — documentado no próprio `CLAUDE.md` do projeto. Qualquer um com a chave anon lê e escreve tudo.
> - **`FUP Novax - Trigger`** — nome de outro cliente vivo dentro da instância da Knewin. Mesmo padrão de "restos de outro projeto" encontrado na Ebramed.
> - **Três caminhos de envio de WhatsApp coexistindo** (nó nativo, Uazapi, Mega API). Migração inacabada ou redundância não declarada — em qualquer caso, três lugares para dar manutenção.
> - **Workflows de rascunho em produção:** `My workflow`, `My workflow 2`, `My workflow 3`, `Rascunho`, `Dedupe Tool Calls (Memory Fix)`. O último tem nome de correção de bug e está desativado — vale saber se o bug voltou.
> - **Dois provedores de embedding** entre os workflows de ingestão (OpenAI em um caminho, Vertex em outro). Índices com modelos diferentes não são comparáveis; se ambos alimentam a mesma tabela, a busca degrada.

---

## Competências que este projeto comprova

| Competência | Evidência |
|---|---|
| Arquitetura de agente com tools | 14 tools de responsabilidade única, cada uma um workflow versionado |
| RAG aplicado | Dois índices segregados por propósito, ingestão versionada, modelo e dimensão declarados |
| Integração profunda de CRM | Travessia de associações HubSpot v4, owners API, criação e associação de contato/negócio |
| Regra de negócio em sistema | Cliente / vendedor vinculado / janela de 90 dias como roteamento executável |
| Design de cadência | Duas cadências independentes, handoff, jitter anti-padrão, saída por interação |
| Saída estruturada de LLM | Structured Output Parser em todos os 4 agentes de follow-up |
| Operação | Monitoramento dedicado, workflow de erro global, descrições na plataforma |

## Como contar isso

- **Recrutador (1 linha):** "SDR de IA em produção no WhatsApp com 14 tools, RAG em pgvector e triagem automática contra HubSpot — 34 workflows, 26 ativos."
- **Cliente:** "O agente não fala com ninguém antes de saber se já é cliente e quem é o vendedor dono da conta."
- **Entrevista técnica:** puxe a segregação dos índices RAG, a árvore de triagem no HubSpot e o follow-up com memória + schema. São três decisões com trade-off real.

> [!question] Em aberto
> - Qual foi o resultado: leads qualificados, agendamentos, conversão?
> - Quanto do sistema é seu e quanto é de outra pessoa do time? Preciso saber para não reivindicar o que não é seu.
> - O `Dedupe Tool Calls (Memory Fix)` está desativado — o problema foi resolvido na raiz ou só contornado?

<!-- fonte: leitura da instância n8n via MCP em 2026-08-29, somente leitura. Nenhuma credencial, URL de instância, ID de projeto ou endpoint interno registrado neste vault. -->
