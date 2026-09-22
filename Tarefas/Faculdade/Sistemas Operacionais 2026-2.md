---
type: tarefas
tags: [faculdade, sistemas-operacionais, estudo, laboratorio]
data: 2026-09-09
---

# Sistemas Operacionais 2026/2

Professor: Luis Antonio de Souza Junior  
Responsável: [[USER|Yan Simmer]]

## Mapa de aulas

- Aula 0 — Introdução à disciplina — estudo — material revisado
- Aula 1 — Introdução a SO (histórico, tipos e classificações) — estudo + execução — material revisado
- Aula 2 — Processos (conceito, contexto, troca de contexto, BCP) — estudo + execução — pendente
- Aula 3 — Escalonamento de processos — estudo + execução — pendente
- Aula 4 — Unix: Kernel Mode — estudo — material revisado
- Aula não identificada — demais conteúdos e laboratórios após Unix Kernel Mode (Escalonamento Tradicional vs. Kernel Preemptivo; laboratório de chamadas ao sistema; Sinais no Unix; Lab0; Lab1; Lab2) — estudo + execução — pendente/material revisado conforme checkbox em Tarefas
- Aula 13 — Revisão P1 — estudo — pendente
- Aula 09 — Sincronização por Busy-Wait — estudo + execução — pendente
- Aula 11 — Semáforos — estudo — pendente

> [!question] Em aberto: a numeração de aulas 0–4 vem da confirmação direta do Yan em 2026-09-09 (ver "Progresso confirmado"), não de numeração oficial do professor nos e-mails. Os itens posteriores a Unix Kernel Mode (incluindo Lab0, Lab1 e Lab2) não têm aula de conteúdo confirmada nos e-mails registrados — apenas os laboratórios têm prazo de entrega (ver Prazos e lacunas).

> [!question] Em aberto (2026-09-18): "Aula 09 — Sincronização por Busy-Wait" chegou numerada pelo professor, mas aparece depois de "Aula 13 — Revisão P1" nesta lista porque foi adicionada por último, na ordem de chegada dos e-mails — não pela ordem numérica das aulas. Não há confirmação de conteúdo para as aulas 5 a 8 e 10 a 12 nos e-mails registrados; a numeração real da disciplina segue incerta.

<!-- fonte: Gmail educacional, e-mails de Luis Antonio de Souza Junior no Google Sala de Aula, mapa reconstruído em 2026-09-10 a partir do arquivo existente -->

## Tarefas

### Estudo

- [x] Estudar a introdução à disciplina de Sistemas Operacionais.
- [x] Estudar introdução a Sistemas Operacionais: histórico, tipos e classificações; ler as páginas 23–30 do material complementar e assistir aos vídeos indicados.
- [x] Estudar processos: conceito, contexto, troca de contexto e bloco de controle de processo (BCP); consultar os textos e vídeos indicados.
- [x] Resolver os exercícios de Introdução à SO.
- [x] Resolver os exercícios de Processos e Estrutura de Controle.
- [x] Estudar escalonamento de processos; consultar Maziero, seções indicadas, e os vídeos sobre algoritmos de escalonamento.
- [x] Resolver os exercícios de Escalonamento.
- [x] Estudar Unix: Kernel Mode, incluindo contexto histórico, modos de operação da CPU e execução em Kernel Mode; assistir ao vídeo sobre interrupções até 8min15s.
- [ ] Estudar Unix: Escalonamento Tradicional versus Kernel Preemptivo; consultar o material complementar e os dois vídeos indicados.
- [x] Estudar os exercícios sobre Unix, Kernel e Escalonamento Tradicional.
- [ ] Estudar o laboratório de chamadas ao sistema (kernel), com `fork()`, concorrência entre processos pai e filho, user ID e process group ID.
- [ ] Estudar Sinais no Unix em C; ler o material complementar, revisar `pause()`, o efeito de `exec()` sobre handlers e assistir aos vídeos indicados.
- [ ] Estudar o laboratório Lab2 — SVC (parte 2): comunicação entre processos pai e filho, alteração de código no processo filho e reconhecimento da troca de estados.
- [ ] Aula 13 — Revisão P1: estudar o material de revisão para a P1; o e-mail trouxe apenas o título, sem detalhar o conteúdo.
- [ ] Aula 09 — Estudar sincronização por busy-wait: introdução à sincronização de processos, região crítica e exclusão mútua, mecanismos de sincronização por busy-wait; assistir ao vídeo indicado da UNIVESP sobre Busy Wait.
- [ ] Aula 11 — Estudar semáforos: resolução de exclusão mútua utilizando semáforos (kernel + bloqueio de processos para acesso à região crítica); problema do produtor/consumidor com e sem paralelismo utilizando semáforos; consultar Silberschatz (seções 7.4, 7.5 e início da 7.6) e assistir ao vídeo "Semaphores" (Xoviabcs, ~9min).

### Execução

- [x] Executar o Lab0 — Processos no Linux: identificar e visualizar processos no shell, observar estados, executar processos em background, manipular prioridade e environment, verificar swap e estrutura de controle.
- [x] Entregar o Lab0 — Processos no Linux em PDF, com nome e matrícula no cabeçalho e no nome do arquivo. Prazo informado: 2026-08-24.
- [x] Executar o Lab1 — SVC e preparar o PDF de respostas e um arquivo `.c` por tarefa de implementação. Prazo informado: 2026-08-31.
- [x] Entregar o Lab1 — SVC em um `.zip`, seguindo o padrão de nome e cabeçalho exigido. Prazo informado: 2026-08-31.
- [x] Executar o Lab2 — SVC (parte 2) e preparar o PDF de respostas e um arquivo `.c` por tarefa de implementação.
- [x] Entregar o Lab2 — SVC (parte 2) em um `.zip`, seguindo o padrão de nome e cabeçalho exigido. Prazo informado: 2026-09-14.
- [ ] Aula 09 — Resolver os exercícios de Sincronização por Busy-Wait/HW.

## Prazos e lacunas

- Lab0 — 2026-08-24; entregue.
- Lab1 — 2026-08-31; entregue.
- Lab2 — 2026-09-14; entregue em 2026-09-13 (um dia antes do prazo).

> [!question] Em aberto (2026-09-18): nenhum prazo explícito apareceu no e-mail dos exercícios de Sincronização por Busy-Wait/HW (Aula 09).

> [!question] Em aberto (2026-09-22): nenhum prazo explícito apareceu no material da Aula 11 — Semáforos; não há lista de exercícios associada até o momento.

## Progresso confirmado (2026-09-09)

Confirmado diretamente pelo Yan: aulas 0–4 estudadas (introdução à disciplina; introdução a SO; processos; escalonamento de processos; Unix Kernel Mode), lista de exercícios de Introdução à SO resolvida, e Lab0 e Lab1 executados e entregues.

<!-- fonte: confirmação direta de [[USER|Yan Simmer]] em conversa, 2026-09-09 -->

## Correção (2026-09-09)

O registro anterior desta seção dizia Lab1 e Lab2 entregues por engano; o correto é Lab0 e Lab1. Corrigido conforme confirmação do Yan.

<!-- fonte: correção direta de [[USER|Yan Simmer]] em conversa, 2026-09-09 -->

## Fonte e escopo

Foram considerados os materiais e atividades publicados entre 2026-08-10 e 2026-09-04 no Google Sala de Aula da disciplina. Os avisos sobre sala, cancelamento e reposição de aula não foram convertidos em tarefas.

<!-- fonte: Gmail educacional, e-mails de Luis Antonio de Souza Junior no Google Sala de Aula, coletados em 2026-09-09 -->

## Verificação (2026-09-10)

Nenhum e-mail novo de Luis Antonio de Souza Junior nas últimas 24h.

<!-- fonte: Gmail educacional, verificação em 2026-09-10, sem e-mails novos -->

### Avisos

- 2026-09-10: Luis Antonio de Souza Junior avisou que os gabaritos das listas de exercícios podem ser vistos pessoalmente na sala do professor, na manhã de 2026-09-11 (sexta) ou 2026-09-14 (segunda); quem quiser ver deve enviar e-mail para combinar o horário.
- 2026-09-14: Confirmado por e-mail direto com Luis Antonio de Souza Junior (não via Google Sala de Aula): horário marcado para conferir o gabarito dos exercícios na sala do professor **hoje, 2026-09-14, a partir das 11h**.
- 2026-09-14: Lembrete automático do Google Sala de Aula (SO_2026_2, INF15980) informou que o prazo de entrega do Lab2 - SVC (parte 2) era 14 de set.; já registrado como entregue (ver Prazos e lacunas).
- 2026-09-19: Luis Antonio de Souza Junior avisou, no Google Sala de Aula, que as notas da P1 estão disponíveis na planilha de acompanhamento de notas e faltas (aba "Notas"), na seção Geral de Atividades da disciplina.
- 2026-09-22: Luis Antonio de Souza Junior avisou, no Google Sala de Aula (postado em 2026-09-21 14:23 BRT), sobre a SIS (https://life.inf.ufes.br/sis/): "Se tiverem interesse: tem que se inscrever." Ação opcional (inscrição), não é tarefa de estudo/entrega.

## Atualização (2026-09-11)

Dois e-mails novos de Luis Antonio de Souza Junior: um aviso sobre gabaritos (ver Avisos) e um novo material, "Aula 13 - Revisão P1" (adicionado a Estudo e ao Mapa de aulas). O e-mail do material trouxe apenas o título, sem conteúdo detalhado.

<!-- fonte: Gmail educacional, e-mails de Luis Antonio de Souza Junior no Google Sala de Aula, coletados em 2026-09-11 -->

## Verificação (2026-09-12)

Nenhum e-mail novo de Luis Antonio de Souza Junior nas últimas 24h.

<!-- fonte: Gmail educacional, verificação em 2026-09-12, sem e-mails novos -->

## Verificação (2026-09-13)

Nenhum e-mail novo de Luis Antonio de Souza Junior nas últimas 24h.

<!-- fonte: Gmail educacional, verificação em 2026-09-13, sem e-mails novos -->

## Atualização (2026-09-13)

Confirmado diretamente pelo Yan: listas 1, 2 e 4 de exercícios feitas. Marcadas em Tarefas > Estudo como: lista 1 = "exercícios de Introdução à SO" (já estava marcada), lista 2 = "exercícios de Processos e Estrutura de Controle", lista 4 = "exercícios sobre Unix, Kernel e Escalonamento Tradicional". A lista 3 ("exercícios de Escalonamento") permanece pendente.

> [!question] Em aberto: a nota não tinha as listas numeradas oficialmente pelo professor; a numeração 1–4 foi inferida pela ordem sequencial dos itens de "exercícios" em Tarefas > Estudo, seguindo o padrão de outras disciplinas do vault (ex.: [[TBO 2026-2]]).

<!-- fonte: confirmação direta de [[USER|Yan Simmer]] em conversa, 2026-09-13 -->

## Atualização (2026-09-13, 2)

Confirmado diretamente pelo Yan: lista 3 de exercícios ("exercícios de Escalonamento") feita. Marcada em Tarefas > Estudo. Todas as quatro listas de exercícios da disciplina (1, 2, 3 e 4) estão concluídas.

<!-- fonte: confirmação direta de [[USER|Yan Simmer]] em conversa, 2026-09-13 -->

## Atualização (2026-09-13, 3)

Confirmado diretamente pelo Yan: Lab2 — SVC (parte 2) executado e entregue, um dia antes do prazo (2026-09-14). Marcado em Tarefas > Execução; status atualizado em Prazos e lacunas.

> [!question] Em aberto: entrega confirmada, mas sem nota ou feedback do professor até o momento.

<!-- fonte: confirmação direta de [[USER|Yan Simmer]] em conversa, 2026-09-13 -->

## Atualização (2026-09-14)

Dois e-mails novos envolvendo Luis Antonio de Souza Junior nas últimas 24h: (1) um lembrete automático do Google Sala de Aula sobre o prazo do Lab2 - SVC, já cumprido (ver Avisos); (2) uma troca de e-mail direta confirmando horário para conferir o gabarito dos exercícios — hoje, 2026-09-14, às 11h, na sala do professor (ver Avisos). Nenhum item novo em Estudo ou Execução; nenhuma tarefa marcada como concluída a partir desses e-mails.

<!-- fonte: Gmail educacional, thread "A data de entrega é amanhã: Entrega Lab2 - SVC" (Google Sala de Aula) e thread "Gabarito dos Exercícios SO" (e-mail direto com Luis Antonio de Souza Junior), coletados em 2026-09-14 -->

## Verificação (2026-09-15)

Nenhum e-mail novo de Luis Antonio de Souza Junior nas últimas 24h.

<!-- fonte: Gmail educacional, verificação em 2026-09-15, sem e-mails novos -->

## Verificação (2026-09-16)

Nenhum e-mail novo de Luis Antonio de Souza Junior nas últimas 24h.

<!-- fonte: Gmail educacional, verificação em 2026-09-16, sem e-mails novos -->

## Verificação (2026-09-17)

Nenhum e-mail novo de Luis Antonio de Souza Junior nas últimas 24h.

<!-- fonte: Gmail educacional, verificação em 2026-09-17, sem e-mails novos -->

## Atualização (2026-09-18)

Dois e-mails novos de Luis Antonio de Souza Junior nas últimas 24h: (1) material de estudo "Aula 09 - Sincronização por Busy-Wait" (postado 2026-09-17 15:02 BRT), sobre introdução à sincronização de processos, região crítica, exclusão mútua e mecanismos de sincronização por busy-wait, com vídeo indicado da UNIVESP; (2) lista de exercícios "Exercícios - Sincronização por Busy-Wait/HW" (postado 2026-09-17 16:39 BRT), sem prazo explícito. Classificados como material de estudo e lista de exercícios, respectivamente; adicionados a Tarefas > Estudo, Tarefas > Execução e ao Mapa de aulas como Aula 09.

<!-- fonte: Gmail educacional, e-mails de Luis Antonio de Souza Junior no Google Sala de Aula ("Novo material: Aula 09 - Sincronização por Busy-Wait"; "Novo material: Exercícios - Sincronização por Busy-Wait/HW"), coletados em 2026-09-18 -->

## Atualização (2026-09-19)

Um e-mail novo de Luis Antonio de Souza Junior nas últimas 24h: aviso no Google Sala de Aula (postado em 2026-09-18 15:05 BRT) informando que as notas da P1 estão disponíveis na planilha de acompanhamento de notas e faltas, aba "Notas", seção Geral de Atividades. Classificado como aviso (sem ação de estudo/entrega); adicionado em Tarefas > Avisos.

> [!question] Em aberto: o e-mail não traz a nota do Yan nem o link direto da planilha — apenas informa que ela foi atualizada.

<!-- fonte: Gmail educacional, e-mail de Luis Antonio de Souza Junior no Google Sala de Aula ("Novo comunicado: Boa tarde pessoal! As notas da P1..."), postado em 2026-09-18 15:05 BRT, coletado em 2026-09-19 -->

## Verificação (2026-09-20)

Nenhum e-mail novo de Luis Antonio de Souza Junior nas últimas 24h.

<!-- fonte: Gmail educacional, verificação em 2026-09-20, sem e-mails novos -->

## Verificação (2026-09-21)

Nenhum e-mail novo de Luis Antonio de Souza Junior nas últimas 24h.

<!-- fonte: Gmail educacional, verificação em 2026-09-21, sem e-mails novos -->

## Atualização (2026-09-22)

Dois e-mails novos de Luis Antonio de Souza Junior nas últimas 24h: (1) material de estudo "Aula 11 - Semáforos" (postado 2026-09-21 12:30 BRT), sobre resolução de exclusão mútua com semáforos e o problema do produtor/consumidor, com material complementar (Silberschatz, seções 7.4–7.6) e vídeo indicado; (2) aviso "Sobre a SIS" (postado 2026-09-21 14:23 BRT), divulgando o link https://life.inf.ufes.br/sis/ e informando que é preciso se inscrever para quem tiver interesse. Classificados como material de estudo e aviso, respectivamente; o primeiro adicionado a Tarefas > Estudo e ao Mapa de aulas como Aula 11, o segundo adicionado a Tarefas > Avisos.

> [!question] Em aberto: o e-mail sobre a SIS não explica o que é a SIS (sigla não expandida) nem se a inscrição é relevante para a disciplina ou apenas uma divulgação externa.

<!-- fonte: Gmail educacional, e-mails de Luis Antonio de Souza Junior no Google Sala de Aula ("Novo material: Aula 11 - Semáforos"; "Novo comunicado: Pessoal, Sobre a SIS..."), coletados em 2026-09-22 -->
