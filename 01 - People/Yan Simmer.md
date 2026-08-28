---
type: person
tags: [pessoa, smartside, equipe, dev]
company: "[[smartside.ai]]"
role: Desenvolvedor
links: ["[[smartside.ai]]", "[[Ebramed - CRM IA (Isabela)]]", "[[Knewin - Nina (Agente IA de Qualificação)]]", "[[AEVO - BDR IA Brasil]]", "[[José Lucas Ribeiro]]", "[[smartside.ai - Company Brain (Segundo Cérebro)]]", "[[smartside.ai - Workspace de Desenvolvimento (Harness)]]"]
github: yanzino6
---

# Yan Simmer

> Aparece como "Ian"/"Iazê"/"Arian" nas transcrições (erro de transcrição). Também "Ian Zino" / "Ian Zino 6" — é o **nick de GitHub e de jogos** (`yanzino6`), usado desde criança, não um erro de transcrição.

- **Empresa:** [[smartside.ai]] — desenvolvedor / **Engenheiro de IA** (título usado no kickoff da [[AEVO]]).
- **Iniciativas internas:** autor da proposta do segundo cérebro / [[smartside.ai - Company Brain (Segundo Cérebro)|Company Brain]] (jul/2026).

## Compromissos

### [[Ebramed - CRM IA (Isabela)]] — jul/2026
- [ ] Criar campo personalizado "tipo de contato" (aluno/lead) e destacar o número do Ensino — [[2026-07-23 Ebramed - Funcionamento do CRM]]
- [ ] Diferenciar mentoria/matrícula → mover direto para Ganho
- [x] ~~Reativar números + sessão de testes (c/ [[José Lucas Ribeiro]])~~ → **superado em 18/08**: arquitetura de múltiplos números descartada
- [x] ~~Investigar estratégia híbrida (API oficial + API não oficial)~~ → **superado em 18/08**: operação passa a ser 100% API Oficial

### [[Ebramed - CRM IA (Isabela)]] — ago/2026
> Itens abertos nas sessões de 18 e 19/08. Vários são **defeitos do CRM**, não features novas.
- [ ] Corrigir a **exportação de contatos** (botão não ativa) e habilitar exportação por etapa do funil e filtros — [[2026-08-19 Ebramed - Treinamento de Campanhas (Marketing)]]
- [ ] Fazer o campo `lista` subir como **tag** (múltiplas por contato), senão a métrica por campanha quebra — [[2026-08-19 Ebramed - Treinamento de Campanhas (Marketing)]]
- [ ] Rever o formato de "Listas" para suportar campos personalizados na importação — [[2026-08-19 Ebramed - Treinamento de Campanhas (Marketing)]]
- [ ] Configurar a Isabela para preencher especialidade/tipo/e-mail quando vierem em branco — [[2026-08-19 Ebramed - Treinamento de Campanhas (Marketing)]]
- [ ] Ajustar o campo `especialidade` para lista fechada (hoje é texto livre e quebra audiências) — [[2026-08-19 Ebramed - Treinamento de Campanhas (Marketing)]]
- [ ] Remover as origens que não são API Oficial da lista de campanhas — [[2026-08-19 Ebramed - Treinamento de Campanhas (Marketing)]]
- [ ] Avaliar busca por texto dentro das conversas — [[2026-08-19 Ebramed - Treinamento de Campanhas (Marketing)]]
- [ ] Criar o campo personalizado `fonte` + preenchimento automático pela mensagem de origem — [[2026-08-18 Ebramed - Abordagem Ativa e Rastreamento de Campanhas]]
- [ ] Criar os campos `respondeu` e `quando respondeu` — [[2026-08-18 Ebramed - Abordagem Ativa e Rastreamento de Campanhas]]
- [ ] Adicionar filtro por etapa do funil na exportação de contatos — [[2026-08-18 Ebramed - Abordagem Ativa e Rastreamento de Campanhas]]
- [ ] Configurar valor padrão de especialidade quando o campo vier em branco — [[2026-08-18 Ebramed - Abordagem Ativa e Rastreamento de Campanhas]]
- [ ] Ajustar o mecanismo de campanhas removendo a lógica de múltiplos números — [[2026-08-18 Ebramed - Abordagem Ativa e Rastreamento de Campanhas]]

### [[Knewin - Nina (Agente IA de Qualificação)]]
- [ ] Ajustar CRM smartside: tags/marcos de cada ação da Nina, responsável correto, marcar agendamento, campo HubSpot Contact ID — [[2026-07-03 Knewin - Ativação Nina]]
- [ ] Desenvolver abordagem ativa (leads parados) e agendamento automático (V1)

### [[AEVO - BDR IA Brasil]]
- **Papel:** execução da produção dos agentes de IA (LDR, Lead Scorer, BDR).
- **Obrigação de processo — [[AEVO - Processo de Sandbox (BDR AI)]]:** nenhuma mudança vai direto para produção.
  - [ ] Alinhar cada mudança com [[Victor Hugo]] na reunião semanal de sexta, documentada antes do desenvolvimento
  - [ ] Implementar em ambiente isolado (leads fictícios ou perfis internos), nunca apontando para perfil real
  - [ ] Executar os 3 cenários obrigatórios (duplicidade · contaminação · mensagem errada) e enviar o log a Victor
  - [ ] Monitorar logs ativamente nas **2 primeiras horas** pós-ativação; qualquer anomalia = pausa imediata
  - [ ] Concluir a migração para **datatables do n8n** (elimina dependência do Google Sheets) — em andamento desde fev/2026

### [[smartside.ai - Company Brain (Segundo Cérebro)]] — interno
- [ ] Definir escopo e casos de uso do Company Brain com [[Arthur Tosi]] e [[Pedro]]; só depois estruturar a página no Notion — [[2026-07-30 smartside.ai - Company Brain (Segundo Cérebro)]]

### [[smartside.ai - Workspace de Desenvolvimento (Harness)]] — interno
- [ ] Clonar o repositório do [[Matheus Simões]], rodar o setup do Claude na raiz e testar o fluxo — [[2026-07-30 smartside.ai - Company Brain (Segundo Cérebro)]]
- [x] Enviar o usuário do GitHub para o [[Matheus Simões]] — [[2026-07-30 smartside.ai - Company Brain (Segundo Cérebro)]]

## Reuniões
- [[2026-08-19 Ebramed - Treinamento de Campanhas (Marketing)]]
- [[2026-08-18 Ebramed - Abordagem Ativa e Rastreamento de Campanhas]]
- [[2026-07-30 smartside.ai - Company Brain (Segundo Cérebro)]]
- [[2026-07-23 Ebramed - Funcionamento do CRM]]
- [[2026-07-03 Knewin - Ativação Nina]]
- [[2025-12-04 AEVO - Kickoff BDR IA]]
