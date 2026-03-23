# Slack Bot Design

## Commands
- `/ask <question>`: standard RAG answer with citations
- `/ask-deep <question>`: slower mode with expanded retrieval
- `/sources <query>`: return top matching sources only

## Mention Behavior
- `@bot 질문`: respond in-thread by default
- If question has no matching context, ask clarification + suggest source tags

## Response Template
1. Short answer (2-5 lines)
2. Evidence bullets
3. Source references (doc title + section/chunk id)
4. Confidence level (high/medium/low)

## Security
- Slack signing secret verification mandatory
- Restrict allowed workspace/channel list
- redact tokens and PII in logs

