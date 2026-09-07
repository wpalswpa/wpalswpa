# wpalswpa

데이터 적재 → 학습 → 서빙 → 재학습이 이어지는 ML 시스템의 흐름을 설계하고 지키는 쪽을 지향합니다.
아래 저장소들은 공통으로 **"이 수치를 믿을 수 있는 이유"를 먼저 확인한 흔적**을 남기려 했습니다 — 분할을 전처리보다 먼저, 해석은 두 방법으로 교차 확인, 좋게 나온 숫자는 누수부터 의심.

## 작업물

| 저장소 | 한 줄 | 확인할 것 |
|---|---|---|
| [lol-win-prediction](https://github.com/wpalswpa/lol-win-prediction) — LoL 승패 예측·승리요인 분석 | 10분 시점 숫자 13개로 승패를 예측하고 왜·언제 틀리는지까지 돌려주는 서비스 ([라이브](https://p4.sumzip.com)) | 시드 10개 반복검증 0.7366±0.0081 · pytest 24개 · 입력 계약 `schema.json` · 모델카드 · 자급형 제출물 빌더 |
| [stt-llm-depression-screening](https://github.com/wpalswpa/stt-llm-depression-screening) — 음성 기반 우울 위험 스크리닝 | Whisper 전사 → LLM zero-shot 분류, 비임상 연구 (2025 KICS 하계학술발표회) | 전사 품질(WER)을 독립 지표로 먼저 측정 · 발표 이후 재검증 섹션 |
| [stroke-facial-asymmetry-screening](https://github.com/wpalswpa/stroke-facial-asymmetry-screening) — 안면마비 전이학습 + Grad-CAM | 얼굴 이미지로 마비/정상 판별하는 스크리닝 보조 프로토타입 | 데이터 출처 편향을 사전 인지 → 입력 통제 → Grad-CAM으로 판단 근거 검증 |
| [dementia-screening](https://github.com/wpalswpa/dementia-screening) — 웨어러블 라이프로그 치매 위험 스크리닝 | 활동·수면 변동성 지표 → 위험군 분류 → FastAPI 서비스 + 치매안심센터 연계 | 피처 선택 누수를 찾아 고치고 낮아진 성능을 택함 · 순열 검정 · 재학습 데이터 루프 |

주력 도구: Python · pandas · scikit-learn · Airflow · BigQuery · SQL · pytest · FastAPI · TensorFlow/Keras · OpenCV · Whisper
