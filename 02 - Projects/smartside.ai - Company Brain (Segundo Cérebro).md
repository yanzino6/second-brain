---
type: project
tags: [projeto, interno, smartside, company-brain, second-brain, notion, gestao-conhecimento]
status: em-definicao-de-escopo
company: "[[smartside.ai]]"
owners: ["[[Yan Simmer]]", "[[Arthur Tosi]]", "[[Pedro]]"]
sponsor: "[[Matheus Simões]]"
links: ["[[smartside.ai]]", "[[2026-07-30 smartside.ai - Company Brain (Segundo Cérebro)]]", "[[smartside.ai - Workspace de Desenvolvimento (Harness)]]"]
updated: 2026-07-30
---

# smartside.ai — Company Brain (Segundo Cérebro)

> Iniciativa **interna**. Nenhum dado de cliente entra neste projeto.
> Origem: [[2026-07-30 smartside.ai - Company Brain (Segundo Cérebro)|reunião de 30/jul/2026]], provocada por [[Yan Simmer]] a partir do vault Obsidian que já vinha construindo.

## Status
**Em definição de escopo.** Nada será construído antes de responder *para que serve o Company Brain na smartside.ai*. [[Matheus Simões]] declarou isso como bloqueador de todas as demais decisões.

## Problema
A empresa não tem um local único onde o conhecimento interno (projetos, clientes, processos, pessoas, ferramentas) fique armazenado de forma consumível por agentes de IA. Hoje cada pessoa gerencia contexto do próprio jeito.

## Hipótese em revisão
A conclusão da reunião foi que **a dor real talvez não seja um Company Brain**, e sim um **agente de gestão de tarefas e projetos** (ver [Alternativa](#alternativa-chief-of-staff--hermes-agent)). O maior beneficiário identificado é a camada administrativa e de relacionamento com cliente — [[José Lucas Ribeiro]], [[Victor Hugo]], Edu (vendas/upsell/cross-sell), [[Pedro]] (cobrança) — não a camada técnica.

## Regras de arquitetura já decididas
- **Repositório = Notion.** Página/workspace dedicado. Escolhido porque já é uma árvore de markdown com hierarquia e link nativos, resolve compartilhamento **e** permissão por pessoa, e tem MCP.
- **Acesso do agente = MCP + index ("LLM RAG").** Um CLAUDE.md/index descrevendo bem a estrutura basta para consulta direcionada. **Sem Vector Store, sem embeddings.**
- **Company Brain é um componente do second brain individual, não um sistema à parte.** Distribuído como template/repositório versionado que cada pessoa clona.
- **A camada da empresa não é viva.** O agente **não** edita o Company Brain; ele só se atualiza puxando o repositório. A camada pessoal fica acima, fora do versionamento (gitignore).
- **O template carrega as regras** de como a IA gerencia o second brain — não fica cada um fazendo do seu jeito.
- **Curadoria humana obrigatória.** Papel de **guardião**: valida o que entra na base da empresa e faz análise retroativa do que se torna obsoleto.
- **Plataforma própria só depois de validar no Notion.**

## Riscos e problemas em aberto
- ⚠️ **Escopo indefinido** — bloqueia tudo. Sem recorte, vira "birimbolo de informações".
- ⚠️ **Base ruim piora o agente.** Conteúdo desatualizado não é neutro; envenena o contexto. Exige rotina de sanitização, não só de ingestão.
- ⚠️ **Permissão na camada MCP.** No Notion a permissão é nativa; via conector/MCP não há resposta de como restringir o que cada pessoa acessa.
- ⚠️ **Sustentação do papel de guardião** — ninguém foi nomeado.
- ⚠️ **Sem prazo.** Nenhum item deste projeto tem data acordada.

## Alternativa: Chief of Staff / Hermes Agent
Recorte mais estreito que resolveria a dor concreta, proposto por [[Matheus Simões]]:
- Agente com papel de BPO de gestão de demandas e tarefas.
- Conectado a Linear, Notion, grupos de WhatsApp com cliente, Slack/Discord.
- Cobra pessoas, recobra, mantém boards atualizados.
- Envia briefing pré-reunião — ex.: estado das tarefas dos devs na caixa do [[Flávio Parreiras]] antes do alinhamento de projeto.

## Desdobramento comercial (ideia, sem decisão)
Company Brain como **feature da plataforma do cliente**, ao lado de Agent Catalog e Observability Panel:
- Alimentado pela ferramenta de diagnóstico automatizado.
- Vira fonte de conhecimento para construção de novos projetos (organograma, ferramentas, processos, documentos).
- Chatbot em que o cliente descreve uma ideia, o agente avalia aderência ao contexto, orquestra a ideação do projeto e encaminha ao time de vendas.
- Coerente com a diretriz vigente: **produto só nasce de dor interna já resolvida, replicável e com mercado grande**.

## Próximos passos
- [ ] [[Yan Simmer]] + [[Arthur Tosi]] + [[Pedro]]: definir escopo e casos de uso
- [ ] Estruturar a página do Company Brain no Notion (só após o escopo)
- [ ] Definir o guardião e a rotina de curadoria/sanitização
- [ ] Resolver o modelo de permissão na camada MCP

## Notas relacionadas
[[smartside.ai]] · [[2026-07-30 smartside.ai - Company Brain (Segundo Cérebro)]] · [[smartside.ai - Workspace de Desenvolvimento (Harness)]] · [[Harness Engineering - Fábrica de Software]] · [[00 - MOC Interno smartside.ai]]
