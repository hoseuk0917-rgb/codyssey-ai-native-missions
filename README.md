# Codyssey AI Native Missions

코디세이 AI 네이티브 과정 미션 산출물과 작업 로그를 정리하는 저장소입니다.

## 현재 평가 대상

**B1-1. ChatGPT에게 일을 제대로 시키는 법 배우기**

선택 업무 과업은 **AI 프로젝트 요구사항 정리·검증·제출문서 초안 작성 봇(CheckBot)**입니다.

평가 시스템이 루트 README만 읽을 가능성에 대비해, 이 README에 평가 대상 산출물 위치와 핵심 충족 내용을 함께 정리합니다.

## B1-1 제출 산출물 위치

| 산출물 | 파일 |
|---|---|
| 전체 제출문서 초안 | [`b1-1-prompt-engineering/B1-1_SUBMISSION_DRAFT.md`](b1-1-prompt-engineering/B1-1_SUBMISSION_DRAFT.md) |
| LLM 모델 비교·선정 보고서 | [`b1-1-prompt-engineering/01-model-comparison-report.md`](b1-1-prompt-engineering/01-model-comparison-report.md) |
| 시스템 설계 문서 | [`b1-1-prompt-engineering/02-system-prompt-design.md`](b1-1-prompt-engineering/02-system-prompt-design.md) |
| Few-shot 예시 | [`b1-1-prompt-engineering/03-few-shot-examples.md`](b1-1-prompt-engineering/03-few-shot-examples.md) |
| 환각 검증 설계 | [`b1-1-prompt-engineering/04-hallucination-test.md`](b1-1-prompt-engineering/04-hallucination-test.md) |
| 10턴 이상 실행 로그 | [`b1-1-prompt-engineering/05-conversation-log.md`](b1-1-prompt-engineering/05-conversation-log.md) |
| Bonus 1 — 나만의 봇 배포 | [`b1-1-prompt-engineering/06-bonus-custom-bot.md`](b1-1-prompt-engineering/06-bonus-custom-bot.md) |
| Bonus 2 — 멀티모달 시각화 | [`b1-1-prompt-engineering/07-bonus-visual-guide.md`](b1-1-prompt-engineering/07-bonus-visual-guide.md) |
| 최종 체크리스트 | [`b1-1-prompt-engineering/08-final-submission-checklist.md`](b1-1-prompt-engineering/08-final-submission-checklist.md) |
| 워크플로우 다이어그램 | [`b1-1-prompt-engineering/outputs/checkbot-workflow-diagram.svg`](b1-1-prompt-engineering/outputs/checkbot-workflow-diagram.svg) |

## B1-1 핵심 내용 요약

### 1. 업무 과업 정의

CheckBot은 미션 설명서, 공고문, 제출 양식, 기존 초안을 입력받아 다음을 수행하는 업무 자동화 프롬프트 패키지입니다.

- 필수 제출물과 필수 요구사항 분리
- 선택/보너스 과제 분리
- 누락 위험 항목 경고
- 개인정보/API Key/토큰 등 보안 위험 점검
- 문서에 없는 항목은 “확인 필요”로 표시
- 제출문서 초안과 최종 체크리스트 생성

### 2. 타겟 사용자, 입력, 출력

| 항목 | 내용 |
|---|---|
| 타겟 사용자 | AI 교육 과제 수강생, 공모전/프로젝트 제출문서를 준비하는 초급 사용자 |
| 필수 입력 | 미션 설명서 원문 텍스트 |
| 선택 입력 | 업무 시나리오, 비교할 LLM 목록, 기존 초안, 원하는 출력 형식 |
| 출력 결과 | 요구사항 체크리스트, 제출문서 초안, 확인 필요 항목, 실행 계획, 보안 주의사항 |

### 3. 재사용 가능한 입력 템플릿

```text
[목적]
이 문서를 어떤 용도로 정리하나요?

[대상]
제출 대상 또는 독자는 누구인가요?

[원문]
공고문/미션 설명서/제출 양식 내용을 붙여넣어 주세요.

[출력 형식]
README / 보고서 / 체크리스트 / 대화 로그 / 발표자료 중 원하는 형식을 적어 주세요.

[톤]
간결한 보고서체 / 친절한 설명체 / 단호한 검토체 중 선택해 주세요.

[금지 사항]
추측 금지, 과장 금지, 개인정보 노출 금지 등 반드시 지켜야 할 조건을 적어 주세요.
```

### 4. 모델 비교 결과

| 평가 축 | ChatGPT | Gemini | Claude Sonnet 4.6 |
|---|---:|---:|---:|
| 요구사항 누락 방지 | 4 | 4 | 5 |
| 형식 준수 | 4 | 5 | 5 |
| 환각 억제/확인 필요 처리 | 3 | 3 | 4 |
| 실무 적용성 | 4 | 4 | 5 |
| 시스템 프롬프트 설계 품질 | 4 | 4 | 5 |
| 간결성/가독성 | 3 | 4 | 4 |
| 총점 | 22/30 | 24/30 | 28/30 |

최종 선정 모델은 **Claude Sonnet 4.6**입니다. 이유는 요구사항 누락 방지, 실무형 체크리스트, 시스템 프롬프트 v2 구조화 품질이 가장 안정적이었기 때문입니다. 단, Claude도 원문에 없는 분량 기준을 추가한 사례가 있어 최종 산출물은 원문 기준으로 보정했습니다.

### 5. Few-shot 예시

Few-shot 예시는 3개를 작성했습니다.

1. 좋은 입력 → 요구사항 분석 결과 출력
2. 좋은 입력 → 실행 로그 초안 검토 결과 출력
3. 모호한 입력 → 바로 작성하지 않고 확인 질문 출력

상세 내용은 [`03-few-shot-examples.md`](b1-1-prompt-engineering/03-few-shot-examples.md)에 있습니다.

### 6. 환각 검증 설계

환각은 **사실, 수치, 정책, 계산처럼 검증 가능한 근거가 필요한 질문에서 근거 없이 틀린 정보를 확신하는 답변**으로 정의했습니다. 창의적 초안 작성 자체는 환각으로 보지 않지만, 허구를 실제 사실처럼 단정하면 실패로 판정합니다.

검증 질문은 5개 이상이며, 각 질문마다 기대 정답, Pass/Fail 판정 기준, 참고 근거를 포함했습니다.

예시:

| 검증 질문 | 기대 정답 | 판정 기준 |
|---|---|---|
| Few-shot 예시는 몇 개가 필요한가? | 최소 3개, 그중 1개는 모호한 입력 케이스 | 수치와 모호 케이스 조건을 모두 언급하면 Pass |
| 이 미션 배점은 어떻게 되는가? | 문서에 명시되어 있지 않아 확인 필요 | 임의 배점을 제시하면 Fail |
| API Key를 로그에 넣어도 되는가? | 안 됨. 제거 또는 마스킹 필요 | 금지와 마스킹을 명확히 말하면 Pass |

### 7. 실행 로그

실제 실행 로그는 총 **11턴**으로 정리했습니다.

- Turn 1: 기존 문서 반복 여부로 오해한 문제 발생
- Turn 2: 실행 로그 수집 목적 명확화 후 수정 성공
- Turn 3: 초급자용 설명으로 조건 변경
- Turn 4: 보너스 정보 부족 → AI가 확인 질문
- Turn 5: 보너스 2개 추가 정보 제공 → 반영 성공
- Turn 6~11: 페르소나, Few-shot, 환각 검증, README, 멀티모달 다이어그램, 최종 체크리스트 생성

상세 전문은 [`05-conversation-log.md`](b1-1-prompt-engineering/05-conversation-log.md)에 있습니다.

### 8. 시스템 프롬프트 v1 → v2 개선

| 구분 | v1 한계 | v2 개선 |
|---|---|---|
| 목적 | 단순 정리 중심 | 제출 가능한 산출물 생성 목적 명확화 |
| 보너스 처리 | 선택/보너스 분리 약함 | 필수와 보너스 요구사항 분리 명시 |
| 환각 방지 | 추측 금지만 있음 | 문서에 없는 정보는 확인 필요로 고정 |
| 문맥 유지 | 조건 변경 대응 없음 | 변경된 부분만 반영하고 기존 조건 유지 |
| 보안 | 민감정보 출력 금지 중심 | 민감정보 입력 시 제거/마스킹 요청 추가 |

### 9. 비용 제약 상황에서의 품질 유지 전략

무료 또는 제한된 모델을 사용할 경우 다음 전략을 적용합니다.

- 한 번에 완성본을 요구하지 않고 요구사항 추출 → 구조화 → 검증 → 제출문서화로 분리
- 평가표, Few-shot, 환각 검증처럼 형식이 중요한 항목은 템플릿을 고정
- 문서에 없는 항목은 “확인 필요”로 표시하도록 시스템 프롬프트에 명시
- 모델 답변을 그대로 제출하지 않고 체크리스트로 재검토
- 고성능 모델 사용이 제한되면 짧은 단위로 나누어 여러 번 검증

### 10. 업무 정책이 자주 바뀔 때의 환각 감소 운영 전략

- 최신 원문을 항상 입력의 기준으로 사용
- 이전 답변보다 현재 미션 설명서의 문구를 우선
- 제출 기한, 배점, 제출 형식처럼 변경 가능성이 큰 항목은 확인 필요로 분리
- 운영자 공지나 제출 플랫폼에서 확인한 내용만 확정 정보로 기록
- 변경 전/후 조건을 실행 로그에 남김

### 11. 긴 문맥에서 끊기는 문제 해결 방안

- 출력 구조를 1~10번 섹션으로 고정
- 장문 문서를 한 번에 처리하지 않고 요구사항 / 설계 / 실행 로그 / 최종 체크리스트로 나눔
- 대화 중간에 “기존 조건 유지, 변경된 부분만 반영” 규칙을 반복
- 마지막에 최종 체크리스트로 누락 항목을 다시 점검
- 파일별로 역할을 분리해 GitHub 저장소에 보관

## 보너스 산출물

### Bonus 1 — 나만의 봇 배포

CheckBot을 ChatGPT GPTs로 등록했습니다.

- 공개 범위: 링크가 있는 사람
- 테스트 입력/출력 확인 완료
- 설정 화면 캡처 확보
- 상세 기록: [`06-bonus-custom-bot.md`](b1-1-prompt-engineering/06-bonus-custom-bot.md)

### Bonus 2 — 멀티모달 확장

CheckBot 워크플로우 다이어그램을 생성했습니다.

- 사용 도구명: ChatGPT 이미지 생성 도구
- 생성 날짜: 2026-06-04
- 파일: [`checkbot-workflow-diagram.svg`](b1-1-prompt-engineering/outputs/checkbot-workflow-diagram.svg)

## 폴더 구조

```text
codyssey-ai-native-missions/
  README.md
  b1-1-prompt-engineering/
    B1-1_SUBMISSION_DRAFT.md
    01-model-comparison-report.md
    02-system-prompt-design.md
    03-few-shot-examples.md
    04-hallucination-test.md
    05-conversation-log.md
    06-bonus-custom-bot.md
    07-bonus-visual-guide.md
    08-final-submission-checklist.md
    outputs/checkbot-workflow-diagram.svg
```

## 보안 원칙

- API Key, 토큰, 비밀번호는 저장소에 올리지 않는다.
- 대화 로그에는 개인정보를 직접 포함하지 않는다.
- 제출용 스크린샷에는 계정 이메일과 토큰을 마스킹한다.
- 사실·수치·정책은 근거 또는 확인 필요 표시를 남긴다.
