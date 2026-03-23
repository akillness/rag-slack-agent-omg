# Context: Saga RAG Slack Agent

## Workflow Context
- 사용자는 Slack에서 질문(멘션 또는 slash command)을 입력
- 봇은 Saga API로 게임/문서 컨텍스트를 조회하고 답변+출처를 반환
- 고빈도 질의는 세션 컨텍스트로 요약 저장해 후속 질의 품질 개선

## Affected Users
| Role | Responsibility | Skill Level |
|------|----------------|-------------|
| PM/기획 | 정책·밸런스·업데이트 문서 질의 | 중 |
| 운영/CS | 이슈 응답/근거 확인 | 중 |
| 개발자 | API/문서/세션 디버깅 | 상 |
| 리더십 | 주간 요약/핵심 인사이트 확인 | 중 |

## Current Workarounds
1. 노션/드라이브 수동 검색 후 링크 붙여넣기
2. 팀별 문서 저장소 분산으로 최신본 확인에 시간 소모
3. 질문마다 담당자 DM 의존

## Adjacent Problems
- 문서 최신성 검증(버전 충돌)
- 출처 없는 AI 답변에 대한 신뢰 이슈
- Slack 스레드 맥락이 길어질수록 정확도 저하

## User Voices
- “답은 빨리 오는데 출처가 없어서 못 믿겠다.”
- “같은 질문이 팀마다 반복된다.”
- “정확한 문서 버전을 확인하는 데 시간이 오래 걸린다.”

## API Readiness Notes
- OpenAPI 문서 확인: `GET /openapi` 또는 `/openapi.json`
- 핵심 사용 후보:
  - `POST /games/{id}/query`
  - `POST /rag/search`
  - `POST /search/agent/query`
  - `POST /rag/context`
  - `GET /health`
