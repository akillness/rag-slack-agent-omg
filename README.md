# RAG Slack Agent (OMG-based Plan)

This repository documents a practical plan to build a personal RAG-based AI agent delivered through a Slack bot.

## Goals
- Build a reliable RAG pipeline (ingest → index → retrieve → answer)
- Expose it via Slack bot commands and thread-aware interactions
- Operate with measurable quality (source-grounded answers)

## Documents
- [Architecture](docs/architecture.md)
- [Implementation Plan](docs/implementation-plan.md)
- [Slack Bot Design](docs/slack-bot-design.md)
- [Execution Checklist](docs/execution-checklist.md)

## MVP Definition
1. Ingest Markdown/PDF/Notion-export docs
2. Vector retrieval with citation chunks
3. Slack `/ask` command + mention-based Q&A
4. Evaluation set with answer+citation scoring

