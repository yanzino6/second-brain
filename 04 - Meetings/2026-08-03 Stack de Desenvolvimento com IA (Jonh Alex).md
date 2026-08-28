---
type: meeting
date: 2026-08-03
tags: [reuniao, interno, smartside, ia, desenvolvimento, harness, ferramentas, transferencia-de-conhecimento]
attendees: ["Jonh Alex (Jonhvmp) — apresentador, ⚠️ afiliação não confirmada", "[[Flávio Parreiras]]", "⚠️ 1–2 participantes da smartside.ai não identificáveis no transcript"]
project: ["[[smartside.ai - Workspace de Desenvolvimento (Harness)]]"]
company: "[[smartside.ai]]"
source: "07 - Archive/AI Development.md"
recording: https://fathom.video/share/Q4xXBfV65sGzWyEoEwvdM7jy9gEyAPoQ
duration: 87min
---

# 2026-08-03 · Stack de Desenvolvimento com IA (Jonh Alex)

> Google Meet **impromptu**, 87 min. Sessão de **transferência de conhecimento**: Jonh Alex (Jonhvmp) apresenta ao time da smartside.ai o stack e o workflow de desenvolvimento com IA que ele usa. Sem pauta comercial e sem cliente na call.
> **Todo o conteúdo técnico está consolidado em [[Stack de Desenvolvimento com IA - Ferramentas e Workflow]]** — esta ata guarda o enquadramento, as decisões, os compromissos e os riscos.

## ⚠️ Qualidade da fonte — ler antes de usar esta ata

**As 87 minutas estão atribuídas a um único locutor.** O transcript tem exatamente um marcador de fala (`@0:00 — Jonh Alex`) e nenhum outro em 838 linhas: perguntas, respostas e demos de 4+ pessoas viraram um monólogo contínuo.

- **Toda atribuição de fala abaixo é inferência de contexto**, não dado da transcrição.
- Nomes próprios foram destruídos. Decodificação principal: **"ARNs"/"Arns"/"Arnes"/"ARDS" = harness**.
- É o **mesmo defeito** que impediu a atribuição dos compromissos do app financeiro em [[2026-07-30 smartside.ai - Company Brain (Segundo Cérebro)|30/jul]]. Duas reuniões seguidas perdidas pelo mesmo motivo — ver [Riscos](#riscos-e-sinalizações).

**Participantes** — por decisão do usuário, nenhuma nota de pessoa foi criada ou atualizada nesta extração.
- **Jonh Alex (Jonhvmp)** — apresentador. ⚠️ Afiliação e cargo **não afirmados**: trata o time como "vocês", fala dos "meus clientes" em separado e menciona que vai "falar com o pessoal da Shiva" sobre a assinatura dele. Aparentemente externo e de alguma forma ligado ao programa Shiva.
- **[[Flávio Parreiras]]** — entrou depois do início (@1:00 ainda estava ausente); endereçado por nome várias vezes.
- ⚠️ **1–2 pessoas da smartside.ai não identificadas** — fizeram as perguntas técnicas e demonstraram um workflow n8n interno. Um "Vitinho" é chamado @6:23 (possivelmente [[Victor Hugo]], **não confirmado**).
- **Citados como ausentes:** "Simões" ([[Matheus Simões]]) · "o Simmer" ([[Yan Simmer]], estaria à tarde) · "o Edge"/"Ed" ⚠️ (mesmo alias que já aparece em [[smartside.ai - Workspace de Desenvolvimento (Harness)]], ainda sem pessoa canônica) · "Lucas" ⚠️ · "Dan" ⚠️.

---

## 1. Decisões

### Firmes
- **Nenhuma decisão firme foi tomada.** A sessão foi expositiva: recomendações do apresentador + perguntas do time. Registrar isso é mais honesto do que promover recomendação a decisão.

### Posições declaradas pelo apresentador (recomendações, não decisões da smartside)
- **Substituir n8n por agente em código** (Python, sem framework) para o agente de atendimento demonstrado. Motivo: liberdade de decidir para onde ir, onde parar e quando reagir — o que o fluxo fixo do n8n não dá. Estimativa dele: ~2 semanas de construção interna.
- **Oferecer Temporal como componente cobrável** em projeto Enterprise ("Flávio, pode cobrar aí"). Motivo: human-in-the-loop e workflows de longa duração, com o especialista do cliente dentro do fluxo.
- **Entregar documentação via MkDocs** e cobrar por ela. Motivo: markdown puro vira site estruturado sem input manual — valor percebido alto, custo baixo.
- **Assinatura em vez de API** para trabalho de codificação. Motivo: custo (ver ressalva nos números).
- **Hospedar Hermes usando os créditos de GCP** ⚠️ — sugestão condicionada a a smartside conseguir os créditos.

### Em aberto (sem decisão)
- **Avaliar Serena para o caso "Claude Code sobre a documentação interna do cliente"** — alguém do time levantou um cliente (⚠️ **não nomeado** no transcript) com Azure DevOps (**15 repositórios**, alguns com +100 arquivos), SharePoint (**200 arquivos**) e um portal de arquitetura interno. Postura declarada: **não desenvolver solução própria**, encaixar ferramenta existente. Conecta diretamente com [[smartside.ai - Company Brain (Segundo Cérebro)]].
- **Testar Serena** — "vou testar, o ponto é que preciso de uma brecha de tempo". ⚠️ Dono não identificável, sem data.
- **Adotar GStack** ⚠️ — reconhecida sobreposição com a biblioteca de skills que o time já desenha; ninguém assumiu a avaliação.
- **Arquitetura final combinando os modelos** — pergunta explícita do time ("ainda estou um pouco confuso como funciona a arquitetura final… como eles atuam juntos?"). Respondida com o fluxo pessoal do apresentador (DeepSeek → Perplexity → Claude Code), **sem desenho para a smartside**.

---

## 2. Compromissos

> ⚠️ **Atribuição comprometida pela fonte.** Onde o dono não é dedutível com segurança, está marcado — não foi atribuído por chute. Nenhum compromisso foi propagado para páginas de pessoa nesta extração (decisão do usuário).

| Compromisso | Dono | Prazo |
|---|---|---|
| Enviar o **GitHub do Leopold + o deck (PowerPoint)** para o Flávio, que repassa ao time *(ACTION ITEM @85:15)* | Jonh Alex | Na hora / imediato |
| Enviar a **gravação desta reunião** para o Jonh Alex *(ACTION ITEM @0:12)* | ⚠️ smartside, não identificável | — |
| Enviar **áudio de 1 min** para o Flávio ouvir no Uber *(ACTION ITEM @76:37)* | ⚠️ ambíguo no transcript | Imediato |
| Enviar os **links das ferramentas no canal TechOps** — GStack, OpenVicain e Serena declarados como já enviados; **Pandas em dúvida** ("faltou algum? acho que sim") | Jonh Alex | Parcialmente feito na call |
| **Testar Serena** e colocar para rodar | ⚠️ smartside, não identificável | Sem data ("preciso de uma brecha") |
| Adicionar **suporte a Codex** no Leopold (hoje só Claude) | Jonh Alex | Roadmap, sem data |
| Falar com **o pessoal da Shiva** sobre a assinatura do Claude cancelada | Jonh Alex | — |
| Resetar o **AnyDesk** em casa *(ACTION ITEM @42:13)* — item operacional trivial, registrado só por fidelidade | ⚠️ não identificável | Ao chegar em casa |

**Nenhum prazo absoluto foi acordado em toda a reunião.**

---

## 3. Preferências de trabalho

- **Canal interno:** **TechOps** (Discord) segue sendo onde circulam links e referências técnicas — consistente com [[2026-07-30 smartside.ai - Company Brain (Segundo Cérebro)|30/jul]].
- **Terminal/CLI acima de app e web** — "o CLI é mais completo; o app e o web são baseados nele, mas menos completos".
- **Não buscar a ferramenta perfeita** — pegar as disponíveis e adaptar ao próprio workflow, usando o Claude para adaptar.
- **Não reinventar a solução do cliente** — aprendizado explícito de projeto anterior em que a equipe técnica do cliente não conseguiu manter um desenho próprio.
- **Self-host de open source** quando a máquina aguentar.
- Do lado da smartside: **n8n é a base de automação**; **Hermes é usado pouco**; houve cuidado explícito de **não abrir workflow de cliente na tela** ("a maior parte não é interno, é projeto pro cliente, então não pode").

---

## 4. Insights-chave

Consolidados em detalhe em **[[Stack de Desenvolvimento com IA - Ferramentas e Workflow]]**. Os quatro que mais mudam decisão:

1. **O harness roda local porque o custo do contexto foi empurrado para a sua máquina** — e é justamente isso que permite **se injetar dentro dele** (hooks, skills, MCP, memória) em vez de construir ferramenta nova por fora.
2. **System Prompt vs. harness/agente** é a decisão de arquitetura reutilizável: exemplos no prompt **pesam** e enviesam a saída (LLM é next-token), então system prompt serve a nicho pequeno e contido; para múltiplos pontos de coleta de contexto, entregue a caixa de ferramentas + um caminho orientado e **deixe o modelo escolher de onde puxar**. Anti-padrão: afirmar no prompt onde o dado está.
3. **Serena existe para entender código; economia de token é consequência.** Busca por símbolo monta a árvore de dependências — árvore de autenticação completa com 3% de janela de contexto.
4. **"O uso de IA é saber o que dá para pedir."** O gargalo não é a ferramenta, é o vocabulário de quem pede — daí o NotebookLM entrar no fluxo como etapa de *descobrir o pedível*, não de aprender a fundo.

---

## Riscos e sinalizações

- 🔴 **Automação de redes sociais relatada como sucesso.** O caso do Comet — agente que "foi atrás no LinkedIn, Reddit, Facebook, saiu postando, comentando" para gerar 10 acessos numa landing page — foi apresentado como win e **não foi contestado na call**. Postagem/comentário automatizados em plataformas de terceiros violam ToS, expõem a bloqueio de conta e a dano reputacional, e conflitam com "não pegamos atalhos morais para bater metas" ([[SOUL]]). **Vale ser dito ao time antes que alguém replique.**
- 🔴 **Números financeiros inconsistentes — não usar.** Sobre créditos de cloud o transcript encadeia "10k… pegou 10k, a gente pegou 20k… pegou 100k, a gente pegou 100 mil dólares" (AWS), mais GCP "infinita em dois anos" condicionada a negociação e OpenAI "~5 mil dólares essa semana"; e "o Dan gastou 10k de dólar, enquanto eu gastei 200k dólar com a assinatura". **Nada disso foi registrado como fato** — ver [[smartside.ai]]. Reconferir na fonte antes de qualquer dimensionamento ou proposta.
- 🟡 **Transcrição inutilizável para responsabilização — segunda ocorrência.** Duas reuniões consecutivas (30/jul e 03/ago) tiveram compromissos perdidos por colapso de locutor no Fathom. Se atas viraram insumo do segundo cérebro, **isso é uma falha de processo, não um detalhe** — vale testar diarização/outra ferramenta ou pedir que cada um se identifique ao falar.
- 🟡 **Recomendações com base de evidência fina.** Leopold em modo workflow: 2 testes. PRD do Perplexity: 2 testes. Reescrever o agente de atendimento em código a partir disso é decisão de ~2 semanas apoiada em amostra de 2.
- 🟡 **Sobreposição não endereçada.** GStack (~23 skills) cobre boa parte do que o time está construindo à mão em [[smartside.ai - Workspace de Desenvolvimento (Harness)]]. Ninguém ficou dono de comparar — risco de continuar construindo o que já existe.
- 🟡 **Nenhum dono e nenhuma data** saíram de 87 minutos de conteúdo denso. O conhecimento entrou no vault; a ação não tem responsável.

## Notas relacionadas
[[Stack de Desenvolvimento com IA - Ferramentas e Workflow]] · [[smartside.ai]] · [[smartside.ai - Workspace de Desenvolvimento (Harness)]] · [[smartside.ai - Company Brain (Segundo Cérebro)]] · [[Harness Engineering - Fábrica de Software]] · [[2026-07-30 smartside.ai - Company Brain (Segundo Cérebro)]] · [[00 - MOC Interno smartside.ai]]
