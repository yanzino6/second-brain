---
type: solucao
cliente: Boavista Tecnologia
papel: Engenheiro de IA — arquitetura e construção
stack: [n8n, n8n Data Tables, Supabase, Unipile (LinkedIn), Microsoft Graph API, Kommo CRM, Google Vertex AI, Google Gemini, MCP]
escala: 21 workflows · ~560 nós
tags: [solucao, bdr, outbound, linkedin, rate-limiting, lead-scoring, mcp, portfolio]
analisado: 2026-08-29
fonte: leitura direta da instância n8n via MCP (somente leitura)
---

# Boavista — BDR de LinkedIn com Fila por Score

> Máquina de prospecção outbound no LinkedIn e e-mail corporativo, operando por persona. **21 workflows, ~560 nós.**
> O que distingue esta solução das outras: **engenharia de rate limiting**. LinkedIn bane conta que se comporta como robô, então boa parte do sistema existe para o robô não parecer robô.

## O problema

Prospecção no LinkedIn tem teto rígido e invisível. Convite demais, rápido demais, ou fora de horário humano, e a conta é restringida — levando junto o perfil real da pessoa. E o volume precisa ir para os leads certos primeiro, porque o teto diário é escasso.

---

## O pipeline

```
Injeção de leads (Google Sheets → Data Tables → Supabase)
        ▼
Scorer          agente LLM classifica: department · seniority · score 1–4
        ▼
Cria Queue      fila por prioridade, com cota configurável por score
        ▼
Invite Sender   dispara convite com jitter, dentro de janela de horário
        ▼
New Connection  webhook: conexão aceita
        ▼
Enrich+Approach enriquece e aborda com agente
        ▼
Message Received  trigger de resposta (Outlook / Microsoft Graph)
        ▼
FUPs            9 agentes LLM de follow-up
```

---

## As decisões que valem defender

### 1. Rate limiting como requisito de primeira classe
O `Invite Sender` não dispara em loop. Ele tem três travas independentes:

**Intervalo com jitter, no próprio trigger:**
```js
minutesInterval: (160 - Math.random() * 10).floor()
```
Aproximadamente um convite a cada 150–160 minutos, nunca no mesmo intervalo duas vezes.

**Janela de horário:** um `IF` compara a hora corrente (`$now.toISO().slice(11,13)`) contra limites — fora do horário comercial, não dispara. Convite às 3h da manhã é assinatura de automação.

**Fila com estado:** só busca linhas onde `Invite_Sent` está vazio, e marca depois de enviar. Sem reenvio, sem duplicata.

As três juntas são o que mantém a conta viva. Isoladas, nenhuma resolve.

### 2. Parser de URL de LinkedIn defensivo
```js
let identifier = url.split('/').filter(Boolean).pop();
identifier = identifier.split('?')[0].split('#')[0];
if (!identifier || identifier.toLowerCase() === 'people') { /* pega o segmento anterior */ }
```
Trata barra final, query string, fragmento, e o caso em que a URL termina em `/people`. Detalhe pequeno, mas é a diferença entre a fila rodar e a fila quebrar silenciosamente em 5% dos leads.

### 3. Fila de prioridade com cota configurável
O `Cria Queue` (47 nós) processa os leads em ordem de score (1 → 2 → 3 → 4). Cada faixa tem seu próprio `Limit`, e o teto vem de um nó **`Settings`**:
```
quantidade_score_1 · quantidade_score_2 · quantidade_score_3 · quantidade_score_4
```
Um lugar só para ajustar a distribuição do volume diário entre as faixas — sem tocar em lógica. Isso é o começo de configuração separada de código.

Há ainda uma limpeza diária às 2h que apaga linhas sem `Full_Name`, para o lixo não entrar na fila.

### 4. Scoring por LLM com saída estruturada
O `Scorer` recebe só três campos (nome, empresa, cargo) e devolve schema fixo:
```json
{ "department": "Innovation", "seniority": "Manager", "score": "2" }
```
Classificação restrita a schema, não texto livre — o score alimenta a fila diretamente, então precisa ser um valor confiável.

### 5. E-mail corporativo via Microsoft Graph com SendAs
Envio a partir de **shared mailbox** com SendAs: dispara em nome de outra pessoa sem precisar da credencial dela. É o jeito correto (e auditável) de fazer isso no ecossistema Microsoft — a alternativa comum, que é pedir a senha da pessoa, é o que se costuma ver.

A detecção de resposta usa `microsoftOutlookTrigger`, não polling de caixa.

### 6. Persona como unidade de replicação
Cada workflow existe em versão genérica e versão nomeada (`LDR - Scorer` / `Scorer - Marcelo`, `BDR - Invite Sender` / `Invite Sender Marcelo`). O sistema escala clonando o conjunto por pessoa que empresta o perfil.

> [!warning] O custo desse padrão
> É exatamente o problema P2-12 que ele mesmo diagnosticou na Ebramed: clones sem fonte única de verdade. Uma correção precisa ser aplicada N vezes. Funciona com 2 personas; com 6 vira dívida.

### 7. Migração de persistência visível no meio do caminho
Três camadas convivem hoje:
- `Injeta Leads na tabela` ainda lê **Google Sheets**
- Os workflows de fila escrevem em **Data Tables do n8n** *e* em **Supabase**, em paralelo
- `TEMP - Migrate Enrich_person` — migração pontual, documentada: *"one-time migration: reads Enrich_person from Data Table and updates Supabase via REST API"*

É a saída de planilha-como-banco em andamento. A escrita dupla é a estratégia certa para migrar sem parar a operação — mas é estado transitório, e transitório que dura vira permanente.

### 8. Ele escreveu um MCP Server
`MCP Server Ekyte` — um workflow n8n com `mcpTrigger` expondo **14 tools** do Ekyte (tarefas, tickets, workspaces, projetos, boards, notas, notificações, formulários) para consumo por qualquer cliente MCP.

Está marcado "(Ignorar)" e desativado, mas a competência conta: **não é só consumir MCP, é publicar um servidor MCP.** Poucos no mercado fizeram isso.

---

## Competências que este projeto comprova

| Competência | Evidência |
|---|---|
| Engenharia de rate limiting | Jitter no trigger + janela de horário + fila com estado, as três combinadas |
| Fila de prioridade | Processamento por faixa de score com cota configurável em nó `Settings` |
| Classificação com LLM | Saída estruturada por schema alimentando decisão automatizada |
| Integração Microsoft 365 | Graph API com shared mailbox e SendAs; trigger nativo do Outlook |
| Código defensivo | Parser de URL que trata quatro formatos de entrada |
| Migração de dados sem downtime | Escrita dupla Data Tables + Supabase, com migração pontual documentada |
| **Autoria de MCP Server** | 14 tools de um sistema externo expostas via `mcpTrigger` |

## Como contar isso

- **Recrutador (1 linha):** "Máquina de prospecção em LinkedIn com fila priorizada por score de LLM e rate limiting com jitter, janela de horário e controle de estado — mais um MCP Server expondo 14 tools de um sistema externo."
- **Cliente:** "Prospecção automatizada que não queima a conta de quem empresta o perfil."
- **Entrevista técnica:** o rate limiting é o melhor gancho — mostra que você pensa no sistema operando contra uma plataforma adversarial, não só no caminho feliz. O MCP Server é o diferencial raro.

---

## Resultados (coleta 2026-05-13 · persona Rodrigo)

> Fonte: `~/Documents/metricas-de-projetos-smarts-ai/boavista/resultado_indicadores.md`, consultado no Supabase do cliente.

### O funil inteiro

| Etapa | Valor | Benchmark de mercado | Leitura |
|---|---|---|---|
| Leads injetados | 1.696 | — | importados em lote em 29/04 |
| Invites enviados | **663** | — | — |
| Invites aceitos | **220** | <20% ruim · 30-40% bom | **33,2% — bom** |
| First messages | 265 | — | — |
| Respostas | **20** | <5% ruim · 5-10% média | **7,5% — na média** |
| **Agendamentos** | **0** | — | **o funil morre aqui** |

### Aceitação por mês — a queda

| Mês | Enviados | Aceitos | Taxa |
|---|---|---|---|
| Fev/2026 | 7 | 6 | 85,7% |
| Mar/2026 | 203 | 117 | **57,6%** |
| Abr/2026 | 278 | 60 | **21,6%** |
| Mai/2026 (parcial) | 175 | 37 | 21,1% |

A taxa despencou de 57,6% para 21,6% **exatamente quando o volume foi ampliado** — ICP mais largo, afinidade média menor. É a lição mais transferível do projeto: em prospecção, volume e taxa de aceitação são trade-off, não somam.

### Onde a resposta acontece
| Touchpoint | Respostas |
|---|---|
| Após a primeira mensagem | **13 (65%)** |
| Após o follow-up | 5 |
| Após o breakup | 2 |

65% respondem à mensagem de abertura — o copy de abertura é o ponto mais alavancável da cadência inteira.

**Tempo até aceite:** média **2,8 dias** (máx. 28,8). Invite com mais de 7 dias sem aceite tem chance baixíssima de virar — dado que justifica prazo de expiração na fila.

> [!warning] Leitura honesta destes números
> **1. Zero agendamentos.** 663 invites, 220 aceites, 20 respostas, **nenhuma reunião marcada**. A engenharia do sistema é boa e as taxas de topo são defensáveis, mas o objetivo comercial não foi atingido no período medido. Isso precisa ser dito antes que um entrevistador pergunte.
>
> **2. O gargalo não é o que parece.** Aceitação em 33,2% é "bom" e resposta em 7,5% é "média". O buraco está entre **responder** e **agendar** — 20 conversas viraram zero reunião. Isso é problema de qualificação e de handoff, não de rate limiting nem de copy de invite.
>
> **3. Instrumentação quebrada, de novo.** O campo `Department` está **100% vazio** nas conexões aceitas, o que impede qualquer corte por área — justamente o corte que explicaria quais respostas valiam a pena. E `Invite_Sent` aceita texto não-timestamp (7 linhas com "Not possible"), obrigando filtro manual em toda query.

### O padrão que atravessa três clientes
> [!danger] Achado transversal
> **Ebramed:** campanha de 985 contatos disparada antes de os campos `fonte` e `respondeu` existirem.
> **Boavista:** `Department` 100% vazio, bloqueando o corte por área.
> **Farmly:** flag `status='replied'` nunca marcada — o relatório diria "0 respostas".
>
> Três clientes, o mesmo defeito de classe: **o sistema opera, mas a camada de medição não mede.** Em todos os três foi o Yan quem descobriu.
>
> Isso é competência (ele encontra instrumentação quebrada) **e** alerta (os sistemas sobem sem medição funcionando). Vale virar checklist: nenhum agente entra em produção sem o campo de resultado testado com dado real.

> [!question] Em aberto
> - A maioria dos workflows está inativa e só a persona "Marcelo" está ligada — projeto reduzido ou em transição?
> - A migração Sheets → Data Tables → Supabase foi concluída? Hoje há escrita em três lugares.
> - O MCP Server Ekyte foi abandonado ou é reaproveitável? É o item mais raro do seu portfólio inteiro.

<!-- fonte: leitura da instância n8n via MCP em 2026-08-29, somente leitura. Nenhuma credencial, URL de instância ou ID de tabela registrado neste vault. -->
