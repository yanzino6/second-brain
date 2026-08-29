---
type: knowledge
tags: [conhecimento, harness-engineering, agentes, workflow-desenvolvimento, ia, engenharia]
scope: geral
source_meeting: "[[2026-07-30 smartside.ai - Company Brain (Segundo Cérebro)]]"
links: ["[[smartside.ai - Workspace de Desenvolvimento (Harness)]]"]
updated: 2026-07-30
---

# Harness Engineering — Fábrica de Software

> Conhecimento **geral e reutilizável** (client-agnostic). Capturado da explicação de [[Matheus Simões]] em [[2026-07-30 smartside.ai - Company Brain (Segundo Cérebro)|30/jul/2026]], a partir de um vídeo que ele assistiu; [[Arthur Tosi]] citou um artigo da Anthropic sobre o mesmo tema.
> ⚠️ Fonte primária (vídeo e artigo) **não linkada** — foi compartilhada no canal TechOps do Discord e não capturada na transcrição.

## Tese central
> **"Os bons engenheiros hoje não estão desenvolvendo código — estão desenvolvendo a fábrica que desenvolve código."**

O sistema que o engenheiro constrói não é o produto; é o sistema que constrói sistemas. Feito bem, a parte que desenvolve fica cada vez melhor, até virar uma fábrica de software que anda sozinha. Uma pessoa com essa estrutura montada consegue tocar muitos projetos em paralelo.

## Os três atores de geração de valor
1. **Engenheiro** — dá o prompt, revisa, aprova, decide.
2. **Agente** — planeja, constrói, testa, revisa, simplifica.
3. **Código** — a camada determinística.

**Por que o código importa tanto:** é a coisa mais rápida, mais escalável e mais confiável que existe. Executa imediatamente e **não tem variação**. Misturar agentes + código determinístico é o que dá confiança de que o entregue está em conformidade — não porque um agente disse que está, mas porque um algoritmo validou.

Instrumentos determinísticos citados: **lint**, **format**, testes **end-to-end**, **CI/CD**.

## Escada de maturidade

### Nível 0 — loop mínimo
`engenheiro → IA → código → review do engenheiro → novo prompt`

### Nível 1 — validação determinística no meio
`prompt do engenheiro → agente de build → linter`
- Se o linter falhar, volta ao agente de build e repete até passar.
- Se passar, vai ao engenheiro. Se aprovado, merge.
- Camadas adicionais: teste de **lint** e teste de **format** (fluxo de uso, telas, botões, posição, padrão de código).
- Ganho: o engenheiro ainda dá prompt e ainda revisa, mas a qualidade do que chega até ele é muito maior.

### Nível 2 — planning como etapa própria
`engenheiro ↔ agente de planning → review do plano → agente de build → agente de teste → engenheiro → merge`
- Se falhar no engenheiro, volta ao **planner agent** e o loop recomeça.

### Nível 3 — escala por paralelismo
Mesmo fluxo, replicado em **várias worktrees**.
- No planning, gera-se a **árvore de dependências** e as worktrees separadas.
- Execução em **waves de desenvolvimento em paralelo**.

### Nível 4 — input estruturado por Kanban
- O Kanban recebe input de **suporte**, **time de produto** e **engenharia**.
- O engenheiro puxa do Kanban e gera os prompts.
- **Scout Agent** identifica o problema (ex.: em caso de bug).
- **Troca de estado automática do card**: prompt dado → card vai para *planning*; planning concluído → card vai para *building*.
- Entrega a um agente de tarefas na sandbox → teste (falhou, volta ao build) → CI/CD → avaliação do engenheiro → merge.

### Nível 5 — roteamento por tipo de demanda
Um **agente orquestrador** faz o deploy de uma sandbox e identifica o tipo de trabalho, cascateando para um workflow específico:
- **Hotfix** → fluxo de hotfix
- **Feature** → fluxo de feature
- **Bug** → fluxo de correção de bug
- **Tarefa** → fluxo de tarefa

### Padrão de hotfix (production crash)
Mentalidade diferente do resto:
1. Vai **direto para o engenheiro**, que precisa estar de prontidão.
2. Engenheiro dá o prompt para o **Scout Agent**, que identifica o problema.
3. **Hotfix Agent** gera múltiplos caminhos de resolução.
4. **Sandbox Builder** solta **vários agentes em paralelo** resolvendo o mesmo problema.
5. **O primeiro que resolver vence** — a solução dele é aprovada.
6. O engenheiro só valida se o bug foi de fato resolvido.

Ganho: resolve muito rápido sem prender o engenheiro no operacional.

## Papéis de agente no fluxo
Orquestrador · criador de sandbox · planning · build/execução de código · teste · review · simplificação de código · review de segurança. Depois de tudo isso, chega ao engenheiro.

## Princípio de gestão
> Humanos gerenciam, agentes executam.

O ponto levantado por [[Arthur Tosi]]: sem esse harness, o engenheiro oscila entre dois extremos ruins — revisar linha por linha até cansar, e então passar a confiar cegamente. O fluxo bem montado permite **gerência que cuida de decisões**, com o humano inserido nos pontos certos.

## Perguntas ainda abertas
- **Qual é exatamente a camada determinística?** O que o código de validação precisa ter para garantir que "se passou, está certo" — apontado por [[Matheus Simões]] como a parte menos clara do modelo.

## Aplicação na smartside.ai
Ver [[smartside.ai - Workspace de Desenvolvimento (Harness)]] — o repositório atual está no **Nível 3** (planning → worktrees → waves → teste/review automático, humano só após 3 falhas).
