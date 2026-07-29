# Templates de gravação — entrevista de onboarding

Padrões derivados das notas já existentes no vault. Se uma nota existente do mesmo tipo
usar formato diferente, **siga a nota existente** — estes templates são fallback.

Regras que valem para todos:

- Frontmatter YAML sempre. `type` e `tags` obrigatórios; `links` com wikilinks entre aspas.
- Título `# Nome` igual ao nome do arquivo.
- Bullets diretos, pt-BR, vocabulário da pessoa preservado.
- Lacuna vira `> [!question] Em aberto: ...` — nunca suposição.
- Procedência ao final de cada seção acrescentada:
  `<!-- fonte: entrevista com [[Nome]], AAAA-MM-DD -->`
- Nunca sobrescrever arquivo existente: acrescentar seção ou ajustar o trecho específico.

---

## `01 - People/<Nome>.md`

```markdown
---
type: person
tags: [pessoa, smartside, equipe, <área>]
company: "[[smartside.ai]]"
role: <Cargo>
aliases: [<Apelido>, <como aparece nas ferramentas>]
links: ["[[smartside.ai]]", "[[<Projeto>]]", "[[<Empresa>]]"]
---

# <Nome>

- **Empresa:** [[smartside.ai]] — **<Cargo>**
- **Entrou em:** <mês/ano>
- **Objetivo na SmartSide:** <objetivo, com a camada de seis meses>

## Dia a dia
- <fluxo de ponta a ponta, operacional>
- **Semanal/mensal:** <trabalho de baixa frequência>

## Ferramentas
| Ferramenta | Para quê |
|---|---|
| <nome> | <uso> |

## Onde ficam as coisas
- <repos, boards, drives, dashboards>

## Projetos
- [[<Projeto>]] — <papel dela>

## Rituais e cadências
- **Reuniões:** <recorrência e propósito>
- **Entregas recorrentes:** <o quê, com que frequência>
- **Reporta-se a:** [[<Nome>]] · **Dependem dela:** [[<Nome>]]
- **Recorre a:** <assunto> → [[<Nome>]]

## Gargalos e dores
- <o que consome tempo e agrega pouco>
- <o que automatizaria hoje>
- <onde fica bloqueada>

## Métricas de sucesso
- **Critério dela:** <...>
- **Critério da empresa:** <...>
- <se divergem, registre as duas visões sem julgar>

## Notas relacionadas
[[smartside.ai]] · [[<Projeto>]] · [[Pessoas - Índice]]

<!-- fonte: entrevista com [[<Nome>]], AAAA-MM-DD -->
```

---

## `02 - Projects/<Projeto>.md`

Nome do arquivo segue o padrão do vault: `<Cliente> - <Projeto>` quando houver cliente.

```markdown
---
type: project
status: <estágio real, ex. "go-live assistido (piloto)">
tags: [projeto, <cliente>, <tema>]
company: "[[<Empresa>]]"
links: ["[[<Empresa>]]", "[[smartside.ai]]", "[[<Pessoa>]]"]
---

# <Cliente> — <Projeto>

> <uma frase: o que o projeto faz>

## Escopo
- <o que faz na prática>

## Tech stack
- **Linguagens/frameworks:** <...>
- **Integrações:** <...>
- **Infra / onde roda:** <...>

## Arquitetura
- **Entrada do dado:** <...>
- **Persistência:** <...>
- **Disparos:** <o que é síncrono, o que é agendado, o que dispara o quê>
- **Integrações externas:** <...>

## Dor do cliente
- <problema real resolvido; o que o cliente fazia antes>

## Decisões históricas
- **<decisão>** — por quê, o que foi tentado antes, que restrição moldou

## O que costuma quebrar
- **<falha>** — como se percebe → como se resolve (→ [[<Runbook>]])

## Quem mexe
- [[<Pessoa>]] — <parte que domina>

<!-- fonte: entrevista com [[<Nome>]], AAAA-MM-DD -->
```

---

## `03 - Companies/<Empresa>.md`

```markdown
---
type: company
tags: [empresa, cliente, <empresa>]
links: ["[[<Projeto>]]", "[[smartside.ai]]"]
---

# <Empresa>

- **Relação:** <cliente ativo / prospect / parceiro> da [[smartside.ai]]
- **Segmento:** <...>
- **Stack relevante:** <...>

## Pessoas
- [[<Nome>]] — <papel>

## Projetos
- [[<Projeto>]]

<!-- fonte: entrevista com [[<Nome>]], AAAA-MM-DD -->
```

---

## `08 - Processes/<Processo>.md`

Um processo por arquivo, repetível por quem nunca o executou.

```markdown
---
type: process
tags: [processo, <cliente ou área>, runbook]
owner: "[[<Nome>]]"
links: ["[[<Projeto>]]", "[[<Nome>]]"]
---

# <Processo>

> **Quando rodar:** <gatilho ou cadência>
> **Dono:** [[<Nome>]]

## Pré-requisitos
- <acessos, ferramentas — sem credenciais>

## Passos
1. <ação concreta: onde, que tela, que botão>
2. <...>

## Verificação
- <como saber que deu certo>

## Quando dá errado
| Sintoma | Causa provável | O que fazer |
|---|---|---|
| <...> | <...> | <...> |

## Armadilhas
- <o que parece funcionar mas não funciona>

<!-- fonte: entrevista com [[<Nome>]], AAAA-MM-DD -->
```

---

## `05 - Knowledge/<Cliente>/<Tema>.md`

Conhecimento de cliente/projeto vai em subpasta do cliente. Só o que é genuinamente
reutilizável e agnóstico de cliente fica na raiz de `05 - Knowledge`.

```markdown
---
type: knowledge
tags: [<cliente>, <tema>, referencia]
company: "[[<Empresa>]]"
links: ["[[<Empresa>]]", "[[00 - MOC <Cliente>]]"]
---

# <Cliente> — <Tema>

## <Seção>
| Termo | Significado |
|---|---|
| **<jargão>** | <significado, no vocabulário da pessoa> |

<!-- fonte: entrevista com [[<Nome>]], AAAA-MM-DD -->
```

---

## `06 - MOCs/` — edição

Não crie MOC novo na entrevista. Acrescente a linha no MOC existente, na seção certa:

```markdown
- [[<Nota nova>]] — <hook de uma linha>
```

`00 - MOC <Cliente>` para nós de um cliente; `Clientes MOC` só se um cliente novo
tiver surgido na entrevista.
