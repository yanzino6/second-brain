---
type: knowledge
tags: [aevo, lei-do-bem, fomento, editais, fiscal, mcti, regulatorio]
company: "[[AEVO]]"
links: ["[[AEVO]]", "[[00 - MOC AEVO]]", "[[AEVO - Radar de Fomento (Mini-App)]]", "[[AEVO - Análise de Concorrente PierX]]"]
---

# AEVO — Lei do Bem e Ecossistema de Fomento

> Base regulatória e de mercado levantada para o [[AEVO - Radar de Fomento (Mini-App)]]. Conhecimento **específico deste cliente** — não misturar com outros compartimentos.

## Alavanca 1 — Lei do Bem (incentivo fiscal)
- **Base legal:** Lei 11.196/2005.
- **Benefício:** dedução adicional de **60% a 100%** dos dispêndios em P&D da base de cálculo de **IRPJ e CSLL** → retorno efetivo de **20,4% a 34%** sobre o investimento em P&D.
- **Elegibilidade da empresa:** regime de **Lucro Real** (não Simples, não Lucro Presumido) · regularidade fiscal (**CND ou CPEN** junto à Receita Federal) · investimento em P&D no período.
- **Natureza:** benefício **automático** — não depende de aprovação prévia, não tem prazo, não tem submissão competitiva. Depende de **gestão rigorosa de evidências** e da submissão anual do **FormP&D ao MCTI**.
- **Retenção de documentação:** trilha auditável pelo MCTI por **5 anos**.

### As 3 categorias elegíveis do MCTI
| Categoria | Definição simplificada |
|---|---|
| **Pesquisa Básica** | Trabalho experimental ou teórico para adquirir novos conhecimentos, sem aplicação prática prevista |
| **Pesquisa Aplicada** | Trabalho original para adquirir novos conhecimentos com objetivo prático determinado |
| **Desenvolvimento Experimental** | Trabalho sistemático usando conhecimentos existentes para criar novos produtos, processos ou sistemas, ou melhorar os existentes |

**Sinais de aderência usados no scoring:** criação de algo novo (produto, processo, sistema) com **incerteza tecnológica** · área tipicamente de P&D (engenharia, TIC, biotecnologia, energia) · objetivo que indica pesquisa/desenvolvimento **vs.** implantação de solução pronta.

### Categorias fiscais de dispêndio
RH · materiais · serviços de terceiros · equipamentos.
Variáveis do cálculo: tipo de dedução · patente sim/não · incremento de pesquisadores.
Campos adicionais necessários por pesquisador para o FormP&D: **titulação, área CNPq, dedicação percentual** — campos que provavelmente não existem na plataforma AEVO.

## Alavanca 2 — Editais de fomento (recursos não-dilutivos)
### Fontes prioritárias da Onda 1 (10–15 órgãos)
| Órgão | Relevância | Complexidade de ingestão |
|---|---|---|
| **FINEP** | Maior agência de fomento à inovação do Brasil | Média |
| **EMBRAPII** | Parcerias com ICTs, alto valor por projeto | Baixa-Média |
| **FAPESP** | Maior FAPE do país, editais frequentes | Média |
| **BNDES** | Linhas de financiamento para inovação | Média |
| **CNPq** | Bolsas e editais de pesquisa | Média |
| **ANEEL** | **P&D regulatório** — casa com o perfil dos clientes AEVO | Média |
| 3–5 FAPEs estaduais | Complemento regional | Variável |

Onda 2: expansão internacional (Grants.gov etc.) e cobertura de 90+ órgãos.

### Instrumentos de fomento (taxonomia)
Financiamento não-reembolsável · bolsas · prêmios de inovação · financiamento reembolsável · fundo de investimentos · edital privado.

## Números de mercado
| Dado | Valor | Fonte |
|---|---|---|
| Disponível para fomento em 2026 | **R$ 10,3 bi** | FINEP, evento Sorocaba, mar/2026 |
| Investimento público em inovação em 2025 (recorde) | **R$ 14,7 bi** | FINEP/MCTI, mai/2025 |
| Empresas em Lucro Real no Brasil | **~194.000** | MCTI |
| Empresas que usam a Lei do Bem | **~4.200 (~2%)** | MCTI, nov/2025, ano-base 2024 |
| Recursos mapeados pelo radar da PierX | **+R$ 19 bi** | PierX |

> O PRD v2 (abr/2026) cita "apenas ~3.500 usam Lei do Bem" enquanto o deck (28/04) cita 4.200. Usar **4.200** — é o dado mais recente e com ano-base explícito.

## Modelo de valor ilustrativo (PRD — premissas NÃO validadas)
| Variável | Valor | Nota |
|---|---|---|
| Investimento anual em P&D | R$ 25M | [P] Hipotético |
| % elegível para Lei do Bem | 50% | [P] Depende da natureza dos projetos |
| Alíquota efetiva (regime base) | **20,4%** | Verificado em lei |
| Taxa de captura atual | 40% | [P] Estimativa — **a mais incerta** |
| Taxa de captura com solução | 85% | [P] Estimativa otimista |
| **Ganho incremental estimado** | **~R$ 1,15M/ano** | Exercício ilustrativo |

> [!warning] Não usar como promessa comercial
> Quatro das cinco variáveis são estimativas não validadas. O próprio documento marca com `[P]`. Levar esse número a cliente sem a ressalva viola o princípio de Transparência do [[SOUL]].

## Riscos regulatórios registrados
- **Portal MCTI muda o formato do FormP&D** (prob. alta) → campos do export como parâmetros configuráveis, nunca hardcoded.
- **Regulação da Lei do Bem muda** (prob. baixa-média, impacto alto) → alíquotas e critérios como parâmetros.
- **Fontes de editais bloqueiam scraping** (prob. alta) → loaders isolados, monitoramento de quebras, fallback manual.

## Contexto interno da AEVO
O mapeamento completo do roadmap de funding é conduzido **internamente pela AEVO** por [[Bruno (AEVO)]] + um consultor da **Energisa**. O Mini-App é o primeiro produto executável dessa frente e seus dados de uso devem alimentar a priorização do roadmap.

## Notas relacionadas
[[AEVO - Radar de Fomento (Mini-App)]] · [[AEVO - Análise de Concorrente PierX]] · [[AEVO - Glossário]]
