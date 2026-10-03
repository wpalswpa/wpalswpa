# 이제민

**LLM 응용 · 개발 도구 · 모델 평가**

AI 기능과 개발 도구를 만들고, 입력·출력과 실패 처리 규칙을 코드로 확인합니다.
아래 프로젝트에 직접 맡은 일과 설계 판단, 다시 실행할 수 있는 근거를 정리했습니다.

## 대표 프로젝트

### 01 · [TrueFit](https://github.com/wpalswpa/truefit-engineering-evidence)
**계약서의 근거 문장을 모델이 만들어 내지 않도록**

LLM에는 쟁점 분류와 문장 구간 선택을 맡기고, 서버가 원문에서 인용문을 추출하도록 설계했습니다. 응답 형식과 구간을 검사하며, 올바른 쟁점을 골랐는지는 별도 평가 대상으로 남겼습니다.

`Python` `Flask` `구조화 출력` · 3인 팀의 제품 설계·AI 연동·서버 검증 담당. 공개 코드는 검증 규칙의 최소 재현입니다.

[설계 판단](https://github.com/wpalswpa/truefit-engineering-evidence/blob/main/docs/decisions/001-source-span-extraction.md) · [검증 코드](https://github.com/wpalswpa/truefit-engineering-evidence/blob/main/validator.py) · [실행 방법](https://github.com/wpalswpa/truefit-engineering-evidence#바로-실행)

### 02 · [AI 의논 도구](https://github.com/wpalswpa/ai-talk-harness-evidence)
**여러 LLM의 판정과 실패를 추적하고, 자동화할 범위를 결정**

CLI 실패 메시지가 발언으로 저장되는 파서 경로를 고쳤습니다. 중단 시점 학습 모델은 비교 실험에서 상수 예측을 넘지 못해 운영 도입을 보류했습니다.

`Python` `CLI 프로세스 연동` `SQLite` · 개인 도구의 설계·계측·검증. 공개 범위는 핵심 모듈과 검사이며 서버·실제 대화 기록은 제외했습니다.

[실패 분석](https://github.com/wpalswpa/ai-talk-harness-evidence/blob/main/docs/decisions/001-failure-banner-contamination.md) · [도입 보류 판단](https://github.com/wpalswpa/ai-talk-harness-evidence/blob/main/docs/decisions/002-stop-automation-no-go.md) · [호출 코드](https://github.com/wpalswpa/ai-talk-harness-evidence/blob/main/talk/bridge.py)

### 03 · [우리 아이 미술관](https://github.com/wpalswpa/kids-art-museum-serving-evidence)
**모델의 품질 미달과 서버 장애에 서로 다른 처리 규칙 적용**

화면·API·모델 워커 사이의 계약을 맡았습니다. 품질 미달은 더 단순한 결과 형식으로 전환하고, 인프라 장애는 같은 단계에서 재시도하도록 구분해 통합 시험에서 확인했습니다.

`TypeScript` `Express` `OpenAPI` `MariaDB` · 4인 팀의 API·작업 처리·계약 검사 설정 담당. 모델·보호자 화면은 팀원 담당이며, 공개 코드는 처리 규칙의 최소 재현입니다.

[처리 규칙과 대안](https://github.com/wpalswpa/kids-art-museum-serving-evidence/blob/main/docs/decisions/002-downgrade-vs-retry.md) · [규칙 코드](https://github.com/wpalswpa/kids-art-museum-serving-evidence/blob/main/fallback.py) · [통합 시험 기록](https://github.com/wpalswpa/kids-art-museum-serving-evidence/blob/main/evidence/README.md)

### 04 · [LoL 승패 예측](https://github.com/wpalswpa/lol-win-prediction)
**승률뿐 아니라 예측 근거와 틀리는 조건까지 확인**

경기 초반 지표로 모델을 비교하고, 직관과 반대인 계수의 부호를 지표 제거 실험으로 점검했습니다. 경기 유형별 오차와 서비스 입력 계약을 함께 정리했습니다. 지표의 상관관계를 인과효과로 해석하지 않습니다.

`Python` `scikit-learn` `Flask` · 4인 팀의 분석·모델링·검증과 후속 서비스 기능 담당.

[실험 보고](https://github.com/wpalswpa/lol-win-prediction/blob/main/docs/experiment_report.md) · [서빙 계약](https://github.com/wpalswpa/lol-win-prediction/blob/main/docs/serving.md) · [재현 순서](https://github.com/wpalswpa/lol-win-prediction/blob/main/docs/REPRODUCE.md)

### 05 · [PassFinder](https://github.com/wpalswpa/AltTab)
**교안 PDF에서 문제를 만들어 풀고 복습하는 학습 서비스**

Vercel의 읽기 전용 파일 경로 때문에 발생한 첫 화면 오류를 수정하고, 개인 AI 설정 없이 교안으로 문제를 만드는 흐름을 설계·구현했습니다. 제출 범위와 후속 v2를 구분해 화면을 보존했습니다.

`JavaScript` `Express` `Vercel` · 5인 팀의 배포 장애 대응·교안 기반 생성·검증 담당. 저장소는 팀 프로젝트의 보존본입니다.

[배포 장애 수정 PR](https://github.com/Snow0821/AltTab/pull/8) · [생성 코드](https://github.com/wpalswpa/AltTab/blob/main/ai-generate.js) · [배포 화면 기록](https://github.com/wpalswpa/AltTab#화면-기록)

### 06 · [상담 음성 전사·LLM 분류 평가](https://github.com/wpalswpa/stt-llm-depression-screening)
**빈 전사가 평가에서 사라지는 오류 수정**

Whisper 전사와 LLM 분류를 비교하고, 후속 점검에서 빈 전사가 평균 오류율에서 누락되는 평가 코드를 고쳤습니다. 합성 입력으로 처리 규칙을 확인했으며, 전체 음성 재평가나 임상 검증 결과는 아닙니다.

`Python` `Whisper` `LLM 평가` · 전사·분류 비교 연구와 후속 평가 코드 점검.

[평가 코드](https://github.com/wpalswpa/stt-llm-depression-screening/blob/main/evaluation.py) · [회귀 검사](https://github.com/wpalswpa/stt-llm-depression-screening/blob/main/tests/test_evaluation.py) · [연구 범위](https://github.com/wpalswpa/stt-llm-depression-screening#문제와-접근)

## 화면으로 보기

<table>
<tr>
<td width="50%" valign="top">
<a href="https://github.com/wpalswpa/kids-art-museum-serving-evidence"><img src="https://raw.githubusercontent.com/wpalswpa/kids-art-museum-serving-evidence/main/evidence/sample-museum.jpg" alt="우리 아이 미술관 팀 서비스의 견본 전시실" width="420"></a><br>
<strong>우리 아이 미술관</strong><br>
팀 서비스의 견본 전시실. 제 담당은 API·작업 처리입니다.
</td>
<td width="50%" valign="top">
<a href="https://github.com/wpalswpa/AltTab#화면-기록"><img src="https://raw.githubusercontent.com/wpalswpa/AltTab/f49a1e153b99852be63b7af395f5e6a63dcad2bd/docs/screenshots/v2-list.png" alt="PassFinder 후속 v2의 배포 시험 목록" width="420"></a><br>
<strong>PassFinder</strong><br>
후속 v2 팀 서비스 화면. 저장소에서 제출 당시 화면도 볼 수 있습니다.
</td>
</tr>
</table>

## 사용한 기술

- **API·데이터:** Python, TypeScript, SQL, Express, Flask, FastAPI, SQLite, MariaDB
- **모델·평가:** scikit-learn, pandas, Whisper, 구조화 출력, 원문 인용 검증
- **검사·자동화:** pytest, unittest, Vitest, Playwright, GitHub Actions, GitLab CI 설정

프로젝트의 코드·검사 작성에는 AI 코딩 도구를 활용했습니다. 문제 정의·설계 판단·검증과 팀원 담당 범위는 각 저장소에서 구분해 설명합니다.

<details>
<summary>이전 분석·학습 프로젝트</summary>

- [활동·수면 지표의 위험군 분류](https://github.com/wpalswpa/dementia-screening): 4인 팀장, 데이터 누수 점검과 FastAPI 프로토타입. 임상 검증을 수행한 서비스는 아닙니다.
- [얼굴 이미지 분류와 편향 점검](https://github.com/wpalswpa/stroke-facial-asymmetry-screening): 개인 전이학습 실습. 이미지 출처 차이와 검증 한계를 함께 기록했습니다.

</details>
