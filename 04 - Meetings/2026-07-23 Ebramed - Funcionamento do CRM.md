---
type: meeting
date: 2026-07-23
tags: [reuniao, ebramed, crm, ia, onboarding]
attendees: ["[[José Lucas Ribeiro]]", "[[Yan Simmer]]", "[[Yara]]", "[[Elizane Andrade]]"]
project: "[[Ebramed - CRM IA (Isabela)]]"
company: "[[Ebramed]]"
source: "[[Transcrição Reunião - Ebramed]]"
recording: https://fathom.video/share/STxMhF4V1Q8Jsx9QcHpjUrMuiPsJMcdm
---

# 2026-07-23 Ebramed — Funcionamento do CRM (Isabela)

> Apresentação do CRM da smartside.ai para a Ebramed e alinhamento da operação do agente comercial **Isabela**. Ausente mas central: **[[Marcos]]** (definiu o funil; várias decisões dependem dele).

**Participantes:** [[José Lucas Ribeiro]], [[Yan Simmer]] (smartside.ai) · [[Yara]] (Coord. Comercial), [[Elizane Andrade]] (Ensino) (Ebramed)

---

## 1. Decisões

- **Funil espelha 100% o da Ebramed** (definido pelo [[Marcos]]): Recepção → Qualificação → Preço Apresentado → Produto de Entrada Convertido → Ganho.
- **Supervisão na fase inicial fica com a [[Yara]].** Vendedores não terão acesso ao CRM nesta fase; todos os leads trabalhados pela Isabela ficam sob o usuário coordenador para supervisão. Motivo: sem handoff/integração com o CRM interno da Ebramed por ora.
- **Gatilhos de handoff** (movem para etapa Handoff + notificação): pedido de transferência humana, cobrança, negociação de preço/parcelamento fora da tabela, pedido de recomendação de saúde/RQE, qualquer promessa, irritação extrema do cliente, alucinação da IA. Base: documento do [[Marcos]].
- **Separar Comercial e Ensino** em números distintos + campo personalizado "tipo de contato" (aluno vs. lead). Decidido por [[Elizane Andrade]] (alinhado c/ Marcos). Motivo: aluno ignora comunicação de ensino por excesso de abordagem comercial → prejudica retenção.
- **Dois agentes de IA:** **Isabela** (comercial, puramente comercial) e **Isadora** (ensino, script já desenvolvido). "Batizado" por [[Elizane Andrade]] e [[Yara]].
- **Regra "Produto de Entrada Convertido"** cobre apenas produtos de entrada (MD Play/Dplay, Masterclass, Mentoria, aulas) — **não** pós-graduação. Pós-graduação convertida = **Ganho**. Diferenciação (mentoria/matrícula → Ganho) a ser implementada pela smartside.
- **Boas práticas de disparo:** até **100 mensagens por número/dia**; subir listas em doses pequenas. Motivo: números usam API não oficial → risco alto de banimento pela Meta.
- **Ao assumir a conversa pelo CRM, a Isabela é pausada** automaticamente.
- **Grupo de WhatsApp permanece o canal principal** de comunicação smartside ↔ Ebramed.

### Pendentes de confirmação (com Marcos)
- **Regra "Preço Apresentado":** interpretação da [[Yara]] é que **qualquer** preço apresentado (pós, mentoria médica/acadêmica/carreira, MD Play) move para essa etapa — a confirmar com [[Marcos]].
- **1 número em API Oficial** entre os ~5 (pergunta trazida do [[Marcos]]): impacto de limite diário, templates e janela de 24h a avaliar antes de decidir.

## 2. Compromissos

**smartside.ai ([[José Lucas Ribeiro]] / [[Yan Simmer]])**
- [ ] Adicionar Yara, Elizane e Marcos aos grupos de notificação (handoff / Isabela / Rando).
- [ ] Criar campo personalizado "tipo de contato" (aluno/lead) e destacar o número do Ensino.
- [ ] Diferenciar mentoria/matrícula → mover direto para **Ganho**.
- [ ] Fazer a reativação dos números e conduzir sessão de testes com os 4 números.
- [ ] Investigar estratégia **híbrida** (API oficial p/ templates + API não oficial p/ atendimento) — em fase teórica, não é imediato.
- [ ] **Go Live: segunda 27/07, no mais tardar terça 28/07** (após reconexão + testes).

**Ebramed ([[Yara]])**
- [ ] Ativar/manter os números em WhatsApp Business conectados (dispositivos dedicados).
- [ ] Alinhar com [[Marcos]]: 1 número em API Oficial + aparelho dedicado por número.
- [ ] Confirmar a regra "qualquer preço apresentado" com [[Marcos]].
- [ ] Levar ao [[Marcos]] a visão de custo da nova precificação da Meta e a estratégia híbrida.
- [ ] Confirmar lista de números e o número de handoff (27 98127-3289).
- [ ] Definir número dedicado do Ensino e a proporção Comercial×Ensino (peso 70-30 / 60-40 / 50-50).
- [ ] Seguir testando; considerar trazer alguém de confiança para apoiar a supervisão.

**Ebramed ([[Elizane Andrade]])**
- [ ] Passar o número dedicado do Ensino.
- [ ] Confirmar script da Isadora (já desenvolvido).

## 3. Preferências (como trabalhar/comunicar)

- **Canal principal:** grupo de WhatsApp; marcar José, Yan ou Cássio para ajustes na base de conhecimento.
- **Ebramed** quer supervisão próxima e detalhada na fase inicial (Yara acompanhando conversa a conversa).
- **[[Yara]]** valida decisões com [[Marcos]] antes de "bater o martelo".
- **Ensino** quer abordagem/1ª mensagem distinta da comercial.
- **smartside** recomenda uma pessoa dedicada e diligente por projeto — padrão dos projetos de maior sucesso.
- Importar contatos em doses controladas.

## 4. Insights-chave

- **Metáfora do "estagiário":** a IA é autônoma 24x7, mas rende como um estagiário — faz o que se pede, mas precisa de orientação humana. Projetos de sucesso têm alguém dando atenção real.
- **Mudança de precificação da Meta:** passará a cobrar por todas as mensagens enviadas; janela de **72h** apenas para leads vindos de anúncios click-to-WhatsApp. Ebramed tem **ciclo de venda ~50 dias** → "72h não dá nem pro cheiro" → custo alto.
- **Estratégia híbrida = oportunidade de produto** (ativo interno reutilizável): API oficial (templates utility/marketing, janela 72h) para campanhas + API não oficial (mais barata) para atendimento. Yara: *"se vocês conseguirem fazer isso, vão ganhar muito dinheiro."*
- **Risco técnico:** API não oficial pode ser banida pela Meta com facilidade ("dois palitos"); números caíram por falta de aparelho dedicado mantendo a sessão.
- **Insight de retenção:** separar Comercial/Ensino existe porque o excesso de abordagem comercial faz o aluno ignorar comunicações de ensino.
- **Telefone é identificador único** no CRM → reimportar a mesma lista sobrescreve/atualiza contatos.

---

## Ações de higiene do vault
- Transcrição-fonte permanece em `00 - Inbox` ([[Transcrição Reunião - Ebramed]]) — sugerir mover para `07 - Archive` após processada (aguardando OK; nunca movo sem permissão).
