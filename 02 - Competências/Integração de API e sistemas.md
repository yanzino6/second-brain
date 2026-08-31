---
type: competencia
nivel: forte
tags: [competencia, api, integracao, crm]
atualizado: 2026-08-31
---

# Integração de API e sistemas

> Integração profunda, não chamada de endpoint — travessia de grafo de CRM, paginação com cursor, upload retomável.

## Provas
- **HubSpot** — travessia de associações v4 contato↔negócio, API de owners, criação e associação. A regra "já é cliente / tem vendedor / interagiu em 90 dias" implementada como roteamento executável.
- **Google Places** — paginação com cursor implementada à mão (init → build → fetch → accumulate → has next?).
- **Meta WhatsApp Cloud API** — criação de template com header de mídia via *resumable upload*; migração de API não oficial para oficial.
- **Microsoft Graph** — envio por shared mailbox com SendAs, trigger nativo de Outlook.
- Outros: Firecrawl, LeadMagic, Unipile, Pipedrive, Kommo, Supabase, Vertex, OpenAI, Azure OpenAI.

## Lacuna
Sem evidência de **construção** de API pública própria (versionamento, contrato, documentação OpenAPI, rate limit do lado servidor). A competência é de consumo e integração.
