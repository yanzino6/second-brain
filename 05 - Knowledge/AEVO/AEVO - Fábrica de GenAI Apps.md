---
type: knowledge
tags: [aevo, fabrica, genai-apps, modelo-entrega, horas, mini-app, extension]
company: "[[AEVO]]"
links: ["[[AEVO]]", "[[00 - MOC AEVO]]", "[[AEVO - Radar de Fomento (Mini-App)]]", "[[AEVO - Envio de Ideias por WhatsApp (Extension)]]"]
---

# AEVO — Fábrica de GenAI Apps

> Modelo de entrega usado pela smartside/Triple AI na frente de **produto** da conta AEVO. Difere do AaaS dos agentes de prospecção: aqui a smartside opera como **fábrica de software por alocação de horas**.

## Como funciona
- **Capacidade:** **100 horas/mês** de Fábrica.
- **Unidade de escopo:** cada produto vira um documento (PRD ou TDD) com **estimativa de horas por fase** e **gates** entre fases.
- **Aprovação:** a AEVO valida o escopo e **aprova a alocação de horas** antes do início.
- **Fase 0 sempre é Discovery**, com gate **Go/No-Go** — nenhuma fase de build começa sem ele.

## Taxonomia de produto da AEVO
| Formato | Definição | Exemplo |
|---|---|---|
| **Mini-App** | Produto standalone, deploy independente, banco próprio, autenticação federada com a AEVO. Não exige acesso ao codebase | [[AEVO - Radar de Fomento (Mini-App)]] |
| **Extension** | Estende a plataforma via API, sem banco próprio | [[AEVO - Envio de Ideias por WhatsApp (Extension)]] |
| **Módulo embarcado** | Nativo no core. Avaliado e **descartado** para MVP: exige acesso ao codebase, alinhamento de squad e release compartilhado | — |

## Portfólio estimado até abr/2026
| Produto | Horas | Prazo | Formato de entrada | Status |
|---|---|---|---|---|
| Innovation Return Management (AEVO Tax + Funding) | 248h | ~2,5–3 meses | Proposta própria | Reduzido → virou Radar de Fomento |
| Radar de Fomento | (deriva das 248h) | — | Proposta própria | Aguarda aprovação de horas |
| Envio de Ideias por WhatsApp | **216h** | ~2 meses | **PRD Ready** (recebido da [[Duda (AEVO)]]) | TDD v1 pronto |

## Padrões de engenharia adotados
- **Harness × Tool × Prompt** — classificação explícita de cada funcionalidade:
  - *Harness* = execução determinística, regra inviolável, acontece sempre (ex.: bloquear envio sem campo obrigatório).
  - *Tool* = o agente decide o momento de chamar (ex.: buscar campanhas ativas).
  - *Prompt* = comportamento definido no system prompt (ex.: interpretar a fase da conversa).
- **Determinismo primeiro:** a Onda 1 do Radar de Fomento é **zero LLM** — regras, atributos e fórmulas. IA/embeddings só quando dados e volume justificarem.
- **Modelo adequado à complexidade:** sub-agentes simples usam modelos mini/nano.
- **Gates por fase:** Go/No-Go → Demo interna → Demo AEVO → Aceite AEVO.

## Ponto de atenção recorrente nos dois documentos
> **Manutenção pós-deploy não entra na estimativa.** Radar de editais e export do FormP&D **não são build once** — fontes mudam, o governo atualiza portais e formulários. Prever horas recorrentes de Fábrica separadamente.

## Formatos de documento
- **PRD** — produto: problema, personas, JTBD, user stories, escopo, métricas, premissas, riscos.
- **TDD** — técnico: arquitetura, componentes, integrações, estimativa por fase, riscos técnicos.
- **PRD Ready** — quando o PRD vem pronto da AEVO e a smartside entra direto no TDD.

## Relação com a campanha interna
A [[AEVO - Campanha GenAI Apps]] é o funil de entrada de ideias que abastece esse roadmap: ideias aprovadas no Comitê de GenAI Apps viram itens de roadmap e, eventualmente, PRDs para a Fábrica.

## Notas relacionadas
[[AEVO - Campanha GenAI Apps]] · [[AEVO - Riscos, Gaps e Pendências]] · [[smartside.ai]]
