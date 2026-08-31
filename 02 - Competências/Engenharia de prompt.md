---
type: competencia
nivel: forte
tags: [competencia, llm, prompt, agentes]
atualizado: 2026-08-31
---

# Engenharia de prompt

> Prompt como sistema com precedência, guardrail e mecanismo próprio — não como instrução em prosa.

## Provas
- [[Ebramed — Isabela, do diagnóstico à migração|Isabela]] — **294 linhas** em tags XML com precedência declarada: regras invioláveis > fluxo > pedido do lead.
- **Compliance do CFM embutido:** proíbe promessa de resultado, comparação com concorrente, urgência falsa e afirmação sobre RQE. Risco jurídico tratado como requisito de sistema.
- **Grounding anti-alucinação:** regra separada proibindo montar, adivinhar ou adaptar URL — o modo de falha real de LLM com link.
- **Orçamento de conteúdo:** mecanismo próprio que conta entregas de informação e força fechamento após a segunda.
- [[Knewin — Nina, SDR de IA com Triagem de CRM|Nina]] — **284 linhas**, com regras de formatação específicas do canal (negrito de WhatsApp é um asterisco, proibido travessão e markdown) e papel deliberadamente estreito.
- Structured Output Parser em 4 agentes de follow-up da Knewin e no scorer da [[Boavista — BDR de LinkedIn com Fila por Score|Boavista]].

## Lacuna
Sem evidência de **avaliação sistemática de prompt** (eval suite, A/B medido, regressão). Os prompts são bons, mas a melhoria é por julgamento, não por medição.

## Como contar
"Escrevi o prompt de um SDR médico com compliance do CFM na camada de prompt e um mecanismo de orçamento de conteúdo que força o fechamento. 294 linhas com precedência declarada entre regras."
