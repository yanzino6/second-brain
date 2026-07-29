---
tags: [biancogres, riscos, gaps, conhecimento, seguranca, lgpd]
aliases: [Riscos, Gaps, Conhecimento, Segurança]
up: "[[00 - MOC Biancogres]]"
---

# Conhecimento, Riscos e Gaps

Nota de "sistema imunológico" do projeto: o que pode dar errado, o que ainda não sabemos, e onde o conhecimento crítico está frágil.

## 🧠 Conhecimento tácito concentrado (maior risco operacional)
- **DR-007 / DR-051** — conhecimento crítico mora em **pessoas-chave sem documentação**:
  - [[Lohayne Rosa]] — **única do PCP** que sabe o processo de programação de produção.
  - [[Mayara Pimentel]] — **única** que sabe os critérios de avaliação de sell-out e premiação; **sai em licença ago–set/2026**. Isto cria uma **janela dura** para a [[PoC - Sell-Out]].
- **DR-014** — conhecimento anotado em **cadernos e cabeça** ([[Wendell Regadas]], [[Alexandre Luz]]).
- **"Priscila IA" (DR-062)** — pessoa vira ponto único de falha para apresentações.
> Implicação: qualquer PoC que capture regras dessas pessoas tem **valor duplo** (eficiência + de-risk da dependência).

## 🔒 Segurança e compliance
- **Postura da TI** ([[Wanisay Thompson]]): assumidamente **"paranoico com segurança"**. Citações: *"Já tive parado, estatizado, porque eu não queria fazer nada que era inseguro"* · *"Não dá para andar na IA hoje, numa empresa do nível da Biancogres, sem correr risco de segurança."*
- **LGPD:** Biancogres = **Controladora**, Smartside = **Operadora**. Multa por quebra de confidencialidade: **R$ 100.000/evento**. Código sempre em repositório privado. Ver [[Contrato e Condições Comerciais]].
- **Risco LGPD concreto (DR-054):** ~8 celulares corporativos/pessoais no SAC sem WhatsApp Business API nem auditoria → a [[PoC - SAC Atendimento]] tem ganho colateral de compliance ao consolidar.

## ⚙️ Restrições operacionais da Biancogres
- **Cadência de infra:** provisionamentos precisam ser pedidos com **1–2 semanas de antecedência**. *"Pedir em cima da hora é sempre um problema."*
- **Presença física:** kick-off e atividades-chave presenciais em **Serra/ES**. *"Presencial gera confiança rápido."*
- **Anti-sobrecarga:** [[Wanisay Thompson]] **não quer abrir mais PoCs** até consolidar as atuais (medo de virar "pato que faz tudo e faz nada"). Já há várias frentes internas rodando (ver abaixo).

## 🧪 PoCs internas já rodando na Biancogres (frentes paralelas)
1. **T2C** — leitura de documentos SESMT (LTCAT) via NLP
2. **PowerOmni (PowerTuning)** — text-to-SQL sobre base Protheus
3. **Genexus** — gestão de APIs
4. **Cursor** — desenvolvimento acelerado (virou produção)
5. **n8n interno** — primeiros fluxos em teste
6. **Transcrição de reuniões** — em validação
7. **TeamField** — em avaliação vs Involves Stage (DR-008)

## ❓ Gaps abertos — a confirmar com o cliente
1. **Cloud provider institucional** (AWS/Azure/GCP/on-premise puro) — nunca mencionado
2. Existência de **tenant Azure** e política de **Azure OpenAI**
3. **LLM de produção** a ser adotado (IBM descartada) → decisão pendente da Smartside
4. **VPN / acessos externos** e método de conexão da equipe Smartside aos sistemas internos
5. **Topologia do servidor n8n** (specs, redundância, backup)
6. **Modelo de acesso aos dados do Protheus** (réplica / data lake / acesso direto)
7. **APIs disponíveis** no Fluid e demais sistemas comerciais
8. Política de **anonimização/mascaramento** de dados
9. **Ambientes** existentes (dev / homolog / prod)

## 🚩 Riscos de execução do projeto
- **Janela da Mayara** (licença) pressiona o cronograma da PoC de Sell-Out.
- **Viabilidade do Caminho A do SAC** depende de "onde mora o status da RPV" (sistema consultável vs e-mail/conversa).
- **Adoção cultural:** histórico de ferramenta que a TI subiu ao BI e o comercial **voltou ao Excel** (DR-010) — risco de a solução não ser adotada se não substituir o Excel de verdade.
- **Documentação/artefatos das PoCs vazios** no Drive na extração — risco de perda de rastreabilidade técnica.

## Ligações
[[Tech Stack]] · [[Mapa de Dores]] · [[Contrato e Condições Comerciais]] · [[Wanisay Thompson]] · [[Mayara Pimentel]] · [[Lohayne Rosa]]
