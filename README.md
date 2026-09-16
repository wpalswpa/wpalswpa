# 이제민 | Python · AI 응용 개발

음성·LLM 연구와 데이터 파이프라인 업무를 경험했습니다. 모델 점수뿐 아니라 입력 품질, 실패 처리, 다시 실행할 수 있는 검증을 함께 확인합니다.

## 대표 작업

| 프로젝트 | 문제와 구현 | 확인할 근거 · 본인 역할 |
|---|---|---|
| [상담 음성·LLM 연구](https://github.com/wpalswpa/stt-llm-depression-screening) | Whisper 전사와 GPT zero-shot 분류 비교 | 석사 연구·2025 KICS 발표. 전사 평가 오류 수정, 오프라인 회귀 검사 8개. 수정 후 전체 성능 재측정은 미완료 |
| [LoL 승패 예측](https://github.com/wpalswpa/lol-win-prediction) | 10분 지표 13개로 승패 예측·근거 설명 | 4인 팀에서 분석·모델링·검증·문서 담당. 홀드아웃 정확도 0.7394와 시드 반복 평균 0.7366을 구분. 입력 계약·모델카드·재현 테스트 |
| [TrueFit 공개 시연](https://truefit-wanted.onrender.com) | 운동 수업의 예약·이용 기록과 이견 회차별 정산. AI가 계약 원문 위치를 선택하고 서버가 인용 복원 | 3인 팀 PM: 문제 정의·서비스 규칙·검증 기준. 백엔드·DB 및 UI·배포는 팀 역할로 구분. 실제 결제·송금은 미연결 |
| [안면마비 이미지 분류](https://github.com/wpalswpa/stroke-facial-asymmetry-screening) | ResNet50 전이학습·얼굴 크롭·Grad-CAM | 대학원 실습. 검증셋 지표와 데이터 출처 편향을 함께 설명 |
| [라이프로그 위험군 분류](https://github.com/wpalswpa/dementia-screening) | 활동·수면 지표와 FastAPI 프로토타입 | 4인 팀장. 누수 점검·수정 과정과 174명 표본의 한계 |

## 경험과 도구

- **Python · pandas · scikit-learn**: 데이터 분석, 모델 비교, 입력 검증, 회귀 검사.
- **Whisper · GPT API · Scikit-LLM**: 음성 전사 및 텍스트 zero-shot 분류 연구.
- **TensorFlow/Keras · OpenCV**: 이미지 전이학습과 시각적 해석 실습.
- **Airflow · BigQuery · SQL**: 넛지헬스케어 데이터 엔지니어링 계약직(2026.05-06). 기존 DAG 구조 파악 및 신규 이벤트 적재 업무 참여.

국민대학교 SW융합대학원 인공지능전공 석사. 공개 저장소에는 연구·교육 프로젝트와 팀 결과물을 구분해 기록하며, 원본 상담 데이터와 사내 코드는 포함하지 않습니다.
