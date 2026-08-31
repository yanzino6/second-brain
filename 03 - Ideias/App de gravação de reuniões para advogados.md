---
type: ideia
categoria: negocio
status: crua
avaliada: nao
capturada: 2026-08-31
origem: entrevista de estruturação do vault
tags: [ideia, saas, juridico, transcricao, freemium]
---

# App de gravação de reuniões para advogados

## Como você contou (bruto, sem edição)

> "Tive uma ideia de aplicação para advogados, para gravar reuniões, registrá-las divididas por clientes, guardando informações importantes ditas pelos speakers e registrando de forma específica do meio jurídico. Modelo de negócios freemium com 3 gravações e planos por número de gravações."

## O que está definido

| Dimensão | O que já existe |
|---|---|
| **Usuário** | Advogado |
| **Job** | Gravar reunião com cliente e não perder o que foi dito |
| **Organização** | Registro dividido **por cliente**, não por data ou arquivo solto |
| **Diferencial declarado** | Extração de informação importante **por speaker** + registro em formato específico do meio jurídico |
| **Modelo** | Freemium — 3 gravações grátis, planos por volume de gravações |

## Por que é uma ideia sua e não genérica

Você já construiu isto três vezes, em outro domínio. A [[Ebramed — Isabela, do diagnóstico à migração|Isabela]] e a [[Knewin — Nina, SDR de IA com Triagem de CRM|Nina]] fazem transcrição de áudio, extração estruturada e registro em CRM por entidade. A [[Farmly — Máquina de Aquisição Outbound|Farmly]] faz extração com schema fechado. O que muda aqui é o domínio e a interface, não a engenharia.

**Isso é vantagem injusta de verdade** — não é ideia que você teria que aprender a executar.

## O que ainda não está respondido

> [!question] Antes de avaliar com `/office-hours` (startup mode)
> - **Demanda:** você conhece advogado que sofre com isso, ou é hipótese? Quem foi a última pessoa que reclamou disso na sua frente?
> - **Status quo:** o que ele faz hoje — grava no celular, anota à mão, secretária transcreve, ou simplesmente esquece?
> - **"Formato específico do meio jurídico":** que formato? Ata, memorando, minuta, timeline processual? Essa é a frase que carrega o produto inteiro e é a mais vaga.
> - **Cunha mais estreita:** qual recorte de advogado? Trabalhista solo, escritório de família, contencioso grande? O produto muda inteiro conforme a resposta.
> - **Por que agora:** Fathom, Granola e Otter já gravam e resumem reunião. O que te faz ganhar de uma ferramenta genérica que o advogado já pode usar hoje?

> [!warning] Restrição do domínio que precisa entrar cedo
> Conversa advogado-cliente é coberta por **sigilo profissional** (OAB) e por **LGPD**, e gravação exige consentimento. Isso não mata a ideia — mas define onde o áudio pode ser processado, se pode sair do país, e quem responde por vazamento. Num produto jurídico isso é requisito de arquitetura, não item de backlog.
>
> É exatamente o tipo de restrição que você já tratou como requisito de sistema no prompt da Isabela, com o CFM.

## Próximo passo

- [ ] Rodar `/office-hours` em **startup mode** para atravessar as seis perguntas forçadas
- [ ] Trazer o design doc gerado para esta pasta
- [ ] Decidir: desenvolver, encostar ou descartar — e **registrar a decisão aqui**, com a data e o motivo

<!-- fonte: capturada na entrevista de estruturação do vault, 2026-08-31 -->
