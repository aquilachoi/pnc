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
npx skills add <owner/repo> -a "*" -y

# 기존 프로젝트 복원 (skills-lock.json 있을 때)
npx skills experimental_install
```

---

## 에이전트별 설정 방법

#### Claude Code

```bash
npx skills add <owner/repo> -a claude
```

`.claude/skills/`에 symlink 생성. Claude Code에서 `/skill-name` 형태로 호출.

#### Gemini CLI

Gemini CLI는 `.agents/skills/`를 직접 읽으므로 별도 설정 불필요.

```bash
npx skills add <owner/repo> -a gemini-cli
```

#### Codex CLI

Codex CLI도 `.agents/skills/`를 직접 읽으므로 별도 설정 불필요.

```bash
npx skills add <owner/repo> -a codex
```

#### Hermes Agent

```bash
npx skills add <owner/repo> -a hermes-agent
```

`.hermes/skills/` → `.agents/skills/` symlink 생성.

---

## 스킬 목록

## 1. mattpocock/skills

**소스:** `github.com/mattpocock/skills`

### 설치 방법

```bash
npx skills add mattpocock/skills -a "*" -y
```

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

```
/setup-matt-pocock-skills
```

이슈 트래커(GitHub/GitLab/로컬 markdown), 트리아지 라벨, 도메인 문서 경로 설정.

---

## 2. JuliusBrussee/caveman

**소스:** `github.com/JuliusBrussee/caveman`

### 설치 방법

```bash
npx skills add JuliusBrussee/caveman -a "*" -y
```

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

---

## 3. imxv/pretty-mermaid-skills

**소스:** `github.com/imxv/pretty-mermaid-skills`

### 설치 방법

```bash
npx skills add imxv/pretty-mermaid-skills -a "*" -y
```

### 설치되는 스킬 목록

| 스킬 | 설명 |
|------|------|
| `pretty-mermaid` | Mermaid 다이어그램을 시각적으로 보기 좋게 생성/개선 |

---

## 4. obra/superpowers

**소스:** `github.com/obra/superpowers`

### 설치 방법

```bash
npx skills add obra/superpowers -a "*" -y
```

### 설치되는 스킬 목록

| 스킬 | 설명 |
|------|------|
| `brainstorming` | 아이디어 브레인스토밍 |
| `using-superpowers` | superpowers 스킬 활용 가이드 |
| `systematic-debugging` | 체계적 디버깅 방법론 |
| `writing-plans` | 구현 플랜 작성 |
| `requesting-code-review` | 코드 리뷰 요청 방법 |
| `receiving-code-review` | 코드 리뷰 수신 및 처리 |
| `test-driven-development` | TDD 방법론 |
| `dispatching-parallel-agents` | 병렬 에이전트 디스패치 |
| `executing-plans` | 플랜 실행 |
| `finishing-a-development-branch` | 개발 브랜치 완료 절차 |
| `subagent-driven-development` | 서브에이전트 기반 개발 |
| `using-git-worktrees` | git worktree 활용 |
| `verification-before-completion` | 완료 전 검증 절차 |
| `writing-skills` | 문서/코드 작성 스킬 |

---

## 5. safishamsi/graphify

**소스:** `github.com/safishamsi/graphify`

### 설치 방법

```bash
npx skills add safishamsi/graphify -a "*" -y
```

### 설치되는 스킬 목록

| 스킬 | 설명 |
|------|------|
| `graphify` | 데이터/개념을 그래프/다이어그램으로 시각화 |

---

## 6. garrytan/gstack

**소스:** `github.com/garrytan/gstack`

### 사전 요건

```bash
brew install oven-sh/bun/bun   # bun 런타임 필요
```

### 설치 방법

gstack은 절대경로 symlink를 사용하므로 **글로벌(user-level)** 에 설치. 프로젝트 repo에 커밋하지 않음.

```bash
git clone --single-branch --depth 1 https://github.com/garrytan/gstack.git \
  ~/.claude/skills/gstack

cd ~/.claude/skills/gstack && ./setup
```

> 설치 위치: `~/.claude/skills/gstack` → 모든 프로젝트에서 자동 사용 가능.  
> Codex CLI / Gemini CLI / Hermes Agent는 별도 설정 불필요 (Claude Code global skill 공유).

### 주요 스킬 목록

| 스킬 | 설명 |
|------|------|
| `gstack` | 메인 진입점. 헤드리스 브라우저 QA/테스트 |
| `browse` | 페이지 탐색, 스크린샷, 요소 상호작용 |
| `qa` | 전체 QA 플로우 (탐색 → 검증 → 버그 리포트) |
| `qa-only` | 브라우저 없이 코드 기반 QA |
| `scrape` | 웹 스크래핑 |
| `design-html` | 디자인 → 프로덕션 HTML/CSS 생성 |
| `design-shotgun` | 여러 UI 변형 동시 생성 |
| `design-review` | 디자인 리뷰 |
| `review` | 코드 리뷰 |
| `investigate` | 버그/이슈 조사 |
| `ship` | 배포 플로우 |
| `health` | 사이트 헬스 체크 |
| `benchmark` | 성능 측정 (Core Web Vitals 등) |
| `ios-qa` / `ios-fix` | iOS 앱 QA/수정 |

### 업그레이드

```bash
/gstack-upgrade
```
