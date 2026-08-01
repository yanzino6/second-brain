# Rotina agendada: Processar Inbox — retomada

> Estado em **2026-07-29**: a rotina **NÃO existe**. Foi configurada e aprovada pelo Yan,
> mas a criação falhou por falta de conexão do GitHub na claude.ai. Toda a config está
> abaixo, pronta para reenvio — não é preciso reentrevistar nada.

## O que travou

Duas tentativas de `RemoteTrigger action:"create"` retornaram:

```
HTTP 401 — authentication_error
"Connect your GitHub account before saving a routine that uses a GitHub repository."
```

Nada foi criado (nenhuma rotina parcial no ar). O repo em si está OK: `git ls-remote`
respondeu `refs/heads/main` = `b8b460d`, então o problema é a conexão do lado da claude.ai,
não o repositório.

São **dois passos distintos**, e é comum ter feito só o segundo:

1. **Conectar a conta GitHub à claude.ai** (OAuth) — é o que o 401 reclama.
   https://claude.ai/settings/profile ou https://claude.ai/code/onboarding?magic=github-app-setup
2. **Instalar o Claude GitHub App no repositório** — permissão é por repo.

Se o repo estiver numa organização (não na conta pessoal `yanzino6`), pode exigir
aprovação de um admin da org.

## Ressalva importante: o repo é provisório

O Yan avisou que `yanzino6/second-brain` é **provisório** e será substituído pelo repo real.

- Se o repo real estiver próximo: **não crie no provisório**, crie direto no real.
- Se já existir rotina apontando para o provisório: não recrie — basta um
  `RemoteTrigger action:"update"` trocando
  `job_config.ccr.session_context.sources[0].git_repository.url`.
- No repo novo, repetir os passos 1 e 2 acima: a permissão do GitHub App **não** é herdada.
- Se a migração renomear pastas (`00 - Inbox`, `01 - People`, …), o prompt abaixo precisa
  ser ajustado junto com a URL.

## Config aprovada

| Campo | Valor |
|---|---|
| `name` | `Processar Inbox do Segundo Cérebro` |
| `cron_expression` | `0 2 * * 2-6` |
| Horário pretendido | 23h America/Sao_Paulo, **seg–sex** |
| `environment_id` | `env_018tKoZc76kyqjpPE8wghSSv` (Default, criado em 2026-07-29) |
| `model` | `claude-sonnet-5` |
| `allowed_tools` | Bash, Read, Write, Edit, Glob, Grep |
| `mcp_connections` | nenhum — a tarefa é toda dentro do repo |
| Entrega | PR em branch `inbox/AAAA-MM-DD`, sem merge |

**Sobre o cron — não "corrija" para `1-5`.** 23h em America/Sao_Paulo (UTC-3) = **02:00 UTC
do dia seguinte**. Portanto seg–sex local = ter–sáb em UTC → `2-6`. Usar `0 2 * * 1-5`
perderia a noite de sexta e criaria uma rodada indevida na noite de domingo.

## Body para recriar

Gere um **UUID v4 minúsculo novo** para `events[].data.uuid`.

```json
{
  "name": "Processar Inbox do Segundo Cérebro",
  "cron_expression": "0 2 * * 2-6",
  "enabled": true,
  "job_config": {
    "ccr": {
      "environment_id": "env_018tKoZc76kyqjpPE8wghSSv",
      "session_context": {
        "model": "claude-sonnet-5",
        "sources": [
          {"git_repository": {"url": "https://github.com/yanzino6/second-brain"}}
        ],
        "allowed_tools": ["Bash", "Read", "Write", "Edit", "Glob", "Grep"]
      },
      "events": [
        {"data": {
          "uuid": "<uuid v4 novo>",
          "session_id": "",
          "type": "user",
          "parent_tool_use_id": null,
          "message": {"role": "user", "content": "<PROMPT — ver seção abaixo>"}
        }}
      ]
    }
  }
}
```

## Prompt do agente (texto exato aprovado)

```text
Você está processando o vault Obsidian "second brain" da SmartSide, num clone limpo do repo. Leia `CLAUDE.md`, `IDENTITY.md`, `SOUL.md` e `USER.md` na raiz antes de qualquer coisa — as convenções deles mandam.

Tarefa: processar todo material bruto em `00 - Inbox/` e arquivá-lo nas pastas canônicas.

Se `00 - Inbox/` estiver vazio (ignorando `.DS_Store` e afins), pare imediatamente, não crie branch nem PR, e reporte "Inbox vazio, nada a processar".

Para cada arquivo no Inbox:

1. Leia e determine o que é: transcrição de reunião, nota sobre pessoa, projeto, empresa, conhecimento ou processo.
2. **Procure antes de criar.** Use Glob/Grep em `01 - People/`, `02 - Projects/`, `03 - Companies/`, `05 - Knowledge/`, `08 - Processes/` para achar a nota canônica que já existe. Uma nota por pessoa, projeto e empresa — nunca duplique. Se existir, acrescente ou ajuste o trecho específico, preservando tudo que já estava lá.
3. Conhecimento específico de cliente/projeto vai em `05 - Knowledge/<Cliente>/`. Só o que é genuinamente reutilizável e agnóstico de cliente fica na raiz de `05 - Knowledge/`. Nunca misture clientes na mesma nota ou pasta.
4. Transcrição de reunião → nota em `04 - Meetings/` nomeada `YYYY-MM-DD Título`, ligada a participantes e projeto; a transcrição bruta vai para `07 - Archive/`.
5. Frontmatter YAML em toda nota (`type`, `tags`, `links`), seguindo o padrão das notas existentes. Ligue com `[[wikilinks]]` nos dois sentidos. Escreva em pt-BR, conciso, bullets.
6. Atualize o MOC correspondente em `06 - MOCs/` quando adicionar nó relevante.
7. Marque procedência: `<!-- fonte: 00 - Inbox/<arquivo>, processado AAAA-MM-DD -->`.

Nunca delete nota: material superado vai para `07 - Archive/`. Após processar, mova o arquivo original do Inbox para `07 - Archive/` com `git mv` — não o deixe no Inbox.

Se algo não couber em nenhuma pasta com confiança, **deixe no Inbox** e explique o porquê no PR — não force classificação. Não invente fatos: lacuna vira `> [!question] Em aberto: ...`.

Se o processamento tocar mais de 20 arquivos, faça só o que é claramente seguro, deixe o resto no Inbox e sinalize no PR.

Ao terminar: crie branch `inbox/AAAA-MM-DD`, commite e abra PR com `gh`. O corpo do PR deve listar arquivos criados, arquivos editados (com o que mudou em cada), o que ficou no Inbox e por quê, e lacunas em aberto. Não faça merge.
```

## Como retomar

1. `ToolSearch select:RemoteTrigger` para carregar a ferramenta.
2. `RemoteTrigger action:"list"` — confirme se a rotina já existe (pode ter sido criada
   depois de 2026-07-29, ou pela UI web). Se existir, **não duplique**: use `update`.
3. Pergunte ao Yan qual repo usar — o provisório ou o real definitivo.
4. Se não existir: `RemoteTrigger action:"create"` com o body acima (UUID novo, URL confirmada).
5. Se voltar 401 de novo, o GitHub ainda não está conectado — não fique reenviando;
   aponte os dois passos da seção "O que travou".
6. Ao criar com sucesso, entregue o link: `https://claude.ai/code/routines/{ID}`.

Rotinas **não podem ser deletadas** via API — para remover, https://claude.ai/code/routines

## Alternativa sem agendamento

Enquanto a rotina não existir, o mesmo processamento pode ser feito na sessão local, sob
demanda, seguindo o prompt acima. Em 2026-07-29 o Inbox tinha 1 arquivo pendente:
`00 - Inbox/Nina.md`.
