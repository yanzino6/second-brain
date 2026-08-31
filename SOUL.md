---
type: system
tags: [valores, principios]
atualizado: 2026-08-31
---

# SOUL.md — O que o trabalho dele demonstra

> Estes princípios não foram declarados numa entrevista — foram **extraídos da obra**, em seis projetos independentes. Cada um tem prova. Se algum estiver errado, corrija: é descrição, não aspiração.

## 1. Projetar contra o modo de falha, não contra o caminho feliz
A assinatura mais consistente. Em quatro clientes diferentes ele chegou nos mesmos primitivos sem ninguém mandar:

- **Idempotência antes de todo envio** — cadência que dispara duas vezes queima o lead
- **Jitter aleatório** entre toques — cadência com intervalo fixo tem assinatura de robô
- **Cadência como máquina de estado persistida**, nunca corrente de `Wait` — sobrevive a restart
- **Validar o canal antes de gastar** — número inválido é detectado, não descoberto pelo erro
- **Cancelar follow-up quando a pessoa responde** — sem isso o sistema cobra quem já respondeu
- **Guardrail é feature** — o que o agente *não* pode fazer merece tanto desenho quanto o que ele faz

Nos projetos acadêmicos, o mesmo instinto: **split agrupado por paciente** nos dois, evitando o vazamento que infla métrica em imagem médica.

## 2. Disciplina de evidência
Na revisão da [[Ebramed — Isabela, do diagnóstico à migração|Ebramed]], a metodologia foi declarada **antes** dos achados: `[PROVADO]` = log de execução real, HTTP medido ou SQL; `[ANÁLISE]` = leitura estática, plausível, não reproduzida.

Sem essa separação, achado sério e palpite ficam no mesmo nível. **É a coisa mais rara do material inteiro.**

## 3. Reportar o que falhou
No [[PAD-UFES-20 — Classificação de Lesões de Pele com Classe Sintética|PAD-UFES-20]], o relatório traz SCC com F1 **0,21** e registra que MEL tem **N=7** no teste — número que não sustenta conclusão. Não escondeu na média.

Na Ebramed, classificou os próprios achados por severidade, incluindo os que apontavam para trabalho dele.

**Corolário:** número frágil é apresentado como frágil. Contar o que não funcionou aumenta a credibilidade do que funcionou.

## 4. Não propagar defeito conhecido
Encontrada a causa-raiz na Ebramed (identidade derivada de um campo inexistente, em três nós duplicados), a trilha nova nasceu com a identidade em **um** nó só, lendo o campo certo. O bug não foi carregado adiante, e a duplicação que o permitia foi eliminada por desenho.

## 5. Restrição de domínio é requisito de arquitetura
Publicidade médica é regulada pelo CFM — então o prompt da Isabela proíbe promessa de resultado, comparação com concorrente, urgência falsa e afirmação sobre RQE. Risco jurídico do cliente tratado como requisito de sistema, não como item de backlog.

## 6. Ingestão sem sanitização é dívida que rende juros
Do Company Brain: **base ruim não é neutra — ela envenena o contexto.** Conteúdo desatualizado piora o agente em vez de deixá-lo igual. Exige rotina de sanitização, não só de ingestão. E escopo vem antes de estrutura.

> Este vault obedece à própria regra: coleta pode ser automática, **entrada é curada**.
