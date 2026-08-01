---
type: reference
tags: [smartside, site, posicionamento, marketing, cases]
source: https://www.smartside.ai
captured: 2026-07-30
links: ["[[smartside.ai]]", "[[AEVO]]"]
---

# smartside.ai — Site Oficial (scrape completo, 30/jul/2026)

> Cópia verbatim do conteúdo público de https://www.smartside.ai. Fonte de verdade para posicionamento externo, copy e números divulgados ao mercado.
> Stack do site: SPA React 19 + TanStack Router + Tailwind 4, pré-renderizado. Sem sitemap.xml.

## Arquitetura do site
- **Rotas:** `/` (home) · `/carreiras` · `/cases/$slug`
- **Idiomas:** PT (raiz) · EN (`/en/`, `/en/careers`) · ES (`/es/`, `/es/carreras`) — conteúdo integralmente traduzido nos 3.
- **Contato:** `contato@smartside.ai` · CTA global "Fale conosco" (modal com e-mail, telefone, necessidade)
- **Social listado no footer:** LinkedIn, Instagram (sem link ativo)
- **Copyright:** © 2026 smartside.ai, Inc.
- **Sem menção a Triple AI, SaaS ou micro aplicações em nenhuma página ou bundle** — o site é 100% Enterprise/serviço.

---

## Home

- **Title:** smartside.ai | IA que gera ROI para grandes empresas
- **Meta description:** A smartside.ai ajuda grandes empresas a gerar ROI com IA, da estratégia à produção.
- **H1 / Hero:** *IA que gera ROI para grandes empresas*
- **Sub-hero:** Confiada por organizações com operações reguladas e complexas
- **Logo wall:** Confiada por organizações reguladas e complexas — Wrist Boa Praça · Fibrasa · ArcelorMittal · AEVO · Unimed

### Manifesto
> Unimos consultoria, tecnologia e capacitação para destravar o potencial das organizações que movem o mundo real.

### Como fazemos? — "Um sistema único que se fortalece a cada nova implementação."
Três pilares:
1. **Roadmap de IA** — Consultores especialistas com metodologia e tecnologia proprietária de IA para identificar e priorizar as principais oportunidades de geração de ROI, sempre alinhadas ao planejamento estratégico da empresa.
2. **Implementação de ponta a ponta** — Desenvolvemos as soluções priorizadas de ponta a ponta, seguindo as suas diretrizes corporativas, e garantindo a manutenabilidade, observabilidade e mensuração de resultado no pós-deploy.
3. **Criamos capacidade** — Seu time capacitado para utilizar as principais ferramentas de mercado, as que desenvolvemos, e a desenvolver as próprias soluções que vão gerar ROI nos próximos anos.

### Setores — "Profundos em setores regulados e críticos"
| Setor | Tagline |
|---|---|
| Indústria | Precisão, escala e resultado no chão de fábrica |
| Saúde | Precisão, compliance e confiança |
| Logística | Velocidade, integração e margem |
| Tecnologia | Agentes em produção, do piloto à escala |

### Chancelas — "Selecionada para os principais programas de tecnologia e IA do mundo"
Google for Startups · AWS Startups · NVIDIA Inception Program · Microsoft for Startups Founders Hub · Perplexity Business Fellowship · **Shiva**

### Closer (time)
- **Título:** O time construindo o futuro da IA aplicada.
- **Desc:** Consultores, engenheiros e cientistas que já colocaram **mais de 300 soluções de IA em produção** — e capacitam o seu time para ir além.

### Footer
- Tagline: Transforme seu modelo de operação com a smartside.ai.
- Seção Cases: heading *"Mudamos o ponteiro dos negócios"* · sub *"Empresas líderes já usam IA aplicada com a smartside.ai para gerar ROI real. Veja os cases e os resultados que entregamos."*

---

## Cases (`/cases/<slug>`)

Estrutura fixa de cada case: breadcrumb → tag de categoria → H1 → dek → 3 métricas → O desafio / A solução / O resultado → quote → FAQ (3 perguntas) → CTA "Quero um diagnóstico como este". Todos publicados em **28/07/2026**.

| Slug | Cliente | Setor | Categoria | Resumo no carrossel |
|---|---|---|---|---|
| `wrist` | Wrist Boa Praça | Logística | Cotações e suprimentos | Cotação em minutos, não horas |
| `fibrasa` | Fibrasa | Indústria | Compras | IA que audita cada compra |
| `arcelormittal` | ArcelorMittal | Indústria | Atendimento e operação de campo | Inspeções de campo em tempo real |
| `aevo` | AEVO | Tecnologia | Transformação completa | 892% de ROI em 4 meses |
| `unimed` | Unimed | Saúde | Capacitação em IA | 200+ pessoas capacitadas em IA |

### 1. Wrist Boa Praça — `/cases/wrist`
- **H1:** Tempo de cotação cai 87% com agentes de IA no ERP Sankhya da Wrist Boa Praça
- **Métricas:** −87% no tempo de atualização de custos e cotação · 30+ fornecedores e sites consultados automaticamente · Milhões de itens (SKUs) com custo monitorado
- **Desafio:** Maior ship chandler da América Latina, abastece navios em todos os portos do Brasil. Cada cotação reúne centenas de itens, pesquisados manualmente em fornecedores, sites e no estoque interno. Quem responde mais rápido fecha a venda. Ciclo antes: ~2 horas por pedido.
- **Solução:** Agentes de IA integrados ao **ERP Sankhya** que cruzam estoque interno, tabelas de preço e sites de 30+ fornecedores. Mantêm o custo de milhões de itens atualizado automaticamente e montam a cotação consolidada para o navio.
- **Resultado:** Ciclo de horas para minutos (−87%). Margem de contribuição composta em tempo real. Equipe responde ao navio mais rápido que a concorrência.

### 2. Fibrasa — `/cases/fibrasa`
- **H1:** R$ 500 mil de retorno em 2 meses: como a Fibrasa passou a validar 100% das compras com IA
- **Métricas:** +R$ 500 mil de retorno nos 2 primeiros meses · 10+ critérios verificados em cada ordem de compra · 100% das requisições validadas antes da aprovação
- **Desafio:** Indústria de embalagens plásticas definia ponto de pedido manualmente → compras repetitivas e ineficientes. Exigência do cliente: a IA **não** podia ser ferramenta paralela; tinha que entrar como etapa obrigatória no fluxo que já existia no ERP, sem sistema novo para aprender.
- **Solução:** **Agente Avaliador de Compras** dentro do **ERP TOTVS Fluig**, monitorando todas as requisições. Antes de cada aprovação analisa contra 10+ critérios (preço médio histórico, consumo, estoque, fornecedor, prazos, erros de digitação) e devolve farol verde/amarelo/vermelho. **Decisão final continua humana** — o agente instrui, não aprova.
- **Resultado:** Camada de inteligência sobre todo o processo de compras. 100% das requisições validadas, análises padronizadas, menos erros. +R$ 500 mil nos dois primeiros meses.

### 3. ArcelorMittal — `/cases/arcelormittal`
- **H1:** Agentes de IA no WhatsApp cortam 90% do tempo de documentação na ArcelorMittal
- **Métricas:** −90% no tempo de documentação dos registros · +30% de capacidade de atendimento, sem novas contratações · 21 dias da ideia à primeira prova de conceito entregue
- **Desafio:** Registros de inspeções de segurança e documentação da Medicina do Trabalho feitos manualmente e de forma assíncrona → perda de informação, dados incompletos, carga administrativa alta, sem fluxo padronizado.
- **Solução:** Agentes conversacionais no **WhatsApp integrados ao SAP**. Em campo, o técnico registra a inspeção em tempo real por texto ou áudio, e os dados chegam padronizados e completos. Na Medicina do Trabalho, o agente faz triagem inicial, resgata histórico do colaborador e gera prontuários padronizados prontos para validação médica.
- **Resultado:** −90% tempo de documentação, +30% capacidade de atendimento sem contratações. **Validação final sempre humana.** Mesmo modelo já serve para triagem e registro de chamados de assistência técnica.

### 4. AEVO — `/cases/aevo`
- **H1:** Como a AEVO colocou 32 agentes de IA em produção em 4 meses, com 892% de ROI
- **Métricas:** 892% ROI do programa, payback em 1,34 meses · R$ 1,08 mi de economia anual projetada · 32 agentes em produção em 4 meses
- **Desafio:** Plataforma líder em gestão da inovação com agenda de IA difusa — iniciativas dispersas, sem governança nem direcionamento. Liderança precisava de programa estruturado com impacto financeiro comprovável.
- **Solução:** Programa **AI-First de 4 meses**: diagnóstico estratégico + priorização de oportunidades + capacitação de **17 Black Belts internos em 4 diretorias**. **76 oportunidades mapeadas**, roadmap executado sprint a sprint.
- **Resultado:** 32 agentes em produção, nova camada operacional de pessoas + IA. 892% ROI, payback 1,34 meses, R$ 1,08 mi/ano projetado. **CEO da AEVO autorizou conversas de referência.**

### 5. Unimed — `/cases/unimed`
- **H1:** Unimed treina mais de 200 profissionais para aplicar IA na operação sem ajuda externa
- **Métricas:** 200+ profissionais capacitados em IA aplicada · 2 públicos (médicos e time de back office) · Zero dependência de terceiros
- **Desafio:** Cooperativa médica queria que a IA deixasse de ser ferramenta pontual e virasse cultura. Desafio não era tecnológico — era formar pessoas.
- **Solução:** Programa de capacitação **prática** em IA aplicada, duas frentes: assistencial (médicos) e administrativa (back office). Foco em uso real no dia a dia, não em teoria.
- **Resultado:** 200+ profissionais usando IA com autonomia real, sem dependência de terceiros.

---

## Carreiras (`/carreiras`)

- **Meta description:** Contratamos construtores e operadores de alta autonomia para colocar agentes de IA em produção em grandes empresas.
- **Lede:** Ajudamos grandes empresas a sair da ambição com IA para o impacto mensurável em produção **em semanas, não meses**, com um modelo operacional repetível construído para as restrições do mundo real.
- **Manifesto:** Contratamos construtores e operadores de alta autonomia, movidos por missão, que se importam mais em entregar impacto em produção do que com teoria, títulos ou conforto, e que prosperam trabalhando lado a lado com o cliente para resolver problemas difíceis de ponta a ponta.
- **Modelo:** *Global no desenho. Local na execução.* — "Operamos em mercados-chave hoje e expandimos continuamente, com times locais embarcados onde quer que a gente implante."

### Cargos abertos
- **Deployment Strategist** — Líderes que resolvem problemas, com mentalidade de dono e forte fluência técnica. Vêm de posições operacionais e técnicas de alto impacto, de consultoria, de fundação de empresas ou dos primeiros funcionários de uma startup, normalmente com formação em computação ou engenharia. **São donos do deployment e medidos pelo resultado no P&L do cliente.**
- **Forward Deployed Engineer (FDE)** — Engenheiros embarcados no cliente, generalistas em integrações, agentes e dados, ou especialistas (ex.: arquitetos de solução de telefonia). Mergulham em fluxos de trabalho complexos para desenhar e entregar agentes de IA que resolvem desafios reais de negócio.
- **Go To Market (GTM)** — Vendedores enterprise consultivos, que entendem a fundo processos de compra, personas e dinâmica organizacional. Não precisam ser profundamente técnicos, mas precisam entender como a tecnologia funciona e **coordenar um pod da smartside.ai**.
- **Outras posições** — operações e liderança conforme a empresa escala.

- **Formulário:** nome, e-mail, telefone, cargo de interesse, LinkedIn/currículo, texto livre. Aviso de privacidade de candidatos referenciado.

---

## Leitura do posicionamento (análise)
- **Vocabulário é Palantir-like e deliberado:** *Forward Deployed Engineer*, *Deployment Strategist*, *pod*, medido no *P&L do cliente*. O modelo comercial vendido é time embarcado no cliente, não produto.
- **Prova social é toda por número, não por adjetivo.** Cada case tem exatamente 3 métricas duras e um FAQ voltado a SEO/AEO.
- **Integração em sistema legado é o diferencial declarado** em 3 dos 5 cases: Sankhya, TOTVS Fluig, SAP. A tese é "IA dentro do fluxo que já existe", nunca ferramenta paralela.
- **"Human in the loop" é dito explicitamente** em Fibrasa e ArcelorMittal — vender para setor regulado exige isso.
- **Capacitação (Black Belts) aparece como entregável de venda**, não como cortesia — é o que sustenta o pilar "Criamos capacidade" e o case Unimed inteiro.
