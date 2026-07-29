---
type: project
status: TDD v1 (abr/2026) — PRD Ready, aguarda Discovery
tags: [projeto, aevo, produto, extension, whatsapp, n8n, multiagente, tdd]
company: "[[AEVO]]"
links: ["[[AEVO]]", "[[smartside.ai]]", "[[00 - MOC AEVO]]", "[[AEVO - Fábrica de GenAI Apps]]"]
---

# AEVO — Envio de Ideias por WhatsApp (Extension)

> Extension do AEVO Innovate: colaboradores enviam **ideias por texto ou áudio no WhatsApp**; um sistema multiagentes no n8n coleta as informações e submete a ideia ao AEVO via API.
> **216 horas (~2 meses de Fábrica a 100h/mês).** Formato de entrada: **PRD Ready** — PRD recebido da [[Duda (AEVO)]].

## Arquitetura — decisões
- **Orquestração:** n8n em **Railway**, instância já operacional.
- **Multiagentes:** agente orquestrador central + sub-agentes especializados, cada um com escopo limitado e modelo adequado à complexidade (mini/nano).
- **Sem banco próprio:** estado da conversa na memória do n8n; dados da ideia via API AEVO; log de auditoria a definir.
- **Pipeline determinístico (harness):** recebimento de mensagens é **100% determinístico, sem LLM**. Decisão de LLM só no orquestrador e sub-agentes.

## Componentes

### 1. Pipeline de recebimento (harness)
| Capacidade | Descrição |
|---|---|
| Webhook WhatsApp | Recebe eventos; aciona indicador de digitação e marca visualização |
| Identificação de mídia | Detecta texto ou áudio; baixa o áudio quando aplicável |
| Transcrição | Áudio → texto via Whisper (a definir); encaminha ao agente |

### 2. Agente Gerente de Mensagens (orquestrador)
Memória persistente, janela de contexto **> 15 mensagens**. Fluxo padrão:
1. Validar usuário → 2. Buscar campanhas ativas e detalhes → 3. Se a campanha tiver IA habilitada, sugerir uso → 4. Coletar informações da ideia.

**Harness × Tool:** validação ao iniciar conversa = *harness* (sempre acontece). Buscar campanhas, apresentar funcionalidades de IA e delegar a coleta = *tools* (o agente decide o momento). Interpretar a fase da conversa = *prompt*.

### 3. Sub-agentes
- **Validação do Usuário** — confere se o número corresponde a usuário cadastrado e ativo (modelo nano).
- **Consulta de Campanhas** — lista campanhas ativas via lista interativa do WhatsApp; coleta config de IA.
- **Envio da Ideia** — coleta estruturada e submissão. Tools: `getCriterios`, `getOpcoesCriterios`, `camposAdicionais`, `getTemas`, `salvarIdeia`, `enviarIdeia`. Bloquear envio sem campos obrigatórios e validar formato são **harness** (regras invioláveis).

### 4. Funcionalidades de IA do AEVO replicadas (5 sub-agentes)
| Sub-agente | Função | Condição |
|---|---|---|
| Organizar Ideia | Organiza as informações que o usuário tem | Ajuda no Envio habilitada |
| Selecionar Campanha | Sugere a campanha mais adequada | Ajuda no Envio habilitada |
| Soluções de Mercado | Identifica soluções que ajudam na implantação | Ajuda no Envio habilitada |
| Corrigir Erros | Revisa a ideia | Ajuda no Envio habilitada |
| Envio Otimizado | Reestrutura a descrição automaticamente | Envio Otimizado habilitado E usuário não forneceu campos específicos |

> Premissa: os **prompts existentes da plataforma AEVO serão disponibilizados** para replicação.

### 5. Sistema de respostas WhatsApp
Texto simples ou listas interativas. Envio é harness; a decisão entre texto e lista é tool. Listas usadas para: campanhas ativas, funcionalidades de IA, campos de seleção (critérios, temas).

## Integrações
| Integração | Tipo | Direção | Prio |
|---|---|---|---|
| WhatsApp — webhook de mensagens (texto/áudio) | Webhook | Entrada | Alta |
| WhatsApp — envio de texto e listas | REST | Saída | Alta |
| WhatsApp — download de mídia | REST | Entrada | Alta |
| AEVO API — usuários | REST | Leitura | Alta |
| AEVO API — campanhas e detalhes | REST | Leitura | Alta |
| AEVO API — critérios / campos / temas | REST | Leitura | Alta |
| AEVO API — submissão de ideias | REST | Escrita | Alta |
| Transcrição de áudio (Whisper) | REST/SDK | Interna | Alta |

## Estimativa por fase
| Fase | Escopo | Horas | Gate |
|---|---|---|---|
| 0 | Discovery — APIs, prompts existentes, UX writing, fluxos de campanha | 24h | **Go/No-Go** |
| 1 | Infra e pipeline base — n8n, recebimento, transcrição, respostas | 40h | — |
| 2 | Agentes core — orquestrador, validação, campanhas, envio | 80h | Demo interna |
| 3 | Funcionalidades de IA do AEVO + integração | 48h | Demo AEVO |
| 4 | Hardening, testes com dados reais, deploy | 24h | **Aceite AEVO** |
| | **Total** | **216h** | ~2 meses |

## Premissas
n8n operacional (Railway) · credenciais da WhatsApp Business API fornecidas pela AEVO · número já aprovado pela Meta · APIs AEVO estáveis conforme documentação Postman · prompts das IAs disponibilizados · acesso a ao menos uma campanha de teste com IA habilitada · limite de sessões simultâneas a definir.

## Riscos
| Risco | Prob. | Impacto | Mitigação |
|---|---|---|---|
| Perda de contexto em conversas longas | Média | **Alto** | Memória persistente, janela >15 msgs, agrupamento de perguntas |
| Conversas longas com formulários complexos | Alta | **Alto** | UX writing otimizada, agrupamento de campos, envio otimizado |
| Rate limiting da API WhatsApp | Baixa | **Alto** | Retry com backoff, monitoramento |
| Qualidade da transcrição (ruído, sotaque) | Alta | Médio | Modelo robusto, confirmação do texto com o usuário |
| Latência WhatsApp → LLM → AEVO | Média | Médio | Indicador de digitação imediato, modelos rápidos nos sub-agentes |
| Prompts das IAs AEVO não documentados | Média | Médio | Levantamento no Discovery, validação antecipada |

## Observações
- **UX writing é crítico:** público-alvo tem menor familiaridade tecnológica. Revisão dedicada no Discovery e validação com usuários reais no Hardening. Textos simples, sem jargão.
- **Evolução futura (fora do escopo):** MS Teams, Messenger, notificações de andamento, gestão de ideias, parecer técnico, anexos multimídia, IA de ideias similares.

## Notas relacionadas
[[AEVO - Fábrica de GenAI Apps]] · [[AEVO - Campanha GenAI Apps]] · [[AEVO - Glossário]]
