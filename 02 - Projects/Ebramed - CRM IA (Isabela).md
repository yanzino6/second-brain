---
type: project
status: pré-go-live
tags: [projeto, ebramed, crm, ia, sdr]
company: "[[Ebramed]]"
links: ["[[Ebramed]]", "[[smartside.ai]]"]
---

# Ebramed — CRM IA (Isabela)

> CRM da [[smartside.ai]] com agentes de IA (SDR) para a [[Ebramed]]. Agente comercial **Isabela** + agente de ensino **Isadora**.

## Escopo
- Abordagem de leads frios da base da Ebramed via WhatsApp (4 números, API não oficial), com escoamento entre números (~25% cada, até 100 msg/número/dia).
- Funil comercial: Recepção → Qualificação → Preço Apresentado → Produto de Entrada Convertido → Ganho.
- Handoff para humano em casos sensíveis (saúde/RQE, negociação, cobrança, irritação, alucinação) com notificação em grupo.
- Base de conhecimento treinada com materiais da Ebramed; calibragem de prompt sob demanda.

## Agentes
- **Isabela** — puramente comercial.
- **Isadora** — ensino (script próprio, já desenvolvido).

## Estado (2026-07-23)
- CRM apresentado e validado pela Ebramed (etapa comercial clara).
- **Bloqueio p/ Go Live:** números de WhatsApp desconectados (falta de aparelho dedicado) → precisam reconectar + sessão de testes.
- **Go Live alvo:** segunda **27/07/2026**, no mais tardar terça **28/07/2026**.

## Em aberto / decisões pendentes
- Regra "qualquer preço apresentado" (confirmar c/ [[Marcos]]).
- 1 número em API Oficial entre os ~5 (limite, templates, janela 24h).
- **Estratégia híbrida** (API oficial p/ campanhas + API não oficial p/ atendimento) — oportunidade estratégica; ainda teórica.
- Impacto da nova precificação da Meta (cobra todas as mensagens; janela 72h só p/ anúncios click-to-WhatsApp) vs. ciclo de ~50 dias da Ebramed.
- Separação Comercial/Ensino: número dedicado + proporção de disparo.

## Notas relacionadas
- [[2026-07-23 Ebramed - Funcionamento do CRM]]
- Fonte: [[Transcrição Reunião - Ebramed]]
