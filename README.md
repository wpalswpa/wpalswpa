# 이제민

**LLM 사후학습·평가 · 신뢰할 수 있는 LLM 연동 · API 계약과 검증 도구**

기준선을 먼저 정하고, 결과를 코드로 판정하고, 기준을 넘지 못하면 도입하지 않습니다. 아래 저장소마다 무엇을 바꿨는지, 어떻게 확인했는지, 어떻게 다시 돌리는지를 첫 화면에 적었습니다.

## 대표 작업

| 저장소 | 무엇이 바뀌었나 | 확인 방법 |
|---|---|---|
| [**rft-instruction-following**](https://github.com/wpalswpa/rft-instruction-following) · 거부 샘플링 미세조정 | Qwen2.5-0.5B-Instruct의 형식 지시 엄격 통과율 **14.4% → 35.6% ± 6.0%p**(학습 시드 3회, 학습에 없던 주제의 시험 160문항). 시스템 프롬프트 기준선은 14.4% 그대로 | 학습 전 커밋한 성공 기준, 시드 반복·선택 규칙 비교, 산술 대조 47→46~48/60, 결정적 판정 함수·시험 |
| [**kids-art-museum-serving-evidence**](https://github.com/wpalswpa/kids-art-museum-serving-evidence) · 작업 처리 규칙과 실행 검증 | 팀 서비스에서 맡은 처리 규칙(품질 미달은 낮춤, 장애는 같은 단계 재시도)을 API·워커·MariaDB로 실행 | GitHub Actions: 계약 검사·장애 주입 11개(시간 초과·503·계약 위반 응답·DB 중지)와 음성 대조, 보호자 화면(TypeScript) Playwright E2E 4개 |
| [**ai-talk-harness-evidence**](https://github.com/wpalswpa/ai-talk-harness-evidence) · 여러 LLM CLI 실행 하네스 | CLI 실패 출력이 발언으로 저장되던 경로(10회 중 8회)를 분리. 종료 자동화는 기준선 60%를 넘지 못해(50%) 도입하지 않음 | 런타임 시험 포함 73개, Ubuntu·Windows CI, 결정 기록 2건 |
| [**stt-llm-depression-screening**](https://github.com/wpalswpa/stt-llm-depression-screening) · 석사 연구 | 음성 전사(WER·CER)와 LLM 분류(정확도·F1)를 나눠 평가. 빈 전사가 평균에서 빠지던 집계 수정 | 합성 입력 회귀 검사 8개, CI. 2025 한국통신학회 하계 발표 |

## 그 밖의 작업

- [TrueFit](https://github.com/wpalswpa/truefit-engineering-evidence): LLM은 문장 구간 번호만 고르고 서버가 원문에서 인용문을 만든다. 범위 밖 구간·모델이 쓴 인용문 거부 검사 10개(3인 공모전 팀, PM 겸 개발).
- [PassFinder](https://github.com/wpalswpa/AltTab): 서버리스 배포의 첫 화면 500(읽기 전용 경로에 폴더 생성)을 런타임 로그로 찾아 고친 [PR](https://github.com/Snow0821/AltTab/pull/8)(5인 팀, 하루 행사).
- [LoL 승패 예측](https://github.com/wpalswpa/lol-win-prediction): 전처리 전 분할·학습 데이터 교차검증, 계수 부호를 지표 제거로 점검(4인 팀).

<details>
<summary>이전 학습 프로젝트</summary>

- [활동·수면 지표의 위험군 분류](https://github.com/wpalswpa/dementia-screening): 피처 선택 누수 수정, 순열 검정(4인 팀장).
- [얼굴 이미지 분류와 편향 점검](https://github.com/wpalswpa/stroke-facial-asymmetry-screening): 이미지 출처 편향 가능성을 기록한 전이학습 실습(개인).

</details>

## 기술

- **학습·평가:** PyTorch, Transformers, PEFT(LoRA), scikit-learn, Whisper, 통계 검정(McNemar·부트스트랩)
- **API·서비스:** Python, TypeScript, FastAPI, Express, OpenAPI, MariaDB, SQLite, Docker Compose
- **검사·자동화:** pytest, Playwright E2E, GitHub Actions, Prometheus 지표, 구조화 로그

코드 작성에는 AI 코딩 도구(Claude Code·Codex)를 사용했습니다. 각 저장소의 설계 문서·결정 기록·커밋 이력에 무엇을 언제 정했는지 남겼습니다.
