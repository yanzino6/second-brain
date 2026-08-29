---
type: knowledge
tags: [track-record, portfolio, ia, agentes, n8n, crm, whatsapp, carreira]
scope: pessoal
updated: 2026-08-28
links: ["[[Harness Engineering - Fábrica de Software]]", "[[Stack de Desenvolvimento com IA - Ferramentas e Workflow]]"]
---

# O que eu construí

> Registro pessoal de track record técnico, consolidado em 28/08/2026 a partir do vault de trabalho antes de ele ser zerado.
> Clientes ficam anonimizados por setor — o que interessa aqui é a engenharia, não a conta.

---

## Agente SDR + CRM próprio para clínica de saúde/ensino
**Papel:** engenheiro de IA, construção e operação · **Estado ao sair do registro:** em produção

Dois agentes de WhatsApp sobre um CRM próprio: um comercial e um de ensino, com base de conhecimento treinada em material do cliente e handoff para humano em casos sensíveis (saúde, negociação, cobrança, irritação, alucinação detectada).

**Decisão de arquitetura que virou aprendizado:** a v1 usava 4–5 números em **API não oficial** com escoamento de volume entre eles (~25% cada, teto de 100 msg/número/dia) para diluir risco de banimento. Não se sustentou — os números foram bloqueados na prática. A v2 migrou para **um único número na API Oficial da Meta**, atendendo receptivo e ativo, com o segundo número só como backup.

- Risco de banimento vai a zero, mas entra custo por mensagem e aprovação de template pela Meta.
- Template de marketing custa; template de utilidade é gratuito mas aprova mais devagar.
- Todo o mecanismo de distribuição entre números foi jogado fora junto — complexidade construída contra um problema que a plataforma oficial já resolvia.

**Armadilhas de modelagem que custaram caro:**
- Variável obrigatória vazia = mensagem **não enviada, em silêncio**. Sem validação prévia da base, a campanha simplesmente não chega e não avisa.
- Campo de categorização como **texto livre** quebra qualquer segmentação depois. Tinha que ser lista fechada desde o início.
- Campo de origem sobrescrito a cada importação em vez de acumular como tag → impossível medir por campanha.

**A lição mais cara:** a primeira campanha real (985 contatos, ~R$ 315) disparou **antes** da instrumentação de rastreamento existir. Os dois campos que o cliente mais queria medir — origem do lead e se respondeu — ainda não estavam no ar. Gastou-se dinheiro para gerar dado que não dava para ler.

> [!tip] Regra que levo daqui
> Instrumentação antes de volume. Se não dá para medir, não dispara.

---

## Agente de qualificação de leads para empresa de monitoramento de mídia
**Papel:** engenheiro de IA · **Estado ao sair do registro:** go-live assistido (piloto em 1 landing page)

SDR de IA que recebe lead de formulário, qualifica por **SPIN** em conversa natural de WhatsApp (áudio, imagem, documento, com memória) e faz triagem contra o CRM do cliente antes de responder qualquer coisa.

**Arquitetura:**
- Consulta o CRM por e-mail/telefone na entrada: já é cliente? tem vendedor vinculado? entrou há menos de 90 dias? A resposta muda todo o roteamento.
- Saídas: qualificado → agendamento · ticket avulso → checkout + pitch · sem fit → perdido · sem resposta → follow-up · caso sensível → transbordo humano.
- Sync bidirecional entre o CRM do cliente e o CRM próprio.

**Cadência que funcionou:** 3 toques em 24h (15 min · ~3h · ~16h), fim de semana desligado por padrão. Lead que converte e não manda mensagem em 5 min cai para vendedor humano.

**Guardrails explícitos no agente:** não fala preço, não promete resultado, não usa dado fora do CRM, resiste a prompt injection, mantém tom de marca. Transbordo obrigatório quando o lead pede humano, se irrita, entra em loop de não-entendimento, se revela cliente no meio da conversa, ou insiste em preço.

> [!tip] Regra que levo daqui
> O que o agente **não** pode fazer merece tanto design quanto o que ele faz. Guardrail é feature.

---

## BDR de IA para SaaS de inovação corporativa
**Papel:** execução da produção dos agentes (LDR, Lead Scorer, BDR) · **Estado:** descontinuado

Prospecção outbound automatizada em LinkedIn e e-mail, com meta de sair de ~400 para 2.000 leads qualificados/mês sem escalar custo na mesma proporção. Personalização por lead (perfil, interações prévias, sinais de engajamento) no lugar de disparo genérico.

**O processo de sandbox foi o ativo real.** Nenhuma mudança ia direto para produção:
1. Alinhamento e documentação **antes** de desenvolver, na reunião semanal.
2. Implementação em ambiente isolado — leads fictícios ou perfis internos, **nunca** apontando para perfil real.
3. Três cenários obrigatórios antes de liberar: **duplicidade · contaminação de base · mensagem errada**, com log enviado ao responsável.
4. Monitoramento ativo de log nas **2 primeiras horas** pós-ativação. Qualquer anomalia = pausa imediata.

**Migração técnica:** saída de Google Sheets para **datatables do n8n**, eliminando a dependência de planilha como banco de dados de operação.

> [!tip] Regra que levo daqui
> Agente que fala com pessoa real em nome de alguém precisa de sandbox com cenários de falha nomeados. "Testei e funcionou" não é teste.

---

## Segundo cérebro / Company Brain
**Papel:** autor da proposta · **Estado:** parado em definição de escopo

Proposta nascida do vault Obsidian que eu já mantinha por conta própria. Virou discussão de arquitetura de conhecimento consumível por agente.

**Decisões de arquitetura a que chegamos (valem para qualquer segundo cérebro):**
- **Markdown com hierarquia e link nativo** basta como repositório. Não precisa de plataforma dedicada.
- **Acesso do agente = MCP + index bem escrito.** Um arquivo de índice descrevendo a estrutura resolve consulta direcionada. **Sem Vector Store, sem embeddings.**
- **A camada compartilhada não é viva.** O agente não edita a base comum; ele se atualiza puxando o repositório. A camada pessoal fica por cima, fora do versionamento.
- **As regras de como a IA gerencia a base moram na própria base**, versionadas — senão cada sessão faz do seu jeito.
- **Curadoria humana é obrigatória.** Alguém valida o que entra e faz varredura retroativa do que ficou obsoleto.

**O risco central, que se confirmou:** base ruim não é neutra — ela **envenena o contexto**. Conteúdo desatualizado piora o agente em vez de deixá-lo igual. Exige rotina de sanitização, não só de ingestão.

**Segundo risco:** sem recorte de escopo, vira depósito. A pergunta "para que serve" precede a de "como estrutura".

> [!tip] Regra que levo daqui
> Ingestão sem sanitização é dívida que rende juros. E escopo vem antes de estrutura — foi exatamente o que travou esse projeto.

---

## Workspace de desenvolvimento com agentes (harness)
**Papel:** avaliação e teste · Ver [[Harness Engineering - Fábrica de Software]] e [[Stack de Desenvolvimento com IA - Ferramentas e Workflow]]

Repositório único como ponto de partida de qualquer sessão de desenvolvimento: `CLAUDE.md` raiz com bootstrap, regras de roteamento e regras de ouro; cada projeto com git e perfil próprios; biblioteca de skills encadeáveis (entrevista → PRD → issues → waves de build → review).

**Fluxo que já rodava:** planning → árvore de dependências → worktrees separadas → waves de build em paralelo → teste e review automáticos → só sobe para humano se falhar 3× no loop.

> [!tip] Regra que levo daqui
> A ferramenta local não tem system prompt oculto — o workflow está em arquivo no disco. O caminho é **se injetar dentro do harness** (hooks, skills, MCP, memória), não construir ferramenta nova por fora.

---

## Stack que operei
`n8n` (automação e datatables) · `Supabase` · WhatsApp Business API (oficial e não oficial) · HubSpot · CRM próprio · Claude Code + MCP · Obsidian · Git/GitHub

---

<!-- fonte: consolidado do vault de trabalho anterior, 2026-08-28, antes da reinicialização pessoal. Detalhe integral recuperável em git tag `backup-vault-empresa`. -->
