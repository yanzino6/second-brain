---
tags: [biancogres, tech-stack, arquitetura, sistemas, ia]
aliases: [Tech Stack, Stack Tecnológica, Sistemas, Arquitetura]
up: "[[00 - MOC Biancogres]]"
---

# Tech Stack — Biancogres

Stack tecnológica **atual da Biancogres** conforme mapeado no diagnóstico. É sobre esta base que as [[PoC - Sell-Out|PoCs]] e o [[Programa Black Belts|programa de capacitação]] são construídos.

## 1. Sistemas core (ERP e gestão)
| Sistema | Papel | Observações |
|---|---|---|
| **TOTVS Protheus** | ERP principal / base de dados central | Em uso desde **1999**. Fonte da maioria dos dados comerciais. |
| **Senior Sistemas (Senha)** | RH completo | Substituiu o módulo de RH do Protheus (ponto, terceiros, benefícios, avaliação, pagamento). |
| **Fluid** | Fluxo de compras/requisições | Mesma stack usada pela Fibrasa. |
| **Fênix, WMS, Ecosis** | Sistemas complementares tradicionais | — |
| **Bizagi** | Abertura de RPV / workflow | Representantes reclamam da UX (DR-038, DR-052). |

## 2. Dados e BI
- **Power BI** — padrão do comercial, dashboards maduros. Limitação-chave: **não permite comentário online contextual** → causa raiz do Excel paralelo (DR-010).
- **SQL / Toad / ETL tradicional** sobre base Protheus.
- **PowerOmni (PowerTuning)** — PoC interna de **text-to-SQL** (consulta de dados via LLM).

## 3. Automação e IA
| Ferramenta | Uso | Status |
|---|---|---|
| **n8n** ⭐ | Orquestração/integração — plataforma central das PoCs | Self-hosted **community (gratuito)**, em **servidor Linux local** (on-premise), instalado com apoio da [[Ayko]]. Primeiros fluxos em teste. |
| **Claude Code** *("Cloud Code" nos materiais)* | Operador que constrói os fluxos no n8n via **MCP** | Base do método Black Belts |
| **Cursor** | IDE com IA para o time técnico | Adoção **muito forte** desde fev/2026; substituiu o Antigravity → virou produção de fato |
| **Power Automate** | RPA | Em produção desde a pandemia |
| **T2C** | LLM para leitura de documentos SESMT (LTCAT, ~4 mil páginas) | PoC interna |
| **Genexus (GlobalSys)** | Gestão de APIs entre sistemas | Em uso |
| **Transcriptor** | Transcrição de reuniões presenciais | Em teste |

> [!info] Método de construção Smartside
> `Código (baixo nível)` → **n8n (fluxo visual / alto nível)** → **Claude Code (o operador que você comanda em português)**. O n8n também é o **guardrail de governança**: a TI define o que pode ser acessado e tudo fica **auditável**. Ver [[Programa Black Belts]].

## 4. Hospedagem e cloud
**Confirmado:**
- n8n roda **self-hosted, localmente, em servidor Linux interno** (não é VPS, não é cloud pública — **on-premise**).
- O time técnico **não é especialista em Linux** — quem configurou foi a [[Ayko]].

**Gaps abertos (não informados):** cloud provider institucional (AWS/Azure/GCP/on-premise puro), existência de tenant Azure, topologia de rede/conectividade externa → ver [[Conhecimento, Riscos e Gaps]].

## 5. LLMs
- **Ainda não há LLM de produção definido.**
- Testando múltiplas ferramentas via parceiros (T2C, PowerOmni, Genexus).
- **IBM foi considerada e descartada** (volume de tokens necessário).
- [[Marcos Vinícius Nascimento|Vinícius]] pediu direcionamento explícito: *"qual LLM eles vão usar, quais vocês estão usando?"* → decisão pendente da Smartside.

## 6. Canais conversacionais
- **Telegram** — já existe um **bot de estoque** mantido pela TI (candidato a reuso na [[PoC - SAC Atendimento|PoC de RPV]]).
- **WhatsApp** — uso informal via **~8 celulares corporativos/pessoais** sem central nem WhatsApp Business API → risco LGPD (DR-054).
- **Teams**, e-mail, redes sociais (Instagram/Facebook/Google) — atendimento manual (DR-055).

## Dúvidas técnicas em aberto (levantadas pela TI)
1. **Licenciamento do n8n** — quando migrar de community → enterprise? Como compartilhar dados entre fluxos com segurança?
2. **Arquitetura de permissionamento** (cadastro de usuários + grupos + canais + auth por código via email/CPF).
3. **Estratégia de ambientes** — único vs. dev/homolog/prod.
4. **Boas práticas de dev no n8n** — padrões, modularização, versionamento.
5. **Integração com canais** (Telegram, WhatsApp, Teams).

## Ligações
[[Empresa - Biancogres]] · [[PoC - Sell-Out]] · [[PoC - SAC Atendimento]] · [[Programa Black Belts]] · [[Conhecimento, Riscos e Gaps]] · [[Glossário]]
