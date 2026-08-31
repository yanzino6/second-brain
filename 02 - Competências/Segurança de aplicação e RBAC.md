---
type: competencia
nivel: forte
tags: [competencia, seguranca, rbac, postgres]
atualizado: 2026-08-31
---

# Segurança de aplicação e RBAC

> Permissão aplicada na camada do banco, com o frontend como espelho declarado — não como autoridade.

## Provas
- **SmartSide CRM** — subsistema completo: **61 arquivos, +11.685 linhas**.
- **10 migrations** aplicando permissão em **RLS**, não na aplicação.
- Função `has_perm(user, org, permission)` como **fonte única de verdade**; 10 edge functions reescritas para respeitá-la.
- **5.434 linhas** de teste de RLS.
- `src/lib/permissions.ts` documenta a defesa em profundidade com o modo de falha nomeado: *"it is a mirror, not an authority: hiding a button is not enforcement."*
- Identificou **RLS desabilitado** em 8 tabelas na Ebramed e 7 na Knewin, e segredos em texto puro em nós de produção.

## Lacuna
Um projeto só. Não há evidência de autenticação (OAuth, JWT emissão), criptografia, nem revisão de segurança formal fora do contexto de RLS.

## Como contar
"Construí o sistema de permissão por função do CRM: 10 migrations de RLS, uma função SQL como fonte de verdade e 5.434 linhas de teste. O frontend espelha a regra, mas quem decide é o banco."
