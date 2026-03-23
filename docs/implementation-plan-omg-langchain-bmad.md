# Implementation Plan (OMG + langchain-bmad + Survey)

## 0) Scope
- 목표: Saga RAG API를 Slack bot으로 연결한 실사용 MVP
- 기간: 1주
- 성공 기준:
  1. Slack `/ask` + 멘션 질의 응답
  2. Saga API 연동(health/query/search)
  3. 답변에 출처/신뢰도 포함
  4. 평가셋 20문항 기준 최소 정확도 달성

## 1) Survey 결과 반영 (Done)
- 산출물: `.survey/saga-rag-slack-agent/*`
- 핵심 인사이트: 모델보다 retrieval 품질/출처 UX 우선

## 2) OMG Planning Phase
- OMG PLAN에서 아래 4개 스트림 분해
  - Stream A: Slack Bot Runtime
  - Stream B: Saga API Client
  - Stream C: Retrieval/Answer Policy
  - Stream D: Eval/Observability

## 3) langchain-bmad 적용 포인트
- BMAD 단계 분리:
  - **B**reakdown: 기능을 issue 단위로 쪼개기
  - **M**odeling: 질의 흐름(state) 정의
  - **A**utomation: API 호출/검증 자동화
  - **D**elivery: MVP 체크리스트 통과 후 배포
- LangChain 사용 범위:
  - Retriever wrapper for Saga endpoints
  - Output parser(답변+출처 schema)
  - Eval runner(질문셋 자동 채점)

## 4) API-first 구현 순서 (바로 실행 가능)
1. `GET /health` 연결 확인
2. `POST /games/{id}/query` 기본 질의 경로 구현
3. `POST /rag/search`로 근거 문맥 확장
4. `POST /search/agent/query`를 deep mode에 매핑
5. 응답 표준화: `answer`, `sources[]`, `confidence`

## 5) Slack Bot 설계
- Slash command
  - `/ask <question>`: fast mode (`/games/{id}/query`)
  - `/ask-deep <question>`: deep mode (`/search/agent/query`)
- Mention mode
  - thread_ts 기준 대화 컨텍스트 유지
- 에러 정책
  - API timeout 시 사용자에게 재시도 안내 + trace id 출력

## 6) GitHub Issues 백로그 (추천)
1. chore: project scaffold + env schema
2. feat: saga api client + auth middleware
3. feat: slack bolt app + command handlers
4. feat: citation formatter + confidence policy
5. feat: eval runner(20 golden Q)
6. chore: logging + metrics dashboard
7. docs: runbook + rollback guide

## 7) MVP Delivery Checklist
- [ ] Slack command responds within SLA
- [ ] 모든 응답에 출처 포함
- [ ] 무근거 응답 거절 정책 동작
- [ ] 오류/타임아웃 로깅
- [ ] 문서화 완료

## 8) Next Commands (Operator)
- survey 실행/갱신: `.survey/saga-rag-slack-agent` 갱신
- omg PLAN: 작업분해 + 우선순위 잠금
- omx EXECUTE: 병렬 구현 후 PR 생성
