# 07. Bonus 2 — 멀티모달 확장 시각 자료 가이드

## 목적

B1-1 보너스 과제 2번인 “멀티모달 확장(업무 결과의 시각화)”을 수행하기 위한 문서입니다.

CheckBot이 생성한 요구사항 분석 흐름을 이미지 생성 AI로 시각화하여, 제출문서에 첨부할 워크플로우 다이어그램 1장을 제작합니다.

---

## 시각 자료 대상

**CheckBot 워크플로우 다이어그램**

사용자가 미션 설명서를 입력하면 보안 검사, 요구사항 분석, 누락 위험 검사, 확인 필요 항목 추출, 제출문서 초안 생성까지 이어지는 흐름을 한 장의 다이어그램으로 표현합니다.

---

## 다이어그램 구조 설명

```text
[시작]
  │
  ▼
[입력 단계]
  사용자가 미션 설명서 텍스트를 붙여넣기
  │
  ▼
[보안 검사]
  개인정보 / API Key / 토큰 포함 여부 확인
  │
  ├─ 감지됨 ──▶ [경고 출력] "해당 정보를 제거 후 재입력하세요" ──▶ [입력 단계로 복귀]
  │
  └─ 이상 없음
        │
        ▼
[요구사항 분석]
  필수 / 선택 / 제약 / 보안 항목 분류
        │
        ▼
[누락 위험 항목 검사]
  ⚠️ 위험도 높은 항목 강조 출력
        │
        ▼
[확인 필요 항목 추출]
  문서에 없는 내용 → "확인 필요" 목록 생성
        │
        ▼
[체크리스트 완료 여부 판단]
  │
  ├─ 미완료 ──▶ [사용자에게 보완 요청] ──▶ [요구사항 분석으로 복귀]
  │
  └─ 완료
        │
        ▼
[제출문서 초안 생성]
  ① LLM 비교 보고서 템플릿
  ② 시스템 설계 문서 템플릿
  ③ 실행 로그 템플릿
        │
        ▼
[최종 출력]
  체크리스트 + 초안 3종 + 확인 필요 목록
        │
        ▼
[종료]
```

---

## 이미지 생성 AI 입력 프롬프트

```text
A clean flowchart diagram showing the CheckBot workflow.
Start → Input (paste mission document) → Security Check
(personal info / API Key detection) → if detected: warning
and return to input / if clean: Requirement Analysis
(classify mandatory / optional / constraint / security)
→ Risk Item Alert → Confirm Needed List → Completeness Check
→ if incomplete: request revision / if complete:
Generate Draft Documents (3 types) → Final Output → End.
Use simple shapes, arrows, and Korean labels.
Minimal style, white background.
```

---

## 한국어 라벨 권장안

| 단계 | 라벨 |
|---|---|
| Start | 시작 |
| Input | 미션 설명서 입력 |
| Security Check | 보안 검사 |
| Warning | 민감정보 제거 요청 |
| Requirement Analysis | 요구사항 분석 |
| Risk Item Alert | 누락 위험 경고 |
| Confirm Needed List | 확인 필요 항목 |
| Completeness Check | 체크리스트 완료 확인 |
| Generate Draft Documents | 제출문서 초안 생성 |
| Final Output | 최종 출력 |
| End | 종료 |

---

## 제출 시 기록할 항목

| 항목 | 기록 |
|---|---|
| 사용 도구명 | 확인 필요 |
| 생성 날짜 | 확인 필요 |
| 이미지 파일명 | outputs/checkbot-workflow-diagram.png 예정 |
| 입력 프롬프트 | 본 문서의 이미지 생성 AI 입력 프롬프트 사용 |
| 개인정보 포함 여부 | 없음 |

---

## 산출물 저장 위치

```text
b1-1-prompt-engineering/outputs/checkbot-workflow-diagram.png
```

실제 이미지를 GitHub에 올릴 경우, 개인정보나 계정정보가 포함되지 않았는지 확인한 뒤 업로드합니다.
