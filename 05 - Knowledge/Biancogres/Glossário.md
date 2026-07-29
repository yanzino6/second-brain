---
tags: [biancogres, glossario, referencia]
aliases: [Glossário, Termos, Siglas]
up: "[[00 - MOC Biancogres]]"
---

# Glossário — termos, sistemas e siglas

## Metodologia e projeto
- **PoC** — Prova de Conceito (o formato do contrato: 90 dias).
- **R.I.P.E.** — método de priorização de dores: **R**ecorrência, **I**mpacto, **P**rontidão, **E**sforço. Ver [[Diagnóstico Comercial]].
- **Black Belt** — colaborador interno capacitado como multiplicador de IA. Ver [[Programa Black Belts]].
- **DR-XXX** — identificador de uma dor no [[Mapa de Dores]] (DR-001 → DR-085).
- **G1 / G2 / G3** — os 3 grupos de oportunidade do diagnóstico (Pré-Visita / Sell-Out / Atendimento).

## Comercial e negócio
- **Sell-in** — venda da fábrica para o cliente (revenda/lojista). Já bem medido (dashboards).
- **Sell-out** — venda real na ponta (do lojista para o consumidor). Mal capturado → foco da [[PoC - Sell-Out]].
- **RPV** — solicitação/registro ligado a reclamação/reposição de material (aberto via Bizagi; passa por CQPA, logística, financeiro, jurídico, indústria).
- **ADV** — Administração de Vendas (~16 pessoas; 6 analistas citados).
- **PCP** — Planejamento e Controle de Produção.
- **GRO** — Gestão de Riscos e Oportunidades / Desenvolvimento Organizacional (uma das 5 áreas).
- **GMR** — indicador de resultado ("o fim") cobrado do marketing (vs "o meio").
- **PPR** — Programa de Participação nos Resultados (nota do comitê de Exibitécnica — DR-041).
- **Exibitécnica** — frente de arquitetura/showroom (projetos em loja); planilha mestra "monstro".
- **Consultor** — profissional na ponta que recebe premiação de sell-out (~150).
- **Representante** — vendedor externo (~125–150) que cobre clientes/lojas.
- **Canal Engenharia / Galeria / Home Centers / Revenda** — canais do comercial.
- **SKU** — código de produto (416 no portfólio); de-para N→1 entre SKU do cliente e SKU Biancogres.

## Sistemas (ver [[Tech Stack]])
- **TOTVS Protheus** — ERP principal (desde 1999).
- **Senior (Senha)** — sistema de RH.
- **Fluid** — compras/requisições.
- **Bizagi** — workflow / abertura de RPV.
- **Fênix / WMS / Ecosis** — sistemas complementares.
- **Power BI** — BI do comercial.
- **Involves Stage** — plataforma de gestão de trade/consultores (R$300 mil/ano — DR-008).
- **Monera** — plataforma de pagamento (premiação).
- **PowerOmni / PowerTuning** — text-to-SQL (PoC interna).
- **T2C** — leitura de documentos via LLM (PoC interna SESMT/LTCAT).
- **Genexus (GlobalSys)** — gestão de APIs.

## IA e automação
- **n8n** — plataforma de orquestração/automação (self-hosted community). Núcleo das PoCs.
- **Claude Code** — nos materiais aparece como **"Cloud Code"**; é o agente que constrói fluxos no n8n via linguagem natural.
- **MCP** — protocolo que conecta o Claude Code ao n8n ("clica, copia a URL, cola").
- **Cursor** — IDE com IA usada pelo time técnico.
- **Power Automate** — RPA em produção desde a pandemia.
- **LTCAT / SESMT** — documentação de saúde/segurança ocupacional (alvo do T2C).

## Empresas e parceiros
- **[[Empresa - Biancogres|Biancogres]]** — cliente (cerâmica, Serra/ES).
- **[[Empresa - Smartside|Smartside.ai]]** — fornecedor (São Paulo/SP).
- **Triple A.I** — plataforma/parceria associada à Smartside.
- **[[Ayko]]** — parceira de NOC/segurança/infra da Biancogres (configurou o n8n).
- **Fibrasa** — empresa do relacionamento (Renato indicou a Smartside; usa Fluid).
- **EMEG / Gilvan** — origem do primeiro contato (2025).

## Ligações
[[00 - MOC Biancogres]] · [[Tech Stack]] · [[Mapa de Dores]]
