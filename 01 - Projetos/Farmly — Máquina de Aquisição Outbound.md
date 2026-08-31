---
type: solucao
cliente: Farmly (café verde / especialidade)
papel: Engenheiro de IA — arquitetura e construção
stack: [n8n, Supabase, PostgreSQL, Google Places API, Firecrawl, LeadMagic, Google Vertex AI, OpenAI, Gmail API, WhatsApp Cloud API, Pipedrive]
escala: 18 workflows · ~400 nós · 4.211 empresas processadas
tags: [solucao, outbound, lead-generation, agente-ia, rag, multimodal, portfolio]
analisado: 2026-08-29
fonte: leitura direta da instância n8n via MCP (somente leitura)
---

# Farmly — Máquina de Aquisição Outbound

> Pipeline outbound completo, de descoberta de empresa até cadência multicanal com CRM sincronizado. **18 workflows, ~400 nós.** Numerado F1→F6 como um sistema, não como automações avulsas.
> Números reais da base: **4.211 empresas processadas · 2.498 enriquecidas (59%) · 1.713 descartadas com motivo registrado.**

## O problema

Vender café verde para torrefadoras artesanais exige achar empresas que (a) existem, (b) realmente torram no local, (c) compram grão verde e (d) têm porte que justifica a conversa. Nada disso está em base comprada. Está espalhado em Google Maps e no site de cada torrefação.

## Arquitetura — o pipeline F1→F6

```
F1  Descoberta          Google Places (paginado) → Firecrawl → classificação LLM
     ↓                  aprovado / rejeitado-com-motivo
F1R Reclassificação     reprocessa o que foi rejeitado quando o critério muda
     ↓
F2  Enriquecimento      LeadMagic (pessoas) → LLM de detecção de persona
     ↓
F3  BDR                 cadência multicanal e-mail + WhatsApp, sync Pipedrive
F6  Orquestrador        versão genérica do F3, roteia por canal disponível
     ↓
F4  Email Handling      tratamento de resposta
F5  SDR                 agente conversacional multimodal de qualificação
```

Todos os 18 workflows apontam para o mesmo **error workflow** e rodam em `America/Sao_Paulo`. Isso é configuração deliberada de operação, não default.

---

## F1 — Descoberta (48 nós)

**Paginação com cursor implementada à mão.** `Init Pagination` → `Build Places Request` → `HTTP Request` → `Accumulate Page` → `Has Next Page?` → volta ao build. Acumula páginas em memória de execução até a API parar de devolver cursor. Três `Schedule Trigger` independentes alimentam caminhos distintos.

**Dedupe antes de gastar dinheiro.** Antes de chamar Firecrawl (que custa por página), consulta o Supabase e só enriquece o que não existe. Ordem correta: a checagem barata vem antes da cara.

**Extração estruturada com schema fechado.** O Firecrawl é chamado com `formats: ["json"]` e um JSON Schema que restringe cada campo a enum:

```
buys_green_coffee : yes | no | unknown
roasts_in_house   : yes | no | unknown
segment           : specialty | commercial | blend | unknown
estimated_size    : micro | small | medium | large | unknown
offers_wholesale  : yes | no | unknown
```

Nada de texto livre nos campos que depois viram filtro. `unknown` é valor de primeira classe — o modelo tem para onde ir quando não sabe, em vez de inventar.

**A decisão automatizada é auditável.** O registro gravado carrega `classification_confidence` e `blacklist_reason`. Dá para responder "por que essa empresa foi descartada?" seis meses depois — e é por isso que existe o **F1R Reclassify**: quando o critério muda, o descarte é reprocessável em vez de perdido.

---

## F2 — Enriquecimento (20 nós)

Cron de 30 min → busca prospects pendentes → LeadMagic para achar pessoas → LLM de **detecção de persona** → `Validar Persona + Status` (código, não confiança cega no modelo) → grava.

Marca o lead como `enriching` **antes** de sair chamando API externa — trava de concorrência simples que impede dois ciclos do cron pegarem o mesmo lead.

Há um caminho para **Clay** inteiro construído e desativado (`Preparar Body Clay`, `Push to Clay`, `Webhook Clay Return`). Rota alternativa avaliada e desligada, preservada em vez de apagada.

---

## F3 — BDR: cadência multicanal (65 nós)

Duas fases documentadas em sticky note no próprio canvas:

**Fase A — entrada.** Pega leads enriquecidos → seleciona a caixa Gmail de origem → monta a copy do dia 1 → **valida se o número existe no WhatsApp antes de disparar** → se inválido, `Mark Phone Invalid` no banco e segue só por e-mail → cria a cadência → cria organização e negócio no Pipedrive → registra a atividade.

**Fase B — continuidade.** A cada 30 min: busca cadências ativas → `Filter Due Now` → `Dedup Check` + `Already Sent?` → monta a copy do dia → dispara no canal → registra no Supabase **e** como atividade no Pipedrive → `Calc Next Action` → atualiza a cadência. No último dia, move o negócio de etapa e encerra.

**Por que isso é bem feito:**
- A cadência é **máquina de estado com data da próxima ação**, não corrente de `Wait`. Sobrevive a restart, dá para inspecionar e dá para pausar.
- **Idempotência explícita** antes de todo envio — cadência que dispara duas vezes queima o lead.
- **Validação de canal antes do gasto** — o número inválido é detectado e marcado, não descoberto pelo erro.
- **Toda ação vira atividade no CRM.** O comercial vê a trilha inteira sem sair do Pipedrive.

---

## F6 — Orquestrador genérico (72 nós)

O F3 refatorado. Em vez de assumir e-mail + WhatsApp, começa com `Analyze Contact Channels` → `Switch Route`: decide a estratégia pelo que o lead **tem**. Sem canal nenhum → caminho de encaminhamento humano ou `discarded`.

É a generalização do caso particular — mesmo motor de cadência, entrada agnóstica de canal.

---

## F5 — SDR conversacional multimodal (105 nós)

O workflow mais complexo da instância.

**Ingestão multimodal com roteamento por tipo:**
| Entrada | Tratamento |
|---|---|
| Áudio | download → transcrição (Whisper) |
| Imagem | download → análise por visão + aviso "analisando imagem" ao lead |
| PDF / XLS / XLSX | `Extract from File` por extensão, com switch dedicado |
| Texto | direto |

**Buffer com debounce.** Agrega mensagens em rajada, `Remove Duplicates`, `Summarize`, `Wait`, e limpa o buffer — para o lead que manda cinco mensagens seguidas gerar **uma** chamada ao agente, não cinco.

**Memória e conhecimento.** Postgres Chat Memory por lead + Supabase Vector Store com embeddings OpenAI como base de conhecimento.

**Quatro tools de saída**, cada uma um workflow separado de ~5 nós: `sample_requested`, `interested_general`, `no_fit`, `schedule_followup`. O padrão de cada uma é idêntico e limpo: *chamada do agente → busca o lead → grava a qualificação → atualiza o status → notifica o humano*. Uma tool, uma transição de estado.

**`desativa fups por interação`** — cancela follow-ups agendados quando o lead responde. Detalhe pequeno cuja ausência faz o sistema cobrar quem já respondeu.

---

## Competências que este projeto comprova

| Competência | Evidência concreta |
|---|---|
| Arquitetura de sistema distribuído | 6 estágios desacoplados, comunicando por estado no banco, não por acoplamento direto |
| Integração de API | Google Places (paginada), Firecrawl, LeadMagic, Gmail, WhatsApp Cloud, Pipedrive, Vertex, OpenAI |
| Extração estruturada com LLM | JSON Schema com enums fechados; `unknown` como valor válido |
| Engenharia de dados | Dedupe antes de custo, trava de concorrência por status, descarte com motivo, reprocessamento |
| Design de agente | Multimodal, memória, RAG, tools de responsabilidade única |
| Confiabilidade | Error workflow global, idempotência antes de envio, validação de canal, máquina de estado persistida |
| Auditabilidade | `classification_confidence`, `blacklist_reason`, log duplo Supabase + CRM |

## Como contar isso

- **Recrutador (1 linha):** "Pipeline outbound em n8n que processou 4.211 empresas com enriquecimento por LLM e cadência multicanal sincronizada ao CRM — 59% de taxa de enriquecimento."
- **Cliente:** "Descubro empresas que ninguém tem em lista, qualifico automaticamente com critério auditável e coloco em cadência sem disparo duplicado."
- **Entrevista técnica:** puxe a paginação com cursor, o schema de enums e a máquina de estado da cadência. São três decisões defensáveis com trade-off claro.

---

## Resultados (coleta 2026-06-01)

> Fonte: `~/Documents/metricas-de-projetos-smarts-ai/farmly/resultados_farmly.md`, consultado no Supabase do cliente.
> **Contrato: R$ 3.897/mês (MRR).** BDR de prospecção ativa **internacional** no nicho de café especial — sem LinkedIn, cadência de 6 toques em 14 dias por e-mail + WhatsApp.

### Volume

| Métrica | Valor |
|---|---|
| Base total gerada | **2.350 leads** |
| Leads únicos abordados | **417** |
| Mensagens outbound | **2.129** (1.755 e-mail · 374 WhatsApp) |
| Abordagem multicanal | 127 leads receberam os dois canais |
| Maio/2026 (último mês fechado) | 401 leads · 1.403 e-mails · 236 WhatsApp |
| Abril/2026 | 149 leads · 350 e-mails · 138 WhatsApp |

### Conversão

| Métrica | Valor | Leitura |
|---|---|---|
| Meta mensal | 2.500 contatos | — |
| Atingimento em maio | **16,0%** | 401 de 2.500 |
| Atingimento em abril | 6,0% | 149 de 2.500 |
| Respostas | 11 inbound reais | **2,6%** sobre 417 abordados |
| Qualificados alta intenção | 2 | — |
| Amostras solicitadas | 2 | — |
| Handoff para SDR humano | **1** | — |

### Qualidade da base

- **16,0%** têm e-mail · **74,1%** têm telefone · **24,3% não têm nem e-mail nem telefone**
- Blacklist em 6,9% — abaixo do limite de 20%
- Geografia: **Europa 53,3% · EUA 41,0%** — mas a meta documentada era **75% EUA / 25% Europa**. A base está invertida em relação ao alvo.

### ROI declarado
Em maio a produtividade equivaleu a **1,00 BDR humano**, com **ROI estimado de 1,67×** sobre o MRR. Na meta de 2.500 abordagens/mês, o ROI projetado é **10,42×**.

> [!warning] Leitura honesta destes números
> **1. O sistema entregou 16% da meta.** Essa é a manchete, não o ROI. Um ROI de 1,67× sobre 16% de atingimento diz que a operação se paga rodando a um sexto da capacidade contratada — o que é bom sinal de eficiência unitária e mau sinal de execução de volume.
>
> **2. A projeção de 10,42× não está provada.** Ela assume 6× o volume mantendo a mesma taxa de resposta. Volume maior quase sempre significa ICP mais largo e resposta menor — foi exatamente o que aconteceu na [[Boavista — BDR de LinkedIn com Fila por Score|Boavista]], onde a aceitação caiu de 57,6% para 21,6% quando o volume subiu. Apresentar 10,42× como resultado seria frágil numa entrevista; apresentar como projeção **com essa ressalva** é forte.
>
> **3. A instrumentação de resposta estava quebrada.** A flag `status='replied'` nunca foi marcada — as 11 respostas só apareceram indo direto nas mensagens inbound. Sem essa investigação, o relatório teria dito "0 respostas".
>
> **4. 24,3% da base não tem canal nenhum.** Um quarto dos leads gerados é inalcançável. Isso é problema do F1/F2, e é onde estaria o ganho mais barato de volume.

### O que citar em entrevista
- ✅ "Construí e operei um BDR internacional sob contrato de R$ 3.897/mês, que processou 2.350 leads e disparou 2.129 mensagens em dois canais."
- ✅ "Descobri que a flag de resposta nunca era marcada e reconstruí a métrica a partir do inbound bruto."
- ⚠️ Não cite os 10,42× sem dizer que é projeção.

> [!question] Em aberto
> - Todos os 18 workflows estão **inativos** hoje — projeto encerrado, pausado, ou migrado? Muda o tempo verbal de tudo.
> - Por que o atingimento travou em 16% da meta? Limite técnico, base sem canal, ou operação pausada?
> - A flag `status='replied'` foi corrigida na origem ou o relatório seguiu contornando?
> - O caminho Clay foi desativado por custo, qualidade ou redundância?

<!-- fonte: leitura da instância n8n via MCP em 2026-08-29, somente leitura. Nenhuma credencial, URL de instância ou ID de projeto registrado neste vault. -->
