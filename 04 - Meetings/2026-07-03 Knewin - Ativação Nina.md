---
type: meeting
date: 2026-07-03
tags: [reuniao, knewin, nina, ia, enablement, go-live]
attendees: ["[[José Lucas Ribeiro]]", "[[Vanessa Ribeiro]]", "[[Yan Simmer]]", "[[Yukio Kohatsu]]", "[[Aline Claro]]", "[[Gabriela Arruda]]", "[[Amanda Botini]]"]
project: "[[Knewin - Nina (Agente IA de Qualificação)]]"
company: "[[Knewin]]"
source: "[[Transcrição - Ativação Nina]]"
recording: https://fathom.video/share/xzvCDKhLz3AgZAXszFdsTsHZzBaUJjsL
---

# 2026-07-03 Knewin — Ativação / Enablement Nina

> Enablement do agente de IA **Nina** (SDR de qualificação) para a Knewin: manual passo a passo, fluxo no HubSpot + CRM smartside, regras de transbordo. Go Live assistido em curso.

**Participantes:** [[José Lucas Ribeiro]], [[Vanessa Ribeiro]], [[Yan Simmer]] (smartside.ai) · [[Yukio Kohatsu]], [[Aline Claro]] (SDR), [[Gabriela Arruda]] (regras de negócio), [[Amanda Botini]] (dados/sistemas) (Knewin)

---

## 1. Decisões

- **Nina é SDR de qualificação, não vendedora.** Qualifica via WhatsApp, não negocia preço nem fecha venda. Design smartside, alinhado c/ Knewin. Motivo: escopo da 1ª fase (outros clientes têm agente que fecha; a Nina não).
- **Método de qualificação = SPIN Selling.** Por: smartside. Motivo: método validado, padrão em pré-vendas, cobre Situação/Problema/Implicação/Necessidade.
- **CRM smartside espelha o pipeline do HubSpot** com sync bidirecional das movimentações; HubSpot é a fonte. Campo "processo de qualificação = smartside" preenchido na conversão do formulário.
- **Timeout de 5 min** (estava documentado errado como 14 min): se o lead converte no form mas não manda mensagem no WhatsApp em 5 min → vai para vendedor via "fluxo de distribuição 02" (pré-vendas). Interino — será substituído pela abordagem ativa da Nina.
- **Cadência de follow-up:** 3 toques nas primeiras 24h (15 min, ~3h, ~16h), respeitando a janela gratuita de 24h da Meta. Sem resposta após o 3º → negócio "sem resposta"/perdido no HubSpot e no CRM smartside. Fim de semana **não** habilitado por padrão (preferência da Knewin a decidir).
- **Adicionar 4º follow-up** (~23h59 / ~24h) — decidido a partir do feedback da [[Aline Claro]] (leads respondem no dia seguinte). Pendente de confirmação da [[Gabriela Arruda]]. Motivo: reduzir perdidos.
- **Horário de operação = 09h18** (não 08h — time não ativo às 8h), por [[Aline Claro]]. Fora do horário, Nina informa a janela de retorno.
- **Gatilhos de transbordo → SDR ([[Aline Claro]]):** lead pede humano; irritação/insatisfação (análise de sentimento); Nina não entende o lead após várias tentativas (loop); descobre no meio da conversa que já é cliente (sem lookup no HubSpot); lead insiste em preço.
- **Transbordo é operado DENTRO do CRM smartside**, não pelo número pessoal da Aline — para preservar rastreamento e memória da Nina. Por [[José Lucas Ribeiro]].
- **Etapa "transbordo humano"** (a.k.a. "precisa de suporte") existe só no CRM smartside; posse passa à Aline, o negócio mantém a etapa atual no HubSpot.
- **Piloto = APENAS 1 landing page (Dino Demanda)** passa pela Nina inicialmente; expandir depois quando estável. Expansão a decidir por [[Gabriela Arruda]].
- **Adicionar campo "HubSpot Contact ID"** (não obrigatório) no CRM smartside p/ export/sync — pedido de [[Amanda Botini]].
- **Guardrails da Nina:** nunca fala preço, nunca promete resultado, não acessa dados fora do HubSpot, resiste a prompt injection, sem linguagem agressiva, segue tom de voz/marca.
- **Dois links de agendamento por segmento:** SMB e Enterprise.

### Em desenvolvimento (decidido, ainda não entregue)
- **Abordagem ativa da Nina** p/ lead parado >5 min (envia template WhatsApp e assume o processo em vez de cair p/ pré-vendas) — alvo: próxima semana (~06–10/07).
- **Agendamento automático** (V1): Nina consulta agendas (SMB/Enterprise), oferece 2 slots mais próximos, agenda e passa ao vendedor. Motivo: reduzir fricção, aumentar conversão.
- **Pitch Dino Demanda como 2º passo do avulso:** antes do checkout, Nina argumenta o "plano demanda" (meio-termo: prazo maior, custo menor que avulso). Por [[Gabriela Arruda]] + [[Aline Claro]]. Motivo: alto volume de avulso; encodar as regras de negócio na Nina (senão não resolve o problema de volume).
- **Não** colocar a Nina no fluxo de compra/self-checkout do Dino (processo muda mês que vem: cartão→PayPal→Sankhya) — mantém o redirect ao checkout + o pitch de demanda.

## 2. Compromissos

**smartside.ai ([[José Lucas Ribeiro]] / [[Yan Simmer]] / [[Vanessa Ribeiro]])**
- [ ] Corrigir docs/fluxos: timeout 14→5 min, texto "pré-vendedor", qualificado→vendedor (não SDR), horário 09h18, +4º follow-up.
- [ ] Desenvolver abordagem ativa da Nina p/ leads parados — alvo próxima semana.
- [ ] Desenvolver agendamento automático (V1).
- [ ] Instruir a Nina a fazer o pitch Dino Demanda ao avulso (montar pitch/KB c/ regras da Knewin).
- [ ] Analisar viabilidade de integração com a **Elefant** (tem API? WhatsApp→HubSpot) e reportar à [[Amanda Botini]].
- [ ] Enviar por e-mail a gravação + manual da Nina p/ Yukio, Amanda, Aline, Gabriela, Vanessa.
- [ ] Ajustar CRM smartside: tags/marcos de cada ação da Nina, responsável correto, marcar ação de agendamento, campo HubSpot Contact ID.
- [ ] Perguntar à **Avante** (no grupo) sobre tráfego na LP do Dino Demanda (nada converteu ainda) — [[José Lucas Ribeiro]].
- [ ] Criar quebra-gelos p/ reativação >24h, se a Knewin solicitar.
- [ ] Disponibilizar painel de monitoramento + check-points quinzenais c/ indicadores (c/ [[Gabriela Arruda]]).

**Knewin**
- [ ] [[Aline Claro]]: testar a Nina pelo formulário do Dino Demanda (e-mail pessoal), colar perguntas reais de leads, mandar insights/scripts p/ José Lucas.
- [ ] [[Aline Claro]]: reportar bugs encontrados.
- [ ] [[Vanessa Ribeiro]]: enviar o link da LP p/ Aline; testar a Nina hoje nos seus cenários.
- [ ] [[Amanda Botini]]: checar tráfego da LP c/ marketing/Avante (via grupo).
- [ ] [[Gabriela Arruda]]: decidir follow-up de fim de semana; confirmar 4º follow-up; decidir quando expandir além da 1 LP.
- [ ] Knewin: enviar atualizações de produto p/ smartside atualizar a KB da Nina.

## 3. Preferências (como trabalhar/comunicar)

- **Canal principal:** grupo de WhatsApp de suporte; feedback em tempo real; reportar bugs a qualquer momento; check-points quinzenais c/ [[Gabriela Arruda]] sobre indicadores.
- **[[Gabriela Arruda]]:** explicação clara/didática; forte ênfase em relevância de marca e tom humano/natural (evitar linguajar robótico "de guia").
- **Atendimento humano sempre dentro do CRM smartside** (não número pessoal) — rastreamento + memória.
- **[[Amanda Botini]]:** governança de dados — quer IDs/campos p/ export/análise futura; quer dados de WhatsApp da qualificação puxados p/ campos do HubSpot.
- **[[Aline Claro]]:** prefere que a Nina tente convencer (avulso→demanda) em vez de só mandar link; valoriza toque humano p/ comprador decidido; quer follow-up extra no dia seguinte.
- **smartside:** "criatividade é o limite"; transparência de que todo Go Live exige ajuste.
- Testar com e-mail pessoal (não @knewin) p/ a Nina tratar como lead real.

## 4. Insights-chave

- **Go Live assistido:** smartside acompanha 100% no lançamento; todo cliente exige calibragem pós-lançamento — expectativa alinhada + loop de feedback em tempo real.
- **Tensão humano×IA em compra de alta intenção:** [[Aline Claro]] — comprador decidido pode desconfiar de IA; converter avulso→demanda exige calor humano e concessões comerciais. Contraframe da [[Gabriela Arruda]]: isso são **regras de negócio** codificáveis na KB da Nina, senão o deploy não resolve o volume de avulso. Questão estratégica: quanto do julgamento humano codificar vs. transbordar.
- **Viés consultivo da Nina** já observado (teste da [[Vanessa Ribeiro]]): sugere pautas, analisa setor, dá segurança ao lead — força reutilizável.
- **Elefant:** ferramenta que leva conversas de WhatsApp p/ o HubSpot (p/ vendedores); oportunidade de capturar também dados da fase de qualificação. Ressalva do José: p/ os dados da Nina não precisa intermediário — atualiza o HubSpot direto.
- **Janela de 24h da Meta** governa a cadência; além dela exige templates pagos / quebra-gelos.
- **Checkout em transição** (cartão→PayPal→Sankhya, futuro self-checkout) → cautela de arquitetura: não automatizar processo prestes a mudar.
- **Estrutura de planos:** avulso → plano demanda (meio-termo, não recorrente, prazo maior/mais barato) → recorrente/fidelidade. Demanda é a nova opção p/ escoar volume de avulso.
- **Soluções que a Nina indica:** New Monitoring, CC Clipping, CC Mailing, Dino (Demanda + avulso).
- **Resistência a prompt injection** embutida.
- Piloto de-riscado: começar com 1 LP p/ evitar IA não calibrada atingindo todos os fluxos.

---

## Ações de higiene do vault
- Transcrição-fonte permanece em `00 - Inbox` ([[Transcrição - Ativação Nina]]) — sugerir mover p/ `07 - Archive` após processada (aguardando OK; nunca movo sem permissão).
