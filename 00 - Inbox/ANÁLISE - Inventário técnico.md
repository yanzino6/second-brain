---
type: analise
status: processado
tags: [analise, inventario, portfolio, evidencia, carreira]
data: 2026-08-29
escopo: ~/Documents/smartside (6 projetos) · github.com/yanzino6 (11 repos) · currículo atual
---

# ANÁLISE — Inventário técnico

> Varredura completa do que existe hoje como **evidência** do trabalho do Yan, feita em 29/08/2026.
> Regra aplicada: nada de credencial, chave, ID de projeto, URL de instância ou telefone de teste entra neste vault. Onde a prática importa, registrei a prática — nunca o valor.
> Nomes de cliente ficam aqui porque este vault é privado e o Yan precisa navegar os próprios arquivos. A versão externa é anonimizada — ver [[O que eu construí]].

---

## Veredito em uma linha

A evidência é muito mais forte do que o currículo declara. O gargalo do portfólio **não é falta de material** — é que o material está espalhado em pastas locais sem git, e o currículo descreve atribuição em vez de resultado.

---

## 1. Ebramed — Agente SDR Isabela · **o ativo mais forte**
`~/Documents/smartside/Ebramed` · 397 MB · ⚠️ **sem versionamento git**

### O que existe
| Artefato | Escala | O que prova |
|---|---|---|
| `PROMPT_ISABELA_v4.md` | 294 linhas | Engenharia de prompt de nível sênior |
| `REVISAO_FLUXOS.md` | 420 linhas | Análise de causa-raiz em produção |
| `TESTES_01` matriz de edge cases | 164 linhas | Taxonomia de severidade e priorização |
| `TESTES_02` roteiros conversacionais | 295 linhas | QA de comportamento de agente |
| `TESTES_03` payloads de integração | 461 linhas | Teste de contrato |
| `TESTES_04` + `testes/harness.mjs` | 129 + 429 linhas | Automação de teste pronta para CI |
| `rag_cursos_ebramed/` + `comercial/` | 35 documentos curados | Curadoria de corpus RAG |

### Engenharia de prompt — o que o v4 faz de não-óbvio
- Estruturado em **tags XML** (`<identidade>`, `<regras_invioláveis>`, `<rotina_interna>`, `<checagens>`, `<fluxo>`) com **precedência declarada**: regras > fluxo > pedido do lead.
- **Grounding anti-alucinação explícito:** "nunca invente carga horária, módulos, coordenador, duração, valor, link, depoimento ou estatística". Regra separada proibindo **montar ou adivinhar URL**, mesmo quando o padrão parece óbvio — que é exatamente o modo de falha real de LLM.
- **Compliance regulatório embutido:** publicidade médica é regulada pelo CFM. O prompt proíbe promessa de resultado, comparação com concorrente, urgência falsa, e proíbe afirmar que a pós concede RQE ou título de especialista. Isso é risco jurídico do cliente tratado na camada de prompt.
- **Orçamento de conteúdo** — mecanismo próprio: conta quantas mensagens já entregaram informação nova; depois da segunda, a próxima é obrigatoriamente de fechamento. Racional declarado: *"excesso de conteúdo é tão ruim quanto conteúdo nenhum: mantém o lead confortável sem decidir."*
- **Escada de ofertas** com degradação controlada, para o lead nunca sair sem alternativa.
- **Rotina interna silenciosa** (chain-of-thought estruturado) antes de cada mensagem.

### A revisão de fluxos — por que vale mais que o resto
Declara a metodologia antes dos achados: **[PROVADO]** = confirmado com log de execução real, resposta HTTP medida ou consulta SQL; **[ANÁLISE]** = leitura estática, plausível, não reproduzido. Essa disciplina de evidência é rara e é a coisa mais contratável do material inteiro.

**18 achados classificados em P0/P1/P2.** A causa-raiz (P0-1) é exemplar:

> Os nós derivavam o telefone de `body.chat.phone`. **`body.chat` não existe no payload real do provedor.** Resultado: telefone sempre vazio → `sessionKey` vazia → **todos os leads compartilhavam a mesma memória de conversa**. Uma causa explicando quatro sintomas distintos.

Outros P0: um dos 4 shards devolvendo 404 e descartando 100% das mensagens; a tool de funil falhando com 401, fazendo o funil nunca registrar preço apresentado.

Achados de **segurança**: RLS desabilitado em 8 tabelas, segredos em texto puro nos nós, custo por turno sem teto.

### O harness
429 linhas, Node 18+, **zero dependências**. Códigos de saída distintos (`0` ok, `1` falha, `2` config faltando, `3` erro inesperado) — desenhado para pendurar em CI ou cron. Configuração inteira por variável de ambiente. Casos agrupados (`webhooks`, `links`, `rag`, `identidade`, `filtros`) para rodar só o que interessa.

> [!danger] Risco imediato
> 397 MB de material sem git. Um `rm` acidental ou HD queimado apaga o ativo mais forte do portfólio.

---

## 2. SmartSide CRM — sistema RBAC · **a melhor prova de engenharia de software**
`~/Documents/smartside/smartside-crm` · repo git · React 18 + TypeScript + Vite + Supabase

**Escala do projeto:** 280 arquivos TS/TSX · 58.794 linhas · 34 edge functions · 113 migrations · 679 commits totais.
**Participação do Yan:** 20 commits — mas o volume engana, ver abaixo.

### A entrega principal: permissionamento por função (ago/2026)
**61 arquivos, +11.685 linhas.** Não é um commit de ajuste — é um subsistema de segurança inteiro.

| Camada | O que foi feito |
|---|---|
| Banco | 10 migrations aplicando permissão na camada de **RLS**, não na aplicação |
| Função | `has_perm(user, org, permission)` como **fonte única de verdade** |
| Edge functions | 10 funções reescritas para respeitar a permissão no servidor |
| Testes | **5.434 linhas de SQL de teste de RLS** em 8 arquivos |
| Frontend | `src/lib/permissions.ts` — espelho React da função SQL |

### O detalhe que mostra maturidade
O comentário no topo de `permissions.ts`:

> *"This module answers the SAME question has_perm answers, with the same precedence, so a screen never offers a control the database will refuse. It is a **mirror, not an authority**: hiding a button is not enforcement. Every permission is enforced in RLS and in the edge functions; this exists only so the UI agrees with them."*

Isso é defesa em profundidade explicada por escrito, com o modo de falha nomeado. É o tipo de coisa que distingue quem entende segurança de quem só implementa a tela.

### Outras contribuições
- **Pipeline de template do WhatsApp (Meta):** criação de template com header de mídia via *resumable upload*, formatter dedicado, envio de campanha por template funcionando de ponta a ponta.
- **Integração de provedor WhatsApp:** edge functions de connect / disconnect / status / send-message.
- **Inbox:** fixar conversas no topo.
- **Correções:** convites múltiplos, criação de origem por admin, mensagens de erro de conexão, coluna inexistente em constraint de autoridade de edição.
- **Tooling:** `CLAUDE.md` do projeto, baseline de lint, documentação de cobertura do eslint.

---

## 3. Farmly — pipeline de geração e enriquecimento de leads
`~/Documents/smartside/Farmly` · ⚠️ sem git

Stack: Google Places API · Firecrawl · Gmail API · Meta WhatsApp API Oficial · Supabase · Pipedrive.

**Números reais** (dá para citar em entrevista):
- `farmly_leads_base.csv` — **2.498 leads enriquecidos** com 15 campos (empresa, domínio, site, redes, endereço, contato, e-mail, telefone, deal do Pipedrive, query de região, flag de abordagem).
- `leads_discarded_no_enrichment.csv` — **1.713 descartados** por não enriquecer.
- Total processado: **~4.211 empresas**, taxa de enriquecimento ≈ **59%**.
- Segmentação geográfica por bairro (100 bairros mapeados para torrefações artesanais).

O descarte estar em arquivo separado é bom sinal: mostra critério de qualidade explícito em vez de empurrar lead ruim para o funil.

---

## 4. Boavista — BDR outbound multicanal
`~/Documents/smartside/Boavista` · ⚠️ sem git

Stack: **Microsoft Graph API** (e-mail via shared mailbox com SendAs) · **Unipile** (LinkedIn) · Supabase · Kommo CRM.
Duas personas ativas operando em paralelo, com convenção de nome de workflow padronizada (`[Cliente] - [Tipo] - [Descrição]`).

O SendAs via shared mailbox é detalhe técnico não trivial — permite disparo em nome de outra pessoa sem credencial dela.

---

## 5. Knewin — Agente Nina
`~/Documents/smartside/Knewin` · ⚠️ sem git

`prompt.md` v2, **284 linhas**. Stack: WhatsApp Cloud API (Meta) · Supabase + pgvector (embeddings 1536) · OpenAI + Azure OpenAI · HubSpot.

Diferenças de design em relação à Isabela, que mostram adaptação e não cópia:
- **Contexto injetado por turno** (nome, é-cliente, produto já mapeado) usado como atalho para não refazer etapa concluída — desenho de estado sem máquina de estado.
- **Regras de formatação específicas do canal:** negrito de WhatsApp é `*um*` asterisco, proibido travessão e markdown. Detalhe que quase todo mundo erra.
- Papel deliberadamente estreito: qualifica e faz ponte, **não fecha negócio**.

---

## 6. Alquimia
`~/Documents/smartside/Alquimia` — só um `venv`. **Nada aproveitável.**

---

## 7. GitHub — github.com/yanzino6
Conta criada out/2024 · 11 repositórios públicos · 0 stars · bio desatualizada (diz "CT Junior" como empresa).

| Repo | Stack | O que é | Vale para portfólio? |
|---|---|---|---|
| `ARMv7-A-Arqcomp-26-1` | Python + Logisim | Processador ARMv7-A com controle **microprogramado** (uROM + PLAs), datapath modular, relatório de 404 linhas, bateria de testes com verificadores automatizados em Python. Trabalho em equipe (4 pessoas), 7 commits do Yan | **Sim** — prova fundamento de arquitetura de computadores |
| `ProjetoPiloto` | TypeScript | Backend em camadas (controllers / services / models / routes / middlewares) com JWT. 19 commits, todos dele. Da diretoria de Tecnologia do CT Junior | **Sim** — prova backend estruturado |
| `desafio-upcities` | — | Desafio técnico da UpCities: ordenação auditável de fila de creche por critérios de decreto municipal. **Só o README — não resolvido** | **Oportunidade em aberto** |
| `estudos-tbo` | C | Técnicas Básicas de Otimização (?) | Estudo |
| `estudos-sistemas-operacionais` | — | Disciplina de SO, criado 29/08/2026 | Estudo |
| `exercABBFreqPalavras` | C | Árvore binária de busca — frequência de palavras | Estudo |
| `exercicios-gerais` | C | Programação II (fork) | Estudo |
| `PIC2024-DDY` | C++ | — | Estudo |
| `2024-2-template-TP1-etapa-2`, `Template_Trabalho` | — | Templates de trabalho | Não |
| `second-brain` | — | Este vault | Meta |

---

## Achados que mudam o que fazer a seguir

### 1. O currículo subdeclara a competência — este é o problema principal
| Currículo diz | Evidência mostra |
|---|---|
| React (básico) | Subsistema RBAC de 11.685 linhas em React/TS + Supabase, com espelho de permissão no frontend |
| Node.js (básico) | Harness de teste de 429 linhas, zero dependências, com códigos de saída para CI |
| Supabase / PostgreSQL | 5.434 linhas de teste de RLS, 10 migrations de política de segurança, função `has_perm` como fonte de verdade |
| *(não aparece)* | Análise de causa-raiz em produção com disciplina [PROVADO]/[ANÁLISE], 18 achados classificados |
| *(não aparece)* | Compliance regulatório (CFM) implementado na camada de prompt |
| *(não aparece)* | Engenharia de teste: matriz de edge cases com taxonomia de severidade S1–S4 |

Declarar "básico" no que se domina não é humildade — é o recrutador filtrando você fora antes da entrevista.

### 2. Nenhum bullet do currículo tem número
Tudo é atribuição ("desenvolvimento de agentes de SDR"), nada é resultado. Os números existem e estão levantados: 4.211 empresas processadas · 2.498 leads enriquecidos · 58.794 linhas no CRM · 11.685 linhas de RBAC · 18 achados de produção · 985 contatos na primeira campanha.

### 3. Quatro projetos sem versionamento
Ebramed (397 MB), Farmly (396 MB), Boavista, Knewin. É onde está a melhor prova de competência, e está a um acidente de sumir.

### 4. O GitHub público não conta a história certa
Quem abrir hoje vê exercício de faculdade em C. O trabalho de agente, RBAC e teste — que é o diferencial — não está lá, e boa parte não pode estar (código de cliente). Falta um repositório público que demonstre a competência sem expor cliente.

### 5. `desafio-upcities` está parado
Desafio técnico real, de agosto, com só o README. O enunciado é bom (fila auditável por critério legal, dados sujos de prefeitura) e casa exatamente com o que ele sabe fazer.

---

## Lacunas — o que ainda não sei
> [!question] Em aberto
> - Início e fim reais na smartside (o currículo diz set/2025–atual; o vault antigo tinha registro até ago/2026).
> - Sobreposição smartside (set/2025–atual) × CT Junior Gerente (jun–dez/2025): foi simultâneo? Se sim, vale explicitar, porque some no formato atual.
> - O que aconteceu com o `desafio-upcities` — processo seletivo ainda em pé?
> - Projetos anteriores a jan/2025 e trabalho de faculdade fora os repos listados.
> - Se existe material de Solvee, Shopcão, AEVO e Biancogres em outro lugar (apareciam no vault antigo, não têm pasta local).

<!-- fonte: varredura de ~/Documents/smartside, github.com/yanzino6 e Curriculo_Yan_Simmer.pages em 2026-08-29 -->
