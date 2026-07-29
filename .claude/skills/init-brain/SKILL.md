---
name: init-brain
description: Conduz a entrevista de onboarding de um membro do time da SmartSide no segundo cérebro (vault Obsidian) e transforma a conversa em notas ligadas em "01 - People", "02 - Projects", "03 - Companies", "05 - Knowledge" e "08 - Processes". Use sempre que alguém pedir para entrevistar, onboardar, documentar, "puxar o conhecimento" ou registrar alguém no cérebro — inclusive quando a pessoa só disser que vai usar o cérebro pela primeira vez, que entrou no time agora, ou que quer despejar o que sabe no vault. Na dúvida entre conduzir a entrevista e só criar uma nota solta, use esta skill.
---

# Entrevista de onboarding no segundo cérebro

Esta skill extrai, em uma única sessão, o que um membro do time sabe e faz, e escreve esse conhecimento no vault de forma ligada ao que já existe. O valor não está em preencher um formulário: está em capturar o que só existe na cabeça da pessoa — fluxos operacionais reais, decisões antigas, o que costuma quebrar, o que a incomoda.

A entrevista é feita **de uma sentada só**, com **uma pergunta por vez**.

## Fase 0 — Ler o vault antes de abrir a boca

Nunca comece a entrevista sem antes ler o cérebro. Sem isso a entrevista vira redundante e as notas viram ilhas soltas.

Leia, nesta ordem:

1. `CLAUDE.md`, `IDENTITY.md`, `SOUL.md`, `USER.md` na raiz — convenções, tom e contexto da empresa.
2. `06 - MOCs/` — os mapas de conteúdo dão a topologia do vault em poucos arquivos.
3. `01 - People/` — quem já está documentado, e o formato que essas notas seguem.
4. `02 - Projects/` e `03 - Companies/` — projetos e clientes existentes, com atenção a arquitetura, stack e responsáveis.
5. `08 - Processes/` — processos já escritos, para não reescrever o que existe.

**Se `CLAUDE.md` do vault definir convenções (nomenclatura de arquivo, frontmatter, tags, idioma), elas mandam. Esta skill é o padrão de fallback.**

Ao final da leitura, monte mentalmente três listas — elas guiam a entrevista inteira:

- **Já sabemos**: fatos que não precisam ser perguntados, só confirmados.
- **Sabemos pela metade**: projetos documentados por outra pessoa, onde falta a visão de quem executa.
- **Pontos de divergência a testar**: coisas que outra pessoa descreveu e que este entrevistado pode enxergar diferente. Divergência entre duas cabeças é informação valiosa, não erro a corrigir.

## Como conduzir

**Uma pergunta por vez.** Nunca despeje uma lista de perguntas de uma vez — a pessoa responde tudo de forma rasa. Espere a resposta, processe, então pergunte a próxima.

**Cave até a resposta ser operacional.** "Cuido do CRM" não é resposta. A barra é: *alguém que nunca fez isso conseguiria repetir o trabalho lendo a nota?* Se não, continue perguntando. Bons follow-ups:

- "Me leva no passo a passo de uma vez que você fez isso essa semana."
- "Você faz isso onde exatamente? Que tela, que ferramenta?"
- "E quando dá errado, o que acontece?"
- "Quem recebe isso depois de você?"

**Espelhe respostas densas.** Quando a pessoa descrever arquitetura ou fluxo, reformule com suas palavras e peça correção: "Deixa eu ver se entendi: X chama Y, Y grava em Z, e o n8n dispara isso a cada hora. Tá certo?". Isso corrige mal-entendidos antes de virarem nota.

**Aproveite o que já está no vault.** Em vez de "o que é o Outreach Hub?", pergunte: "O Outreach Hub está documentado como uma plataforma de prospecção com agentes para LinkedIn e e-mail. Isso bate com o que você faz nele, ou tem parte que ficou de fora?"

**Não invente.** Se a pessoa não souber, registre como lacuna explícita na nota (`> [!question] Em aberto: ...`) em vez de preencher com suposição plausível.

**Adapte o volume.** Um dev sênior em três projetos rende mais que alguém que entrou semana passada. Se a pessoa é nova e ainda não tem projeto, pule o Bloco 3 e aprofunde em Trabalho e Objetivos.

Abra avisando: são de 40 a 60 minutos, é de uma sentada só, e no fim ela revisa tudo antes de qualquer coisa ser gravada.

## Bloco 1 — Pessoal

- Nome (e como prefere ser chamado / como aparece nas ferramentas)
- Quando entrou na SmartSide
- Qual o maior objetivo dela dentro da SmartSide

No objetivo, cave uma camada: "o que precisaria acontecer nos próximos seis meses para você sentir que está indo nessa direção?"

## Bloco 2 — Trabalho

- Cargo
- O dia a dia, com **detalhe operacional**: fluxos de trabalho de ponta a ponta, não descrição de cargo
- Ferramentas que usa, e para quê cada uma
- Onde ficam as coisas com que trabalha (repos, boards, drives, dashboards)
- Em quais projetos e iniciativas está envolvida, e com que papel em cada um

Para o dia a dia, o melhor gancho é temporal: "me conta uma segunda-feira típica sua, da hora que abre o computador". Depois: "e o que acontece só uma vez por semana ou por mês?" — o trabalho de baixa frequência é o que mais se perde.

Feche o bloco com a lista de projetos, que vira o roteiro do Bloco 3.

## Bloco 3 — Projetos (repita para cada projeto)

Rode este bloco inteiro para um projeto antes de passar ao próximo. Misturar projetos confunde a pessoa e embaralha as notas.

1. **O que o projeto faz** — em uma frase, e depois na prática
2. **Tech stack** — linguagens, frameworks, ferramentas, integrações, infra, onde roda
3. **Arquitetura** — o que interage com o que, de que forma, com qual objetivo. Cave: por onde entra o dado, onde ele fica, o que dispara o quê, o que é síncrono e o que é agendado, quais integrações externas existem
4. **Dor do cliente** — que problema real isso resolve, e o que o cliente fazia antes
5. **Decisões históricas** — por que está assim? O que já foi tentado e não deu certo? Que restrição (cliente, prazo, custo, ferramenta) moldou a solução? Esse é o conhecimento que mais se perde quando alguém sai
6. **O que costuma quebrar** — falha mais comum, como se percebe, como se resolve. Isso vira runbook em `08 - Processes`
7. **Papel dela e quem mais mexe** — quem toca esse projeto além dela, e quem procurar para cada parte

Se o projeto já está documentado no vault, comece por 1–4 em modo confirmação ("está escrito assim; concorda?") e gaste o tempo ganho em 5 e 6, que quase nunca estão escritos.

## Bloco 4 — Rituais e cadências

- Reuniões recorrentes de que participa, com que frequência e para quê
- Entregas recorrentes (relatório semanal, fechamento mensal, deploy)
- Para quem se reporta e quem depende do trabalho dela
- A quem recorre quando trava — por assunto ("quem você procura quando quebra a integração do HubSpot?")

O último item constrói o mapa de "quem sabe o quê". Insista nele.

## Bloco 5 — Conhecimento tácito e runbooks

- Que gambiarra ou detalhe não óbvio alguém precisaria saber para não se ferrar no trabalho dela
- O que ela explica repetidamente para outras pessoas
- Armadilhas conhecidas: "o que parece funcionar mas não funciona?"
- Jargão interno que ela usa (siglas, apelidos de fluxo, nomes de cliente) e o significado

O gancho mais produtivo: "se você sumisse por duas semanas, o que quebraria e ninguém saberia consertar?"

## Bloco 6 — Gargalos e dores próprias

- O que consome mais tempo e agrega menos
- O que ela automatizaria hoje se pudesse
- Onde ela costuma ficar bloqueada esperando outra pessoa ou sistema
- O que na ferramenta atual atrapalha

Não conserte nada aqui. A função é registrar; virar pauta é decisão de outra pessoa.

## Bloco 7 — Métricas de sucesso

- Como ela sabe que fez um bom trabalho
- Que número ou sinal ela acompanha (se algum)
- Como o sucesso dela é medido pela empresa — e se isso bate com o critério dela

Divergência entre os dois últimos é achado relevante. Registre sem julgar.

## Bloco 8 — Divergências e confirmações

Feche com os pontos de divergência levantados na Fase 0. Apresente sem apontar culpado: "isso está registrado de um jeito no cérebro e você descreveu diferente — qual versão está mais atual?"

Registre as duas visões quando não houver convergência clara, marcando quem disse o quê.

## O que nunca registrar

Corte na hora, mesmo que a pessoa fale espontaneamente:

- Salário, remuneração, participação, dados financeiros pessoais
- Avaliação de desempenho ou opinião sobre colegas — reclamação sobre pessoas não entra no vault
- Credenciais, chaves de API, tokens, senhas, strings de conexão
- Dados de cliente sob NDA, dados pessoais de terceiros, conteúdo de base de clientes
- Informação de saúde, religião, política ou vida pessoal

Se surgir, apenas siga: "isso eu não vou registrar, mas obrigado pelo contexto". Não interrompa o fluxo com sermão, e não deixe rastro nem no resumo.

Frustração com processos e ferramentas **entra** (é o Bloco 6). Frustração com pessoas, não.

## Resumo final para revisão

Antes de escrever qualquer arquivo, apresente o resumo estruturado por bloco, em português, e liste explicitamente:

- Arquivos que serão **criados**
- Arquivos existentes que serão **editados**, com o que muda em cada um
- Lacunas que ficaram em aberto

Pergunte: "algo aqui está errado, faltando, ou que você prefere que não fique registrado?" Só grave depois do aceite. Se a pessoa corrigir, aplique e mostre de novo a parte alterada.

## Gravação no vault

Siga os templates em `references/templates.md`.

Distribuição do conteúdo:

| Conteúdo | Destino |
|---|---|
| Perfil, cargo, objetivo, dia a dia, rituais, dores, métricas | `01 - People/<Nome>.md` (criar) |
| Projeto: o que faz, stack, arquitetura, dor do cliente, decisões | `02 - Projects/<Projeto>.md` (criar ou editar) |
| Cliente mencionado | `03 - Companies/<Empresa>.md` (criar ou editar) |
| Runbook, fluxo operacional repetível | `08 - Processes/<Processo>.md` (criar ou editar) |
| Jargão, aprendizado avulso, conceito | `05 - Knowledge/<Tema>.md` (criar ou editar) |
| Novos nós relevantes | `06 - MOCs/` (editar o MOC correspondente) |

Regras de escrita:

- **Nunca sobrescreva arquivo existente.** Acrescente seção ou ajuste o trecho específico, preservando o que já estava lá.
- **Marque a procedência** do que veio desta entrevista: `<!-- fonte: entrevista com [[Nome]], AAAA-MM-DD -->` ao final da seção acrescentada. Quando duas fontes divergem, mantenha as duas com atribuição.
- **Ligue tudo com `[[wikilinks]]`**: a nota da pessoa aponta para projetos, empresas e processos, e cada um deles aponta de volta. Nota sem link é nota morta no Obsidian.
- Frontmatter YAML conforme o padrão já usado nas notas existentes do vault; se não houver padrão, use o dos templates.
- Escreva em pt-BR, em prosa direta. Preserve o vocabulário da pessoa — se ela chama de "disparo", a nota chama de "disparo", com o termo formal entre parênteses na primeira ocorrência.
- Nada de invenção: se um campo não foi coberto, deixe explícito como lacuna em vez de omitir ou preencher.

## Ao terminar

Mostre a lista final de arquivos criados e editados, e diga à pessoa quais lacunas ficaram em aberto para ela completar depois. Se algo relevante não coube em nenhuma pasta, deixe em `00 - Inbox/` com nota do motivo.
