---
type: competencia
nivel: forte
tags: [competencia, teste, qa, ci]
atualizado: 2026-08-31
---

# Engenharia de teste automatizado

> A competência mais bem provada do acervo — três evidências independentes, em três contextos diferentes.

## Provas
- [[Ebramed — Isabela, do diagnóstico à migração|Ebramed]] — harness de **429 linhas**, Node 18+, **zero dependências**, com códigos de saída distintos (`0` ok · `1` falha · `2` config · `3` erro) para pendurar em CI ou cron. Configuração por variável de ambiente, casos agrupados por domínio.
- [[Ebramed — Isabela, do diagnóstico à migração|Ebramed]] — **1.049 linhas** de documentação de teste: matriz de casos de borda com taxonomia de severidade **S1–S4** ancorada em impacto de negócio, roteiros conversacionais e payloads de integração.
- **SmartSide CRM** — **5.434 linhas de SQL de teste de RLS** em 8 arquivos, cobrindo permissões, campanhas, contatos, funis, mensagens e dashboard.
- [[BreaKHis — Classificação de Câncer de Mama em Histopatologia|BreaKHis]] — validação cruzada agrupada por paciente, conjunto de teste avaliado uma única vez.

## Lacuna
Nenhum teste em **TypeScript/JavaScript de frontend** (Jest, Vitest, Playwright). A cobertura é de backend, SQL e script. Numa vaga de dev full-stack isso aparece.

## Como contar
"Escrevi um harness de teste de 429 linhas sem dependência nenhuma, com exit codes para CI, e 5.434 linhas de teste de RLS em SQL. Teste para mim não é cobertura, é prova de que a regra vale."
