# Solution Landscape: Saga RAG Slack Agent

## Solution List
| Name | Approach | Strengths | Weaknesses | Notes |
|------|----------|-----------|------------|-------|
| Saga API + Slack App (권장) | 기존 RAG API 직접 연동 | 구현 속도 빠름, 도메인 적합 | API 스키마 의존성 | 이번 프로젝트 기본안 |
| LangChain Agent + Saga retriever wrapper | 에이전트 오케스트레이션 추가 | 라우팅/툴콜 유연 | 복잡도 증가 | langchain-bmad 적용에 적합 |
| Bolt 단독 + 수동 retrieval | 최소 의존성 | 단순함 | 확장성 낮음 | 단기 PoC 전용 |
| 벡터DB 직접 구축 + Slack | 완전 제어 | 커스텀 최적화 | 구축비용 큼 | 현 시점 비권장 |

## Categories
- API-first RAG 통합
- Agent Orchestration 기반
- Minimal bot integration
- Full custom platform

## What People Actually Use
- Slack + 기존 내부 검색 API를 먼저 붙인 뒤, 품질 문제가 생기면 reranker/eval을 붙여 확장하는 패턴이 많음

## Frequency Ranking
1. API-first + Slack bot
2. LangChain/Graph 기반 라우팅 추가
3. 사내 벡터플랫폼 직접 구축

## Key Gaps
- “출처 포맷 표준”과 “신뢰 점수 표시”가 빠진 경우 운영 저항이 큼

## Contradictions
- “에이전트 붙이면 자동으로 정확해진다” vs 실제로는 retrieval 품질/평가셋이 성패를 좌우

## Key Insight
- 지금은 “모델 고도화”보다 “근거 있는 응답 UX + 운영 지표(정확도/재현성)”가 ROI가 높다.

## Trend Sources
- LangChain RAG patterns: https://python.langchain.com/docs/concepts/rag/
- Weaviate RAG guides: https://weaviate.io/developers/weaviate/starter-guides/generative
- Pinecone RAG resources: https://www.pinecone.io/learn/retrieval-augmented-generation/
- Slack platform bots: https://api.slack.com/automation/overview
- Anthropic tool use patterns: https://docs.anthropic.com/en/docs/build-with-claude/tool-use
