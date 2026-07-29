---
tags: [biancogres, poc, sell-out, agente-ia, g2]
aliases: [PoC Sell-Out, PoC G2, Agente Sell-Out]
up: "[[00 - MOC Biancogres]]"
grupo: G2 · Fluxo de Sell-Out
status: Em execução
---

# PoC — Sell-Out (G2)

Uma das **2 PoCs** entregues no projeto. Nasce do grupo [[Diagnóstico Comercial|G2 · Fluxo de Sell-Out]], a **maior densidade quantitativa** do diagnóstico (+7.000 h/ano em jogo). Frame: *"Primeiro organizar o sell-out, pois sem sell-out não há sell-in."*

## A dor (o que resolve)
O dado que mede a **venda real na ponta (PDV)** chega à fábrica em **formato livre** — Excel, PDF, foto, áudio, WhatsApp. A [[Mayara Pimentel]] gasta **~20 dias úteis/mês** decifrando isso à mão:
- **50 representantes × 3 marcas + rodapé** vêm misturados
- **PROCV manual** de cada SKU do cliente → SKU Biancogres
- Corrige **CPF inconsistente** que trava o upload (DR-049)
- A [[Erika Couto]] gasta **+8h toda sexta** na prévia semanal (DR-069)
- **Pessoa-chave única** — a Mayara **sai em licença em agosto/2026** ⚠️
Dores endereçadas: **DR-001, DR-049, DR-069** (+ contexto DR-010, DR-051).

## Conceito da solução — "normalizar o dado na entrada"
Traduzir o que chega em **qualquer formato** para um dado limpo, num **template Excel que a própria Mayara define**. Ela para de digitar/comparar e passa a **revisar**.

```
Arquivo bruto (Excel/PDF/foto/áudio)
      → IA extrai (modelo otimizado por tipo de arquivo)
      → De-para de SKU por cliente (N→1)
      → Template Excel da Mayara (campos editáveis)
```

### Detalhes técnicos importantes
- O **de-para não é 1:1**: vários códigos de cliente apontam para um mesmo SKU Biancogres (**N→1**), e cada cliente usa o seu.
- A **planilha que a Mayara já mantém** vira a base que **alimenta e treina** o modelo.
- **Otimização de custo:** a busca é **por cliente** — o modelo só olha os SKUs daquele cliente, não o banco inteiro.

### Escopo da PoC × Etapa 2
- **PoC:** normalizar tudo no template Excel da Mayara (campos editáveis). Já resolve a dor maior.
- **Etapa 2 (futuro):** fazer tudo dentro da própria ferramenta (sem Excel) + propor dashboard de sell-out.

## Perguntas de viabilidade (endereçadas à TI)
1. Podemos usar a planilha de de-para da Mayara para alimentar/treinar? Qual a cobertura por cliente?
2. Qual a facilidade de acessar a tabela de SKU do cliente e a da Biancogres? (viabiliza o de-para automático)
3. Distribuição real dos formatos recebidos (Excel vs foto vs PDF vs áudio)? Há amostra p/ calibrar?
4. Conseguimos uma **janela com a Mayara antes da licença** para capturar as regras com ela?
5. O projeto antigo de sell-out no Protheus expõe API? Em que estado está?

## Pessoas-chave
- Dona do processo: [[Mayara Pimentel]] (operação, sai em licença)
- Cobertura da licença / gestora: [[Raquel Rangel]]
- Prévia semanal: [[Erika Couto]]
- Contexto de canal: [[Fábio]], [[Gabriel Felipe Amorim]]

## Estrutura no Drive
Pasta `03 · PoCs em execução / 3.2 PoC G2 · Sell-Out`. Subpastas previstas: Documentação técnica, Fluxos n8n, Prompts e configurações, Testes e validações, Resultados e métricas, Gravações.
> ⚠️ As subpastas de documentação/resultados estavam **vazias** na extração — confirmar artefatos técnicos e métricas com o time.

## Ligações
[[Diagnóstico Comercial]] · [[Mapa de Dores]] · [[PoC - SAC Atendimento]] · [[Tech Stack]] · [[Mayara Pimentel]]
