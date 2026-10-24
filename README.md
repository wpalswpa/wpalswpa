# 이제민

**직접 써 보며 발견한 불편을 요구사항과 처리 규칙으로 바꾸고, 구현 결과를 다시 확인합니다.**

모델의 결과가 서비스 안에서 제대로 쓰이도록 설계하고 검증하는 일을 합니다. 모델을 비교해 고르고, 생성이 느리거나 실패할 때의 처리 규칙을 정하고, 결과를 시험과 측정으로 확인합니다.

## 대표 작업

### [LoL 승패 예측과 핵심 승리요인 분석](https://github.com/wpalswpa/lol-win-prediction)

4인 팀 프로젝트에서 분석·모델링·검증·문서와 서비스 기능을 맡았습니다. 경기 시작 10분 시점의 팀 지표 13개로 최종 승패를 예측하고, 왜 그렇게 판단했는지와 언제 틀리는지까지 보여 줍니다.

- **모델 선택:** 시험셋을 전처리보다 먼저 떼어 두고, 학습셋 5겹 교차검증으로 모델 8종을 비교해 로지스틱 회귀를 골랐습니다. 떼어 둔 시험셋에서 2위 나이브베이즈와 비교하니 정확도는 0.7394 대 0.7313으로 비슷했고, 예측 확률의 오차(Brier)는 0.1756 대 0.2179로 로지스틱 회귀가 더 낮았습니다.
- **해석:** 킬 차이 계수가 음수로 나와 골드 차이와의 상관(0.92)을 확인했고, 골드를 뺀 재학습에서 계수가 +0.508로 바뀌는 것을 보고 모델카드에 계수 해석 주의를 적었습니다.
- **검증:** 공개 회귀 검사 25개 통과(원본 데이터가 필요한 재학습 검사 2개는 건너뜀), GitHub Actions. 과정 기간에 공개 운영했고 지금은 로컬에서 실행합니다.
- [실험 보고](https://github.com/wpalswpa/lol-win-prediction/blob/main/docs/experiment_report.md) · [모델카드](https://github.com/wpalswpa/lol-win-prediction/blob/main/model_card.md)

### [우리 아이 미술관 작업 처리 규칙](https://github.com/wpalswpa/kids-art-museum-serving-evidence)

쌓여 가는 아이 그림을 가족 미술관 콘셉트로 보여 주는 4인 팀 프로젝트에서 API 서버·작업 큐·결과 처리 규칙을 맡았고, 그 규칙을 개인 공개 재현으로 다시 만들었습니다.

- **규칙:** 생성 결과를 기다리지 않도록 올리는 즉시 원본 액자를 겁니다. 품질 미달은 한 단계 낮춘 결과로 대체하고, 인프라 장애만 첫 시도를 포함해 최대 3회 시도합니다.
- **검증:** 단위 16개, 장애 주입·DB 복구 통합 13개, Playwright E2E 4개. 시간 제한을 일부러 바꾸면 실패하는 역검사도 둡니다. 가짜 모델 서버를 쓰므로 실제 생성 품질과 부하는 재지 않았습니다.
- [원본 먼저 전시](https://github.com/wpalswpa/kids-art-museum-serving-evidence/blob/main/docs/decisions/001-original-first.md) · [낮춤과 재시도 분리](https://github.com/wpalswpa/kids-art-museum-serving-evidence/blob/main/docs/decisions/002-downgrade-vs-retry.md) · [타입 생성](https://github.com/wpalswpa/kids-art-museum-serving-evidence/blob/main/docs/decisions/005-typed-contract.md)

### [찾았슈의 계약 범위 검색과 RAG 비교](https://github.com/wpalswpa/foundshu-rag-evidence)

보험 약관에서 받을 수 있는 보험금을 찾아 주는 개인 프로젝트입니다. 이름이 비슷한 특약의 조항이 섞이지 않도록 회사·상품·판본·특약으로 검색 범위를 먼저 좁혔습니다.

- **비교:** 직접 만든 합성 사례 24건(필요한 조항이 정해진 18건, 조항을 붙이면 안 되는 6건)으로 비교했습니다. 필요한 조항을 모두 찾은 사례는 낱말 검색 3→18건, 의미 검색 4→17건으로 늘었고, 다른 범위 조항이 섞인 사례는 24건에서 0건이 됐습니다.
- **범위:** 한 상품의 세 특약에 집중한 조항 검색 평가이며, 답변이나 보험금 지급 판단의 정확도가 아닙니다.

### [상담 음성 전사와 LLM 분류 평가](https://github.com/wpalswpa/stt-llm-depression-screening)

학술대회에서 발표한 상담 음성 전사·LLM 분류 비교의 평가 코드입니다. 저는 빈 전사가 오류율 평균에서 빠지는 문제를 찾았습니다. 평가 코드 수정과 빈 전사·정답 누락·잘못된 입력을 확인하는 회귀 검사 8개 작성은 AI 코딩 도구가 수행했습니다. 비임상 연구입니다.

## 그 밖의 작업

| 작업 | 확인한 것 |
|---|---|
| [PassFinder 팀 배포 오류 수정](https://github.com/Snow0821/AltTab/pull/8) | 교안 기반 문항 생성 서비스의 첫 화면 500 오류를 런타임 로그로 확인하고, Vercel에서 임시 폴더를 쓰도록 고친 PR이 팀 저장소에 병합됨 |
| [치매 위험 스크리닝](https://github.com/wpalswpa/dementia-screening) | 5일 교육 팀 프로젝트(팀장). 활동·수면 지표 위험군 분류와 데이터 누수 점검 |

Python · scikit-learn · Whisper · TypeScript · Express · OpenAPI · pytest · Playwright · GitHub Actions · Docker Compose

코드와 검사 작성에는 Claude Code·Codex를 사용했습니다. 작업마다 설계서에 목표와 끝나는 조건을 먼저 적고, 결과를 시험과 측정으로 확인했습니다. 본인이 정한 문제·기준과 팀원의 구현 범위는 각 저장소의 설계·결정 기록에서 구분했습니다.
