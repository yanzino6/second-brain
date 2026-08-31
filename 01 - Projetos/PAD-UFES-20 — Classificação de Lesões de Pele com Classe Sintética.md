---
type: projeto-academico
contexto: Inteligência Computacional em Saúde — UFES (atividade 3)
papel: autor
stack: [Python, PyTorch, torchvision, scikit-learn, ResNet18/34/50, Pillow]
dataset: PAD-UFES-20 — 544 pacientes · 6 classes clínicas + 1 sintética
tags: [academico, deep-learning, visao-computacional, saude, dermatologia, dados-sinteticos, portfolio]
codigo: ativ3-ias-main/
analisado: 2026-08-31
---

# PAD-UFES-20 — Classificação de Lesões de Pele com Classe Sintética

> Classificador de 7 classes para lesões de pele: as 6 categorias diagnósticas do PAD-UFES-20 (BCC, SCC, ACK, SEK, NEV, MEL) **mais uma classe `SEM`** construída sinteticamente para o caso "não é foto de lesão".
> Usa **apenas a imagem** — nenhum metadado clínico.

## A ideia que diferencia o projeto

Um classificador de 6 classes treinado só em lesões **sempre devolve uma lesão**. Aponte a câmera para o dedo, para a mesa ou tire a foto tremida, e ele responde "BCC com 80% de confiança". Em produto real isso é o modo de falha mais provável e o mais perigoso.

A solução foi criar uma **7ª classe `SEM`** (sem lesão / foto errada), gerada a partir do próprio dataset por **quatro famílias de técnicas**:

| Técnica | O que gera |
|---|---|
| `t_pele_saudavel` | Recorte dos cantos da imagem — pele sem lesão |
| `t_oclusao` | Dedo na lente, obstrução parcial |
| `t_foto_errada` | Corrupções fortes: blur, superexposição, ruído, zoom-out, rotação |
| `t_combinacao` | Composição das anteriores |

**Por que quatro famílias e não uma:** com uma técnica só, o modelo aprende a detectar *aquele artefato específico* em vez do conceito "isto não é uma lesão avaliável". A diversidade é o que força a generalização. 500 amostras geradas (`NUM_SEM = 500`).

Isso é desenho de dado, não só de modelo — e é raro num trabalho de disciplina.

---

## Anti-vazamento, de novo

544 pacientes, vários com múltiplas fotos da mesma lesão. Split por imagem colocaria fotos quase idênticas em treino e teste.

**`StratifiedGroupKFold` em dois estágios**, agrupando por paciente e estratificando por classe, gerando 70/15/15:
1. Estágio 1: separa o teste do restante.
2. Estágio 2: separa validação do treino, com a fração recalculada em relação ao *trainval*.

Detalhes que mostram cuidado:
- **`patient_id` e `lesion_id` são usados só para dividir, nunca como entrada do modelo** — está escrito no código.
- Há **fallback documentado** para `train_test_split` estratificado quando não existe `patient_id`, com o risco de leakage anotado explicitamente no docstring. Degradar com aviso, em vez de degradar em silêncio.
- Papéis separados: **validação** seleciona o melhor modelo (F1-macro) e ajusta o LR; **teste** é avaliado uma única vez no fim, recarregando o melhor checkpoint.

## Treino

Estratégia em **duas fases**, o padrão correto para transfer learning com pouco dado:

| Fase | Épocas | O que treina | LR |
|---|---|---|---|
| 1 — warmup | 3 | Só a cabeça de classificação (backbone congelado) | `1e-3` |
| 2 — finetune | 17 | Rede inteira | `3e-4` |

Backbone selecionável por variável de ambiente (`resnet18` / `resnet34` / `resnet50`; padrão `resnet34`). Dropout 0,4 · weight decay `1e-4` · batch 32 · seed 42 fixa.

**Desbalanceamento severo** — MEL ~52 contra BCC ~845 — tratado com class weights na loss, e **seleção do melhor modelo por F1-macro**, não por acurácia. Com essa distribuição, acurácia premiaria ignorar as classes raras.

`config.py` centraliza caminhos, mapa de classes, normalização e hiperparâmetros, e é importado **tanto pelo treino quanto pela inferência** — garantindo que a normalização usada no treino seja exatamente a da inferência. É a fonte clássica de bug silencioso em produção, resolvida por construção.

`inferencia.py` é autossuficiente: lê `entrada.csv` (id, path) e grava `resultado.csv`.

---

## Resultados (teste held-out, 400 imagens)

**Acurácia 74,8% · F1-macro 0,697 · Balanced accuracy 0,687**

| Classe | Precisão | Recall | F1 | N |
|---|---|---|---|---|
| **SEM** | **1,00** | 0,90 | **0,95** | 72 |
| NEV | 0,85 | 0,80 | 0,82 | 35 |
| SEK | 0,79 | 0,76 | 0,78 | 34 |
| ACK | 0,72 | 0,83 | 0,77 | 104 |
| BCC | 0,79 | 0,69 | 0,73 | 121 |
| MEL | 0,67 | 0,57 | 0,62 | 7 |
| **SCC** | 0,18 | 0,26 | **0,21** | 27 |

**A hipótese central se confirmou:** `SEM` é a melhor classe do modelo — **precisão 1,00**, F1 0,95. Nenhuma imagem de lesão real foi classificada como "sem lesão". A classe sintética funcionou.

**O fracasso é o SCC** (F1 0,21). A matriz de confusão mostra por quê: dos 27 SCC, **14 viraram BCC** e 6 viraram ACK. São três lesões que se parecem clinicamente — e com só 27 exemplos de teste e poucos no treino, o modelo não aprendeu a fronteira.

**MEL tem N=7 no teste.** F1 0,62 sobre 7 amostras não sustenta conclusão nenhuma — é ruído. Vale dizer isso em voz alta, porque é exatamente o número que um candidato menos cuidadoso apresentaria como resultado.

> [!note] O que eu faria diferente
> As duas classes fracas (SCC, MEL) são as raras. O caminho seria oversampling dirigido ou augmentation específica para elas, e reportar intervalo de confiança em vez de ponto para classes com N < 30.

---

## Competências que este projeto comprova

| Competência | Evidência |
|---|---|
| **Engenharia de dados sintéticos** | 4 famílias de técnicas para uma classe negativa, com racional anti-atalho |
| Pensamento de produto em ML | Antecipou o modo de falha real (foto que não é lesão) e resolveu no dado |
| Rigor experimental | Split agrupado em dois estágios, fallback com risco documentado, teste único |
| Transfer learning | Warmup + finetune com LRs separados, backbone parametrizável |
| Configuração como código | `config.py` compartilhado entre treino e inferência |
| **Honestidade de resultado** | Reporta F1 0,21 do SCC e o N=7 do MEL em vez de esconder na média |

## Como contar isso

- **Recrutador:** "Classificador dermatológico de 7 classes com classe sintética 'sem lesão' para rejeitar entradas inválidas — precisão 1,00 nessa classe."
- **Entrevista técnica:** o gancho é a classe `SEM`. Explique por que um classificador fechado é perigoso em produto, como você gerou o negativo e por que precisou de 4 técnicas em vez de 1. Depois, entregue o SCC como o que não funcionou e por quê — isso vale mais que o acerto.

Relacionado: [[BreaKHis — Classificação de Câncer de Mama em Histopatologia]] — mesma disciplina de split por paciente.

<!-- fonte: código e logs em ativ3-ias-main/, analisados em 2026-08-31 -->
