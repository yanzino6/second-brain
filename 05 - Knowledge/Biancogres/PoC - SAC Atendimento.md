---
tags: [biancogres, poc, sac, atendimento, agente-ia, g3]
aliases: [PoC SAC, PoC G3, Agente Atendimento, PoC Atendimento]
up: "[[00 - MOC Biancogres]]"
grupo: G3 · Eficiência no Atendimento
status: Em execução
---

# PoC — SAC / Atendimento (G3)

Uma das **2 PoCs** do projeto. Nasce do grupo [[Diagnóstico Comercial|G3 · Eficiência no Atendimento]] — a frente com **menor fricção operacional** e o **sponsor mais convicto** do diagnóstico ([[Eduarda Ishiy]]).

## A dor (o que resolve)
O SAC atende em **8 canais que não conversam** e gasta a maior parte do tempo **respondendo o que já tem resposta**. Em paralelo, o **status de cada caso é invisível** para quem está na ponta.
- **1.200 atendimentos N1/mês** (725 e 722 cravados em jan/fev)
- **57% são determinísticos** (já têm resposta pronta)
- **~50% do volume** entra por um único canal: **Fale Conosco**
- **200–250 RPVs/mês** entram, com status invisível na ponta
Dores endereçadas: **DR-006, DR-052, DR-054, DR-055, DR-056**.

## Dois caminhos apresentados (decisão conjunta com a TI)

### 🅰️ Caminho A — Agente de status de RPV no Telegram
O representante (e o SAC) consulta o andamento de uma **RPV pelo Telegram** e recebe o status na hora — sem ligar 4–5x para a assistente.
- **Por que é forte:** reusa o **bot de estoque do Telegram** que a TI já mantém (menor superfície técnica); toca **dois públicos** (rep + SAC); endereça a principal queixa da pesquisa anual de representantes.
- **Magnitude:** ~10h por caso espinhoso de RPV ([[Fellipi Teixeira]] estima ~2h dele + 3–4h do assistente + horas da assistente SAC). 200–250 RPVs/mês cruzam **5 áreas**.
- **Pergunta que define a viabilidade:** o status da RPV passa por **CQPA, logística, financeiro, jurídico, indústria**. Se já está num sistema consultável (Bizagi/Protheus) → simples. Se parte mora em e-mail/conversa → vira projeto de processo.

### 🅱️ Caminho B — Núcleo de atendimento N1 (Fale Conosco)
Ponto único onde a IA resolve o **atendimento determinístico do Fale Conosco** (~50% do volume, sob controle da Biancogres).
```
1. Triagem   → lê o contato, identifica intenção, roteia
2. Resolução → responde o determinístico com base curada
3. Humano no loop → escala o que exige julgamento; cada resolução vira aprendizado
```
- Começa no Fale Conosco; WhatsApp/redes/Reclame Aqui entram na expansão.
- **Indicador:** taxa de resolução real do N1 determinístico. **Meta honesta de partida: 40–60%.**
- **Ganho colateral de compliance:** consolidar o WhatsApp tira os **~8 celulares pessoais** de circulação (endereça LGPD — DR-054).

### A × B lado a lado
| | Caminho A (RPV/Telegram) | Caminho B (Núcleo N1) |
|---|---|---|
| Tamanho | Menor, mais rápido | Maior, mais estrutural |
| Reuso | Alto (bot Telegram já existe) | Médio (integra ao Fale Conosco) |
| Valor | Quase certo, dois públicos | Ataca ~700 N1/mês determinísticos |
| Risco | Depende de onde mora o status | Curadoria de base + escopo |

## Perguntas de viabilidade (à TI)
- Onde mora o status da RPV hoje (sistema consultável ou e-mail/mesa)?
- O bot de estoque do Telegram pode ser estendido por nós, ou integramos por trás?
- Como o Fale Conosco funciona por trás? Dá p/ integrar direto?
- Estado do FAQ / base de conhecimento? Quem valida o conteúdo é a [[Eduarda Ishiy|Eduarda]]?
- Já existe conta **WhatsApp Business API** verificada? Quem é responsável?

## Pessoas-chave
- Sponsor / dona do processo: [[Eduarda Ishiy]] (Coord. SAC)
- Representante que sente a dor de RPV: [[Fellipi Teixeira]]
- Volume de RPV citado por: [[Jackson Junior]]

## Estrutura no Drive
Pasta `03 · PoCs em execução / 3.1 PoC G3 · SAC · Eficiência no Atendimento`. Subpastas previstas: Documentação técnica, Fluxos n8n, Prompts e configurações, Testes e validações, Resultados e métricas, Gravações.
> ⚠️ Subpastas de documentação/resultados **vazias** na extração — confirmar artefatos e métricas com o time.

## Ligações
[[Diagnóstico Comercial]] · [[Mapa de Dores]] · [[PoC - Sell-Out]] · [[Tech Stack]] · [[Eduarda Ishiy]]
