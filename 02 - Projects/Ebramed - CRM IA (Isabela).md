---
type: project
status: em produção (1ª campanha ativa desde 19/08/2026)
tags: [projeto, ebramed, crm, ia, sdr, campanhas, api-oficial]
company: "[[Ebramed]]"
links: ["[[Ebramed]]", "[[smartside.ai]]"]
---

# Ebramed — CRM IA (Isabela)

> CRM da [[smartside.ai]] com agentes de IA (SDR) para a [[Ebramed]]. Agente comercial **Isabela** + agente de ensino **Isadora**.

## Escopo
- Abordagem e reativação de leads da base da Ebramed via WhatsApp, com **campanhas** disparadas pelo CRM.
- Funil comercial: Recepção → Qualificação → Preço Apresentado → Produto de Entrada Convertido → Ganho.
- Handoff para humano em casos sensíveis (saúde/RQE, negociação, cobrança, irritação, alucinação) com notificação em grupo.
- Base de conhecimento treinada com materiais da Ebramed (links no Drive compartilhado); calibragem de prompt sob demanda.
- **Fora de escopo (contratado):** integração com o RD (Conversas/CRM). Tecnicamente viável, não contratada.

## Agentes
- **Isabela** — puramente comercial.
- **Isadora** — ensino (script próprio, já desenvolvido).

## Arquitetura de WhatsApp — mudança de rota (18/08/2026)
- **Antes (jul/2026):** ~4–5 números em **API não oficial**, com escoamento entre números (~25% cada, até 100 msg/número/dia). Motivo: evitar banimento.
- **Agora:** **um único número na API Oficial da Meta**, atendendo receptivo **e** ativo. Motivo: os múltiplos números não se viabilizaram (bloqueios); a API Oficial zera o risco de banimento. O segundo número fica só como backup.
- **Consequência:** o mecanismo de distribuição entre múltiplos números foi descartado; a seção **Marketing/Campanhas** do CRM passa a ser o caminho oficial de disparo.

## Regras operacionais
- **Custo:** R$ 0,32 por mensagem em template de **marketing**. Template de **utilidade** não tem custo, mas aprova mais devagar na Meta.
- **Templates exigem 2 variáveis obrigatórias:** `nome` + `especialidade`. Se qualquer uma vier vazia, **a mensagem não é enviada**.
- **Ebramed pode criar templates novos**, mas não deve editar os já publicados; precisa avisar a smartside para ativação.
- **Etapas do funil não podem ser alteradas pela Ebramed** — quebra as atualizações automáticas da Isabela.
- **Importação de listas:** usar **mesclar** (preserva histórico e permite medir por campanha).
- Clique no botão do template conta como resposta e move o contato para **Qualificação**.
- Follow-up automático da Isabela **só vale para quem já respondeu** — campanhas precisam de templates de follow-up próprios.
- Duas campanhas simultâneas são permitidas, desde que não compartilhem o mesmo lead/link.

## Estado (2026-08-19)
- **Em produção.** Primeira campanha real ativada por [[Tainara Lameira]]: **985 contatos**, 329 disparos/dia, início às 11h, sem fim de semana, até sexta **21/08/2026**. Custo estimado ~R$ 315.
- [[Tainara Lameira]] operando o CRM com autonomia (cria campos, templates, listas, audiências e campanhas).
- **Ponto focal do cliente mudou:** [[Yara]] → [[Tainara Lameira]] (ver Riscos).

## Em desenvolvimento (assumido, sem prazo formalizado)
- [ ] Corrigir **exportação de contatos** (botão não ativa) + exportar por etapa/filtros — **defeito**
- [ ] Campo `lista` subir como **tag** (múltiplas), hoje é sobrescrito a cada importação — **defeito de modelagem**
- [ ] Importação por "Listas" não puxa campos personalizados — **defeito**
- [ ] Campo `especialidade` virar lista fechada (hoje texto livre quebra audiências) — **defeito de modelagem**
- [ ] Campos `respondeu` e `quando respondeu`
- [ ] Campo `fonte` + preenchimento automático pela mensagem de origem (Google/Meta/e-mail/massa)
- [ ] Isabela preencher especialidade/tipo/e-mail quando vierem em branco
- [ ] Remover origens não-API-Oficial da lista de campanhas
- [ ] Busca por texto dentro das conversas
- [ ] Valor padrão de especialidade quando o campo vier em branco
- [ ] Ajustar o mecanismo de campanhas removendo a lógica de múltiplos números

## Em aberto / decisões pendentes
- Regra "qualquer preço apresentado" (confirmar c/ [[Marcos]]) — pendente desde 23/07.
- Ebramed definir: mensagens de abertura por fonte, valor padrão de especialidade, limite diário e janela de horário padrão.
- Separação Comercial/Ensino: número dedicado + proporção de disparo — pendente desde 23/07.
- Diferenciação mentoria/matrícula → Ganho — pendente desde 23/07.
- **Prazo formal** das melhorias de mensuração, pedido por [[Adriano Ribondi]] — sem resposta.

## Riscos
- ⚠️ **Mudança de ponto focal sem repasse formal.** [[Yara]] saiu do comercial e [[Tainara Lameira]] assumiu sem receber o repasse do funil e das regras de handoff. [[José Lucas Ribeiro]] classificou como *"a parte mais crítica"* e adiou.
- ⚠️ **985 mensagens dispararam antes da instrumentação existir.** Os campos `fonte` e `respondeu` — as duas dores declaradas do cliente — ainda não existem. A Ebramed gasta ~R$ 315 e vai medir mal a primeira campanha.
- ⚠️ **Defeitos do produto apareceram ao vivo** na primeira sessão de treinamento (exportação quebrada, importação sem campos personalizados).
- ⚠️ **Retrabalho não precificado:** ~12 itens de desenvolvimento assumidos em duas reuniões, sem prazo nem discussão comercial; boa parte são correções do CRM, não features.
- ⚠️ **Qualidade de dados da base:** 10 telefones inválidos em 998; especialidade em campo livre; templates falham silenciosamente se a variável vier vazia.

## Notas relacionadas
- [[2026-08-19 Ebramed - Treinamento de Campanhas (Marketing)]]
- [[2026-08-18 Ebramed - Abordagem Ativa e Rastreamento de Campanhas]]
- [[2026-07-23 Ebramed - Funcionamento do CRM]]
- Fontes: [[Transcrição Reunião - Ebramed]] · [[Reunião Ebramed]] · [[Reunião Ebramed Treinamento Marketing]]
