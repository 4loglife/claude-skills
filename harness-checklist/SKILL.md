---
name: harness-checklist
description: Run phase-based checklists from the Learn Harness Engineering course (walkinglabs, 14 lectures) against a real repository or agent session, and report each item as pass/fail/partial with evidence and a concrete fix. Use when the user asks to "check", "audit", or "go through the checklist" for an AI coding agent setup — cold-start/repo readiness, session start, task scoping, done-ness before claiming completion, session-end clean state, loop or graph design, or periodic harness hygiene. Triggers include "하네스 체크리스트", "하네스 점검", "세션 종료 체크", "완료 전에 체크해 줘", "클린 상태 확인", "이 저장소 에이전트가 쓰기 좋은지 봐 줘", "루프 만들기 전에 점검". Prefer harness-creator instead when the user wants files scaffolded or a scored HTML report.
---

# 하네스 체크리스트

[Learn Harness Engineering](https://walkinglabs.github.io/learn-harness-engineering/ko/) 강의 14개의 체크리스트를 **단계별로** 묶어, 실제 저장소나 지금 세션에 대고 하나씩 확인하는 스킬입니다.

핵심 전제(1·2강): 실패하면 모델보다 하네스를 먼저 의심한다. 하네스 = 지시 + 도구 + 환경 + 상태 + 피드백.

## 어떤 체크리스트를 돌릴지 고르기

사용자가 단계를 말하지 않으면 상황으로 고른다. 애매하면 **A(콜드 스타트)** 부터.

| 코드 | 언제 | 출처 강의 |
|---|---|---|
| A. 콜드 스타트 | 저장소가 에이전트가 일하기 좋은 상태인지 처음 볼 때 | 1·2·3·4·6 |
| B. 세션 시작 | 새 세션이 이전 작업을 이어받을 때 | 5·6 |
| C. 작업 시작 | 기능 하나를 시작하기 전 범위·완료 조건 정하기 | 7·8·11 |
| D. 완료 판정 | "다 됐다"고 말하기 직전 | 8·9·10 |
| E. 세션 종료 | 세션을 끝내기 전 클린 상태 확인 | 9·12 |
| F. 루프·그래프 설계 | `/goal`, `/loop`, 메이커-체커, 멀티 에이전트를 만들기 전 | 13·14 |
| G. 정기 감사 | 하네스가 부패하지 않았는지 주기적으로 | 2·4·10·12 |

전체 항목과 판정 기준은 `references/checklists.md`에 있다. 고른 섹션만 읽는다. 작성용 양식(핸드오프, 다음 작업, 스프린트 계약, goal 문서, 기능 목록)은 `references/templates.md`.

## 진행 방법

1. **단계를 정한다.** 사용자가 여러 개를 원하면(예: "D랑 E") 순서대로 돌린다. "전체"면 A → G 순서.
2. **증거를 직접 모은다.** 항목마다 추측하지 말고 확인한다.
   - 파일: `AGENTS.md`, `CLAUDE.md`, `README*`, `docs/`, `PROGRESS.md`·`progress.md`, `feature_list.json`·`features.md`, `init.sh`, `Makefile`, `package.json` scripts, `pyproject.toml`, `.nvmrc`·`.python-version`, CI 설정.
   - 상태: `git status`, `git log --oneline -10`, 디버그 흔적 검색(`console.log`, `debugger`, `print(`, `TODO`, `FIXME`, 임시 파일).
   - 명령: 문서에 적힌 시작·검증 명령을 **실제로 실행해 볼 수 있으면 실행**한다. 오래 걸리거나 부작용(배포, DB 변경, 유료 API 호출)이 있으면 실행하지 말고 "미실행"으로 표시한 뒤 사용자에게 묻는다.
3. **판정한다.** 항목마다 하나:
   - `✅ 통과` — 증거가 있다
   - `❌ 실패` — 없거나 깨졌다
   - `⚠️ 부분` — 있지만 불완전하거나 오래됐다
   - `➖ 해당 없음` — 이 프로젝트에 맞지 않는다(이유 한 줄)
   - `❔ 미확인` — 확인할 수 없었다(이유 한 줄)
   "있어 보인다"는 통과가 아니다(9강: 에이전트는 체계적으로 과신한다). 확인하지 못하면 미확인이다.
4. **고칠 방법을 쓴다.** 실패·부분 항목마다 바로 실행할 수 있는 수정 한 가지(파일 이름, 넣을 내용, 명령)를 적는다. 사용자가 원하면 고친다. 단, 사용자가 "점검만"이라고 했으면 파일을 바꾸지 않는다.
5. **보고한다.** 아래 형식.

## 보고 형식

```
## 하네스 체크리스트: <단계 이름> — <저장소/대상>

요약: ✅ n · ⚠️ n · ❌ n · ❔ n   (가장 먼저 고칠 것: <한 줄>)

| # | 항목 | 판정 | 증거 | 고칠 방법 |
|---|---|---|---|---|
| A1 | 새 세션이 저장소만으로 제품이 뭔지 알 수 있다 | ✅ | README.md 1~5행 | — |
| A5 | 표준 검증 명령이 있다 | ❌ | AGENTS.md·package.json에 없음 | package.json에 "check": "npm run lint && npm test" 추가, AGENTS.md에 한 줄 |

### 우선순위
1. <가장 효과 큰 것 — 보통 피드백(검증 명령) 쪽, 2강>
2. ...
```

- 증거는 `파일:줄` 이나 실행한 명령과 결과 한 줄로 짧게.
- 우선순위는 최대 3개. 2강 기준으로 **검증 명령(피드백 하위 시스템)** 이 대개 투자 대비 효과가 가장 크다.
- D(완료 판정)에서 하나라도 ❌면 결론은 "아직 완료 아님"이다. 돌려 말하지 않는다.
- E(세션 종료)에서 ❌가 남으면 무엇을 고치고 끝낼지, 또는 핸드오프에 무엇을 적을지 제시한다.

## 하지 말 것

- 체크 항목을 늘리려고 규칙을 새로 지어내지 않는다. 출처는 강의 내용이다.
- 진입 파일(AGENTS.md·CLAUDE.md)에 규칙을 계속 덧붙이라고 권하지 않는다. 4강: 진입 파일은 50~200줄짜리 라우터이고, 세부는 주제 문서로 보낸다.
- 사용자를 퀴즈로 몰아붙이지 않는다. 점검하고, 결과와 고칠 방법을 바로 보여 준다.

출처: walkinglabs/learn-harness-engineering (MIT). 강의 본문: https://walkinglabs.github.io/learn-harness-engineering/ko/
