---
type: competencia
nivel: forte
tags: [competencia, n8n, automacao, integracao]
atualizado: 2026-08-31
---

# Automação de processo de negócio (n8n)

> Quatro sistemas em produção, ~2.260 nós, com os mesmos primitivos de confiabilidade aparecendo de forma independente.

## Provas
- **93 workflows** em 4 instâncias: [[Knewin — Nina, SDR de IA com Triagem de CRM|Knewin]] (34) · [[Boavista — BDR de LinkedIn com Fila por Score|Boavista]] (21) · [[Ebramed — Isabela, do diagnóstico à migração|Ebramed]] (20) · [[Farmly — Máquina de Aquisição Outbound|Farmly]] (18).
- **Cadência como máquina de estado persistida**, com data da próxima ação — nunca corrente de `Wait`. Sobrevive a restart e é inspecionável.
- **Idempotência antes de todo envio** (dedupe check + `already sent?`).
- **Rate limiting** com jitter no trigger, janela de horário e fila com estado.
- Error workflow global em todas as instâncias; tools de responsabilidade única (uma transição de estado por workflow).
- Migração de Google Sheets → n8n Data Tables → Supabase com escrita dupla, sem downtime.

## Lacuna
n8n é ferramenta de nicho. Sem evidência equivalente em orquestrador de mercado mais amplo (Airflow, Temporal, Step Functions) — o que importa para vaga internacional de engenharia de dados.

## Como contar
"Quatro sistemas de agentes em produção, ~2.260 nós. Em todos eles a cadência é máquina de estado persistida, não corrente de espera — porque corrente de espera não sobrevive a restart."
