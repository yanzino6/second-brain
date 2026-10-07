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
- Aula 2 — Processos (conceito, contexto, troca de contexto, BCP) — estudo + execução — material revisado
- Aula 3 — Escalonamento de processos — estudo + execução — material revisado
- Aula 4 — Unix: Kernel Mode — estudo — material revisado
- Aula não identificada — demais conteúdos e laboratórios após Unix Kernel Mode (Escalonamento Tradicional vs. Kernel Preemptivo; laboratório de chamadas ao sistema; Sinais no Unix; Lab0; Lab1; Lab2) — estudo + execução — pendente/material revisado conforme checkbox em Tarefas
- Aula 13 — Revisão P1 — estudo — pendente
- Aula 09 — Sincronização por Busy-Wait — estudo + execução — pendente
- Aula 11 — Semáforos — estudo + execução — pendente
- Aula 12 — Monitores — estudo + execução — pendente
- Aula 14 — Pipes — estudo — pendente
- Aula 15 — Lab 3 - Pipes — execução — pendente
- Aula 16 — Threads (Parte 1) — estudo — pendente

> [!question] Em aberto: a numeração de aulas 0–4 vem da confirmação direta do Yan em 2026-09-09 (ver "Progresso confirmado"), não de numeração oficial do professor nos e-mails. Os itens posteriores a Unix Kernel Mode (incluindo Lab0, Lab1 e Lab2) não têm aula de conteúdo confirmada nos e-mails registrados — apenas os laboratórios têm prazo de entrega (ver Prazos e lacunas).

> [!question] Em aberto (2026-09-29): "Aula 14 — Pipes" chegou numerada pelo professor, mas não há confirmação de conteúdo para a Aula 13 na forma de material próprio (apenas "Revisão P1") nem para eventual aula entre a 12 e a 14 — a numeração real segue parcialmente incerta, como já registrado acima para as aulas 5 a 8, 10 e 13 (esta última é só revisão, não conteúdo novo).

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
- [x] Estudar Unix: Escalonamento Tradicional versus Kernel Preemptivo; consultar o material complementar e os dois vídeos indicados.
- [x] Estudar os exercícios sobre Unix, Kernel e Escalonamento Tradicional.
- [x] Estudar o laboratório de chamadas ao sistema (kernel), com `fork()`, concorrência entre processos pai e filho, user ID e process group ID.
- [x] Estudar Sinais no Unix em C; ler o material complementar, revisar `pause()`, o efeito de `exec()` sobre handlers e assistir aos vídeos indicados.
- [x] Estudar o laboratório Lab2 — SVC (parte 2): comunicação entre processos pai e filho, alteração de código no processo filho e reconhecimento da troca de estados.
- [ ] Aula 13 — Revisão P1: estudar o material de revisão para a P1; o e-mail trouxe apenas o título, sem detalhar o conteúdo.
- [ ] Aula 09 — Estudar sincronização por busy-wait: introdução à sincronização de processos, região crítica e exclusão mútua, mecanismos de sincronização por busy-wait; assistir ao vídeo indicado da UNIVESP sobre Busy Wait.
- [ ] Aula 11 — Estudar semáforos: resolução de exclusão mútua utilizando semáforos (kernel + bloqueio de processos para acesso à região crítica); problema do produtor/consumidor com e sem paralelismo utilizando semáforos; consultar Silberschatz (seções 7.4, 7.5 e início da 7.6) e assistir ao vídeo "Semaphores" (Xoviabcs, ~9min).
- [ ] Aula 12 — Estudar Monitores: sincronização utilizando mecanismo de monitores; estrutura básica de monitor e exclusão mútua; abordagens de Hoare e Hansen para monitores; problemas dos filósofos glutões e produtor/consumidor; implementação de monitores utilizando semáforos; consultar Tanenbaum ("Sistemas Operacionais: projeto e implementação", 3a. ed., seção 2.3.7, pp. 81-85) e os dois vídeos indicados.
- [ ] Aula 14 — Estudar Pipes: comunicação entre processos (modo usuário) utilizando Pipes — conceito e implementação de Pipes e Filas; consultar o material complementar (Celso A. S. Santos, "Programação em tempo real") e os sete vídeos indicados sobre uso de `fork`/`pipe` em C.
- [ ] Aula 16 — Estudar Threads (Parte 1): definição de threads, abstração de processos em fluxos independentes de execução, propriedade de recursos vs. unidade de escalonamento, task control block, comparação entre modelos de threads (user-level e kernel-level), modelos híbridos e documentação pthread (Linux); consultar Tanenbaum, seção 2.2 "Threads" (até 2.2.6, pp. 57-67) e os dois vídeos indicados (um deles com explicação da biblioteca PTHREAD a partir de 25min).

### Execução

- [x] Executar o Lab0 — Processos no Linux: identificar e visualizar processos no shell, observar estados, executar processos em background, manipular prioridade e environment, verificar swap e estrutura de controle.
- [x] Entregar o Lab0 — Processos no Linux em PDF, com nome e matrícula no cabeçalho e no nome do arquivo. Prazo informado: 2026-08-24.
- [x] Executar o Lab1 — SVC e preparar o PDF de respostas e um arquivo `.c` por tarefa de implementação. Prazo informado: 2026-08-31.
- [x] Entregar o Lab1 — SVC em um `.zip`, seguindo o padrão de nome e cabeçalho exigido. Prazo informado: 2026-08-31.
- [x] Executar o Lab2 — SVC (parte 2) e preparar o PDF de respostas e um arquivo `.c` por tarefa de implementação.
- [x] Entregar o Lab2 — SVC (parte 2) em um `.zip`, seguindo o padrão de nome e cabeçalho exigido. Prazo informado: 2026-09-14.
- [ ] Aula 09 — Resolver os exercícios de Sincronização por Busy-Wait/HW.
- [ ] Aula 11 — Resolver os exercícios de Semáforos.
- [ ] Aula 12 — Resolver os exercícios de Monitores ("Exercícios - Monitores"). O e-mail trouxe apenas o título, sem conteúdo detalhado.
- [ ] Aula 15 — Executar o Lab3 - Pipes: laboratório de exercícios sobre comunicação entre processos usando Pipes.
- [ ] Aula 15 — Entregar o Lab3 - Pipes em um `.zip`, com um arquivo `.c` para cada tarefa de implementação de código; nome do aluno e matrícula devem constar no cabeçalho do texto, no cabeçalho de cada `.c` e no nome do arquivo (formato indicado no e-mail: nome_separado_por_underline-matricula, com extensão de exemplo ".pdf" — o e-mail usa esse exemplo apesar de pedir entrega em `.zip`). **Prazo: 2026-10-05.**

## Prazos e lacunas

- Lab0 — 2026-08-24; entregue.
- Lab1 — 2026-08-31; entregue.
- Lab2 — 2026-09-14; entregue em 2026-09-13 (um dia antes do prazo).

> [!question] Em aberto (2026-09-18): nenhum prazo explícito apareceu no e-mail dos exercícios de Sincronização por Busy-Wait/HW (Aula 09).

> [!question] Em aberto (2026-09-22): nenhum prazo explícito apareceu no material da Aula 11 — Semáforos; não há lista de exercícios associada até o momento.

> [!question] Em aberto (2026-09-25): a lista de exercícios da Aula 11 — Semáforos chegou em 2026-09-24, mas o e-mail não trouxe prazo de entrega.

> [!question] Em aberto (2026-09-29): nenhum prazo explícito apareceu no e-mail dos exercícios de Monitores (Aula 12).

- Lab3 - Pipes (Aula 15) — 2026-10-05.

## Progresso confirmado (2026-09-09)

Confirmado diretamente pelo Yan: aulas 0–4 estudadas (introdução à disciplina; introdução a SO; processos; escalonamento de processos; Unix Kernel Mode), lista de exercícios de Introdução à SO resolvida, e Lab0 e Lab1 executados e entregues.

<!-- fonte: confirmação direta de [[USER|Yan Simmer]] em conversa, 2026-09-09 -->

## Progresso confirmado (2026-09-23)

Confirmado diretamente pelo Yan: todos os exercícios resolvidos (Processos, Escalonamento, Unix/Kernel), estudo dos laboratórios feito (chamadas ao sistema e Lab2), Lab2 executado e entregue, e materiais de "Escalonamento Tradicional versus Kernel Preemptivo" e "Sinais no Unix em C" vistos e estudados. Ficam pendentes só o que chegou depois: Aula 13 (Revisão P1), Aula 09 (estudo e exercícios) e Aula 11.

> [!question] Em aberto: o Yan não disse nada sobre Aula 13, Aula 09 e Aula 11; seguem pendentes até ele confirmar.

<!-- fonte: confirmação direta de [[USER|Yan Simmer]] em conversa, 2026-09-23 -->

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
- 2026-09-24 (postado 14:42 BRT): Luis Antonio de Souza Junior avisou que a aula de SO daquele dia começaria pontualmente às 15h, porque precisaria terminá-la mais cedo.
- 2026-10-04 (postado 12:58 BRT): lembrete automático do Google Sala de Aula de que o prazo de entrega do Lab3 - Pipes (Aula 15) é amanhã, 2026-10-05; já registrado em Prazos e lacunas.
- 2026-10-05 (postado 13:05 BRT): Luis Antonio de Souza Junior divulgou, no Google Sala de Aula, a palestra externa "IA na dermatologia: um olhar clínico sobre aplicações atuais e novas fronteiras", com Dr. Bruno Simão dos Santos, promovida pelo LIFE (Laboratório de Inteligência Artificial em Saúde). Data: 2026-10-05 (mesmo dia da postagem), 19h, transmitida pelo canal do LIFE no YouTube (https://www.youtube.com/live/49bB5DUZ6Yo). Participação não obrigatória, sem vínculo direto com o conteúdo de Sistemas Operacionais.
- 2026-10-06 (postado 16:05 BRT): Luis Antonio de Souza Junior avisou, no Google Sala de Aula, para não esquecer de se inscrever no minicurso de quinta-feira (9h) da "semana de informática em saúde" (uso de IA para um problema prático de patologia). Ação opcional (inscrição), não é tarefa de estudo/entrega da disciplina.

> [!question] Em aberto (2026-10-07): o e-mail de 2026-10-06 não informa a data exata dessa "quinta-feira" (possivelmente 2026-10-08, por proximidade com a data de envio, mas isso não está confirmado no texto) nem o link de inscrição do minicurso.

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

## Verificação (2026-09-23)

Nenhum e-mail novo de Luis Antonio de Souza Junior nas últimas 24h.

<!-- fonte: Gmail educacional, verificação em 2026-09-23, sem e-mails novos -->

## Verificação (2026-09-24)

Nenhum e-mail novo de Luis Antonio de Souza Junior nas últimas 24h.

<!-- fonte: Gmail educacional, verificação em 2026-09-24, sem e-mails novos -->

## Atualização (2026-09-25)

Três e-mails novos de Luis Antonio de Souza Junior nas últimas 24h: (1) lista de exercícios "Exercícios - Semáforos" (postado 2026-09-24 10:03 BRT), sem conteúdo detalhado no corpo do e-mail e sem prazo explícito; (2) aviso (postado 2026-09-24 14:42 BRT) de que a aula daquele dia começaria pontualmente às 15h; (3) novo material "Aula 12 - Monitores" (postado 2026-09-24 14:42 BRT), sobre sincronização utilizando mecanismo de monitores, estrutura básica de monitor e exclusão mútua, abordagens de Hoare e Hansen, problemas dos filósofos glutões e produtor/consumidor, e implementação de monitores utilizando semáforos, com material complementar (Tanenbaum, seção 2.3.7) e dois vídeos indicados. Classificados como lista de exercícios, aviso e material de estudo, respectivamente; adicionados a Tarefas > Execução (Aula 11), Tarefas > Avisos e Tarefas > Estudo (Aula 12), e ao Mapa de aulas (linha da Aula 11 atualizada para "estudo + execução"; nova linha para Aula 12).

<!-- fonte: Gmail educacional, e-mails de Luis Antonio de Souza Junior no Google Sala de Aula ("Novo material: Exercícios - Semáforos"; "Novo comunicado: Boa tarde pessoal!..."; "Novo material: Aula 12 - Monitores"), coletados em 2026-09-25 -->

## Verificação (2026-09-26)

Nenhum e-mail novo de Luis Antonio de Souza Junior nas últimas 24h.

<!-- fonte: Gmail educacional, verificação em 2026-09-26, sem e-mails novos -->

## Verificação (2026-09-27)

Nenhum e-mail novo de Luis Antonio de Souza Junior nas últimas 24h.

<!-- fonte: Gmail educacional, verificação em 2026-09-27, sem e-mails novos -->

## Verificação (2026-09-28)

Nenhum e-mail novo de Luis Antonio de Souza Junior nas últimas 24h.

<!-- fonte: Gmail educacional, verificação em 2026-09-28, sem e-mails novos -->

## Atualização (2026-09-29)

Dois e-mails novos de Luis Antonio de Souza Junior nas últimas 24h: (1) novo material "Aula 14 - Pipes" (postado 2026-09-28 12:31 BRT), sobre comunicação entre processos (modo usuário) utilizando Pipes — conceito e implementação de Pipes e Filas —, com material complementar (Celso A. S. Santos, "Programação em tempo real") e sete vídeos indicados; (2) lista de exercícios "Exercícios - Monitores" (postado 2026-09-28 12:57 BRT), sem conteúdo detalhado no corpo do e-mail e sem prazo explícito. Classificados como material de estudo e lista de exercícios, respectivamente; adicionados a Tarefas > Estudo (Aula 14) e Tarefas > Execução (Aula 12), e ao Mapa de aulas (nova linha para Aula 14; linha da Aula 12 atualizada para "estudo + execução").

<!-- fonte: Gmail educacional, e-mails de Luis Antonio de Souza Junior no Google Sala de Aula ("Novo material: Aula 14 - Pipes"; "Novo material: Exercícios - Monitores"), postados em 2026-09-28 entre 12:31 e 12:57 BRT, coletados em 2026-09-29 -->

## Verificação (2026-09-30)

Nenhum e-mail novo de Luis Antonio de Souza Junior nas últimas 24h.

<!-- fonte: Gmail educacional, verificação em 2026-09-30, sem e-mails novos -->

## Verificação (2026-10-01)

Nenhum e-mail novo de Luis Antonio de Souza Junior nas últimas 24h.

<!-- fonte: Gmail educacional, verificação em 2026-10-01, sem e-mails novos -->

## Atualização (2026-10-02)

Dois e-mails novos de Luis Antonio de Souza Junior nas últimas 24h, ambos sobre o mesmo laboratório: (1) novo material "Aula 15 - Lab 3 - Pipes" (postado 2026-10-01 12:29 BRT), descrito apenas como "Laboratório de exercícios - comunicação entre processos usando Pipes."; (2) nova atividade "Entrega Lab3 - Pipes" (postado 2026-10-01 15:48 BRT), pedindo arquivo `.zip` com um `.c` por tarefa de implementação, nome e matrícula no cabeçalho do texto, de cada `.c` e no nome do arquivo, com **prazo em 5 de out. (2026-10-05)**. Classificados como lista/laboratório (tarefa com prazo); adicionados a Tarefas > Execução (Aula 15) e a Prazos e lacunas, e ao Mapa de aulas como nova linha "Aula 15 — Lab 3 - Pipes — execução — pendente".

<!-- fonte: Gmail educacional, e-mails de Luis Antonio de Souza Junior no Google Sala de Aula ("Novo material: Aula 15 - Lab 3 - Pipes"; "Nova atividade: Entrega Lab3 - Pipes"), postados em 2026-10-01 entre 12:29 e 15:48 BRT, coletados em 2026-10-02 -->

## Verificação (2026-10-03)

Nenhum e-mail novo de Luis Antonio de Souza Junior nas últimas 24h. O Lab3 - Pipes (Aula 15) segue com prazo de entrega em 2026-10-05.

<!-- fonte: Gmail educacional, verificação em 2026-10-03, sem e-mails novos -->

## Verificação (2026-10-04)

Nenhum e-mail novo de Luis Antonio de Souza Junior nas últimas 24h. O Lab3 - Pipes (Aula 15) segue com prazo de entrega em 2026-10-05 — amanhã.

<!-- fonte: Gmail educacional, verificação em 2026-10-04, sem e-mails novos -->

## Atualização (2026-10-05)

Um e-mail novo nas últimas 24h, do Google Sala de Aula (SO_2026_2, INF15980): lembrete automático de que o prazo do Lab3 - Pipes (Aula 15) é amanhã, 5 de out. (2026-10-05), repetindo as instruções de entrega já registradas (arquivo `.zip`, um `.c` por tarefa, nome e matrícula no cabeçalho e no nome do arquivo). Classificado como aviso (lembrete automático de prazo já tracked, sem tarefa nova); adicionado em Tarefas > Avisos.

<!-- fonte: Gmail educacional, e-mail do Google Sala de Aula ("A data de entrega é amanhã: Entrega Lab3 - Pipes"), postado em 2026-10-04 12:58 BRT, coletado em 2026-10-05 -->

## Atualização (2026-10-06)

Dois e-mails novos de/via Luis Antonio de Souza Junior nas últimas 24h: (1) novo material "Aula 16 - Threads (Parte 1)" (postado 2026-10-05 14:36 BRT), sobre definição de threads, abstração de processos em fluxos independentes de execução, propriedade de recursos vs. unidade de escalonamento, task control block, modelos user-level/kernel-level e híbridos, e documentação pthread, com material complementar (Tanenbaum, seção 2.2, pp. 57-67) e dois vídeos indicados; (2) divulgação de palestra externa sobre IA na dermatologia (postado 2026-10-05 13:05 BRT), sem vínculo direto com o conteúdo da disciplina (ver Avisos). Classificados como material de estudo e aviso, respectivamente; o primeiro adicionado a Tarefas > Estudo e ao Mapa de aulas como Aula 16, o segundo adicionado a Tarefas > Avisos.

<!-- fonte: Gmail educacional, e-mails de/via Luis Antonio de Souza Junior no Google Sala de Aula ("Novo material: Aula 16 - Threads (Parte 1)"; "Novo comunicado: 📢 PALESTRA | IA NA DERMATOLOGIA"), postados em 2026-10-05 entre 13:05 e 14:36 BRT, coletados em 2026-10-06 -->

## Atualização (2026-10-07)

Um e-mail novo de Luis Antonio de Souza Junior nas últimas 24h: aviso no Google Sala de Aula (postado em 2026-10-06 16:05 BRT) pedindo para não esquecer de se inscrever no minicurso de quinta-feira (9h) da "semana de informática em saúde" (uso de IA para um problema prático de patologia). Classificado como aviso (ação opcional de inscrição, não é tarefa de estudo/entrega da disciplina); adicionado em Tarefas > Avisos, com lacuna sobre a data exata e o link de inscrição.

<!-- fonte: Gmail educacional, e-mail de Luis Antonio de Souza Junior no Google Sala de Aula ("Novo comunicado: Boa tarde pessoal. Não se esqueçam de…"), postado em 2026-10-06 16:05 BRT, coletado em 2026-10-07 -->
