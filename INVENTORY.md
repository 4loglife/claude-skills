# 전체 목록: 스킬 · 플러그인 · MCP · AI 도구

이 저장소에 **파일로 들어 있지 않은 것까지** 모두 정리한 목록입니다. 새 PC에서 같은 환경을 만들 때 위에서부터 차례로 설치하세요. 2026-10-26 기준.

- **✅ 저장소 포함**: 이 저장소 폴더를 `~/.claude/skills/`에 복사하면 끝
- **🔗 원본에서 설치**: 라이선스가 없거나 플러그인·프로그램이라 원본 링크에서 직접 설치

명령은 Git Bash 기준입니다. 플러그인 명령은 Claude Code 안에서 `/plugin ...`으로 실행해도 됩니다.

---

## 1. 개인 스킬 (`~/.claude/skills/`)

| 스킬 | 포함 | 하는 일 | 원본 |
|---|---|---|---|
| anatomy | ✅ | 기술 개념을 인터랙티브 아이소메트릭 SVG로 설명 | [wheresryan22/anatomy](https://github.com/wheresryan22/anatomy) (MIT) |
| tutor · math-tutor · programming-tutor | ✅ | 과외 선생님 (개념은 바로 설명, 문제는 힌트) | [cdmorozov/claude-tutors](https://github.com/cdmorozov/claude-tutors) (MIT) |
| earshot · real-sound | ✅ 스킬 문서만 | 오디오 설명·비교, 영상 사운드트랙 작업. 본체는 아래 3장 | [Leonxlnx/earshot](https://github.com/Leonxlnx/earshot) (MIT) |
| gpt-researcher | ✅ | GPT Researcher 개발용 지식 | [assafelovic/gpt-researcher](https://github.com/assafelovic/gpt-researcher) (Apache-2.0) |
| harness-creator | ✅ | 에이전트 하네스 파일 생성·점수 평가 | [walkinglabs/learn-harness-engineering](https://github.com/walkinglabs/learn-harness-engineering) (MIT) |
| harness-checklist | ✅ | 강의 기반 단계별 하네스 체크리스트 (직접 만듦) | [강의 한국어판](https://walkinglabs.github.io/learn-harness-engineering/ko/) (MIT) |
| xvary-stock-research | ✅ | 미국 주식 `/analyze` `/score` `/compare` | [xvary-research/claude-code-stock-analysis-skill](https://github.com/xvary-research/claude-code-stock-analysis-skill) (MIT) |
| codebase-to-course | 🔗 | 코드베이스를 비개발자용 인터랙티브 강의로 | [zarazhangrui/codebase-to-course](https://github.com/zarazhangrui/codebase-to-course) |
| teach-me | 🔗 | 1:1 AI 튜터 (수준 진단, 질문식 수업) | [claude-code-best/claude-code · teach-me](https://github.com/claude-code-best/claude-code/tree/main/.claude/skills/teach-me) |
| arena | 🔗 | 여러 모델 답을 비교 (Cursor pstack 원본) | [cursor/plugins · pstack/skills/arena](https://github.com/cursor/plugins/tree/main/pstack/skills/arena) |
| reverse-engineer-anything | 🔗 | REA로 바이너리·앱 리버스 엔지니어링 | [morluto/rea](https://github.com/morluto/rea) — 아래 3장 REA 설치 시 함께 생성 |
| ego-browser | 🔗 | 로그인된 브라우저로 웹 작업 자동화 | ego lite 앱 설치·온보딩 시 자동 생성 |
| eli5 | 🔗 | 대상 수준에 맞춰 설명 | 원본 출처 미상 |

```bash
# ✅ 저장소 포함분
git clone https://github.com/4loglife/claude-skills.git ~/claude-skills
mkdir -p ~/.claude/skills && cp -r ~/claude-skills/*/ ~/.claude/skills/

# 🔗 codebase-to-course
git clone --depth 1 https://github.com/zarazhangrui/codebase-to-course.git /tmp/c2c
mkdir -p ~/.claude/skills/codebase-to-course
cp -r /tmp/c2c/SKILL.md /tmp/c2c/references ~/.claude/skills/codebase-to-course/

# 🔗 teach-me
git clone --depth 1 --filter=blob:none --sparse https://github.com/claude-code-best/claude-code.git /tmp/ccb
git -C /tmp/ccb sparse-checkout set .claude/skills/teach-me
cp -r /tmp/ccb/.claude/skills/teach-me ~/.claude/skills/

# 🔗 arena
mkdir -p ~/.claude/skills/arena
curl -sL -o ~/.claude/skills/arena/SKILL.md https://raw.githubusercontent.com/cursor/plugins/main/pstack/skills/arena/SKILL.md
```

---

## 2. 플러그인

### 모든 프로젝트 (user 범위)

| 플러그인 | 하는 일 | 마켓플레이스 저장소 | 설치 |
|---|---|---|---|
| gamedev | Godot·Unity·Unreal·Roblox 등 게임 개발 스킬 90여 개 | [gamedev-skills/awesome-gamedev-agent-skills](https://github.com/gamedev-skills/awesome-gamedev-agent-skills) | `claude plugin marketplace add gamedev-skills/awesome-gamedev-agent-skills` → `claude plugin install gamedev@awesome-gamedev-agent-skills` |
| text-to-cad | 파라메트릭 CAD, STEP/STL/DXF, 3D 프린팅 슬라이스 (MCP 포함) | [earthtojake/text-to-cad](https://github.com/earthtojake/text-to-cad) | `claude plugin marketplace add earthtojake/text-to-cad#latest` → `claude plugin install text-to-cad@earthtojake` → `uvx cadgen telemetry off` |
| imozuru | 모르는 분야를 용어·사람·원문 순으로 파고드는 리서치 | [MaryCache/imozuru](https://github.com/MaryCache/imozuru) | `claude plugin marketplace add MaryCache/imozuru` → `claude plugin install imozuru@imozuru` |
| watch | 영상 URL을 받아 프레임·자막으로 내용 파악 | [bradautomates/claude-video](https://github.com/bradautomates/claude-video) | `claude plugin marketplace add bradautomates/claude-video` → `claude plugin install watch@claude-video` |
| ifixai | AI 진단 도구 | [ifixai-ai/iFixAi](https://github.com/ifixai-ai/iFixAi) | `claude plugin marketplace add ifixai-ai/iFixAi` → `claude plugin install ifixai@ifixai-community` |
| typesafe | 타입이 있는 AI 판단 프리미티브로 기능 만들기 | [typesafe-ai/skills](https://github.com/typesafe-ai/skills) | `claude plugin marketplace add typesafe-ai/skills` → `claude plugin install typesafe@typesafe-ai` |

### 특정 프로젝트에만 설치된 것 (Anthropic 공식 마켓플레이스)

원래 `orca/workspaces/new/master-2` 프로젝트에만 설치돼 있습니다. 새 PC에서는 아래처럼 user 범위로 설치해도 됩니다.

| 플러그인 | 하는 일 | 설치 |
|---|---|---|
| superpowers | 계획·TDD·디버깅 등 작업 방법 스킬 묶음 ([obra/superpowers](https://github.com/obra/superpowers)) | `claude plugin install superpowers@claude-plugins-official --scope user` |
| frontend-design | 프런트엔드 디자인 품질 가이드 | `claude plugin install frontend-design@claude-plugins-official --scope user` |
| code-review | PR 코드 리뷰 | `claude plugin install code-review@claude-plugins-official --scope user` |
| playwright | Playwright 브라우저 자동화 MCP | `claude plugin install playwright@claude-plugins-official --scope user` |

공식 마켓플레이스: [anthropics/claude-plugins-official](https://github.com/anthropics/claude-plugins-official)

---

## 3. MCP 서버 · 따로 설치한 프로그램

| 이름 | 하는 일 | 원본 | 설치 |
|---|---|---|---|
| earshot | 오디오 듣기 MCP (CPU, 모델 약 1.1GB, Python 3.10+, ffmpeg) | [Leonxlnx/earshot](https://github.com/Leonxlnx/earshot) | 아래 명령 |
| REA | 리버스 엔지니어링 MCP + `reverse-engineer-anything` 스킬 (Node.js) | [morluto/rea](https://github.com/morluto/rea) | `npx -y rea-agents@6.5.0 setup --client claude_code --yes` |
| ego lite | `ego-browser` 명령과 스킬을 제공하는 브라우저 앱 | — | 앱 설치 후 온보딩 |

```bash
# earshot
git clone https://github.com/Leonxlnx/earshot ~/tools/earshot
cd ~/tools/earshot
python -m venv .venv
.venv/Scripts/python -m pip install torch --index-url https://download.pytorch.org/whl/cpu
.venv/Scripts/python -m pip install -e ".[mcp,llm]"
.venv/Scripts/python -m earshot doctor --fetch
claude mcp add earshot --scope user -e EARSHOT_THREADS=3 -- "$HOME/tools/earshot/.venv/Scripts/python.exe" -m earshot mcp
```

### claude.ai 계정에 연결된 것

새 PC에서 같은 계정으로 로그인하면 그대로 따라옵니다. 따로 설치할 것 없음.
Gmail · Google Calendar · Google Drive · Claude Docs · higgsfield · Figma · 법률 플러그인(commercial/privacy/ai-governance/corporate/ip/employment-legal, law-student, legal-builder-hub, cocounsel-legal) · PDF.net · 유튜브 · Unity MCP(계정 커넥터)

---

## 4. 참고용 AI 도구 (설치 안 함, 필요할 때 설치)

### AI 리서치 도구 — 출처: [@DivyanshT91162 트윗](https://x.com/DivyanshT91162/status/2112522016012325052)

| 도구 | 하는 일 | 설치 |
|---|---|---|
| [GPT Researcher](https://github.com/assafelovic/gpt-researcher) | 웹·문서를 읽고 출처 달린 보고서 작성 | `pip install gpt-researcher` |
| [Oxylabs Web API MCP](https://github.com/oxylabs/web-api-mcp) | 웹 스크래핑 MCP (유료 키) | `uv tool install git+https://github.com/oxylabs/web-api-mcp` |
| [Haystack](https://github.com/deepset-ai/haystack) | RAG·검색 파이프라인 프레임워크 | `pip install haystack-ai` |
| [Khoj](https://github.com/khoj-ai/khoj) | 내 문서에 질문하는 개인 AI | `pip install 'khoj[local]'` |
| [LlamaIndex](https://github.com/run-llama/llama_index) | 문서를 LLM에 연결하는 데이터 프레임워크 | `pip install llama-index` |
| [RAGFlow](https://github.com/infiniflow/ragflow) | 문서 이해 중심 RAG 엔진 (Docker) | `docker compose up -d` (저장소 `docker/`) |
| [Docling](https://github.com/docling-project/docling) | PDF·Office 문서를 Markdown으로 변환 — **Claude 스킬 포함** | `pip install docling` |
| [Open WebUI](https://github.com/open-webui/open-webui) | 로컬 모델용 ChatGPT식 웹 화면 | `pip install open-webui` |
| [Onyx (Danswer)](https://github.com/onyx-dot-app/onyx) | 사내 문서 검색·챗 (Docker) | `docker compose up -d` |
| [PrivateGPT](https://github.com/zylon-ai/private-gpt) | 완전 오프라인 문서 Q&A | `poetry install --extras "ui llms-ollama ..."` |

### 스스로 개선하는 AI 도구 — 출처: [@Shruti_0810 트윗](https://x.com/Shruti_0810/status/2112459406524960941)

| 도구 | 하는 일 | 설치 |
|---|---|---|
| [SWE-agent](https://github.com/SWE-agent/SWE-agent) | GitHub 이슈를 스스로 고치는 에이전트 | `pip install -e .` |
| [Aider](https://github.com/Aider-AI/aider) | 터미널 AI 페어 프로그래밍 (Ollama 가능) | `pip install aider-install && aider-install` |
| [OpenHands](https://github.com/OpenHands/OpenHands) | 오픈소스 코딩 에이전트 플랫폼 | `uv tool install openhands --python 3.12` |
| [DSPy](https://github.com/stanfordnlp/dspy) | 프롬프트를 자동 최적화하는 프레임워크 | `pip install dspy` |
| [TextGrad](https://github.com/zou-group/textgrad) | 텍스트 피드백으로 "미분"해 개선 | `pip install textgrad` |
| [EvoAgentX](https://github.com/ANative-Lab/EvoAgentX) | 에이전트 워크플로를 진화시킴 | `pip install evoagentx` |
| [ADAS](https://github.com/ShengranHu/ADAS) | 에이전트 설계 자체를 자동 탐색 (연구 코드) | `pip install -r requirements.txt` |
| [OpenEvolve](https://github.com/algorithmicsuperintelligence/openevolve) | AlphaEvolve식 코드 진화 | `pip install openevolve` |
| [SWE-smith](https://github.com/SWE-bench/SWE-smith) | 코딩 에이전트 학습 데이터 생성 | `pip install swesmith` |
| [AutoGPT](https://github.com/Significant-Gravitas/AutoGPT) | 자율 에이전트 플랫폼 (Docker) | `docker compose up -d` (`autogpt_platform/`) |

### 게임 개발

| 도구 | 하는 일 |
|---|---|
| [MCP Unity](https://github.com/CoderGamester/mcp-unity) | Unity 에디터를 MCP로 조작 |
| [Godot MCP](https://github.com/Coding-Solo/godot-mcp) | Godot 실행·디버그 MCP |
| [TripoSR](https://github.com/VAST-AI-Research/TripoSR) | 이미지 한 장으로 3D 모델 |
| [drei](https://github.com/pmndrs/drei) · [react-three-rapier](https://github.com/pmndrs/react-three-rapier) | 웹 3D(React Three Fiber) 도구·물리 |
| [Colyseus](https://github.com/colyseus/colyseus) | 멀티플레이 게임 서버 |

### UI 디자인

| 도구 | 하는 일 |
|---|---|
| [superdesign](https://github.com/superdesigndev/superdesign-skill) | 디자인 에이전트 플러그인 |
| [better-design](https://github.com/marvkr/better-design) | UI 품질 개선 스킬 |
| [design-taste](https://github.com/madebymustafa/design-taste) | 디자인 감각 스킬 묶음 |
| [Canvas UI](https://github.com/DavidHDev/canvas-ui) · [Paper Shaders](https://github.com/paper-design/shaders) · [UI Layouts](https://github.com/ui-layouts/uilayouts) · [Hyperiux](https://github.com/Hyperiux-Immersion-Labs/hyperiux-components) · [Motion Primitives](https://github.com/ibelick/motion-primitives) · [Cursify](https://github.com/ui-layouts/cursify) · [Trickle UI Kit](https://github.com/akaieuan/trickle-UI-kit) | React UI 컴포넌트·셰이더·애니메이션 |

### 리버스 엔지니어링

[Ghidra](https://github.com/NationalSecurityAgency/ghidra) · [JADX](https://github.com/skylot/jadx) · [Frida](https://github.com/frida/frida) · [mitmproxy](https://github.com/mitmproxy/mitmproxy) · [ILSpy](https://github.com/icsharpcode/ILSpy) · [Apktool](https://github.com/iBotPeaches/Apktool) · [Sourcegraph](https://github.com/sourcegraph/sourcegraph) · [Semgrep](https://github.com/semgrep/semgrep) · [Tree-sitter](https://github.com/tree-sitter/tree-sitter) · [Binwalk](https://github.com/ReFirmLabs/binwalk)

### 그 밖에

- [awesome-osint-arsenal](https://github.com/rawfilejson/awesome-osint-arsenal) — OSINT 도구 모음
- [Hugging Face datasets](https://github.com/huggingface/datasets) — `pip install datasets`
- [pstack (cursor/plugins)](https://github.com/cursor/plugins/tree/main/pstack) — Cursor용 플러그인 묶음, 지금은 arena 스킬만 따로 사용

### 받아 둔 학습 자료

- [walkinglabs/learn-harness-engineering](https://github.com/walkinglabs/learn-harness-engineering) — 하네스 엔지니어링 강의 ([한국어판](https://walkinglabs.github.io/learn-harness-engineering/ko/))
- [caramaschiHG/awesome-ai-agents-2026](https://github.com/caramaschiHG/awesome-ai-agents-2026) — AI 에이전트 목록
