---
type: competencia
nivel: medio
tags: [competencia, metricas, dados, produto]
atualizado: 2026-08-31
---

# Análise de métricas e indicadores de produto

> Definir o que medir, medir contra benchmark, e dizer quando o número não presta.

## Provas
- Repositório de **padronização de métricas** dos agentes de IA, com definição canônica de tools, conceitos e métricas de SDR — documento principal para o time de dev.
- [[Boavista — BDR de LinkedIn com Fila por Score|Boavista]] — funil end-to-end com benchmark de mercado por etapa: aceitação 33,2% ("bom"), resposta 7,5% ("média"), **0 agendamentos**.
- [[Farmly — Máquina de Aquisição Outbound|Farmly]] — atingimento de meta, qualidade de base por canal, distribuição geográfica contra alvo, e ROI sobre MRR.
- **Notas de qualidade de dado dentro do relatório:** `created_at` que reflete importação em lote e não entrada orgânica; coluna que aceita texto não-timestamp; campo 100% vazio bloqueando um corte.

## Lacuna
As análises são descritivas. Sem teste A/B conduzido, sem coorte, sem significância — e sem nenhum caso em que uma decisão tenha sido tomada e o efeito medido depois.

## Como contar
"Levantei o funil end-to-end de um BDR contra benchmark de mercado e mostrei que o gargalo não estava onde todos olhavam: aceitação e resposta estavam na faixa boa, e mesmo assim o agendamento era zero."
