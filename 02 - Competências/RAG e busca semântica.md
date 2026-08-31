---
type: competencia
nivel: medio
tags: [competencia, rag, embeddings, pgvector]
atualizado: 2026-08-31
---

# RAG e busca semântica

> Retrieval desenhado por propósito, com ingestão versionada e modelo declarado.

## Provas
- [[Knewin — Nina, SDR de IA com Triagem de CRM|Knewin]] — **dois índices segregados**: `consultar_base_produtos` (o que o produto é) e `consultar_perguntas_produto` (o que perguntar). Índice único misturaria descrição com pergunta de descoberta e a busca traria a coisa errada.
- Ingestão versionada em workflow, com modelo e dimensão declarados: `text-multilingual-embedding-002`, 768d, Google Vertex.
- [[Ebramed — Isabela, do diagnóstico à migração|Ebramed]] — corpus curado à mão: 25 programas de curso + 10 documentos comerciais convertidos para markdown estruturado. Diagnosticou o chunking quebrado numa reingestão.
- [[Farmly — Máquina de Aquisição Outbound|Farmly]] — vector store Supabase com embeddings OpenAI.

## Lacuna
Sem evidência de **avaliação de retrieval** (recall@k, precision, teste de relevância). A qualidade do índice é assumida, não medida. Também não há reranking nem busca híbrida.
