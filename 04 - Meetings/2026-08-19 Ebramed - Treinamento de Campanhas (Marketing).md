---
type: meeting
date: 2026-08-19
tags: [reuniao, ebramed, crm, ia, campanhas, treinamento, marketing, go-live]
attendees: ["[[José Lucas Ribeiro]]", "[[Yan Simmer]]", "[[Tainara Lameira]]", "[[Adriano Ribondi]]", "[[Yara]]"]
project: "[[Ebramed - CRM IA (Isabela)]]"
company: "[[Ebramed]]"
source: "[[Reunião Ebramed Treinamento Marketing]]"
recording: https://fathom.video/share/WM4zKNBy91BmLcDVo3aQe43hsfpsxb46
---

# 2026-08-19 Ebramed — Treinamento de Campanhas (Marketing)

> Treinamento hands-on de 50 min: [[Tainara Lameira]] compartilhou a tela e foi guiada do zero até **ativar a primeira campanha real em produção** (985 contatos). Sessão gerou também a lista de defeitos e pendências do CRM.
>
> **[[Marcos]] confirmou presença na véspera, mas não entrou.**

**Participantes:** [[José Lucas Ribeiro]], [[Yan Simmer]] (smartside.ai) · [[Tainara Lameira]], [[Adriano Ribondi]], [[Yara]] ([[Ebramed]])

---

## 1. Decisões

- **Passagem de bastão do comercial da Ebramed: [[Yara]] → [[Tainara Lameira]].** Comunicado pela própria [[Yara]]: *"A Tainara está assumindo, José. Eu vou para outra área aqui dentro da empresa, mas eu estou assessorando 100% a Tainara. [...] Mas o comercial Ebramed, a coordenadora é a Tainara."* Yara segue muito próxima na transição inicial.
- **Primeira campanha real ativada em produção.** Por: [[Tainara Lameira]], orientada por [[José Lucas Ribeiro]]. Configuração: 985 contatos, template quebra-gelo aprovado pela Meta, **limite de 329 disparos/dia**, início às **11h**, sem envio em sábado/domingo, funil principal. Motivo do limite: distribuir em três dias (qua→sex 21/08) e não estressar a base.
- **O campo `lista` passará a subir como TAG (múltiplas por contato)**, não como campo simples. Por: [[José Lucas Ribeiro]] + [[Yan Simmer]], a partir de objeção do [[Adriano Ribondi]]. Motivo: campo único é sobrescrito a cada nova importação — o mesmo lead em duas campanhas perde o vínculo com a primeira e a métrica por campanha quebra.
- **Remover da lista de origem de campanha todas as opções que não sejam API Oficial.** Por: [[José Lucas Ribeiro]]. Motivo: só existe um número/origem válido agora.
- **O follow-up automático da Isabela NÃO se aplica a quem for abordado por campanha.** Por: [[Yan Simmer]]. Motivo: a cadência automática foi construída para o fluxo anterior de abordagem e só atende quem já respondeu. Para campanhas, a Ebramed precisa criar os próprios templates de follow-up (recomendado usar template de **utilidade**, sem custo).
- **[[Tainara Lameira]] recebe autonomia para criar campos personalizados e templates.** Por: [[José Lucas Ribeiro]] — criou o campo `e-mail` ao vivo em vez de a smartside criar por ela.
- **Filtro provisório de "quem respondeu" = etapa "Em Qualificação".** Por: [[José Lucas Ribeiro]], como contorno enquanto o campo `respondeu` não existe: quem responde sai de Recepção e cai em Qualificação automaticamente.
- **Duas campanhas podem rodar simultaneamente**, desde que não compartilhem o mesmo lead/link — senão *"vira uma salada"*.

### Defeitos e pendências identificados ao vivo
- **Exportar contatos não funciona** — o botão não ativa. Detectado na tela, com o cliente assistindo.
- **Importação por "Listas" não puxa campos personalizados** — só funcionou via Contatos + audiência filtrada. O formato de lista precisa ser revisto.
- **A Isabela não preenche especialidade/tipo/e-mail** quando o lead chega proativamente pelo WhatsApp.
- **Campo `especialidade` é texto livre** — "pediatra" vs. "pediatria" quebra os filtros de audiência. Deveria ser lista fechada.
- **10 telefones inválidos** na base de 998 (985 subiram).
- Tela de audiências não abriu para a Tainara na primeira tentativa (problema pontual, resolvido no retry).
- **Não há busca por texto dentro das conversas** — Tainara não conseguiu achar quem escreveu *"bônus 5 mil"*.

## 2. Compromissos

**smartside.ai — [[Yan Simmer]] / [[José Lucas Ribeiro]]**
- [ ] Corrigir a **exportação de contatos** e habilitar exportação por etapa do funil e filtros
- [ ] Fazer o campo `lista` subir como **tag** (múltiplas tags por contato)
- [ ] Remover as origens que não são API Oficial da lista de campanhas
- [ ] Configurar a Isabela para **preencher especialidade/tipo/e-mail** quando vierem em branco
- [ ] Rever o formato de "Listas" para suportar campos personalizados na importação
- [ ] Ajustar o campo `especialidade` para formato de lista fechada
- [ ] Avaliar busca por texto dentro das conversas
- [ ] Criar os campos `respondeu` / `quando respondeu` (herdado de [[2026-08-18 Ebramed - Abordagem Ativa e Rastreamento de Campanhas]])
- [ ] **Formalizar um prazo** para as melhorias de mensuração — pedido explícito do [[Adriano Ribondi]], ainda sem resposta
- [ ] Enviar as gravações de **18/08 e 19/08** no grupo de WhatsApp

**Ebramed — [[Tainara Lameira]]**
- [ ] Acompanhar a campanha de 985 contatos (329/dia, início 11h) até **sexta 21/08**
- [ ] Criar uma lista pequena de teste (ela + Karen) e treinar a criação de mensagens
- [ ] Padronizar a nomenclatura de templates (sem espaços)
- [ ] Assumir a coordenação comercial: funil, handoff e designação de vendedor atento

**Ebramed — [[Yara]]**
- [ ] Assessorar a [[Tainara Lameira]] na transição (100% no início)

**Ebramed — [[Adriano Ribondi]]**
- [ ] Receber e validar o prazo formalizado das melhorias de mensuração

## 3. Preferências (como trabalhar/comunicar)

- **Treinamento hands-on em vez de demo:** o cliente compartilha a tela e é guiado. Deu autonomia real — a Tainara criou campo, template, lista, audiência e campanha sozinha na mesma sessão.
- **[[Adriano Ribondi]] exige prazos formalizados** para itens de desenvolvimento: *"vocês conseguem passar um prazo pra gente [...] depois formaliza um prazo?"*
- Gravações das reuniões devem ser enviadas no **grupo de WhatsApp**.
- Dúvidas do dia a dia: grupo de WhatsApp — *"qualquer dúvida que vocês tiverem, podem acionar a gente ali no grupo"*.
- **[[Tainara Lameira]] usa o RD Conversas como referência de UX** (botões, negrito/itálico, redirecionamento) e compara as funcionalidades.
- Horário de disparo pensado para o público: início às 11h *"considerando que são médicos"*.

## 4. Insights-chave

- **A conta mudou de dono no meio do projeto.** O ponto focal validado em julho ([[Yara]]) sai do comercial; [[Tainara Lameira]] entra vindo do marketing/inbound, sem histórico do funil nem do handoff. O próprio [[José Lucas Ribeiro]] classificou o repasse como *"a parte mais crítica"* — e adiou para depois.
- **Go-live comercial de fato foi 19/08**, não julho: a primeira campanha ativa saiu nesta sessão, com custo estimado de **~R$ 315** (985 × R$ 0,32).
- **Template de utilidade tem custo zero** (vs. R$ 0,32 do marketing), mas aprovação mais lenta na Meta — alavanca direta de custo para os follow-ups dentro da janela de 24h.
- **Clique em botão do template conta como resposta** e move o contato para Qualificação — mas não dá para saber *quem* clicou sem entrar em Conversas uma a uma.
- **O gargalo do projeto é arquitetura de dados, não IA.** As três dores do cliente — campo livre em `especialidade`, campo único sobrescrito em `lista`, exportação quebrada — são todas de modelagem e produto do CRM. A IA já foi validada.
- **A Ebramed disparou antes de a instrumentação existir.** [[Adriano Ribondi]]: *"Essas questões a gente formaliza, eles formalizam para a gente que volta"* — a decisão foi disparar agora e medir depois.
- **Aprovação de template pela Meta é rápida** (minutos, na prática observada), o que viabiliza criar template e disparar na mesma sessão.
- **Sem restrição de volume conhecida na API Oficial** além do custo — mas o [[Yan Simmer]] sinalizou relatos de problemas com números na Meta: *"a meta toda hora prega alguma coisa na gente"*.

---

## Notas relacionadas
- Reunião anterior: [[2026-08-18 Ebramed - Abordagem Ativa e Rastreamento de Campanhas]]
- Projeto: [[Ebramed - CRM IA (Isabela)]]
