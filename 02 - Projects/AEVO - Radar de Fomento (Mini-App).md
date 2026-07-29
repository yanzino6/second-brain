---
type: project
status: proposta (PRD v2 abr/2026 — aguarda aprovação de horas e Discovery)
tags: [projeto, aevo, produto, mini-app, fomento, lei-do-bem, prd]
company: "[[AEVO]]"
links: ["[[AEVO]]", "[[smartside.ai]]", "[[00 - MOC AEVO]]", "[[AEVO - Análise de Concorrente PierX]]", "[[AEVO - Lei do Bem e Ecossistema de Fomento]]"]
---

# AEVO — Radar de Fomento (Mini-App)

> **Missão:** *"Seus projetos de inovação já estão na AEVO. A gente acha o edital certo pra cada um deles."*
> Mini-App que monitora editais de fomento, cruza automaticamente com os projetos do gestor e notifica sobre oportunidades relevantes.

## Histórico dos documentos
| Doc | Data | Nota |
|---|---|---|
| `PRD_Innovation_Return_Management_AEVO` v1/v2 | 16/04/2026 | Escopo maior: **AEVO Tax** (Lei do Bem completa) + **AEVO Funding** — 248h |
| `PRD_Radar_Fomento_AEVO` v1/v2 | 16–21/04/2026 | Escopo reduzido e focado: radar + matching + *scoring* Lei do Bem |
| `Apresentacao_Radar_Fomento_AEVO` | 28/04/2026 | Deck de venda — assinado como **Triple AI** |

> O escopo evoluiu de *Innovation Return Management* (dois módulos pesados) para o **Radar de Fomento** como primeiro produto executável. A gestão completa de Lei do Bem saiu do MVP; ficou apenas o **indicador de aderência**.

## O problema
- Ecossistema brasileiro de fomento (FINEP, FAPESP, EMBRAPII, BNDES, CNPq, ANEEL, FAPEs estaduais, Grants.gov) disponibiliza bilhões em recursos **não-dilutivos**, mas a descoberta é fragmentada em dezenas de portais.
- Gestor com **30–40 projetos ativos** cruza projeto × edital "de cabeça" ou em planilha.
- **Ponto de saída da jornada:** quando o projeto avança para financiamento, o cliente sai da AEVO.
- **Argumento de renovação fraco:** "gerenciamos X projetos" vs. "X projetos + R$ Y em oportunidades identificadas".

## Oportunidade de mercado (deck abr/2026)
- **R$ 10,3 bi** disponíveis para fomento em 2026 (FINEP, evento Sorocaba mar/2026)
- **R$ 14,7 bi** de investimento público em inovação em 2025 — recorde (FINEP/MCTI)
- **~2%** das empresas elegíveis usam a Lei do Bem (MCTI nov/2025: 4.200 de ~194.000 em Lucro Real)

## Funcionalidades do MVP
1. **Radar de editais** — monitoramento contínuo, campos estruturados (órgão, tema, valor, prazo, instrumento, elegibilidade, localidade, público-alvo), busca com as **6 dimensões de filtro** espelhadas do PierX, favoritos. Onda 1: **10–15 órgãos prioritários** do Brasil.
2. **Importação de projetos** (Onda 1, standalone) — upload de Excel/PPTX/DOCX com extração e classificação automática; exportação manual da AEVO; cadastro manual.
3. **Matching automático e contínuo** — bidirecional (projeto → edital **e** edital → projeto), com *score* de aderência 0–100%. Critérios eliminatórios zeram o score.
4. **Alertas** — quando edital acima do *threshold* é detectado. Canal a definir (e-mail e/ou in-app).
5. **Dashboard / Pipeline de Oportunidades** — funil tipo CRM: Identificado → Em análise → Em preparação → Submetido → Resultado. Valor total em R$ por estágio.
6. **Scoring de aderência à Lei do Bem** — indicador Alta/Média/Baixa por projeto (ver seção abaixo).

## Scoring Lei do Bem — duas camadas
**Camada 1 — pré-requisitos da empresa (tenant, configurado uma vez):** regime de **Lucro Real**, regularidade fiscal (CND/CPEN), investimento em P&D no período. Se falha, todos os projetos ficam "Não elegível".
**Camada 2 — classificação do projeto:** avalia atributos contra as 3 categorias MCTI (Pesquisa Básica, Pesquisa Aplicada, Desenvolvimento Experimental). Sinais de aderência: criação de algo novo com incerteza tecnológica; área típica de P&D (engenharia, TIC, biotec, energia); objetivo de pesquisa/desenvolvimento vs. implantação de solução pronta.
**Output:** indicador + justificativa resumida + próximo passo sugerido ("consulte seu contador ou consultoria especializada").

> [!warning] Limite explícito
> O indicador é **triagem, não parecer fiscal**. O Mini-App indica potencial; não confirma elegibilidade.

## Diferenciais vs. [[AEVO - Análise de Concorrente PierX|PierX]]
| Dimensão | PierX | Mini-App AEVO |
|---|---|---|
| Cadastro de projetos | Usuário cadastra do zero | Já estão na AEVO (upload na Onda 1, API na Onda 2) |
| Direção do match | Projeto → edital, manual | Bidirecional, automático e contínuo |
| Ecossistema | Standalone | Integrado ao funil AEVO (ideias → projetos → editais) |
| Lei do Bem | Autodiagnóstico básico | Scoring de aderência por projeto |
| Infra de IA | Sem IA proprietária | Potencial uso da **SLM própria da AEVO** (R$ 17M FINEP) |
| Monetização | PLG → upsell consultivo | Módulo SaaS (escala sem serviço) |

> O diferencial **não é geográfico** (o PierX já cobre internacional) — é **estrutural**: os dados dos projetos já estão na plataforma.

## Impacto na jornada
`Ideação → Projetos → Portfólio → Execução` **→ Fomento → Lei do Bem → Dispêndios**
Efeitos: aumento de *switching cost* e retenção · *expansion revenue* (módulo contratado à parte) · argumento de renovação financeiro · sinergia com a SLM própria (tese de ecossistema sobre o investimento FINEP).

## Estimativa (versão Innovation Return Management — 248h)
| Fase | Escopo | Horas | Gate |
|---|---|---|---|
| 0 | Discovery — dados/APIs da AEVO, regulatório Lei do Bem/FormP&D, entrevistas com clientes piloto, stack | 48h | **GO / NO-GO** |
| 1 | AEVO Tax — motor de regras, classificação P&D, pesquisadores, dispêndios, evidências, cálculo fiscal, export FormP&D, frontend | 80h | Demo interna |
| 2 | AEVO Funding — ingestão, loaders, indexação, matching, scoring, alertas, frontend | 56h | Demo AEVO |
| 3 | Integração final — dashboard consolidado, fluxo entre módulos | 40h | — |
| 4 | Hardening — segurança, tenant, criptografia, residência BR, deploy, doc | 24h | **Aceite AEVO** |
| | **Total** | **248h** | ~2,5–3 meses a 100h/mês |

> Manutenção pós-deploy **não está** na estimativa. O radar e o export do FormP&D não são *build once* — fontes mudam, o governo atualiza portais.

## Arquitetura
- **Mini-App standalone**: deploy independente, banco próprio, **autenticação federada (SSO/OAuth)** com a AEVO. Não exige acesso ao codebase da AEVO. Alternativas (módulo embarcado, extensão) avaliadas como de baixa viabilidade para o MVP.
- **Onda 1 é 100% determinística — zero LLM.** Classificação por regras, matching por atributos, cálculos por fórmula. IA/embeddings é Onda 2.
- Infraestrutura proposta: **Azure, região Brazil South**.
- Segurança: AES-256 + TLS 1.2+, minimização de PII de pesquisadores (LGPD), segregação por tenant, log imutável com retenção de 5 anos (auditoria MCTI).

## Fora do escopo (Onda 2+)
Integração via API com a AEVO · gestão completa de Lei do Bem (pesquisadores, dispêndios detalhados, cálculo exato, FormP&D, evidências) · submissão automatizada ao MCTI · cobertura de 90+ fontes e internacional · matching por IA/embeddings · dashboard de ROI consolidado · expansão regulatória (Rota 2030, Lei de Informática) · playbooks setoriais.

## Métricas de sucesso
**Estratégicas:** valor em recursos mapeados (R$) · submissões originadas · % de clientes AEVO engajados · impacto em retenção (medir em 6 meses).
**Táticas:** 100+ editais ativos na Onda 1 · matches gerados/mês · tempo publicação → notificação **< 48h**.

## Premissas e riscos principais
- **P1** Onda 1 standalone, sem API da AEVO. **P2** sites de fomento acessíveis para scraping, PDFs com texto extraível. **P3** design system da AEVO disponibilizado (ou criado pela smartside a partir do site público). **P4** infra Azure Brazil South. **P5** API é Onda 2.
- Riscos: fontes mudam/bloqueiam (alta) · dados de projeto genéricos demais (média) · **manutenção contínua pós-deploy (certa)** · baixa adoção por ser plataforma separada (média).

## Alinhamento e próximos passos
- O roadmap completo de funding está sendo conduzido **internamente pela AEVO** ([[Bruno (AEVO)]] + consultor da Energisa). Este Mini-App é o primeiro produto executável dessa frente.
- **Oportunidade registrada:** painel unificado de gestão de Mini-Apps para o CS da AEVO ativar módulos por cliente — fora deste escopo.
- Passos: aprovação de direção → aprovação de horas da Fábrica → Discovery com gate Go/No-Go → execução do MVP.
- **Critério Go/No-Go:** (1) a AEVO tem ou pode disponibilizar API de leitura dos dados? (2) a dor é confirmada por ≥2 de 3–5 clientes entrevistados? Ambos sim = Go.

## Notas relacionadas
[[AEVO - Análise de Concorrente PierX]] · [[AEVO - Lei do Bem e Ecossistema de Fomento]] · [[AEVO - Fábrica de GenAI Apps]]
