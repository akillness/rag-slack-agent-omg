# Implementation Plan (OMG style)

## Phase 0 — Bootstrap (Day 1)
- Define scope, allowed sources, and forbidden sources
- Prepare environment variables and secrets policy
- Create baseline project skeleton

## Phase 1 — RAG Core (Day 2-3)
- Implement ingestion for Markdown/PDF
- Build chunking policy by document type
- Add embedding + vector index pipeline
- Validate retrieval with 20 golden queries

## Phase 2 — Slack Integration (Day 4-5)
- Create Slack app and bot token permissions
- Implement `/ask` command and mention handler
- Thread-aware context mode (use thread_ts as conversation key)
- Return answers with source references

## Phase 3 — Quality & Guardrails (Day 6)
- Add low-confidence refusal template
- Add citation-required response policy
- Add simple reranker and duplicate context suppression

## Phase 4 — Launch (Day 7)
- Run smoke test in private Slack channel
- Monitor logs and tune retrieval parameters
- Freeze MVP and write runbook

