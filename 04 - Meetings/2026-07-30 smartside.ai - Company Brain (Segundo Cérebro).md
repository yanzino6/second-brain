---
type: meeting
date: 2026-07-30
tags: [reuniao, interno, smartside, company-brain, second-brain, harness-engineering, ia]
attendees: ["[[Yan Simmer]]", "[[Matheus Simões]]", "[[Arthur Tosi]]"]
project: ["[[smartside.ai - Company Brain (Segundo Cérebro)]]", "[[smartside.ai - Workspace de Desenvolvimento (Harness)]]"]
company: "[[smartside.ai]]"
source: "07 - Archive/Transcrição - 2nd Brain smartside.md"
recording: https://fathom.video/share/F7YiYAY1dsaW_ub4sog3-CpREAyACwHm
duration: 74min
---

# 2026-07-30 · smartside.ai — Company Brain (Segundo Cérebro)

> Reunião **interna**. Nenhum cliente envolvido. Pauta iniciada por [[Yan Simmer]] (proposta de transformar seu segundo cérebro em produto interno) e derivou para Harness Engineering e para o app financeiro.

**Participantes:** [[Yan Simmer]] · [[Matheus Simões]] · [[Arthur Tosi]]
**Citados (ausentes):** [[Pedro]] · [[Matheus Andrade]] · [[José Lucas Ribeiro]] ("Zé") · [[Victor Hugo]] · [[Flávio Parreiras]] · Edu

---

## 1. Decisões

### Firmes
- **Parar de tratar o problema como "Company Brain" e olhar para a dor concreta.** Por: [[Matheus Simões]]. Motivo: Company Brain é uma abstração ampla, sem *job to be done* único — sem definir o caso de uso, não há como definir o que construir nem o que ele **não** será.
- **A dor real da smartside.ai não é um Company Brain, é um agente de gestão de tarefas e projetos.** Por: [[Matheus Simões]], com concordância de [[Yan Simmer]]. Motivo: o maior beneficiário é a camada administrativa e de relacionamento com cliente, não a camada técnica.
- **Notion será o repositório de conhecimento compartilhado.** Por: [[Matheus Simões]]. Motivo: o Notion já é uma árvore de arquivos markdown com hierarquia e link nativos; resolve repositório compartilhado **e** permissão por pessoa; o MCP do Notion dá o acesso ao agente. Caminho mais simples e menos trabalhoso para validar.
- **Plataforma própria só depois da validação no Notion.** Por: [[Matheus Simões]]. Motivo: "usa o Notion, funcionou, ficou bom — aí a gente faz uma plataforma própria".
- **Consulta via MCP + index ("LLM RAG"), não Vector Store / RAG semântico.** Por: [[Matheus Simões]]. Motivo: um CLAUDE.md/index descrevendo bem a estrutura do repositório já permite ao agente saber onde está cada bloco de informação e consultar direcionado — dispensa embeddings.
- **Company Brain = componente estático do second brain individual, distribuído como template/repositório versionado.** Por: [[Matheus Simões]]. Motivo: o contexto do dia a dia é pessoal; a camada da empresa precisa de curadoria controlada e **não deve ser "viva"** — o agente não mexe nela, ela só se atualiza puxando o repositório. Pasta pessoal fica fora (gitignore).
- **Curadoria humana obrigatória — papel de "guardião".** Por: [[Matheus Simões]]. Motivo: base desatualizada não é neutra, ela **piora** o agente. Alguém valida o que entra e faz a análise retroativa do que fica obsoleto.
- **Produto só nasce de dor interna já resolvida.** Por: [[Matheus Simões]] (diretriz vigente da empresa). Motivo: só se vira produto se a dor for replicável e o mercado grande. Primeiro passo é resolver o problema interno.
- **Migração Discord → Slack.** Por: [[Matheus Simões]]. Motivo: mais integrações com outras ferramentas (concordância de [[Yan Simmer]]).

### Descartadas na discussão
- **Grafo próprio / Obsidian como base compartilhada** — proposta de [[Yan Simmer]]; superada pela escolha do Notion.
- **Supabase / bucket / Data Lake ou Data Warehouse como repositório** — discutido e abandonado; o problema não era de armazenamento, era de acesso compartilhado + curadoria.
- **Vector Store (Supabase / Pinecone) com metadados para busca semântica** — proposta de [[Yan Simmer]]; substituída pelo index + MCP.

### Em aberto (sem decisão)
- **Escopo e casos de uso do Company Brain** — bloqueador declarado de todas as próximas decisões. É o próximo passo.
- **Controle de permissão na camada de conector/MCP.** No Notion a permissão é nativa; via MCP não há resposta ainda de como garantir que cada pessoa acesse só o que faz sentido.
- **Company Brain como feature comercial** dentro da plataforma do cliente (ao lado de Agent Catalog e Observability Panel), alimentado pela ferramenta de diagnóstico automatizado, com chatbot para o cliente ideiar projetos e cair no time de vendas. Ideia de [[Matheus Simões]] + [[Yan Simmer]], sem definição.
- **Padronização com o segundo cérebro do [[Matheus Andrade]]** — [[Arthur Tosi]] propôs reunião oficial; sem data.

---

## 2. Compromissos

### smartside.ai — [[Yan Simmer]]
- [ ] Definir escopo e casos de uso do Company Brain com [[Arthur Tosi]] e [[Pedro]]; só depois estruturar a página/workspace no Notion *(ACTION ITEM @40:20)*
- [ ] Clonar o repositório de workspace de desenvolvimento do [[Matheus Simões]], rodar o setup do Claude na raiz da pasta e testar o fluxo *(ACTION ITEM @1:04:30)*
- [x] Enviar o usuário do GitHub para o [[Matheus Simões]] — feito na call

### smartside.ai — [[Arthur Tosi]]
- [ ] Clonar o repositório do [[Matheus Simões]], rodar o setup e testar o fluxo *(ACTION ITEM @1:04:30)*
- [ ] Ler o artigo sobre Harness Engineering — prometido para **30/jul/2026** ("vou ler hoje, mais tarde")
- [ ] Avaliar embutir o **Grill Me With Docs** nas skills iniciais do fluxo de desenvolvimento
- [ ] Propor reunião oficial com [[Matheus Andrade]] para padronizar as duas abordagens de segundo cérebro
- [x] Enviar o usuário do GitHub para o [[Matheus Simões]] — feito na call

### smartside.ai — [[Matheus Simões]]
- [x] Convidar [[Yan Simmer]] e [[Arthur Tosi]] para o repositório do workspace de desenvolvimento — feito na call
- [ ] Enviar a ata e a gravação desta reunião no canal **TechOps** (Discord) e no WhatsApp
- [x] Enviar o vídeo sobre fábrica de software no TechOps — feito na call
- [ ] Puxar [[Yan Simmer]] para a construção do Notion junto com [[Arthur Tosi]] e [[Pedro]]
- [ ] Pesquisar e entender o que é **lint** (assumiu não conhecer, e o conceito é central no fluxo de validação determinística)

> Datas: nenhum prazo absoluto foi acordado além da leitura do artigo por [[Arthur Tosi]] em 30/jul/2026. **Todos os demais itens estão sem data.**

---

## 3. Preferências de trabalho

- **Canal interno:** Discord hoje, **migrando para Slack**. Canal **TechOps** é onde circulam links, vídeos e referências técnicas.
- Atas e gravações são distribuídas **em dois canais** (TechOps + WhatsApp).
- [[Matheus Simões]] prefere **validar com ferramenta existente antes de construir** — "do jeito mais simples possível, da forma que for menos trabalhosa".
- [[Matheus Simões]] exige **caso de uso definido antes da arquitetura** — "definir isso é o papel mais importante".
- Aprendizado por conteúdo compartilhado no time; [[Matheus Simões]] recomenda **assistir à fonte, não o resumo** ("resumi mais e porcamente").
- [[Arthur Tosi]] quer sair da verificação linha a linha e operar por **gerência de decisões** — reconhece que a revisão manual exaustiva cansa e degenera em confiança cega.

---

## 4. Insights-chave

### Sobre gestão de conhecimento
- **Company Brain é abstração, não produto.** Tem vários *jobs to be done*; sem recorte vira "birimbolo de informações".
- **Garbage in, garbage out em escala de agente.** Base desatualizada não é inerte — ela influencia negativamente o agente. Exige rotina de sanitização e análise retroativa: *"se isso está entrando agora, o que já não faz mais sentido?"*.
- **Loop de perguntas noturnas** (referência estudada por [[Yan Simmer]]): em vez de só organizar, o sistema gera um documento de perguntas sobre o que entrou — *isso é relevante? por que essa decisão foi tomada? quem é responsável? qual o status?*. Camada de validação **autotreinável**: captura a decisão uma vez e não repergunta.
- **LLM RAG > Vector Store** para este caso: index bem escrito + estrutura documentada no CLAUDE.md permitem consulta direcionada, sem embeddings.
- **Trade-off local vs. compartilhado:** dentro da pasta o Claude Code navega livremente; via MCP a consulta é direcionada e depende de documentação boa dos métodos e da estrutura.
- **Data Lake vs Warehouse vs Lakehouse** (contexto levantado por [[Yan Simmer]]): Warehouse = dados categorizados, uso em BI; Lake = dados brutos não categorizados, uso em treino de ML. Não aplicável ao caso — descartado.

### Alternativa que emergiu: Chief of Staff / Hermes Agent
Em vez de Company Brain, um agente com papel de BPO de gestão:
- Conectado a Linear, Notion, grupos de WhatsApp com cliente, Slack/Discord.
- Cobra pessoas, recobra, mantém boards atualizados (ClickUp/Linear).
- Manda briefing **antes** das reuniões — ex.: estado das tarefas dos devs na caixa do [[Flávio Parreiras]] antes do alinhamento de projeto (done / em aberto / em progresso).
- Beneficiários diretos apontados por [[Yan Simmer]]: [[José Lucas Ribeiro]], [[Victor Hugo]], Edu (vendas/upsell/cross-sell), [[Pedro]] (cobrança).

### Harness Engineering
Tese central da segunda metade da reunião — detalhe completo em [[Harness Engineering - Fábrica de Software]] e [[smartside.ai - Workspace de Desenvolvimento (Harness)]].
- **"O engenheiro não desenvolve código, desenvolve a fábrica que desenvolve código."**
- Três atores de geração de valor: **engenheiro, agente e código**. O código determinístico (lint, format, teste, CI/CD) é a camada de confiança — *"a coisa mais rápida, escalável e confiável que existe é o código"*.
- Estado atual da smartside.ai: planning → waves de build em worktrees paralelas → teste e review automáticos; só volta ao humano se falhar 3× no loop.
- Conexão declarada com o conceito que **Edmar (Rock Content)** apresentou e que virou insumo do repositório de workflow atual — o vídeo "sobe um nível" a partir dali.

### Skills como unidade de composição
[[Arthur Tosi]] e [[Matheus Simões]] convergiram numa biblioteca de ~10 skills cobrindo o projeto de ponta a ponta: iniciar projeto → entrevista (**Grill Me With Docs**) → PRD → **ADRs** (decisões de arquitetura, imutáveis historicamente) → arquivo de domínio/glossário → issue tracker → 1 arquivo por issue (status, critério de aceite, bloqueios) → tarefa → review → simplificar código → procurar lib → breakdown em issues.

---

## 5. Assunto paralelo — app financeiro

> Tema descolado da pauta, discutido no fim da call durante um compartilhamento de tela.

- App financeiro interno já roda com **dados reais**: lançamento de entradas/saídas, clientes e projetos por empresa, datas de emissão/nota/pagamento, previsão das próximas notas (emissão em lote no dia 1º), a pagar × a receber, atrasados.
- Painéis previstos: **resumo**, **visão de caixa** (mais completa) e **visão de resultado**. Faltam os gráficos.
- **Problema identificado:** performance ruim — recarrega todos os dados a cada troca de página.
- Encaminhamento técnico proposto por [[Matheus Simões]]: expor **CRUD** e criar um **MCP** (no n8n ou próprio) para operar o app conversando com o Claude em vez de abrir o painel — e sem expor token; e implementar **cache**.

**Compromissos** *(ACTION ITEMs @1:08:33 e @1:11:13)*:
- [ ] Criar endpoints CRUD do app financeiro e expor via MCP — ⚠️ **dono não identificável no transcript** (a transcrição colapsou o diálogo sob um único locutor; ver [[Pedro]])
- [ ] Implementar cache no app financeiro para corrigir a performance — ⚠️ mesmo caso
- [ ] Remover o cliente "Katia Brun" do cadastro (já deveria ter saído) — ⚠️ mesmo caso

---

## Notas relacionadas
[[smartside.ai]] · [[smartside.ai - Company Brain (Segundo Cérebro)]] · [[smartside.ai - Workspace de Desenvolvimento (Harness)]] · [[Harness Engineering - Fábrica de Software]] · [[00 - MOC Interno smartside.ai]]
