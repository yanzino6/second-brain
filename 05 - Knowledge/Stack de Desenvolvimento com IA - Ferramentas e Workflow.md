---
type: knowledge
tags: [conhecimento, ia, desenvolvimento, harness, claude-code, ferramentas, workflow, agentes, mcp, skills, prompt-engineering]
links: ["[[Harness Engineering - Fábrica de Software]]", "[[smartside.ai - Workspace de Desenvolvimento (Harness)]]", "[[smartside.ai - Company Brain (Segundo Cérebro)]]", "[[2026-08-03 Stack de Desenvolvimento com IA (Jonh Alex)]]", "[[smartside.ai]]"]
updated: 2026-08-03
---

# Stack de Desenvolvimento com IA — Ferramentas e Workflow

> Conhecimento **geral e reutilizável** (não pertence a nenhum cliente). Extraído da sessão de transferência de conhecimento de **03/ago/2026** — ver [[2026-08-03 Stack de Desenvolvimento com IA (Jonh Alex)]].
> Fonte: apresentação de **Jonh Alex (Jonhvmp)**, convidado externo. É o stack **dele**, relatado por ele — a maior parte não foi verificada de forma independente. Ver [Alertas](#alertas-e-pontos-não-verificados).

> [!warning] Decodificação do transcript
> A transcrição colapsou as 87 min num único locutor e destruiu vários nomes próprios. **"ARNs" / "Arns" / "Arnes" / "ARDS" / "artes" = harness** (a leitura fica coerente em todas as ocorrências e casa com [[Harness Engineering - Fábrica de Software]]). Nomes de ferramentas com grafia incerta estão marcados com ⚠️.

---

## 1. Tese de fundo: por que o harness roda na sua máquina

- O Claude Code **não tem system prompt oculto** — workflow, prompts e guias ficam em arquivos na pasta `.claude` do usuário (global e por projeto).
- Leitura do porquê: manter esse contexto em nuvem, para milhões de usuários, seria custo proibitivo (S3 + tráfego). **A Anthropic empurrou o custo do contexto para a máquina do cliente.**
- Consequência estratégica — **o ponto central da apresentação**:
  > Como os prompts e o workflow estão no disco, você consegue **se injetar dentro do harness** em vez de construir uma ferramenta nova por fora.
- Padrão de ação decorrente: quer melhorar seu workflow? **não crie ferramenta nova — crie algo que se injeta ali dentro** (hooks, skills, MCP, memória).
- Corolário: mexer nesses arquivos mexe **na qualidade da ferramenta**. O produto é o CLI; o que faz ele seguir o seu padrão está na sua máquina.
- CLI > app/web: app e web são baseados no CLI, mas **menos completos**; só o local puxa o `CLAUDE.md` global.

---

## 2. Ferramentas do stack

### Serena — busca de código por símbolo (MCP)
- Em vez de ler o arquivo inteiro, opera por **símbolos**: `find_symbol`, `referencing_symbols`, `replace_symbol_body`.
- Programação é hierárquica (H1 → H2 → Button); ao buscar o símbolo, ele **monta a árvore de dependências** daquele símbolo — o que referencia, o que é componente compartilhado, onde está o contexto/guard/middleware.
- **Propósito é entender código. Redução de custo é consequência, não objetivo.**
  - Anti-caso: "muda a cor do botão" → o agente lê os +500 linhas do arquivo de login inteiro.
  - Com Serena: busca `Button` / `Google Login`, traz só as linhas e o que se relaciona com aquilo.
  - Contra-argumento importante: a alteração real raramente está num arquivo só (adicionar login com Facebook mexe em lógica, estado de sessão, arquivos compartilhados) — a **árvore** é o que resolve, não o recorte.
- Tem **memória de projeto** e onboarding próprio: na inicialização lê a árvore e as memórias, e entende decisões importantes do projeto.
- Forçado via **hook de inicialização de sessão** — "usa Serena independente da tarefa, sempre".
- Demo observada: árvore completa de autenticação (hidratação, refresh token, sign out, seleção/reset de sessão) retornada com **3% de janela de contexto**.
- Uso lateral valioso: **apresentar arquitetura a terceiros e onboarding de dev** — "o cara já fica sabendo a parte de autenticação completa do software".
- Consenso sobre perda de qualidade: **não há** consenso na comunidade (pesquisa feita durante a própria call).

### GStack ⚠️ *(grafia incerta: aparece como G-Stack / JStack / GSTEC)* — biblioteca de skills
- ~**23 skills** cobrindo uma empresa de ponta a ponta: produto, marketing, design, QA, engenharia, CEO.
- Casos de uso relatados:
  - **Skill "CEO"** — debate estratégico sobre um projeto/cliente quando não há um humano sênior disponível.
  - **Skill de produto** — qualifica uma feature com perguntas até provar que ela faz sentido, ou matar a ideia. Ataca o vício de dev: *criar, criar, criar e ninguém usar*.
  - **Skill de QA** — se comporta como um usuário X, abre o navegador e **testa o fluxo de verdade** (clica nos botões), em vez de você testar na mão.
  - **Planejamento** — faz perguntas de arquitetura reais (qual arquitetura, quantos clientes vão acessar, qual latência você precisa), não perguntas rasas.
- Encaixe direto na etapa de **PRD/PDD** já existente no fluxo da smartside.ai.
- Perfil de quem ganha mais: **solo founder e empresas enxutas** — uma pessoa roda a gestão inteira.
- ⚠️ Autoria atribuída na call a "Gary … um dos donos da iCombinator" (provavelmente **Y Combinator**) — **não verificado**.

### OpenVicain ⚠️ + "Wovman"/OVM — memória RAG autônoma local
- ⚠️ Grafia do produto base incerta (OpenVicain / OpenVic / OpenViking). **"Wovman" (OVM) é o nome que o próprio Jonh Alex deu à camada dele** — não é um produto de mercado com esse nome.
- **Database local em SQLite**, conecta a qualquer LLM e também via MCP (inclusive de fora da rede). Instalação simples.
- Como funciona: ao mencionar um assunto na sessão, faz busca RAG nas memórias, **monta uma frase de contexto** a partir do prompt do usuário e **injeta na sessão** só o que é útil.
- Ganho: qualquer sessão nova lembra decisões anteriores — "falei com o cliente e tivemos essas decisões, olha a transcrição" → fica salvo, sem você arquivar nada à mão.
- Recursos: **múltiplos usuários/perfis** com memórias separadas, compartilhamento de contexto de sessão entre chats, **skills compartilhadas** entre perfis.
- Descrito como "um cofre no seu computador — tipo um Obsidian, só que bem estruturado".
- **Custo real medido:** US$ 0,37 de embeddings (OpenAI) entre 19/jul e 03/ago, sobre US$ 5 carregados. Conclusão: **não vale rodar modelo local** — o modelo barato de API resolve. Alternativa citada: AWS Bedrock ⚠️ ("Bedank" no transcript).
- Método de decisão que gerou a escolha (vale mais que a ferramenta):
  > Preciso de X. Existe pronto? Existe → uso e adapto. Não existe → só então construo.

### Temporal — runtime de orquestração de longa duração
- **Open source**, self-hostável (máquina ou Docker); ~**22 mil stars**.
- Roda workflows por **semanas ou meses** com a IA/agente vivo. Caso relatado: manteve o Leopold rodando **2,7 dias** contínuos.
- Recursos: filas, timeout por tarefa, **retry automático com correção** (deu erro → corrige e tenta de novo), SDK, múltiplos agentes e workflows entrelaçados e isolados.
- **Human-in-the-loop nativo:** o workflow faz a pergunta e o Temporal **segura o agente** esperando a resposta humana — você fica na decisão do output.
  - Valor específico em **Enterprise**: coloca o engenheiro/especialista do cliente no meio do fluxo, e o resultado fica melhor do que sem ele.
- Outros use cases prontos: **CI/CD** (pipeline que valida todos os pontos de segurança antes de ir para produção), onboarding de novo usuário na plataforma sem quebrar o fluxo.
- Monetização: modelo tipo **Firecrawl** — open source disponível, mas a maioria paga a nuvem porque o self-host é pesado.
- ⚠️ Afirmado na call que **Anthropic e OpenAI usam** — não verificado.
- **Oportunidade comercial levantada:** oferecer como componente de projeto Enterprise e cobrar por isso.

### Leopold — harness pessoal do apresentador
- Ferramenta própria do Jonh Alex, **open source no GitHub dele** (publicado, não divulgado). Só para Claude; **Codex ainda não suportado** (no roadmap dele).
- **Instalação one-time** que faz o setup completo: instala Serena, instala GStack se não houver, Enhancer, hooks e skills; **Temporal por baixo dos panos**; OVM opcional (é a única parte com custo).
- Traz documentação própria gerada com **MkDocs**.
- **Fluxo:**
  1. **Triage** → **Backlog** → pega a tarefa
  2. **Brief** — debate estruturado via GStack, com perguntas, que captura a missão e o jeito de decidir. Produz: **missão**, **persona** (como o agente atua no projeto), **guardrails** e **plano**.
     - Olha o histórico de como a pessoa trabalha com IA.
     - **Guardrails padrão: `git commit` bloqueado e proibido subir na main.**
  3. **Artefatos** — começam vazios e vão sendo escritos com **as decisões e o porquê** ("decidi por esse caminho porque…").
  4. Execução em dois modos: **run** (agente único, sequencial) ou **workflow** (vários agentes em paralelo, com status e stop).
  5. **Camada de aprendizado** — acumula as decisões e as reaproveita nas tarefas seguintes ("aprendi que a arquitetura tem esse padrão, que o cliente é X…").
- **Diferença central vs. Ralph Loop:** o Ralph só segue o PRD até o fim. Aqui o agente **se auto-responde** às perguntas de confirmação do Claude ("posso seguir com essa parte?") — e ao responder **reformula o próximo passo** ("continue, porém seguindo desta forma, para obter este resultado"). É o que sustenta a autonomia longa.
- ⚠️ Base de evidência pequena: **2 testes** do modo workflow.

### Prompt Enhancer + formato RLHF
- Premissa: **a IA escreve prompt melhor que o humano.** O enhancer reestrutura o seu prompt para cair **na distribuição em que o modelo foi treinado** — e recoloca o que você esqueceu.
- Dá para fazer sem ferramenta: pedir a estrutura no Perplexity e enviar o prompt resultante.
- **Formato RLHF:** arquivo markdown curto (~20 linhas) com overview + a tarefa completa a ser executada 100% do início ao fim.
  - Por que funciona: os modelos foram treinados por reforço guiado por humano, otimizados para **recompensa rápida** (agradar) — por isso são mais diretos e "continentes" e respondem melhor a esse formato.

---

## 3. Princípio de arquitetura: System Prompt **vs.** Harness/Agente

A decisão mais reutilizável da sessão.

| | **System Prompt** | **Harness / agente** |
|---|---|---|
| Quando usar | Nicho pequeno e contido | Muitos dados, várias áreas, **vários pontos de coleta de contexto** |
| Exemplo dado | Atendimento de padaria | Cliente industrial com ERP + segundo sistema |
| Como opera | Você descreve o fluxo e a personalidade | Você entrega a **caixa de ferramentas** (Gmail, Outlook, Calendar, APIs) + um **caminho orientado** |
| Quem decide | Você | **O modelo decide o que fazer**, dentro do caminho |

- **Exemplos no prompt têm peso.** LLM é next-token: se você escreve "responda o cliente desta forma", ela **pesa para aquele lado**. Repetir "padaria" faz a saída inteira pesar para padaria — ótimo quando o nicho é pequeno, ruim quando não é.
- **Anti-padrão:** afirmar no prompt **onde** o dado está ("puxa daqui"). Se não estiver lá, o fluxo morre.
- **Padrão:** deixar o agente avaliar qual é o melhor ponto de coleta para aquele contexto — não achou no A, vai no B, e não para na primeira falha. **É isso que vira autonomia.**
- "Caminho orientado" = labirinto de hamster: liberdade de decisão dentro de um trajeto que leva a um ponto.
- Instrução prática para gerar artefatos: pedir **"AI Native", sem exemplos**, justamente para não enviesar.

---

## 4. Cadeia de ferramentas por etapa do trabalho

O workflow declarado, na ordem:

| Etapa | Ferramenta | Uso |
|---|---|---|
| **Entender o problema** | **DeepSeek** (reasoning) | Antes de codar: quebrar a tarefa, entender o resultado esperado. Também: jogar a transcrição do cliente e pedir "pense bem em todos os problemas e vamos discutir soluções". Considerado um dos poucos modelos de raciocínio realmente lento e eficiente. |
| **Pesquisar e especificar** | **Perplexity** (Deep Research) | **Uso principal: gerar o PRD.** Pesquisa o nicho + a empresa + a prática de PRD e devolve o documento. Também gera **personas pesquisadas em comunidades reais** (ex.: advogado → comunidades de advogados), em tempo real. |
| **Executar** | **Claude Code + Leopold** | Terminal. Do PRD ao software. |
| **Saber o que pedir** | **NotebookLM** (Gemini) | Onde ele aprendeu a usar IA. Pesquisa um tema, gera **mapa mental** → pega um tópico → pede o resumo → cola no Claude. Leitura leve, o objetivo **não é dominar o assunto**. |
| **Design e front** | **Gemini** (modo **Canvas**) | Considerado **o melhor em UI/design** — "ninguém diz que foi feito com IA". Usado via CLI, não API. Também texto, pesquisa e aprendizagem. |
| **Conversar e visualizar** | **ChatGPT** (modo áudio, modo work) | Modo áudio com acesso à máquina: fala e ele desenvolve. Ajustar proposta comercial a partir da gravação da reunião. Imagens e **SVG** para explicar ao cliente o que seria complexo em texto. |
| **Agir no navegador** | **Comet** (Perplexity) | Navegador próprio → **mais autonomia** que a extensão do Claude (que "só tira print"). ⚠️ Ver alerta. |
| **Acompanhar o mercado** | **Panda(s)** ⚠️ | Agregador centralizado: Product Hunt, GitHub, Dribbble, TechMundo, referências de design. |
| **Documentar** | **MkDocs** | Markdown puro → site estruturado, responsivo, multi-idioma, dark/light, menu, **sem input manual**. Recomendado como **entregável cobrável** ao cliente. |

**Insight que amarra a cadeia:**
> "O uso de IA é isso: você precisa saber **o que dá para fazer** para conseguir pedir. Não é 'faça aí'. Faça aí o quê?"

Comparativo concreto do impacto: pedido genérico *"cria um harness aí"* vs. o pedido informado — *"harness para este contexto, com workflows dinâmicos gerados sob demanda, múltiplos agentes com janelas de contexto limpas, verificação adversária por IA usando um modelo barato, recuperável e adaptável a novos contextos"*. Saber o vocabulário **é** a vantagem.

**Validação prática do PRD:** PRD gerado no Perplexity + Leopold produziu sistema completo em 2 de 2 tentativas. Case Ping Pong: Electron multiplataforma (Windows/Mac), câmera em tempo real filmando a mesa, conexão remota, calibração, torneio e jogadores — tudo especificado no PRD e construído.

---

## 5. Princípios de adoção de ferramenta

- **Não espere a ferramenta perfeita.** Pegue as disponíveis e adapte ao *seu* workflow — usando o próprio Claude para adaptar. Você desenvolve, conversa com cliente e decide diferente de todo mundo; a ferramenta ideal para outra pessoa não é a sua.
- Sobre a ansiedade de acompanhar tudo (pergunta feita na call): ou você decide *"isso é bom o suficiente para mim"* e segue, ou tenta estar sempre na melhor — e enlouquece. Não há terceira via.
- **Não reinventar a solução do cliente.** Aprendizado relatado de projeto anterior: entregou desenho próprio e a **equipe técnica do cliente não conseguiu entender/manter**. Desde então, mesmo tendo o desenho na cabeça, busca ativamente uma biblioteca/ferramenta existente.
- **Assinatura > API** para trabalho de codificação — ver [Custos](#6-custos-e-números-observados).
- Preferência por **self-host de open source** quando a máquina aguenta.

---

## 6. Custos e números observados

> ⚠️ Todos relatados de memória em call, **vários inconsistentes no transcript**. Não usar em proposta comercial sem reconferir.

- **Memória RAG (OVM):** US$ 0,37 em ~15 dias — irrisório. Decisão de não rodar modelo local baseada nisso.
- **Assinatura vs. API:** ordem de grandeza citada de US$ 10k em API contra o valor de assinatura para trabalho equivalente. ⚠️ Os números falados ("200k dólar" de assinatura) são incoerentes — a conclusão qualitativa **"API não vale para codar"** é o que se sustenta.
- **Suspeita levantada sobre créditos:** o cálculo de consumo de crédito "não bate" com o valor real — crédito parece queimar mais rápido. Vale medir antes de dimensionar um projeto em cima de crédito.
- **Janela de contexto:** ~258k no CLI contra ~1M no aplicativo ⚠️ (números do transcript, não conferidos).

---

## 7. Alertas e pontos não verificados

- 🔴 **Comet / automação de redes sociais — risco real.** Foi relatado como sucesso um agente que, para conseguir 10 acessos numa landing page, "foi atrás no LinkedIn, Reddit, Facebook, saiu postando, comentando" até trazer as pessoas.
  **Não adotar como prática.** Postagem e comentário automatizados em plataformas de terceiros violam ToS, expõem a bloqueio de conta e a dano reputacional, e conflitam com **Transparência** e com "não pegamos atalhos morais" ([[SOUL]]). A capacidade do navegador agêntico é legítima; **esse uso não é.**
- ⚠️ **Grafias não confirmadas:** GStack/G-Stack/JStack/GSTEC · OpenVicain/OpenVic/OpenViking · Panda(s) · Bedrock ("Bedank"). Confirmar antes de instalar ou citar.
- ⚠️ **"Hermes"** foi apresentado como ferramenta self-hostável (cron jobs, modo Kanban, auto-correção de erro) que o time usa pouco. **Não confundir** com o "Hermes / Chief of Staff" que [[Yan Simmer]] e [[Matheus Simões]] usaram como *nome de conceito* para um agente de gestão em [[2026-07-30 smartside.ai - Company Brain (Segundo Cérebro)|30/jul]] — são coisas distintas com o mesmo nome no vault.
- ⚠️ **Autorias e adoções afirmadas sem fonte:** GStack criado por "Gary" da Y Combinator; Temporal usado por Anthropic e OpenAI; Gemini como "absoluto" em design.
- ⚠️ **Base de evidência fina:** Leopold em modo workflow foi testado 2×; o PRD do Perplexity, 2×.
- ⚠️ **Referência de mercado citada:** "Gamefic" ⚠️ — empresa que orquestraria meta-ads e blog inteiramente por agentes. Não verificada.

---

## Onde isso encaixa na smartside.ai

- **Injeção no harness em vez de ferramenta nova** → reforça a tese de [[Harness Engineering - Fábrica de Software]] e o desenho de [[smartside.ai - Workspace de Desenvolvimento (Harness)]].
- **Serena (busca por símbolo) + memória local** → candidato direto à *camada de contexto* que falta no workspace, e ao caso "Claude Code sobre a documentação interna" do [[smartside.ai - Company Brain (Segundo Cérebro)]] — com a vantagem de **não exigir Vector Store**, coerente com a decisão de 30/jul (MCP + index).
- **GStack** → sobreposição forte com a biblioteca de ~10 skills desenhada pelo time; avaliar adotar em vez de construir.
- **Temporal** → cobre o "manter agente vivo" e o human-in-the-loop que o fluxo de waves ainda não tem; possível componente cobrável em Enterprise.
- **MkDocs** → entregável de documentação de baixo custo e alto valor percebido.

## Notas relacionadas
[[2026-08-03 Stack de Desenvolvimento com IA (Jonh Alex)]] · [[Harness Engineering - Fábrica de Software]] · [[smartside.ai - Workspace de Desenvolvimento (Harness)]] · [[smartside.ai - Company Brain (Segundo Cérebro)]] · [[00 - MOC Interno smartside.ai]]
