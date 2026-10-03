# 이제민 | 개발 과정의 계약 검사와 LLM 출력 검증

계약서 분석에서 LLM이 문장을 생성하는 대신 원문 구간을 선택하고, 서버가 그 인용을 원문과 대조하도록 설계했습니다.
아이 작품과 그날의 말을 가족이 함께 간직하는 미술관 서비스에서는 화면·API·모델 워커의 경계를 API 계약으로 정하고, CI에서 계약 lint와 사본 일치를 검사했습니다.
승패 예측에서는 정확도뿐 아니라 계수의 부호와 경기 유형별 오차를 확인했고,
음성 연구에서는 빈 전사가 평가에서 빠지는 오류를 수정했습니다.

## 먼저 볼 작업

| 해결한 문제 | 맡은 일 | 판단과 구현을 확인할 근거 |
|---|---|---|
| **[LLM 응답을 계약 원문과 연결](https://github.com/wpalswpa/truefit-engineering-evidence)** | 3인 팀 제품 설계·AI 연동. 공개 저장소는 검증 규칙을 별도로 재현 | [구간 선택의 이유](https://github.com/wpalswpa/truefit-engineering-evidence/blob/main/docs/decisions/001-source-span-extraction.md) · [회귀 검사](https://github.com/wpalswpa/truefit-engineering-evidence/blob/main/tests/test_contract_examples.py) |
| **[우리 아이 미술관](https://github.com/wpalswpa/kids-art-museum-serving-evidence)** | 4인 팀의 API 계약(OpenAPI)·작업 큐·낮춤 체인·CI(lint·타입·단위 시험·계약 lint, 계약 정본과 사본 일치 검사) 담당. 웹 담당자는 이 계약에서 TypeScript 타입을 생성해 사용. 팀 원본은 비공개이며 공개 저장소는 상태 규칙을 표준 라이브러리로 재현 | [낮춤과 재시도를 나눈 이유](https://github.com/wpalswpa/kids-art-museum-serving-evidence/blob/main/docs/decisions/002-downgrade-vs-retry.md) · [규칙 검사](https://github.com/wpalswpa/kids-art-museum-serving-evidence/blob/main/tests/test_fallback.py) · [실제 시험 기록](https://github.com/wpalswpa/kids-art-museum-serving-evidence/blob/main/evidence/README.md) |
| **[예측 결과의 해석과 입력 검증](https://github.com/wpalswpa/lol-win-prediction)** | 4인 팀 분석·모델링·검증 및 후속 서비스 기능 | [실험 보고](https://github.com/wpalswpa/lol-win-prediction/blob/main/docs/experiment_report.md) · [서빙 계약](https://github.com/wpalswpa/lol-win-prediction/blob/main/docs/serving.md) · [재현 순서](https://github.com/wpalswpa/lol-win-prediction/blob/main/docs/REPRODUCE.md) |
| **[음성 전사 실패를 평가에 반영](https://github.com/wpalswpa/stt-llm-depression-screening)** | 석사 연구의 Whisper·LLM 비교와 후속 평가 코드 점검 | [평가 코드](https://github.com/wpalswpa/stt-llm-depression-screening/blob/main/evaluation.py) · [빈 전사 등 회귀 검사](https://github.com/wpalswpa/stt-llm-depression-screening/blob/main/tests/test_evaluation.py) |

TrueFit, 우리 아이 미술관, 음성 연구의 공개 회귀 검사는 API 키나 원본 개인정보 없이 실행할 수 있습니다.
각 README에 실행 방법, 본인·팀의 담당 범위, 결과의 조건과 한계를 적었습니다.
저장 응답·합성 입력 검사와 실제 모델 정확도, 과거 연구 수치와 수정 후 결과를 구분합니다.

## 추가 작업

- [라이프로그 위험군 분류](https://github.com/wpalswpa/dementia-screening): 4인 팀장, 활동·수면 지표 모델과 FastAPI 프로토타입. 임상 검증 범위를 갖추지 않은 학습 프로젝트입니다.
- [얼굴 이미지 분류와 편향 점검](https://github.com/wpalswpa/stroke-facial-asymmetry-screening): 개인 전이학습 실습. 서로 다른 이미지 출처의 영향을 포함하며 의료 진단 성능으로 해석하지 않습니다.

## 사용한 기술과 경험

| 경험 | 기술 |
|---|---|
| 데이터 처리 실무 | Python · SQL · Airflow · BigQuery |
| 모델 분석·평가 | pandas · scikit-learn · TensorFlow/Keras · OpenCV |
| 음성·LLM 연동 | Whisper · GPT API · 구조화 출력 · 원문 구간 검증 |
| 서비스 구현·회귀 검사 | Flask · FastAPI · SQLite · pytest · unittest |
| 모델 서빙 운영 | 작업 큐 · 낮춤·재시도 규칙 · Node.js · Express · MariaDB |
| API 계약·CI | OpenAPI 계약 정본 · Redocly 계약 lint · GitLab CI(lint·타입·단위 시험·계약 lint) · TypeScript(Express API, Vue 운영 화면) · Vitest · Supertest |

기업별 이력서와 포트폴리오에서는 맡을 업무에 맞는 사례를 골라 설명합니다.
이 GitHub는 공통으로 확인할 수 있는 작업과 근거를 모아 둔 공간입니다.
