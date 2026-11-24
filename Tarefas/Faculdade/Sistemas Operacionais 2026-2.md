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
- Aula 17 — Threads (Parte 2) — estudo — pendente
- Aula 18 — Lab 4 - Semáforos e Pthread — execução — pendente
- Aula 19 — Revisão P2 (Sincronização, IPC e Threads) — estudo — pendente
- Aula 20 — Gerência de Memória — estudo + execução — pendente
- Aula 22 — Paginação — estudo + execução — pendente
- Aula 23.1 — Algoritmos de Substituição de Páginas — estudo + execução — pendente
- Aula 23.2 — Laboratório 5 - Memória Compartilhada — execução — pendente
- Aula 24 — Sistemas de Arquivos — estudo + execução — pendente
- Aula não identificada — Trabalho Prático (TP), 1ª Etapa — execução — pendente
- Aula 25 — Extra - Virtualização e Docker — estudo — pendente

> [!question] Em aberto (2026-11-13): não há material correspondente a uma "Aula 21" nos e-mails coletados — a numeração salta de Aula 20 (postada 19/10) para Aula 22 (mesmo dia, 19/10). Não se sabe se houve aula 21 só presencial, sem material publicado, ou outro motivo.

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
- [ ] Aula 17 — Estudar Threads (Parte 2): implementação de threads no Linux (pthread.h), implementação de exemplos/exercícios; sete vídeos indicados (introdução a pthreads; diferença entre processos e threads; race conditions; mutex em C/pthread_mutex; criação de threads em loop; passagem de argumentos para threads em C; exemplo prático de soma de números em um array).
- [ ] Aula 19 — Estudar a Revisão P2: sincronização, IPC e Threads. O e-mail trouxe apenas o título e o tema geral, sem detalhar conteúdo.
- [ ] Aula 20 — Estudar Gerência de Memória: conceitos de memória e mapeamento de memória física, controle de espaços de memória física; dois vídeos indicados (What is Virtual Memory?; Operating System Memory Management: Process, Fragmentation, Deallocation).
- [ ] Aula 22 — Estudar Paginação: memória virtual, paginação, tradução de endereço virtual-físico, TLB, tabela de páginas multinível e tabela de páginas invertida; consultar Tanenbaum (seção 3.3 "Memória Virtual", pp. 114-122) e cinco vídeos do MIT indicados (paginação básica, page faults, aritmética de TLB/tradução de endereço, exemplos de memória virtual, tabelas de páginas multinível).
- [ ] Aula 23.1 — Estudar Algoritmos de Substituição de Páginas: algoritmos de tratamento de Page Fault e projeto com Working Set; consultar Tanenbaum (seção 3.4 "Algoritmos de Substituição de Páginas", pp. 122-133, e seção 3.5 "Questões de projeto para sistemas de paginação" até 3.5.5, pp. 133-137).
- [ ] Aula 24 — Estudar Sistemas de Arquivos: gerência de arquivos, sistemas de arquivos e suas estruturas internas, tipos de arquivos (UNIX), implementação de sistemas de arquivos e diretórios, estrutura i-node (UNIX), arquivos compartilhados, gerenciamento de espaço em disco; consultar Tanenbaum, capítulo 4 "Sistemas de Arquivos" até a seção 4.4.3 inclusa (pp. 158-190), pulando as seções 4.1, 4.2, 4.3.5, 4.3.6, 4.3.7 e 4.4.2 por indicação do próprio professor.
- [ ] Aula 25 — Estudar a aula extra sobre Virtualização e Docker. O e-mail trouxe apenas o título, sem conteúdo detalhado.

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
- [ ] Aula 18 — Executar o Lab 4 - Semáforos e Pthread (implementação de compartilhamento de variáveis entre threads e entre processos) e entregar em `.zip`, um arquivo `.c` por tarefa de implementação de código; nome e matrícula no cabeçalho do texto, de cada `.c` e no nome do arquivo (mesmo formato nome_separado_por_underline-matricula, com extensão de exemplo ".pdf" no e-mail apesar de pedir `.zip` — mesma inconsistência já vista no Lab3). **Prazo: 2026-10-19.**
- [ ] Aula 20 — Resolver os "Exercícios - Gerência de Memória". O e-mail trouxe apenas o título, sem conteúdo detalhado nem prazo.
- [ ] Aula 22 — Resolver os "Exercícios - Paginação" (exercícios resolvidos do MIT, para conferência).
- [ ] Aula 23.1 — Resolver os "Exercícios - Algoritmos de Substituição de Páginas". O e-mail trouxe apenas o título, sem conteúdo detalhado nem prazo.
- [ ] Aula 23.2 — Executar o Laboratório 5 - Memória Compartilhada e entregar seguindo o mesmo padrão de nome/cabeçalho dos laboratórios anteriores (nome_separado_por_underline-matricula.PDF). **Prazo: 2026-10-29.**
- [ ] Aula 24 — Resolver os "Exercícios - Sistemas de Arquivos". O e-mail trouxe apenas o título, sem conteúdo detalhado nem prazo.
- [ ] Aula não identificada — Trabalho Prático (TP), 1ª Etapa: entregar link do repositório GitHub (adicionar o usuário do professor, `luisouza`, como colaborador) ou `.tar.gz` com fontes e arquivos de descrição do TP; em entregas por GitHub, será considerado o momento do último commit. **Prazo: 2026-12-04, até as 07h59.** Especificação v1 publicada em 2026-10-24, com aviso de que "alterações ainda podem ser realizadas na especificação" — conferir se a versão final mudou antes de entregar.

## Prazos e lacunas

- Lab0 — 2026-08-24; entregue.
- Lab1 — 2026-08-31; entregue.
- Lab2 — 2026-09-14; entregue em 2026-09-13 (um dia antes do prazo).

> [!question] Em aberto (2026-09-18): nenhum prazo explícito apareceu no e-mail dos exercícios de Sincronização por Busy-Wait/HW (Aula 09).

> [!question] Em aberto (2026-09-22): nenhum prazo explícito apareceu no material da Aula 11 — Semáforos; não há lista de exercícios associada até o momento.

> [!question] Em aberto (2026-09-25): a lista de exercícios da Aula 11 — Semáforos chegou em 2026-09-24, mas o e-mail não trouxe prazo de entrega.

> [!question] Em aberto (2026-09-29): nenhum prazo explícito apareceu no e-mail dos exercícios de Monitores (Aula 12).

- Lab3 - Pipes (Aula 15) — 2026-10-05.
- Lab 4 - Semáforos e Pthread (Aula 18) — 2026-10-19.
- Lab. 5 - Memória Compartilhada (Aula 23.2) — 2026-10-29.
- **Trabalho Prático (TP), 1ª Etapa — 2026-12-04, até as 07h59.** Prazo corrigido pelo professor em 2026-10-27 (estava 04/11/2026 na especificação v1 de 2026-10-24, considerada "offsynch" pelo próprio professor); reconfirmado em 2026-11-09 na atividade de entrega.
- **P2 (2ª Prova) — confirmada para 2026-11-19 (quinta-feira).** Depois de adiada de uma data não registrada nesta nota para 2026-11-16 (por manutenção de energia na UFES em 11 e 12/11), e depois reconfirmada para 19/11 em 2026-11-11 ("Não haverão mais alterações nesta data"). **Próxima na data desta coleta (2026-11-13) — faltam 6 dias.**

> [!question] Em aberto (2026-11-13): nenhum e-mail capturado nesta busca (2026-10-15 a 2026-11-13) menciona a data original da P2 antes do primeiro adiamento — não é possível reconstruir quando a prova estava marcada originalmente sem revisar e-mails anteriores a 2026-10-15.

> [!question] Em aberto (2026-11-13): o e-mail "Grupos dos Trabalhos" (postado 2026-10-22) não traz a lista de duplas em texto plano, nem confirma se o Yan já está em uma dupla para o Trabalho Prático — é preciso abrir a postagem no Google Sala de Aula.

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

- 2026-10-08: e-mail do LIFE (Laboratório de Inteligência Artificial em Saúde, `life@inf.ufes.br`, não é o professor nem o Google Sala de Aula) confirmou, para quem se inscreveu, o minicurso "Introdução à histopatologia digital e análise de imagens com IA" da 3ª Semana de Informática em Saúde (SIS), em 08/10/2026 (quinta-feira), 9h às 11h30, via Google Meet (https://meet.google.com/vmc-nosu-hsh). **Resolve** a lacuna de data e link registrada em 2026-10-07. Minicurso sem vínculo direto obrigatório com o conteúdo de Sistemas Operacionais (ação opcional de inscrição, já confirmada).
- 2026-10-18 (lembrete automático): prazo de entrega do Lab 4 - Semáforos e Pthread (Aula 18) é amanhã, 19/10; já registrado em Execução e Prazos e lacunas.
- 2026-10-22 (postado 16:13 BRT): Luis Antonio de Souza Junior publicou "Grupos dos Trabalhos" no Google Sala de Aula, listando os grupos (duplas, 2 membros) dos trabalhos práticos. O e-mail não traz a lista em texto plano — ver lacuna em Prazos e lacunas.
- 2026-10-27 (postado 19:44 BRT): Luis Antonio de Souza Junior avisou que corrigiu o prazo de entrega do Trabalho Prático, que estava "offsynch": a data correta é 04/12/2026, até as 07h59 — substitui o prazo de 04/11/2026 informado inicialmente na especificação v1 (2026-10-24). Já registrado em Execução e Prazos e lacunas.
- 2026-10-28 (lembrete automático): prazo de entrega do Lab. 5 - Memória Compartilhada (Aula 23.2) é amanhã, 29/10; já registrado em Execução e Prazos e lacunas.
- 2026-11-10 (postado 10:53 BRT): manutenção de energia na UFES em 11 e 12/11 cancelou as atividades acadêmicas do campus de Goiabeiras nesses dias; a P2 foi remarcada para segunda-feira, 16/11.
- 2026-11-11 (postado 10:53 BRT): Luis Antonio de Souza Junior confirmou que a P2 ficará para a semana seguinte, dia 19/11 (quinta-feira) — "não haverão mais alterações nesta data". Substitui a data de 16/11 anunciada no dia anterior. O professor mencionou que o cronograma já passou por "127 alterações" nas aulas e provas no semestre. **Prova com data próxima na data desta coleta (2026-11-13).**

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
>
> **Parcialmente resolvida em 2026-10-08:** o e-mail do LIFE sobre o minicurso de histopatologia digital (ver seção "Atualização (2026-10-08)") chama o evento de "3ª Semana de Informática em Saúde (SIS)" — a sigla significa Semana de Informática em Saúde. Ainda não confirmado se a inscrição tem relevância para a disciplina de Sistemas Operacionais ou é só divulgação externa do LIFE.

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

## Atualização (2026-10-08)

Um e-mail novo nas últimas 24h relacionado à disciplina, mas não vindo de Luis Antonio de Souza Junior nem do Google Sala de Aula: o LIFE (Laboratório de Inteligência Artificial em Saúde, `life@inf.ufes.br`) confirmou, para os inscritos, o minicurso "Introdução à histopatologia digital e análise de imagens com IA" da 3ª Semana de Informática em Saúde (SIS), em 08/10/2026 (hoje, quinta-feira), 9h às 11h30, via Google Meet (https://meet.google.com/vmc-nosu-hsh). Classificado como aviso (ação opcional já confirmada, sem ação de estudo/entrega da disciplina); adicionado em Tarefas > Avisos. Resolve a lacuna sobre data exata e link, registrada em 2026-10-07.

<!-- fonte: Gmail educacional, e-mail do LIFE/UFES ("Minicurso: Introdução à histopatologia digital e análise de imagens com IA"), remetente life@inf.ufes.br, postado em 2026-10-07 19:25 BRT, coletado em 2026-10-08 -->

## Verificação (2026-10-09)

Nenhum e-mail novo de Luis Antonio de Souza Junior nas últimas 24h.

<!-- fonte: Gmail educacional, verificação em 2026-10-09, sem e-mails novos -->

## Verificação (2026-10-10)

Nenhum e-mail novo de Luis Antonio de Souza Junior nas últimas 24h.

<!-- fonte: Gmail educacional, verificação em 2026-10-10, sem e-mails novos -->

## Verificação (2026-10-11)

Nenhum e-mail novo de Luis Antonio de Souza Junior nas últimas 24h.

<!-- fonte: Gmail educacional, verificação em 2026-10-11, sem e-mails novos -->

## Verificação (2026-10-12)

Nenhum e-mail novo de Luis Antonio de Souza Junior nas últimas 24h.

<!-- fonte: Gmail educacional, verificação em 2026-10-12, sem e-mails novos -->

## Verificação (2026-10-13)

Nenhum e-mail novo de Luis Antonio de Souza Junior nas últimas 24h.

<!-- fonte: Gmail educacional, verificação em 2026-10-13, sem e-mails novos -->

## Verificação (2026-10-15)

Nenhum e-mail novo de Luis Antonio de Souza Junior nas últimas 48h (busca estendida para cobrir 2026-10-14, dia em que esta rotina não gerou relatório).

<!-- fonte: Gmail educacional, verificação em 2026-10-15, sem e-mails novos -->

## Atualização (2026-11-13) — processamento retroativo

Esta rotina não executou entre 2026-10-16 e 2026-11-12 (gap de 28 dias). Processados agora, com atraso, 21 e-mails de Luis Antonio de Souza Junior/Google Sala de Aula, de 2026-10-15 a 2026-11-11: 9 materiais de estudo (Aula 17 - Threads Parte 2; Aula 18 - Lab 4; Aula 20 - Gerência de Memória; Aula 22 - Paginação; Aula 23.2 - Lab 5; Especificação do TP v1; Aula 19 - Revisão P2; Aula 23.1 - Substituição de Páginas; Aula 24 - Sistemas de Arquivos), 3 listas de exercícios (Exercícios - Paginação; Exercícios - Gerência de Memória; Exercícios - Substituição de Páginas), 2 novas atividades com prazo (Entrega Lab 4; Entrega Lab. 5; Entrega TP - 1ª Etapa, totalizando 3 atividades com prazo) e 7 avisos (2 lembretes automáticos de prazo, Grupos dos Trabalhos, correção do prazo do TP, manutenção de energia, e os dois avisos sobre a data da P2). Todos os itens novos foram adicionados a Mapa de aulas, Tarefas > Estudo, Tarefas > Execução, Tarefas > Avisos e Prazos e lacunas, nas seções correspondentes acima.

**Destaque urgente:** a P2 está confirmada para 2026-11-19 (quinta-feira), a 6 dias da data desta coleta, depois de dois adiamentos (ver Avisos e Prazos e lacunas). O Trabalho Prático, 1ª Etapa, tem prazo confirmado em 2026-12-04 às 07h59, após correção de data pelo próprio professor.

<!-- fonte: Gmail educacional, e-mails de Luis Antonio de Souza Junior no Google Sala de Aula (busca after:2026/10/15 before:2026/11/14 from:classroom.google.com), 21 threads lidos integralmente, coletado em 2026-11-13 -->

## Verificação (2026-11-14)

Nenhum e-mail novo de Luis Antonio de Souza Junior nas últimas 24h. A P2 segue confirmada para 19/11/2026 e o Trabalho Prático (1ª Etapa) para 04/12/2026 às 07h59.

<!-- fonte: Gmail educacional, verificação em 2026-11-14, sem e-mails novos -->

## Verificação (2026-11-15)

Nenhum e-mail novo de Luis Antonio de Souza Junior nas últimas 24h. A P2 segue confirmada para 19/11/2026 — faltam 4 dias — e o Trabalho Prático (1ª Etapa) para 04/12/2026 às 07h59.

<!-- fonte: Gmail educacional, verificação em 2026-11-15, sem e-mails novos -->

## Verificação (2026-11-16)

Nenhum e-mail novo de Luis Antonio de Souza Junior nas últimas 24h. A P2 segue confirmada para 19/11/2026 — faltam 3 dias — e o Trabalho Prático (1ª Etapa) para 04/12/2026 às 07h59.

<!-- fonte: Gmail educacional, verificação em 2026-11-16, sem e-mails novos -->

## Atualização (2026-11-22) — processamento retroativo de 2026-11-17 a 2026-11-22

Esta rotina ficou sem executar entre 2026-11-17 e 2026-11-21. Processado agora, com atraso: um e-mail de Luis Antonio de Souza Junior, datado de 2026-11-16 (12:58 BRT, não capturado na verificação daquele dia) — novo material "Exercícios - Sistemas de Arquivos" no Google Sala de Aula, sem conteúdo detalhado nem prazo. Classificado como lista de exercícios; adicionado a Tarefas > Execução (Aula 24) e ao Mapa de aulas (linha da Aula 24 atualizada de "estudo" para "estudo + execução").

Também identificado, por busca de e-mails enviados (não é e-mail recebido, mas relevante para o acompanhamento da disciplina): em 2026-11-17 (17:57 BRT) o próprio Yan enviou e-mail a Luis Antonio de Souza Junior perguntando os horários em que ele estaria na sala nos dias seguintes, para tirar dúvidas para a P2. **Nenhuma resposta do professor chegou até esta coleta (2026-11-22)** — a P2 ocorreu em 19/11/2026, três dias após o e-mail, sem confirmação de que o Yan conseguiu tirar as dúvidas antes da prova.

Busca por remetente (classroom.google.com) confirmou que não há mais e-mails de Luis Antonio de Souza Junior entre 2026-11-17 e 2026-11-21, nem qualquer e-mail com nota ou feedback da P2 (realizada em 19/11) até esta coleta.

> [!question] Em aberto (2026-11-22): nenhum e-mail com o resultado ou feedback da P2 (realizada em 19/11/2026) chegou até a coleta desta rotina.

<!-- fonte: Gmail educacional, e-mail de Luis Antonio de Souza Junior no Google Sala de Aula ("Novo material: \"Exercícios - Sistemas de Arquivos\""), postado em 2026-11-16 12:58 BRT; e-mail enviado pelo próprio Yan ("Horários para tirar dúvidas"), 2026-11-17 17:57 BRT, sem resposta até 2026-11-22; coletados com atraso em 2026-11-22 -->

## Atualização (2026-11-24)

Um e-mail novo de Luis Antonio de Souza Junior nas últimas 24h: novo material "Aula 25 - Extra - Virtualização e Docker" no Google Sala de Aula (postado em 2026-11-23 12:09 BRT). O e-mail traz apenas o título, sem conteúdo detalhado. Classificado como material de estudo; adicionado a Tarefas > Estudo e ao Mapa de aulas como Aula 25 (aula extra, numerada pelo próprio professor). Continua sem resposta o e-mail enviado pelo Yan em 2026-11-17 perguntando horários para tirar dúvidas antes da P2 (ver Atualização 2026-11-22); e nenhum e-mail com nota/feedback da P2 (realizada em 19/11) chegou até esta coleta.

<!-- fonte: Gmail educacional, e-mail de Luis Antonio de Souza Junior no Google Sala de Aula ("Novo material: \"Aula 25 - Extra - Virtualização e Docker\""), postado em 2026-11-23 12:09 BRT (15:10 UTC), coletado em 2026-11-24 -->
