---
type: competencia
nivel: medio
tags: [competencia, pytorch, cnn, saude]
atualizado: 2026-08-31
---

# Deep learning e visão computacional

> Transfer learning aplicado com rigor experimental — a métrica é confiável, e isso é mais raro que o modelo.

## Provas
- [[BreaKHis — Classificação de Câncer de Mama em Histopatologia|BreaKHis]] — 3 backbones (ResNet50, VGG16, MobileNetV2), **AUC 0,8965** em teste held-out, sensibilidade 0,90.
- **O teste bateu a validação cruzada** (0,838 vs 0,844) — evidência de que não houve overfit na seleção.
- [[PAD-UFES-20 — Classificação de Lesões de Pele com Classe Sintética|PAD-UFES-20]] — 7 classes, treino em duas fases (warmup com backbone congelado + finetune), class weights, seleção por F1-macro.
- **Geração de dado sintético:** classe `SEM` construída com 4 famílias de técnicas para o modelo não aprender um artefato único. Resultado: precisão **1,00**.
- Ensemble de 5 folds por média de probabilidade.

## Lacuna
Só classificação de imagem. Sem detecção, segmentação, NLP treinado do zero, nem deploy de modelo em produção. Os dois projetos são acadêmicos — nenhum modelo próprio foi para produção.

## Como contar
"Classificador de histopatologia com AUC 0,90 em teste held-out, usando validação cruzada agrupada por paciente para evitar vazamento — que é o erro clássico da área."
