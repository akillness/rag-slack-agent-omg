# Architecture

## 1) Core Components
- **Ingestion Worker**: collects docs from local files, Google Drive export, Notion export
- **Chunker**: semantic chunking with overlap + metadata tags
- **Embedding Service**: creates vectors for each chunk
- **Vector DB**: stores vectors + metadata
- **Retriever**: top-k + rerank
- **Answer Engine**: LLM answer generation constrained by retrieved context
- **Slack App**: slash commands, mentions, thread replies
- **Observability**: logs, latency, fallback reasons, citation coverage

## 2) Data Flow
1. Source docs -> normalize text
2. Normalize -> chunk + metadata
3. Chunk -> embedding -> vector DB upsert
4. Slack query -> retrieve -> rerank -> answer
5. Answer -> Slack + source citations

## 3) Non-functional Targets
- p95 answer latency: < 8s (MVP)
- citation coverage: >= 90% of responses include source ids
- hallucination guard: abstain if confidence below threshold

