---
type: project
status: go-live assistido (piloto 1 LP)
tags: [projeto, knewin, nina, ia, sdr, qualificacao]
company: "[[Knewin]]"
links: ["[[Knewin]]", "[[smartside.ai]]", "[[Nina]]"]
---

# Knewin — Nina (Agente IA de Qualificação)

> **Nina**: SDR de IA da [[smartside.ai]] para a [[Knewin]]. Qualifica leads de WhatsApp via **SPIN**, faz triagem no HubSpot e transborda p/ humano quando necessário. Não vende/negocia preço.

## Escopo
- Recebe leads (form HubSpot → link WhatsApp) e conduz qualificação natural (áudio, imagem, documentos; tem memória).
- Identifica lead por e-mail/telefone via consulta ao HubSpot (cliente? vendedor vinculado? <90 dias?).
- Encaminha: qualificado → agendamento (SMB/Enterprise); avulso → checkout Dino + pitch demanda; sem fit → perdido; sem resposta → follow-up; casos sensíveis → transbordo p/ SDR.
- Espelha o pipeline do HubSpot no CRM smartside (sync bidirecional).

## Regras-chave (2026-07-03)
- **Qualificação:** SPIN. Critérios de porte/estrutura/área de comunicação/investimento (material da Knewin).
- **Timeout:** lead que converte e não manda msg em **5 min** → vendedor (interino; abordagem ativa em dev).
- **Follow-up:** 3 toques em 24h (15min / ~3h / ~16h); **+4º toque ~24h** (a confirmar c/ Gabriela); FDS off por padrão.
- **Horário:** 09h18.
- **Transbordo → [[Aline Claro]]:** pede humano, irritação, loop sem entendimento, é cliente (descoberto no meio), insiste em preço. Operado no CRM smartside (não no número pessoal).
- **Guardrails:** sem preço, sem promessa de resultado, sem dados fora do HubSpot, anti prompt-injection, tom de marca.

## Em desenvolvimento
- Abordagem ativa da Nina p/ leads parados (alvo: semana de 06–10/07).
- Agendamento automático (V1) — 2 slots mais próximos, agenda e passa ao vendedor.
- Pitch **avulso → Dino Demanda** codificado na KB.
- Ajustes de CRM (tags/marcos de ação, responsável, campo HubSpot Contact ID).
- Painel de monitoramento + check-points quinzenais.

## Em aberto / a decidir
- Integração com **Elefant** (viabilidade/API) — reportar à [[Amanda Botini]].
- Expansão além da 1ª LP (Dino Demanda) — [[Gabriela Arruda]].
- Follow-up de FDS; quebra-gelos >24h (custo Meta); usuários de vendedores no CRM.
- Tráfego da LP Dino Demanda (nada convertido ainda) — checar c/ **Avante**.

## Plataformas
HubSpot (fonte) · WhatsApp · CRM smartside · Elefant · bases de conhecimento (PPTs de produto, central de ajuda, sites, perguntas de qualificação da Aline).

## Notas relacionadas
- [[2026-07-03 Knewin - Ativação Nina]]
- Fonte: [[Transcrição - Ativação Nina]]
