---
type: person
tags: [pessoa, smartside, equipe, dev]
company: "[[smartside.ai]]"
role: Desenvolvedor
links: ["[[smartside.ai]]", "[[Ebramed - CRM IA (Isabela)]]", "[[Knewin - Nina (Agente IA de Qualificação)]]", "[[AEVO - BDR IA Brasil]]", "[[José Lucas Ribeiro]]"]
---

# Yan Simmer

> Aparece como "Ian"/"Iazê"/"Arian" nas transcrições (erro de transcrição).

- **Empresa:** [[smartside.ai]] — desenvolvedor / **Engenheiro de IA** (título usado no kickoff da [[AEVO]]).

## Compromissos

### [[Ebramed - CRM IA (Isabela)]]
- [ ] Criar campo personalizado "tipo de contato" (aluno/lead) e destacar o número do Ensino — [[2026-07-23 Ebramed - Funcionamento do CRM]]
- [ ] Diferenciar mentoria/matrícula → mover direto para Ganho
- [ ] Reativar números + sessão de testes (c/ [[José Lucas Ribeiro]])
- [ ] Investigar estratégia híbrida (API oficial + API não oficial)

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

## Reuniões
- [[2026-07-23 Ebramed - Funcionamento do CRM]]
- [[2026-07-03 Knewin - Ativação Nina]]
- [[2025-12-04 AEVO - Kickoff BDR IA]]
