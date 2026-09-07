# wpalswpa

**좋게 나온 숫자는 먼저 의심한다.** 교차검증 점수가 너무 높아 파이프라인을 되짚었고, 피처 선택에 섞인 누수를 찾아 고친 뒤 낮아진 성능을 결과로 택했다. 발표가 끝난 연구도 다시 열어 전사 단계의 오류를 찾아냈다. 설명되지 않는 숫자는 결과가 아니라고 본다.

**모델은 만드는 것보다 넘기는 것이 어렵다.** 입력 계약(schema)·테스트 24개·모델카드·재현 빌더까지 갖춰야 남이 돌릴 수 있다. 그 포장까지를 내 일로 본다.

**어디서 틀리는지를 숫자로 말한다.** "정확도 74%"보다 "팽팽한 경기 61%, 벌어진 경기 95%"가 쓸 수 있는 정보다. 승리요인 해석은 계수와 permutation 두 방법으로 교차 확인했다.

데이터 적재 → 학습 → 서빙 → 재학습이 한 흐름으로 이어지는 ML 시스템을 설계하고 지키는 엔지니어를 목표로 한다.

## 작업물

| 저장소 | 한 줄 | 확인할 것 |
|---|---|---|
| [lol-win-prediction](https://github.com/wpalswpa/lol-win-prediction) — LoL 승패 예측·승리요인 분석 | 10분 시점 숫자 13개로 승패를 예측하고 왜·언제 틀리는지까지 돌려주는 서비스 ([라이브](https://p4.sumzip.com)) | 시드 10개 반복검증 0.7366±0.0081 · pytest 24개 · 입력 계약 `schema.json` · 모델카드 · 자급형 제출물 빌더 |
| [stt-llm-depression-screening](https://github.com/wpalswpa/stt-llm-depression-screening) — 음성 기반 우울 위험 스크리닝 | Whisper 전사 → LLM zero-shot 분류, 비임상 연구 (2025 KICS 하계학술발표회) | 전사 품질(WER)을 독립 지표로 먼저 측정 · 발표 이후 재검증 섹션 |
| [stroke-facial-asymmetry-screening](https://github.com/wpalswpa/stroke-facial-asymmetry-screening) — 안면마비 전이학습 + Grad-CAM | 얼굴 이미지로 마비/정상 판별하는 스크리닝 보조 프로토타입 | 데이터 출처 편향을 사전 인지 → 입력 통제 → Grad-CAM으로 판단 근거 검증 |
| [dementia-screening](https://github.com/wpalswpa/dementia-screening) — 웨어러블 라이프로그 치매 위험 스크리닝 | 활동·수면 변동성 지표 → 위험군 분류 → FastAPI 서비스 + 치매안심센터 연계 | 피처 선택 누수를 찾아 고치고 낮아진 성능을 택함 · 순열 검정 · 재학습 데이터 루프 |

주력 도구: Python · pandas · scikit-learn · Airflow · BigQuery · SQL · pytest · FastAPI · TensorFlow/Keras · OpenCV · Whisper
