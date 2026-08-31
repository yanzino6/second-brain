---
type: projeto-academico
contexto: Inteligência Computacional em Saúde — UFES, 2026/1 (projeto final)
papel: autor
stack: [Python, PyTorch, torchvision, scikit-learn, ResNet50, VGG16, MobileNetV2]
dataset: BreaKHis — 7.909 imagens · 82 pacientes · 4 magnificações
tags: [academico, deep-learning, visao-computacional, saude, transfer-learning, validacao-cruzada, portfolio]
codigo: trab-IAS-main/
analisado: 2026-08-31
---

# BreaKHis — Classificação de Câncer de Mama em Histopatologia

> Classificação binária (benigno × maligno) de lâminas histopatológicas com *transfer learning*. Projeto final da disciplina de Inteligência Computacional em Saúde, UFES 2026/1.
> O que o torna citável não é o modelo — é a **metodologia clinicamente honesta**.

## O problema

O diagnóstico definitivo de câncer de mama depende da análise de lâminas por um patologista: tarefa demorada e com variabilidade entre observadores. Um classificador serve como apoio à decisão, triando lâminas e destacando casos suspeitos.

**Dataset:** [BreaKHis](https://web.inf.ufpr.br/vri/databases/breast-cancer-histopathological-database-breakhis/) — 7.909 imagens de **82 pacientes**, em 4 magnificações (40X, 100X, 200X, 400X).

---

## A decisão que define o projeto: split por paciente

Cada paciente tem várias imagens — 4 magnificações × múltiplos campos. **Um split aleatório por imagem colocaria o mesmo paciente em treino e teste**, e as métricas inflariam: o modelo estaria reconhecendo o paciente, não a patologia.

O pipeline evita isso em dois níveis:

1. **15% dos pacientes** separados como conjunto de teste isolado — pacientes inteiros, não imagens.
2. No restante, **`StratifiedGroupKFold` (5 folds)**, agrupando por paciente e estratificando por classe.

O identificador do paciente é extraído do nome do arquivo (`SOB_M_DC-14-2523-40-001.png` → paciente `SOB_M_DC-14-2523`). Nenhum paciente aparece em mais de uma partição.

> Esse é *o* erro clássico em machine learning para imagem médica, e é o que separa um número publicável de um número inflado. Aparece em papers revisados por pares até hoje.

## As outras decisões metodológicas

| Decisão | Racional declarado |
|---|---|
| **Transfer learning** com backbones ImageNet, camadas convolutivas congeladas | Só o classificador final é treinado — dataset pequeno demais para treinar do zero |
| **Class weights** na `CrossEntropyLoss` | Base é ~31% benigno / 69% maligno; sem peso, o modelo aprende a chutar "maligno" |
| **Augmentation** só com flips e rotação | Justificado explicitamente: **lâmina não tem orientação canônica**, então a transformação preserva o rótulo |
| **Early stopping** pela perda de validação | Evita memorizar |
| **Ensemble dos 5 folds** (média das probabilidades) | O modelo final não é um fold sortudo |
| **Teste avaliado uma única vez** | Held-out real, não conjunto de ajuste disfarçado |
| Métricas de **sensibilidade, especificidade e AUC** além de acurácia | Acurácia sozinha é inútil em base desbalanceada e em contexto clínico |

---

## Resultados

| Métrica | VGG16 (CV) | **VGG16 (teste)** | ResNet50 (CV) | ResNet50 (teste) |
|---|---|---|---|---|
| Acurácia | 0,8442 | **0,8381** | 0,8011 | 0,7792 |
| Sensibilidade (maligno) | 0,8849 | **0,9006** | 0,8596 | 0,8261 |
| Especificidade (benigno) | 0,7453 | **0,7500** | 0,6593 | 0,7133 |
| F1-macro | 0,8129 | **0,8302** | 0,7595 | 0,7713 |
| AUC-ROC | 0,8975 | **0,8965** | 0,8183 | 0,8383 |

**Duas leituras que valem em entrevista:**

1. **O teste bate a validação cruzada** (0,838 vs 0,844 em acurácia; 0,8965 vs 0,8975 em AUC). Isso é evidência de que não houve overfit na seleção de modelo — o pipeline anti-vazamento funcionou.
2. **VGG16 supera ResNet50 em todas as métricas**, contrariando a intuição de "rede mais nova é melhor". Com as convoluções congeladas, o que importa é a qualidade das features do ImageNet para esse domínio, não a profundidade.

**Perfil de erro:** sensibilidade (0,90) bem acima da especificidade (0,75). Para triagem oncológica esse é o trade-off **certo** — falso positivo custa uma segunda leitura, falso negativo custa um diagnóstico perdido. Vale saber dizer que a escolha foi consciente.

**Análise por magnificação** (VGG16, teste):

| Mag | N | Acurácia | Sensib. | Especif. |
|---|---|---|---|---|
| 40X | 347 | 0,8012 | 0,9031 | 0,6689 |
| 100X | 372 | **0,8683** | 0,9067 | 0,8095 |
| 200X | 348 | 0,8391 | 0,8696 | 0,7943 |
| 400X | 310 | 0,8419 | 0,9266 | 0,7293 |

100X é o melhor ponto de operação; 40X é o pior, com especificidade despencando para 0,67 — em baixa magnificação falta detalhe celular para descartar benigno com segurança.

---

## Competências que este projeto comprova

| Competência | Evidência |
|---|---|
| Deep learning aplicado | Transfer learning com 3 backbones, PyTorch, treino e avaliação completos |
| **Rigor experimental** | Split agrupado por paciente em dois níveis, teste avaliado uma única vez |
| Estatística de avaliação | Média ± desvio por fold, matriz de confusão, curva ROC, estratificação por magnificação |
| Tratamento de desbalanceamento | Class weights derivados da frequência |
| Leitura de domínio | Métricas clínicas e trade-off sensibilidade/especificidade justificado |
| Reprodutibilidade | README com passo a passo, `requirements.txt`, caminho de dados configurável |

## Como contar isso

- **Recrutador:** "Classificador de histopatologia mamária com AUC 0,90 em teste held-out, usando validação cruzada agrupada por paciente para evitar vazamento."
- **Entrevista técnica:** o gancho é o split. Explique por que o split por imagem infla a métrica, e por que o teste ter batido a CV é a prova de que o pipeline estava certo.

Relacionado: [[PAD-UFES-20 — Classificação de Lesões de Pele com Classe Sintética]] — mesmo cuidado anti-vazamento, problema multiclasse.

<!-- fonte: código e relatórios em trab-IAS-main/, analisados em 2026-08-31 -->
