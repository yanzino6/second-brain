---
type: competencia
nivel: forte
tags: [competencia, estatistica, avaliacao, ml]
atualizado: 2026-08-31
---

# Rigor experimental e avaliação

> Saber quando um número é confiável — e dizer quando não é.

## Provas
- **Split agrupado por paciente nos dois projetos acadêmicos** (`StratifiedGroupKFold`), evitando o vazamento que infla métrica em imagem médica. É *o* erro clássico da área.
- [[PAD-UFES-20 — Classificação de Lesões de Pele com Classe Sintética|PAD-UFES-20]] — fallback documentado com o risco de leakage anotado no docstring. Degradar com aviso, não em silêncio.
- Papéis separados: validação seleciona o modelo, teste é avaliado **uma única vez**.
- **Reporta o que falhou:** SCC com F1 0,21 e MEL com N=7 no teste, explicitamente marcado como insuficiente para conclusão.
- Métricas escolhidas pelo domínio: sensibilidade, especificidade e AUC além de acurácia; F1-macro como critério de seleção em base desbalanceada.

## Lacuna
Sem intervalo de confiança nem teste de significância. As comparações entre modelos são por ponto, não por diferença estatisticamente sustentada.

## Como contar
"Reporto N pequeno como N pequeno. O F1 de 0,62 daquela classe tinha 7 amostras de teste — não sustenta conclusão, e está escrito no relatório."
