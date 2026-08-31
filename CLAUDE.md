# CLAUDE.md — Convenções do vault

Vault pessoal do [[USER|Yan Simmer]]. Leia [[USER]], [[SOUL]] e [[IDENTITY]] antes de escrever qualquer coisa.

## Estrutura
| Pasta | Conteúdo |
|---|---|
| `00 - Inbox/` | Entrada bruta, ainda não processada |
| `01 - Projetos/` | Um projeto ou solução por nota — a fonte densa |
| `02 - Competências/` | Uma competência por nota: provas linkadas + lacuna |
| `03 - Ideias/` | Ideia com status e data |
| `04 - Sessões/` | Log automático de sessão (hook), destilado depois |

**Código não mora no vault.** A nota registra e aponta para o caminho no disco.

## Regras de escrita
- **pt-BR**, prosa direta. Preserve o vocabulário dele.
- **Frontmatter YAML** em toda nota: `type`, `tags`, data.
- **Wikilink é obrigatório.** Nota sem link é nota morta no Obsidian.
- **Número, não adjetivo.** "985 contatos, R$ 315" em vez de "campanha grande".
- **Lacuna explícita, nunca suposição.** Se não sabe, escreve `> [!question] Em aberto: ...`. Preencher com o plausível é a pior falha possível aqui.
- **Nunca sobrescreva** nota existente: acrescente seção ou ajuste o trecho.
- **Procedência** no fim do que foi acrescentado: `<!-- fonte: ..., AAAA-MM-DD -->`.

## Regra dos resultados — obrigatória
**Definida pelo Yan em 31/08/2026.**

Ao registrar qualquer projeto, **sempre analise o resultado**. Não é opcional e não é seção decorativa.

1. **Tem resultado?** Traga o número, com a fonte e a data da coleta.
2. **Não tem?** **Entreviste-o**: como mediu ou como mediria, e com que métrica.
3. **Avalie a métrica.** Ela mede o que promete? Tem baseline? Tem N suficiente? Contra que benchmark?
4. **Ajude a melhorar.** Aponte a métrica melhor quando a escolhida for fraca.

Projeto registrado sem resultado é meio projeto. Ele vira prova de que a pessoa constrói, não de que a coisa funcionou — e é resultado que ganha entrevista.

Fonte primária de métricas: `~/Documents/metricas-de-projetos-smarts-ai/`, uma pasta por cliente.

## Regra das ideias
Quando o trabalho atual encostar em algo de `03 - Ideias/`, **traga de volta sem ele pedir** — com a data de captura e o motivo da relevância. Ideia parada não é ideia morta; é ideia esperando contexto.

## Ao registrar competência
Toda competência aponta para **evidência linkada**, nunca para adjetivo. Competência declarada sem prova no vault nasce com a lacuna marcada — o buraco é informação tão útil quanto o acervo.
