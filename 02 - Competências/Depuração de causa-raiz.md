---
type: competencia
nivel: forte
tags: [competencia, debug, producao]
atualizado: 2026-08-31
---

# Depuração de causa-raiz

> Achar a origem em vez de tratar sintoma, com evidência de runtime — não leitura de código no papel.

## Provas
- [[Ebramed — Isabela, do diagnóstico à migração|Ebramed]] — revisão de **420 linhas** sobre 5 workflows de 121+ nós. Metodologia declarada **antes** dos achados: `[PROVADO]` (log real, HTTP medido, SQL) vs `[ANÁLISE]` (leitura estática).
- **A causa-raiz:** os nós liam `body.chat.phone`, campo inexistente no payload do provedor. Telefone vazio → sessionKey vazia → **todos os leads compartilhando a mesma memória**. **Uma causa explicando quatro sintomas.**
- **18 achados** classificados em P0/P1/P2, incluindo os que apontavam para trabalho próprio.
- [[Farmly — Máquina de Aquisição Outbound|Farmly]] — descobriu que a flag `status='replied'` nunca era marcada; reconstruiu a métrica a partir do inbound bruto.

## Lacuna
Nenhuma. É a competência mais forte do acervo.

## Como contar
"Achei em produção a causa que fazia todos os leads compartilharem a mesma sessão de conversa — e provei com o payload real capturado do webhook, não com leitura de código."
