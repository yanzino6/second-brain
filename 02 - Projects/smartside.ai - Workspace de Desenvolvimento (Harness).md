---
type: project
tags: [projeto, interno, smartside, harness, skills, claude-code, workflow-desenvolvimento]
status: em-teste
company: "[[smartside.ai]]"
owner: "[[Matheus Simões]]"
links: ["[[smartside.ai]]", "[[2026-07-30 smartside.ai - Company Brain (Segundo Cérebro)]]", "[[Harness Engineering - Fábrica de Software]]", "[[smartside.ai - Company Brain (Segundo Cérebro)]]", "[[Stack de Desenvolvimento com IA - Ferramentas e Workflow]]", "[[2026-08-03 Stack de Desenvolvimento com IA (Jonh Alex)]]"]
updated: 2026-08-03
---

# smartside.ai — Workspace de Desenvolvimento (Harness)

> Iniciativa **interna**. Repositório GitHub que serve de ponto de partida para qualquer sessão de desenvolvimento na smartside.ai.
> Construído por [[Matheus Simões]] (com o Edge). Apresentado a [[Yan Simmer]] e [[Arthur Tosi]] em [[2026-07-30 smartside.ai - Company Brain (Segundo Cérebro)|30/jul/2026]].

## Status
**Em teste.** [[Yan Simmer]] e [[Arthur Tosi]] foram convidados ao repositório na própria reunião e ainda precisam clonar, rodar o setup e usar.

## Como funciona
- Toda sessão do Claude começa **no terminal da pasta raiz** do repositório.
- **CLAUDE.md raiz** contém: diretrizes de bootstrap (instalação e setup, roda no primeiro prompt), **regras de roteamento** e **regras de ouro**.
- Cada pasta dentro de `Project/` tem **Git próprio e CLAUDE.md de perfil**; a raiz sabe trazer o contexto do projeto específico conforme o que a pessoa pede.
- Onboarding: clonar o repositório numa pasta, dar um prompt na raiz → ele faz o setup e pergunta o que você quer fazer. A partir de uma ideia, trabalha com você até o deploy.

## Biblioteca de skills
Skills do fluxo de desenvolvimento, encadeáveis:
- Conduzir **entrevista** → gerar **PRD** → quebrar em **issues** → disparar desenvolvimento em **waves**
- Fazer **review**
- Começar **protótipo**
- **Simplificar código**
- **Procurar lib**
- **Breakdown** em issues

### Grill Me With Docs (a incorporar)
Trazido por [[Arthur Tosi]] — evolução do "Grill Me". Faz a entrevista de projeto e produz:
- **PRD**
- **ADRs** — um arquivo por decisão de arquitetura, **imutáveis historicamente**
- **Arquivo de domínio** — glossário dos termos mais usados no projeto
- **Issue tracker** — onde está cada arquivo
- **Um arquivo por tarefa/issue** com status, critério de aceite e bloqueios

Proposta em aberto: embutir o Grill Me With Docs dentro da skill de iniciar projeto, em vez de mantê-las separadas.

## Fluxo atual (nível de abstração já implementado)
1. Planning
2. Criação da **árvore de dependências** e geração de **worktrees separadas**
3. **Waves de build em paralelo**
4. Teste e review automáticos
5. Só sobe para revisão humana + novo planning **se falhar 3× no loop**

Corresponde ao estágio "escala com worktrees" do modelo descrito em [[Harness Engineering - Fábrica de Software]].

## Evolução pretendida
Subir para as camadas superiores do modelo (ver [[Harness Engineering - Fábrica de Software]]):
- **Kanban** recebendo input de suporte, produto e engenharia
- **Setup sandbox** roteando por tipo de demanda (hotfix / feature / bug / tarefa)
- **Troca de estado automática** do card conforme o estágio do agente
- **Fluxo de hotfix** com agentes paralelos competindo pela resolução
- Trazer para dentro do workspace uma **camada de contexto** (hoje o repositório é só workflow + skills; o contexto o usuário alimenta conforme usa) — é aqui que o [[smartside.ai - Company Brain (Segundo Cérebro)|Company Brain]] se encaixaria, junto com skills específicas para as ferramentas da empresa

## Compromissos abertos
- [ ] [[Yan Simmer]] — clonar, rodar o setup e testar
- [ ] [[Arthur Tosi]] — clonar, rodar o setup e testar
- [ ] [[Arthur Tosi]] — avaliar embutir o Grill Me With Docs nas skills iniciais
- [ ] [[Arthur Tosi]] — propor reunião oficial com [[Matheus Andrade]] para padronizar as abordagens
- [ ] [[Matheus Simões]] — pesquisar e entender **lint** (camada determinística central no modelo)

## Insumos externos avaliados (03/ago/2026)
> Trazidos na sessão com Jonh Alex — ver [[2026-08-03 Stack de Desenvolvimento com IA (Jonh Alex)]] e o detalhe em [[Stack de Desenvolvimento com IA - Ferramentas e Workflow]].
> **Nada foi decidido nem adotado.** Nenhum item abaixo tem dono.

| Insumo | Onde encaixaria | Status |
|---|---|---|
| **Serena** (MCP de busca por símbolo, com memória de projeto) | A **camada de contexto** que hoje falta no workspace; e o caso "Claude Code sobre documentação interna" do [[smartside.ai - Company Brain (Segundo Cérebro)]] — sem exigir Vector Store, coerente com a decisão de MCP + index de 30/jul | ⚠️ "Vou testar" — dono não identificável, sem data |
| **GStack** ⚠️ (~23 skills cobrindo empresa inteira) | **Sobreposição direta** com a biblioteca de ~10 skills desenhada pelo time. Traz também skill de QA que testa o fluxo no navegador como usuário real | ⚠️ Ninguém ficou dono de comparar |
| **Temporal** (runtime open source de longa duração) | Cobre o que o fluxo de waves não tem: manter agente vivo por dias/semanas, filas, retry com correção e **human-in-the-loop** (segura o agente esperando resposta humana). Também CI/CD de segurança pré-produção | Recomendado como componente **cobrável** em Enterprise |
| **Leopold** (harness pessoal do apresentador, open source) | Referência de fluxo: Triage → Brief (missão/persona/guardrails/plano) → artefatos com registro de decisões → run *ou* workflow multiagente → camada de aprendizado entre tarefas. **Guardrail padrão: `git commit` bloqueado e proibido subir na main** | GitHub + deck a serem repassados via [[Flávio Parreiras]] |
| **MkDocs** | Documentação: markdown puro → site responsivo e multi-idioma sem input manual | Recomendado como entregável cobrável |

**Padrão de fundo que vale registrar:** como o harness roda local e não tem system prompt oculto, o caminho é **se injetar dentro dele** (hooks, skills, MCP, memória) em vez de construir ferramenta nova por fora.

## Riscos
- ⚠️ Nenhum prazo acordado para os testes.
- ⚠️ **Sobreposição não endereçada com o GStack** — o time pode estar construindo à mão uma biblioteca de skills que já existe pronta. Ninguém ficou responsável por comparar (03/ago/2026).
- ⚠️ Recomendações de 03/ago vêm de **base de evidência fina** (Leopold em workflow: 2 testes; PRD via Perplexity: 2 testes).
- ⚠️ A camada de validação determinística ("o que exatamente esse código precisa ter para me dar segurança de que, se passou, está certo") foi explicitamente apontada por [[Matheus Simões]] como **a parte menos clara** do modelo.
- ⚠️ Existe um segundo cérebro/workspace paralelo mantido por [[Matheus Andrade]]; sem a reunião de padronização, o time diverge em duas abordagens.

## Notas relacionadas
[[smartside.ai]] · [[Harness Engineering - Fábrica de Software]] · [[smartside.ai - Company Brain (Segundo Cérebro)]] · [[Stack de Desenvolvimento com IA - Ferramentas e Workflow]] · [[2026-07-30 smartside.ai - Company Brain (Segundo Cérebro)]] · [[2026-08-03 Stack de Desenvolvimento com IA (Jonh Alex)]] · [[00 - MOC Interno smartside.ai]]
