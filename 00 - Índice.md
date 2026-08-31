---
type: indice
atualizado: 2026-08-31
---

# Índice

> Ativo de carreira do [[USER|Yan Simmer]]. Fonte densa; o recorte por plateia se monta a partir daqui.
> Leia [[CLAUDE]] antes de escrever. [[SOUL]] descreve o que a obra demonstra. [[IDENTITY]] define como eu opero.

## Projetos

**Produção — smartside.ai**
- [[Ebramed — Isabela, do diagnóstico à migração]] — causa-raiz provada, migração para API Oficial, harness de teste
- [[Knewin — Nina, SDR de IA com Triagem de CRM]] — 14 tools, RAG segregado, triagem no HubSpot
- [[Farmly — Máquina de Aquisição Outbound]] — pipeline F1→F6, BDR internacional · **R$ 3.897/mês**
- [[Boavista — BDR de LinkedIn com Fila por Score]] — rate limiting, fila por score, MCP Server

**Acadêmico — UFES, IA em Saúde**
- [[BreaKHis — Classificação de Câncer de Mama em Histopatologia]] — AUC 0,8965 em held-out
- [[PAD-UFES-20 — Classificação de Lesões de Pele com Classe Sintética]] — classe sintética com precisão 1,00

## Competências

**Fortes — com prova múltipla**
- [[Engenharia de teste automatizado]] · [[Depuração de causa-raiz]] · [[Rigor experimental e avaliação]]
- [[Segurança de aplicação e RBAC]] · [[Engenharia de prompt]]
- [[Automação de processo de negócio (n8n)]] · [[Integração de API e sistemas]]

**Médias**
- [[RAG e busca semântica]] · [[Deep learning e visão computacional]] · [[Análise de métricas e indicadores de produto]]

**Raras**
- [[MCP — Model Context Protocol]] — publicou servidor, não só consumiu

**⚠️ A verificar — declaradas sem prova no vault**
- [[Inglês técnico escrito]] — crítico para o alvo internacional
- [[Liderança técnica e gestão]] — maior lacuna em relação ao alvo declarado

## Ideias
- [[App de gravação de reuniões para advogados]] — crua, não avaliada

## Pendências

> Sessão encerrada em **31/08/2026** com o vault recém-construído. Esta lista é o ponto de retomada — comece por aqui numa sessão nova.

### Prioridade alta — fecham lacuna do alvo declarado

- [ ] **Entrevista sobre [[Liderança técnica e gestão]]** — *maior lacuna do vault*. Ele quer gestão no leque (estágio/PJ/internacional) mas não há **nenhum** artefato: tamanho do time no CT Junior, projetos entregues, o que a linha de serviço de Automação & IA que ele criou faturou ou vendeu, rituais que conduzia, alguma decisão sobre pessoas. Está tudo na cabeça dele — é a lacuna mais rápida de fechar e a de maior retorno.
- [ ] **Material em inglês** que sustente [[Inglês técnico escrito]] — hoje só há indício (comentários e README do CRM). Começar abrindo `~/Documents/Yan_Simmer_Resume_EN_1.pages`, que ainda não foi analisado. Para vaga internacional, "avançado" sem documento longo não sustenta.
- [ ] **Resultado de negócio da [[Ebramed — Isabela, do diagnóstico à migração|Ebramed]] e da [[Knewin — Nina, SDR de IA com Triagem de CRM|Knewin]]** — únicos projetos ainda sem número. Aplicar a regra dos resultados do [[CLAUDE]]: se não houver dado, entrevistá-lo sobre como mediu ou mediria, avaliar a métrica e ajudar a melhorar. Fonte a checar primeiro: `~/Documents/metricas-de-projetos-smarts-ai/` (tem pastas `zuvia`, `solvee`, `tee-fashion`, `esag` ainda não lidas).

### Dívida minha — prometido e não entregue

- [ ] **Reescrever as skills do vault.** `.claude/skills/init-brain/` e `.claude/skills/meeting-extract/` continuam escritas para a smartside.ai — falam em cliente, compartimentação de dados e "membro do time". Ele aprovou a reescrita para contexto pessoal no início da sessão e eu não fiz.

### Infraestrutura

- [ ] **Hook de `Stop`** gravando sessão em `04 - Sessões/` (a pasta existe e está vazia). Registra atividade bruta; a destilação em nota é curadoria humana — ver [[USER]] e a regra de sanitização em [[SOUL]]. Configurar via `settings.json`.
- [ ] **Decidir sobre `mcp-obsidian/`** — continua na raiz do vault. Nenhuma referência encontrada em config; se estiver morto, remover (código não mora no vault).
- [ ] **Commit.** As 33 notas estão no disco mas **não commitadas**. O estado anterior da empresa está preservado na tag `backup-vault-empresa` (commit `023cfe7`), recuperável com `git checkout backup-vault-empresa -- .`

### Trabalho de conteúdo

- [ ] **Rodar `/office-hours` (startup mode)** na ideia [[App de gravação de reuniões para advogados]] e trazer o design doc gerado para `03 - Ideias/` — a skill salva em `~/.gstack/` por padrão, fora do vault.
- [ ] **Reescrever o currículo** a partir das notas. O atual subdeclara: diz "React (básico)" e "Node.js (básico)" ao lado de 11.685 linhas de RBAC e um harness de 429 linhas. Nenhum bullet tem número, embora os números existam.
- [ ] **Consolidar `00 - Inbox/`** — `O que eu construí.md` ficou mais pobre que as 6 notas de projeto; vale virar índice delas ou ser arquivado. `ANÁLISE - Inventário técnico.md` e `RAW - Currículo atual.md` já cumpriram função e podem ser destilados.

### Achado técnico com prazo — não é do vault, mas é do trabalho dele

- [ ] **O legado da Ebramed continua ativo e quebrado.** `Agente SDR - Ebramed - Conversas 01` está ligado em produção com os três nós `Infos Manuais*` ainda lendo `body.chat.phone` — o campo que a revisão dele provou não existir. A trilha `API Oficial` nasceu correta. As duas rodam em paralelo, então o comportamento depende de por onde o lead entra. **Corrigir ou desligar; manter as duas é o pior cenário.**
