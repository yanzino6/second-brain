---
type: knowledge
tags: [aevo, sandbox, processo, qualidade, deploy, seguranca, bdr, descontinuado]
company: "[[AEVO]]"
links: ["[[AEVO]]", "[[00 - MOC AEVO]]", "[[AEVO - BDR IA Internacional (ABM & GTM Europa)]]", "[[AEVO - BDR IA Brasil]]"]
---

> [!failure] Descontinuado
> A frente de BDR IA (Internacional + Brasil) foi encerrada — informado em 27/07/2026. Este processo só se aplica se/quando a operação de prospecção for retomada. Preservado como histórico.

# AEVO — Processo de Sandbox (BDR AI)

> `[Aevo Internacional] Processo_Sandbox_Smartside` — **v1.0, fevereiro/2026, Confidencial.**
> Processo **obrigatório** de validação e teste para toda e qualquer mudança técnica nos agentes de prospecção antes de ativação em produção (perfis reais de clientes).

## Por que existe (o incidente)
Mudanças técnicas implementadas **direto em produção** geraram:
- Erros de abordagem **reputacionalmente sensíveis**
- Mensagens enviadas para **leads errados**
- **Duplicidade** de disparos
- **Contaminação entre perfis**

> Este documento é a resposta institucional a um incidente real. Deve ser lido antes de qualquer mexida nos agentes AEVO.

## Escopo — aplica-se obrigatoriamente a
- Alterações de fluxo ou lógica de disparo
- Mudanças de prompt ou mensagens de abordagem
- Alterações de infraestrutura (migração de banco, integração etc.)
- Ativação de novos perfis de prospecção
- Reativação após pausa
- **Qualquer correção de bug** que afete comportamento de envio

## Camadas de segurança ativas
| Camada | O que faz | Status (fev/2026) |
|---|---|---|
| Verificação de duplicidade | Impede mensagem para o mesmo lead mais de uma vez | ✅ Implementado |
| Remoção de memória do agente | Elimina contaminação de dados entre perfis distintos | ✅ Implementado |
| Agente validador de conteúdo | Verifica nome, empresa e coerência da mensagem antes do disparo | ✅ Implementado |
| Migração para **datatables (n8n)** | Elimina dependência do Google Sheets | 🔄 Em andamento |

## Processo de deploy (5 etapas)
1. **Alinhamento** — [[Victor Hugo]] e [[Yan Simmer]] definem o que será implementado na reunião semanal (sexta) ou por e-mail. A mudança é documentada antes de qualquer desenvolvimento; prazo de ativação acordado.
2. **Desenvolvimento em ambiente controlado** — Yan implementa em ambiente isolado, que não aponta para perfil real do cliente. Leads fictícios ou perfis internos da smartside. **Nenhuma mudança vai direto para produção, sem exceções.**
3. **Bateria de testes obrigatórios** — os 3 cenários abaixo. Qualquer falha volta para desenvolvimento. Yan registra os resultados e envia o log para Victor.
4. **Go/No-Go com Victor** — validação do log, pode ser assíncrona. Reprovado = corrige e repete a bateria.
5. **Produção com janela de observação** — nas primeiras **2 horas** Yan monitora os logs ativamente. Qualquer anomalia = **pausa imediata**, nunca correção em produção. Após 2h sem incidentes, operação considerada estável.

## Bateria de testes — 3 cenários obrigatórios
| Cenário | O que testa | Camada ativada | Resultado esperado |
|---|---|---|---|
| **A — Duplicidade** | Envia sequência para o mesmo lead duas vezes | Verificação de duplicidade | 2ª tentativa bloqueada |
| **B — Contaminação** | Roda dois perfis distintos em sequência | Remoção de memória | Perfil 2 não carrega dados do perfil 1 |
| **C — Mensagem errada** | Injeta lead com nome diferente do contexto | Agente validador | Mensagem barrada e sinalizada |

> **Regra de aprovação:** todos os três precisam passar. **Não há aprovação parcial.**

## Diretrizes invioláveis
- Nenhuma mudança vai direto para produção.
- A decisão pode ser oficializada na sexta **ou** por e-mail — mas a **ativação nunca é no mesmo dia da decisão**.
- Os três cenários de teste são obrigatórios, não opcionais.
- Anomalia em produção = **pausa imediata**. Nunca corrigir em produção.
- O go/no-go da smartside é sempre validado por **Victor** antes da ativação e compartilhado com o time AEVO, tendo **[[Richa]] como ponte de contato principal**.

## Responsabilidades
| Responsável | Papel |
|---|---|
| [[Yan Simmer]] (Dev) | Desenvolvimento em testes, execução dos cenários, envio do log para Victor |
| [[Victor Hugo]] (CS) | Validação do log (go/no-go), alinhamento com o cliente, decisão de pausa |
| [[Richa]] (CEO) | Validador das implementações do lado AEVO |

## Manutenção do documento
**v1.0 — fevereiro/2026.** Deve ser revisado **a cada 90 dias ou após qualquer incidente em produção**.

> [!warning] Revisão vencida
> Considerando a data de hoje (27/07/2026), o documento está **~3 ciclos de revisão atrasado**. Nenhuma v1.1 ou posterior foi encontrada no Drive. Ver [[AEVO - Riscos, Gaps e Pendências]].
