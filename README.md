# 이제민

**개발 도구와 API 계약의 실패를 추적하고, 테스트·CI로 재발을 막습니다.**

팀원이 쓰는 계약, LLM CLI 실행 환경, 배포 오류를 다룹니다. 문제를 재현하고 선택의 이유를 기록하며, 자동화가 기준선보다 나은지 확인합니다.

## 대표 작업

### [LLM CLI 실행 하네스](https://github.com/wpalswpa/ai-talk-harness-evidence)

두 AI 도구 사이에 답을 옮기는 일을 줄이려고 만든 개인 실행 도구의 핵심 모듈입니다. CLI 실패 출력이 발언으로 저장되던 경로를 분리하고 Windows에서 여러 줄 입력이 잘리던 경로를 stdin 전달로 고쳤습니다. 입력을 읽지 않는 CLI와 출력 파이프 대기도 시간 제한으로 종료합니다.

- **검증:** 가짜 CLI와 `.CMD` 래퍼를 실행하는 회귀 검사. Windows 89 통과, Ubuntu 83 통과·6 건너뜀.
- **판단:** 대화 종료 학습 모델은 라벨 10건에서 정확도 50%로 기준선 60%보다 낮아 도입하지 않았습니다. 실제 작업 시간 절감은 아직 측정하지 않았습니다.
- [입력 전달·시간 제한 결정](https://github.com/wpalswpa/ai-talk-harness-evidence/blob/main/docs/decisions/003-codex-prompt-via-stdin.md) · [종료 자동화 판단](https://github.com/wpalswpa/ai-talk-harness-evidence/blob/main/docs/decisions/002-stop-automation-no-go.md)

### [미술관 API 계약과 개발 자동화](https://github.com/wpalswpa/kids-art-museum-serving-evidence)

4인 팀에서 맡은 API·작업 처리 규칙을 개인 공개 재현으로 만들었습니다. 품질 미달은 한 단계 낮추고 인프라 장애는 같은 단계를 재시도합니다. OpenAPI에서 화면 타입을 생성하고 계약과 생성물의 불일치를 CI에서 찾습니다.

- **검증:** 단위 16개, 장애 주입·DB 복구 통합 13개, TypeScript 화면 Playwright E2E 4개. 시간 제한을 일부러 바꿨을 때 검사가 실패하는 역검사도 수행합니다.
- **범위:** 팀 코드의 사본이 아닌 공개 재현입니다. 가짜 모델 서버를 사용하며 실제 모델 품질·부하 성능은 측정하지 않았습니다.
- [타입 생성 결정](https://github.com/wpalswpa/kids-art-museum-serving-evidence/blob/main/docs/decisions/005-typed-contract.md)

### [찾았슈의 계약 범위 검색과 RAG 비교](https://github.com/wpalswpa/foundshu-rag-evidence)

보험 청구 준비 도구에서 이름이 비슷한 특약의 조항이 섞여 회사·상품·판본·특약으로 검색 범위를 제한했습니다. 판본이 불명확하면 근거를 붙이지 않고, 같은 특약의 제외 조항도 함께 보입니다.

- **비교:** 자체 합성 24건 중 조항이 필요한 18건에서 완전 회수 사례가 낱말 검색 3→18건, 의미 검색 4→17건이었습니다. 한 상품의 세 특약에 집중된 검색 평가이며 답변·지급 정확도가 아닙니다.
- **공개:** 원본 시제품 캡처, 가상 자료로 실행하는 검색 규칙, 인용문 없는 원본 평가 기록. 생성 답변은 기본 판정에서 제외했습니다.

### [PassFinder 팀 배포 오류 수정](https://github.com/Snow0821/AltTab/pull/8)

교안 기반 문항 생성 서비스의 첫 화면이 500으로 열리지 않았습니다. 런타임 로그의 읽기 전용 경로 오류를 확인하고 Vercel에서 임시 폴더를 사용하도록 고친 PR이 팀 저장소에 병합됐습니다. 원인 확인·수정에는 Claude Code를 사용했습니다. 동료가 만든 생성 경로도 제가 추가한 문항 검사 함수를 호출합니다.

## 평가·검증 사례

| 작업 | 확인한 것 |
|---|---|
| [형식 지시 미세조정](https://github.com/wpalswpa/rft-instruction-following) | Qwen2.5-0.5B의 엄격 통과율 14.4% → 35.6%(시드 3회 평균, 160문항). 학습과 같은 지시 종류에서의 결과 |
| [상담 음성 평가 코드](https://github.com/wpalswpa/stt-llm-depression-screening) | 빈 전사가 오류율 집계에서 빠지던 조건 수정, 합성 입력 회귀 검사 8개. 수정 뒤 연구 전체 재평가는 미실시 |
| [TrueFit 인용 검증](https://github.com/wpalswpa/truefit-engineering-evidence) | 모델은 구간 번호를 고르고 서버가 원문 인용을 생성. 범위·입력 타입 검사 11개. 공개 시연은 중단 |
| [LoL 승패 예측](https://github.com/wpalswpa/lol-win-prediction) | 데이터 분할·모델 비교·입력 계약 점검. 공개 검사 25 통과, 원본 데이터가 필요한 재학습 검사 2개 건너뜀 |

Python · TypeScript · OpenAPI · FastAPI · Express · Docker Compose · pytest · Playwright · GitHub Actions

코드와 검사 작성에는 Claude Code·Codex를 사용했습니다. 본인이 정한 문제·기준과 팀원의 구현 범위는 각 저장소의 설계·결정 기록에서 구분했습니다.
