---
type: meeting
date: 2026-08-18
tags: [reuniao, ebramed, crm, ia, campanhas, whatsapp, api-oficial]
attendees: ["[[José Lucas Ribeiro]]", "[[Yan Simmer]]", "[[Marcos]]", "[[Yara]]", "[[Tainara Lameira]]", "[[Adriano Ribondi]]"]
project: "[[Ebramed - CRM IA (Isabela)]]"
company: "[[Ebramed]]"
source: "[[Reunião Ebramed]]"
recording: https://fathom.video/share/xywqfTxAN6yjxtcGm8fhwP2yDjNtGTmW
---

# 2026-08-18 Ebramed — Abordagem Ativa e Rastreamento de Campanhas

> Sessão de 54 min para colocar a **Isabela** em uso ativo (reativação de base) e responder às dúvidas de rastreamento do time de marketing. Entrada de duas pessoas novas no projeto: [[Tainara Lameira]] e [[Adriano Ribondi]].

**Participantes:** [[José Lucas Ribeiro]], [[Yan Simmer]] (smartside.ai) · [[Marcos]] (Marcus Vinicius Tatagiba), [[Yara]] (Yara Lacerda), [[Tainara Lameira]], [[Adriano Ribondi]] ([[Ebramed]] / Grupo Educar Mais)

---

## 1. Decisões

- **Abandonar a arquitetura de múltiplos números; operar com um único número na API Oficial.** Por: [[Marcos]] + [[José Lucas Ribeiro]]. Motivo: os ~5 números existiam apenas porque não havia API Oficial; na prática não se viabilizou (bloqueios da Meta). Com a API Oficial o risco de banimento é praticamente zero e o mesmo número atende receptivo **e** ativo. Marcos: *"Qual foi o motivo de ter mais outros números? [...] Exatamente, não faz sentido."*
  - **Consequência:** a seção **Marketing/Campanhas** do CRM (desenhada para um número só) passa a ser o caminho oficial de disparo.
  - O segundo número permanece cadastrado apenas como **backup**, sem atrapalhar a operação.
- **Rastreamento de origem por mensagem de entrada + campo personalizado**, não por UTM. Por: [[Yan Simmer]], atendendo [[Adriano Ribondi]] e [[Tainara Lameira]]. Motivo: não há UTM no fluxo WhatsApp; cada fonte (Google, Meta, e-mail, disparo em massa) usa uma mensagem de abertura distinta, e o CRM preenche o campo `fonte` automaticamente ao reconhecê-la.
- **A Ebramed não edita as etapas do funil por conta própria.** Por: [[José Lucas Ribeiro]]. Motivo: as etapas estão acopladas ao mecanismo da Isabela — alterar quebra as atualizações automáticas de etapa. Pedidos de mudança passam pela smartside.
- **Templates: a Ebramed pode criar novos livremente; não deve editar os já publicados.** Por: [[Yan Simmer]], a pedido de [[Marcos]]. Motivo: os templates ativos usam duas variáveis obrigatórias (nome + especialidade); remover ou acrescentar variável faz o disparo falhar. Templates novos exigem aviso à smartside para entrarem em atividade.
- **Importação de listas usa "mesclar"**, não "sobrescrever". Por: [[José Lucas Ribeiro]] + [[Yan Simmer]]. Motivo: preserva o histórico do contato e permite medir performance por campanha; mesclar unifica tags e preenche só os campos vazios.
- **Integração com o RD (Conversas/CRM) está fora do escopo contratado.** Por: [[Yara]] + [[José Lucas Ribeiro]]. Motivo: o escopo inicial contemplava apenas o CRM da smartside. Tecnicamente possível, mas não contratado — a Ebramed segue usando as duas plataformas.
- **Sessão dedicada de treinamento de marketing/campanhas agendada para 19/08 às 10h** (quarta), a pedido de [[Marcos]] — a operação de campanhas não estava na pauta do dia.

### Em desenvolvimento (decidido, ainda não entregue)
- Filtro por **etapa do funil** na exportação de contatos.
- Campo personalizado `fonte` + preenchimento automático pela mensagem de entrada.
- Campos personalizados `respondeu` e `quando respondeu`.
- Valor padrão de especialidade para leads sem especialidade preenchida.

### Pendente de confirmação (Ebramed define internamente)
- Qual será o **valor padrão de especialidade** ([[Marcos]] sugeriu "pós-graduação médica" / "especialização médica").
- **Limite diário de disparos** e **janela de horário** das abordagens.

## 2. Compromissos

**smartside.ai — [[Yan Simmer]]**
- [ ] Criar o campo personalizado `fonte` e configurar o preenchimento automático a partir da mensagem de origem (depende das mensagens da Ebramed)
- [ ] Adicionar filtro por etapa do funil na exportação de contatos
- [ ] Criar os campos personalizados `respondeu` e `quando respondeu`
- [ ] Configurar valor padrão de especialidade quando o campo vier em branco
- [ ] Ajustar o mecanismo de campanhas removendo a lógica de distribuição entre múltiplos números

**smartside.ai — [[José Lucas Ribeiro]]**
- [ ] Incluir [[Tainara Lameira]] e [[Adriano Ribondi]] no grupo de WhatsApp do projeto
- [ ] Enviar convite de calendário do treinamento de **19/08 às 10h** para Yan, Tainara, Adriano, Marcus e Yara

**Ebramed — [[Tainara Lameira]] / [[Adriano Ribondi]]**
- [ ] Definir e enviar ao [[Yan Simmer]] as **mensagens de abertura específicas por fonte** (Google, Meta, e-mail, disparo em massa)
- [ ] Definir e enviar o **valor padrão de especialidade** para leads sem especialidade
- [ ] Subir os links de materiais (e-books etc.) na pasta do Drive da IA — a Isabela envia **link**, não arquivo
- [ ] Preparar base de teste (Excel), template e horário e passar ao [[Yan Simmer]] para o primeiro disparo real

**Ebramed — [[Yara]]**
- [ ] Enviar o e-mail ao [[José Lucas Ribeiro]] para receber o convite do treinamento

## 3. Preferências (como trabalhar/comunicar)

- **Canal principal:** grupo de WhatsApp do projeto. Materiais e links no Drive compartilhado.
- **Convenção do [[Marcos]]:** nomear a pasta/caixa do Drive com a data de atualização (*"caixa atualizada em 18 do 8"*) para que a smartside saiba qual está vigente.
- **[[Marcos]] quer autonomia operacional** — não depender da smartside a cada disparo: *"para não ficar toda hora te enchendo o saco"*. A Ebramed já opera RD Conversas e Speed Marketing e quer a mesma dinâmica.
- **[[Marcos]] prioriza validar demanda antes de investir em engenharia:** *"não adianta ficar com um monte de programação e de tag [...] 500 integrações, mil trabalhos e sem venda."*
- Ebramed pede acesso às **gravações** das reuniões.
- Reunião curta: temas não urgentes vão para sessão dedicada em vez de estender a chamada.

## 4. Insights-chave

- **Reversão estratégica do desenho de julho.** A arquitetura de múltiplos números — núcleo do que foi construído em julho e da sessão de [[2026-07-23 Ebramed - Funcionamento do CRM]] — foi descartada. A adoção da API Oficial tornou obsoleto o mecanismo de distribuição desenvolvido pelo [[Yan Simmer]]. Há retrabalho a assumir.
- **Custo por mensagem = R$ 0,32** (template de marketing na API Oficial). O limitador de volume deixou de ser risco de banimento e passou a ser orçamento — [[Marcos]]: *"O limite é o bolso."*
- **Duas variáveis obrigatórias nos templates (nome + especialidade).** Se qualquer uma vier vazia, a mensagem **não é enviada**. Risco direto de falha em massa numa base sem especialidade preenchida.
- **A dor real da Ebramed é mensuração, não automação.** [[Tainara Lameira]]: *"Isso é o que a gente mais precisa"* — saber quem respondeu e por qual campanha. [[Adriano Ribondi]]: rastrear origem Google vs. Meta. O CRM ainda não entrega nenhum dos dois.
- **Ineficiência de marketing como oportunidade dimensionada.** [[Marcos]]: *"se 50% não responde, minha eficiência é só de 50%"* — a base de não respondentes é o público mais valioso para a Isabela reativar.
- **[[Marcos]] valida a qualidade da Isabela:** *"ela está muito boa, até com argumentação [...] ela já passou do teste"*.
- **Relacionamento forte:** Marcos posiciona a Ebramed como *"um dos melhores clientes"* da smartside e reconhece o esforço da equipe — *"eu trabalho dez vezes mais sem eles"*.
- **A Isabela só conhece contextos novos (ex.: e-books) depois que o link entra na base de conhecimento via Drive** — e envia link, nunca arquivo (peso).
- **Contexto do projeto dado pelo [[Marcos]]:** o projeto começou em julho e priorizou fazer a IA funcionar antes de integrações e gestão de dados — *"se eu fosse fazer tudo, a gente não ia conseguir fazer nada"*. Agora entra a fase de campanhas, integrações e dados.

---

## Notas relacionadas
- Reunião seguinte: [[2026-08-19 Ebramed - Treinamento de Campanhas (Marketing)]]
- Reunião anterior: [[2026-07-23 Ebramed - Funcionamento do CRM]]
- Projeto: [[Ebramed - CRM IA (Isabela)]]
