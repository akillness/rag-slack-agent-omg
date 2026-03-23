# Platform Map: Saga RAG Slack Agent

## Settings
| Concern | Claude/OMC | Codex/OMX | Gemini/OHMG | Common Layer |
|---------|------------|-----------|-------------|--------------|
| Model/runtime | 모델 alias + 세션별 오버라이드 | 모델 alias + session override | 모델/think 설정 | `settings.model` |
| Retrieval params | top-k/rerank prompt-based | tool-call + param routing | workflow param injection | `settings.retrieval` |
| Context window | prompt budget 관리 | chunked prompt merge | staged context load | `settings.context_budget` |

## Rules
| Concern | Claude / OMC | Codex / OMX | Gemini / OHMG | Common Layer |
|---------|---------------|-------------|---------------|--------------|
| Citation required | system rule 강제 | response schema 강제 | workflow post-check | `rules.citation_required` |
| No-source abstain | fallback 문구 | confidence threshold | guardrail node | `rules.abstain_when_low_conf` |
| Slack safety | external action confirmation | channel allowlist | send policy | `rules.external_send_policy` |

## Hooks
| Lifecycle | Claude | Codex | Gemini | Common Layer |
|-----------|--------|-------|--------|--------------|
| pre-query | query normalize | tool route | workflow triage | `hooks.pre_query` |
| post-retrieve | context quality check | rerank hook | evidence filter | `hooks.post_retrieve` |
| post-answer | citation formatter | schema validator | quality gate | `hooks.post_answer` |
| error | retry + summarize | retry + report | retry policy | `hooks.on_error` |

## Platform Gaps
- 플랫폼별 “에이전트 팀 실행” 방식은 다르지만, Slack RAG 봇에는 `settings/rules/hooks` 공통층으로 추상화 가능
