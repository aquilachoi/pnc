# 설치된 Skills

## 에이전트별 지원 현황

모든 스킬 원본은 `.agents/skills/`에 저장. Codex/Gemini CLI는 이 디렉터리를 직접 읽음. Claude Code/Hermes는 별도 symlink 디렉터리 사용.

| 에이전트 | Project skillsDir | 방식 |
|---------|------------------|------|
| Claude Code | `.claude/skills/` | symlink → `.agents/skills/` |
| Hermes Agent | `.hermes/skills/` | symlink → `.agents/skills/` |
| Codex CLI | `.agents/skills/` | 직접 읽기 (별도 디렉터리 불필요) |
| Gemini CLI | `.agents/skills/` | 직접 읽기 (별도 디렉터리 불필요) |
| GitHub Copilot | `.agents/skills/` | 직접 읽기 |

---

## 설치 방법

### 사전 조건

```bash
# Node.js 필요 (npx 사용)
node --version   # v18 이상 권장
```

### 기본 설치 명령

```bash
# 설치된 에이전트 자동 감지 후 모두에 설치
npx skills add mattpocock/skills
npx skills add JuliusBrussee/caveman

# 특정 에이전트만 지정해 설치
npx skills add mattpocock/skills -a claude
npx skills add mattpocock/skills -a gemini
npx skills add mattpocock/skills -a codex
npx skills add mattpocock/skills -a hermes

# 모든 에이전트에 강제 설치
npx skills add mattpocock/skills -a "*"
```

### 기존 프로젝트 복원 (skills-lock.json 있을 때)

```bash
# skills-lock.json 기반으로 동일 버전 복원
npx skills experimental_install
```

---

## 에이전트별 설정 방법

#### Claude Code

```bash
npx skills add mattpocock/skills -a claude
npx skills add JuliusBrussee/caveman -a claude
```

`.claude/skills/`에 symlink 생성. Claude Code에서 `/skill-name` 형태로 호출.

#### Gemini CLI

Gemini CLI는 `.agents/skills/`를 직접 읽으므로 별도 설정 불필요.  
`gemini` 바이너리가 PATH에 있으면 `npx skills add` 시 자동 감지.

```bash
npx skills add mattpocock/skills -a gemini-cli
npx skills add JuliusBrussee/caveman -a gemini-cli
```

#### Codex CLI

Codex CLI도 `.agents/skills/`를 직접 읽으므로 별도 설정 불필요.  
`codex` 바이너리 또는 `~/.codex` 디렉터리 존재 시 자동 감지.

```bash
npx skills add mattpocock/skills -a codex
npx skills add JuliusBrussee/caveman -a codex
```

#### Hermes Agent

```bash
npx skills add mattpocock/skills -a hermes-agent
npx skills add JuliusBrussee/caveman -a hermes-agent
```

`.hermes/skills/` → `.agents/skills/` symlink 생성. 현재 프로젝트에 이미 설정됨.

---

## 1. mattpocock/skills

**소스:** `github.com/mattpocock/skills`

### 설치되는 스킬 목록

| 스킬 | 설명 |
|------|------|
| `diagnose` | 버그/성능 이슈 단계별 진단 루프 |
| `grill-me` | 플랜/디자인 인터뷰 방식 스트레스 테스트 |
| `grill-with-docs` | CONTEXT.md, ADR 기반 플랜 검증 |
| `handoff` | 대화 내용을 다른 에이전트용 handoff 문서로 압축 |
| `improve-codebase-architecture` | 코드베이스 아키텍처 개선 기회 탐색 |
| `prototype` | 터미널 앱 또는 UI 변형 프로토타입 생성 |
| `setup-matt-pocock-skills` | 이 스킬 모음 초기 설정 (이슈 트래커, 라벨 등) |
| `tdd` | TDD 방식 구현 |
| `to-issues` | 플랜/스펙을 GitHub 이슈로 분해 |
| `to-prd` | 요구사항을 PRD로 변환 |
| `triage` | 이슈 트리아지 state machine |
| `write-a-skill` | 새 skill 작성 |
| `zoom-out` | 현재 작업의 더 큰 맥락 파악 |

### 초기 설정 (최초 1회)

설치 후 프로젝트별 설정 필요:

```
/setup-matt-pocock-skills
```

이슈 트래커(GitHub/GitLab/로컬 markdown), 트리아지 라벨, 도메인 문서 경로 설정.

---

## 2. JuliusBrussee/caveman

**소스:** `github.com/JuliusBrussee/caveman`

### 설치되는 스킬 목록

| 스킬 | 설명 |
|------|------|
| `caveman` | 토큰 ~75% 절감 압축 통신 모드. 6단계 intensity 지원 |
| `cavecrew` | 전문화된 서브에이전트 팀 오케스트레이션 |
| `caveman-commit` | 압축 스타일 git 커밋 메시지 생성 |
| `caveman-compress` | CLAUDE.md 등 메모리 파일을 caveman 포맷으로 압축 |
| `caveman-help` | caveman 모드/커맨드 퀵 레퍼런스 |
| `caveman-review` | 초압축 코드 리뷰 코멘트 생성 |
| `caveman-stats` | 세션 토큰 절감 통계 확인 |

### 사용 방법

```
/caveman          # full 모드 활성화 (기본)
/caveman lite     # 라이트 모드 (문장 유지, filler만 제거)
/caveman ultra    # 최대 압축 (약어, 화살표 표기)
/caveman wenyan-full  # 문언문 스타일 최대 압축
stop caveman      # 일반 모드 복귀
```

### Intensity 레벨

| 레벨 | 토큰 절감 | 특징 |
|------|---------|------|
| lite | ~20-30% | filler 제거, 문장 구조 유지 |
| full | ~50-60% | 관사 제거, 단편 OK (기본값) |
| ultra | ~70-75% | 약어, 화살표 인과관계 표기 |
| wenyan-full | ~80-90% | 문언문 최대 압축 |
