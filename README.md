# claude-skills

Claude Code 개인 스킬 모음입니다. 폴더 하나가 스킬 하나이고, `~/.claude/skills/` 아래에 두면 Claude Code가 인식합니다.

플러그인 14개(blender-skills, last30days, 직접 만든 mod 포함), MCP 서버, 참고용 AI 도구까지 포함한 **전체 목록과 설치 링크는 [INVENTORY.md](INVENTORY.md)** 에 있습니다.

## 새 PC에 설치

```bash
git clone https://github.com/4loglife/claude-skills.git ~/claude-skills
mkdir -p ~/.claude/skills
cp -r ~/claude-skills/*/ ~/.claude/skills/
```

업데이트는 `cd ~/claude-skills && git pull` 후 다시 복사합니다. 설치 후 Claude Code를 새로 시작해야 보입니다.

## 스킬 목록

| 스킬 | 하는 일 | 원본 | 라이선스 |
|---|---|---|---|
| anatomy | 기술 개념을 인터랙티브 아이소메트릭 SVG 그림으로 설명 | [wheresryan22/anatomy](https://github.com/wheresryan22/anatomy) | MIT |
| tutor | 과목 공통 과외 선생님 (개념은 바로 설명, 문제는 힌트로 유도) | [cdmorozov/claude-tutors](https://github.com/cdmorozov/claude-tutors) | MIT |
| math-tutor | 수학 과외 | [cdmorozov/claude-tutors](https://github.com/cdmorozov/claude-tutors) | MIT |
| programming-tutor | 프로그래밍 과외 | [cdmorozov/claude-tutors](https://github.com/cdmorozov/claude-tutors) | MIT |
| earshot | 오디오를 설명·비교·검사 (MCP 서버 설치 필요) | [Leonxlnx/earshot](https://github.com/Leonxlnx/earshot) | MIT |
| real-sound | 영상에 실제 녹음으로 사운드트랙 입히기 | [Leonxlnx/earshot](https://github.com/Leonxlnx/earshot) | MIT |
| gpt-researcher | GPT Researcher 코드 개발용 지식 | [assafelovic/gpt-researcher](https://github.com/assafelovic/gpt-researcher) | Apache-2.0 |
| harness-creator | AGENTS.md·CLAUDE.md 등 에이전트 하네스 생성·점검 | [walkinglabs/learn-harness-engineering](https://github.com/walkinglabs/learn-harness-engineering) | MIT |
| harness-checklist | Learn Harness Engineering 강의 기반 단계별 하네스 체크리스트 (직접 만듦) | [walkinglabs/learn-harness-engineering](https://walkinglabs.github.io/learn-harness-engineering/ko/) | MIT |
| vibe-trading | 금융 리서치 툴킷 스킬 (MCP 본체는 `uv tool install vibe-trading-ai`) | [HKUDS/Vibe-Trading](https://github.com/HKUDS/Vibe-Trading) | MIT |
| xvary-stock-research | 미국 주식 `/analyze`, `/score`, `/compare` (SEC EDGAR) | [xvary-research/claude-code-stock-analysis-skill](https://github.com/xvary-research/claude-code-stock-analysis-skill) | MIT |

각 폴더에 원본 라이선스 파일을 그대로 넣었습니다. 준비물:
- earshot: Python 3.10+, ffmpeg와 MCP 서버 설치가 필요합니다. 원본 저장소 안내를 따르세요.
- anatomy, harness-creator: Node.js가 필요합니다.
- xvary-stock-research: Python 3.10+와 `requests`가 필요합니다.

## 여기 없는 스킬

라이선스가 명시되지 않은 스킬은 공개 저장소에 다시 올리지 않았습니다. 원본에서 직접 설치하세요.

- codebase-to-course — [zarazhangrui/codebase-to-course](https://github.com/zarazhangrui/codebase-to-course)
- arena — [cursor/plugins · pstack/skills/arena](https://github.com/cursor/plugins/tree/main/pstack/skills/arena)
- teach-me, eli5, reverse-engineer-anything
