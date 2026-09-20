# 이제민 | Python · AI 응용 개발

음성·LLM 연구와 데이터 파이프라인 업무를 경험했습니다. 모델 출력의 근거와 상태 경계를 설계하고, 공개 서비스 배포·상태 점검·복구 검증까지 연결합니다.

## 대표 작업

| 프로젝트 | 문제와 구현 | 확인할 근거 · 본인 역할 |
|---|---|---|
| [상담 음성·LLM 연구](https://github.com/wpalswpa/stt-llm-depression-screening) | Whisper 전사와 GPT zero-shot 분류 비교 | 석사 연구·2025 KICS 발표. 전사 평가 오류 수정, 오프라인 회귀 검사 8개. 수정 후 전체 성능 재측정은 미완료 |
| [LoL 승패 예측](https://github.com/wpalswpa/lol-win-prediction) | 10분 지표 13개로 승패 예측·근거 설명 | 4인 팀에서 분석·모델링·검증·문서 담당. 홀드아웃 정확도 0.7394와 시드 반복 평균 0.7366을 구분. 입력 계약·모델카드·재현 테스트 |
| [TrueFit 공개 시연](https://truefit-wanted.onrender.com) | 운동 수업의 예약·이용 기록과 이견 회차별 정산. 계약 원문은 strict schema, 분쟁 쟁점은 Jev로 분리하고 서버가 상태 변경을 검증 | 3인 팀 Product/AI integration lead. Render·Vercel AI Gateway 배포, pytest 387건·브라우저 여정 24개·반응형 84건·재시작/백업 복원 게이트. 실제 결제·송금은 미연결 |
| [안면마비 이미지 분류](https://github.com/wpalswpa/stroke-facial-asymmetry-screening) | ResNet50 전이학습·얼굴 크롭·Grad-CAM | 대학원 실습. 검증셋 지표와 데이터 출처 편향을 함께 설명 |
| [라이프로그 위험군 분류](https://github.com/wpalswpa/dementia-screening) | 활동·수면 지표와 FastAPI 프로토타입 | 4인 팀장. 누수 점검·수정 과정과 174명 표본의 한계 |

## 경험과 도구

- **Python · pandas · scikit-learn**: 데이터 분석, 모델 비교, 입력 검증, 회귀 검사.
- **Whisper · GPT API · Scikit-LLM**: 음성 전사 및 텍스트 zero-shot 분류 연구.
- **TensorFlow/Keras · OpenCV**: 이미지 전이학습과 시각적 해석 실습.
- **Airflow · BigQuery · SQL**: 넛지헬스케어 데이터 엔지니어링 계약직(2026.05-06). 기존 DAG 구조 파악 및 신규 이벤트 적재 업무 참여.
- **GCP Compute Engine · Ubuntu · systemd · cron**: 개인 업무 흐름용 Slack·Telegram 자동화를 `e2-micro` VM에 배포. 권한 600 비밀값 파일, 범위 제한 deploy key, KST 예약 실행과 노트북 중복 중지를 검증(2026-09-20).
- **Render · health check**: TrueFit 공개 서버를 배포하고 GCP에서 `/healthz`를 5분 간격으로 점검. 상태 변화·장애 지속 시에만 알리는 흐름과 재시작·백업 복원 릴리스 게이트 구성.

국민대학교 SW융합대학원 인공지능전공 석사. 공개 저장소에는 연구·교육 프로젝트와 팀 결과물을 구분해 기록하며, 원본 상담 데이터와 사내 코드는 포함하지 않습니다.
