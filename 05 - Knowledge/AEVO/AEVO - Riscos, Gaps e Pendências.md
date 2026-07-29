---
type: knowledge
tags: [aevo, riscos, gaps, pendencias, seguranca]
company: "[[AEVO]]"
links: ["[[AEVO]]", "[[00 - MOC AEVO]]"]
---

# AEVO — Riscos, Gaps e Pendências

> Consolidado a partir da extração do Google Drive em **27/07/2026**. Itens marcados 🔴 exigem ação; 🟡 exigem confirmação.

> [!failure] BDR IA descontinuado (27/07/2026)
> As frentes de BDR IA Internacional e Brasil foram encerradas. Os itens **#2, #3 e #6** abaixo (governança semanal, revisão de sandbox, checkpoints ausentes) passam de risco ativo para **pendência histórica** — só voltam a importar se a prospecção for retomada. O item **#4** (faturamento fora do contrato) e a questão comercial do contrato de R$ 46.000 seguem em aberto — ver [[AEVO - Contrato e Condições Comerciais]].

## 🔴 Ação imediata

### 1. Credencial da OpenAI exposta em texto puro
O documento `Colinha aula 2` (pasta `AEVO (Consultoria)`, out/2025) contém um **token de API da OpenAI completo**, em documento do Google Drive. A chave não foi copiada para este vault.
**Ação:** revogar a chave e limpar o documento. Ver [[AEVO - Consultoria e Capacitação]].

### 2. Planilha de governança vazia — histórico (frente descontinuada)
`AEVO_Governanca.xlsx` (mar/2026) tinha toda a estrutura de acompanhamento semanal montada — perfis Rafael e Beatriz, 4 semanas de fevereiro — e **nenhuma linha preenchida**. Todos os indicadores zerados.
Era risco direto de renovação da frente de BDR; **BDR IA foi descontinuado em 27/07/2026**, então o item não exige mais ação — mantido como registro. Ver [[AEVO - Métricas e Metas de Prospecção]].

### 3. Documento de Sandbox com revisão vencida — histórico (frente descontinuada)
O [[AEVO - Processo de Sandbox (BDR AI)]] v1.0 (fev/2026) determinava revisão **a cada 90 dias ou após incidente**. Estava ~3 ciclos atrasado quando a frente de BDR foi descontinuada (27/07/2026) — só volta a valer se a prospecção for retomada.

## 🟡 Confirmar com o time

### 4. Escopos faturados fora do contrato conhecido
Existem NFSe separadas de **AEVO BDR** (fev, mar/2026), **AEVO Consultoria** (abr/2026) e **AEVO PETROS** (jun/2026). O único contrato no Drive é o de R$ 46.000 para ABM/GTM Europa.
**Confirmar:** há aditivos ou contratos paralelos? Onde estão? Ver [[AEVO - Contrato e Condições Comerciais]].

### 5. Campos do contrato em branco
No instrumento assinado, os campos de **Preposto da Contratante** (nome, e-mail, cargo) estão vazios. O valor por extenso ("dez mil reais" para R$ 46.000) e o número de parcelas ("12 (seis)") estão grafados errado.

### 6. Checkpoints ausentes — histórico (frente descontinuada)
Só os checkpoints **2º** (25/11/2025) e **12º** (27/02/2026) estavam na pasta — e o 12º é atalho sem conteúdo acessível. Do 3º ao 11º e todos após fevereiro ficaram fora do Drive. Com o BDR IA descontinuado (27/07/2026), recuperar esses checkpoints deixa de ser prioridade — só relevante para reconstrução histórica.

### 7. Papéis ambíguos no lado AEVO
- **[[Richa]]** é descrito como *CEO* no processo de sandbox, mas aparece nas linhas de *Biz Dev/Sales* e *AE 1* no plano de GTM.
- **Alex** é tratado como *CEO* no plano da Campanha GenAI Apps.
Provável que sejam papéis em escopos distintos (AEVO Internacional × AEVO Brasil), mas **não está documentado**.

### 8. Números institucionais inconsistentes
Slides da AEVO alternam entre 200 e 170 clientes, 500k e 450k usuários, e citam separadamente "300 clientes / 2.000 projetos / 17 anos / 15 países". Definir a versão oficial antes de usar em material.

### 9. Frente de consultoria com escopo desconhecido
Sem ementa, turmas, cronograma ou contrato. Só sobrou material de "aula 2" e diagramas de MCP.

## Riscos herdados dos documentos de produto

### Radar de Fomento
| Risco | Prob. | Impacto | Mitigação registrada |
|---|---|---|---|
| API da AEVO não existe ou é insuficiente | Média | **Alto** | Primeira entrega da Discovery; se inexistente, reavaliar viabilidade |
| Dados de projeto menos estruturados que o esperado | Média | **Alto** | Auditoria com 3–5 clientes na Discovery |
| **Manutenção contínua do radar pós-deploy** | **Certa** | Médio | Prever horas recorrentes de Fábrica, fora da estimativa |
| Fontes de editais mudam ou bloqueiam scraping | Alta | Médio | Loaders isolados, monitoramento de quebras, fallback manual |
| Portal MCTI muda o formato do FormP&D | Alta | Médio | Campos do export como parâmetros configuráveis |
| Regulação da Lei do Bem muda | Baixa-Média | **Alto** | Alíquotas e critérios como parâmetros, não hardcoded |
| Segurança insuficiente para dados fiscais | Média | **Alto** | Banco próprio, região BR, AES-256, segregação por tenant |
| Baixa adoção por ser plataforma separada | Média | Médio | Design system AEVO + autenticação integrada |

**Premissa de dados — níveis de confiança (não validados com o time técnico da AEVO):**
Projetos (nome, área, status) = **Alta** · Colaboradores vinculados = Média-Alta · Horas por colaborador/projeto = Média · Dispêndios por projeto = **Baixa-Média** (pode estar no ERP) · TRL e natureza P&D = **Baixa** · Regime tributário = **Baixa**.

### WhatsApp / Ideias
Perda de contexto em conversas longas (**alto**) · formulários complexos em conversa (**alto**) · rate limiting da API WhatsApp (**alto**) · qualidade de transcrição · latência acumulada · prompts das IAs AEVO possivelmente não documentados.

## Risco de modelo de valor
O cenário ilustrativo de **~R$ 1,15M/ano** de ganho incremental no PRD tem **4 de 5 variáveis marcadas como premissa não validada**. Não usar como promessa comercial sem a ressalva — ver [[AEVO - Lei do Bem e Ecossistema de Fomento]].

## Notas relacionadas
[[00 - MOC AEVO]] · [[AEVO - Governança e Rituais]] · [[AEVO - Processo de Sandbox (BDR AI)]]
