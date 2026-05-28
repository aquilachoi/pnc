# Roo Code 스킬 모드 설정

이 폴더는 `.agents/skills/`의 스킬들을 Roo Code Custom Modes로 변환한 파일을 포함합니다.

## 설치 방법

### 프로젝트 레벨 적용 (이 프로젝트에만)

```bash
cp roocode/.roomodes ./.roomodes
```

### 글로벌 적용 (모든 프로젝트)

Roo Code VSCode 확장에서:
1. `Cmd+Shift+P` → `Roo Code: Open Global Modes`
2. `roocode/.roomodes` 파일의 `customModes` 배열 내용을 붙여넣기

또는 Roo Code 설정 파일에 직접 병합:
```bash
# 글로벌 설정 위치 (예시)
~/.vscode/extensions/roo-code/modes.json
```

## 포함된 모드 (32개)

| 슬러그 | 이름 | 용도 |
|--------|------|------|
| `brainstorming` | Brainstorming | 구현 전 설계 및 스펙 작성 |
| `cavecrew` | Cavecrew | 압축된 서브에이전트 위임 |
| `caveman` | Caveman | 토큰 절약 ~75% 압축 통신 |
| `caveman-commit` | Caveman Commit | Conventional Commits 형식 커밋 메시지 |
| `caveman-compress` | Caveman Compress | 메모리 파일 압축 |
| `caveman-help` | Caveman Help | 캐이브맨 명령어 레퍼런스 |
| `caveman-review` | Caveman Review | 한 줄 PR 리뷰 코멘트 |
| `diagnose` | Diagnose | 체계적 버그 진단 루프 |
| `dispatching-parallel-agents` | Dispatching Parallel Agents | 독립 작업 병렬 에이전트 위임 |
| `executing-plans` | Executing Plans | 구현 계획 실행 |
| `finishing-a-development-branch` | Finishing a Development Branch | 브랜치 완료 (merge/PR/discard) |
| `grill-me` | Grill Me | 설계 스트레스 테스트 인터뷰 |
| `grill-with-docs` | Grill With Docs | 도메인 모델 기반 설계 인터뷰 + 문서 업데이트 |
| `handoff` | Handoff | 세션 인수인계 문서 작성 |
| `improve-codebase-architecture` | Improve Codebase Architecture | 아키텍처 개선 기회 발굴 |
| `prototype` | Prototype | 빠른 검증용 프로토타입 빌드 |
| `receiving-code-review` | Receiving Code Review | 코드 리뷰 수신 및 검증 |
| `requesting-code-review` | Requesting Code Review | 코드 리뷰 요청 |
| `subagent-driven-development` | Subagent-Driven Development | 서브에이전트 기반 계획 실행 |
| `systematic-debugging` | Systematic Debugging | 근본 원인 우선 4단계 디버깅 |
| `tdd` | TDD | Red-Green-Refactor TDD |
| `test-driven-development` | Test-Driven Development (Full) | 수직 슬라이스 TDD |
| `to-issues` | To Issues | 계획 → 이슈 트래커 변환 |
| `to-prd` | To PRD | 대화 맥락 → PRD 변환 |
| `triage` | Triage | 이슈 트리아지 상태 머신 |
| `using-git-worktrees` | Using Git Worktrees | 격리된 작업 공간 설정 |
| `using-superpowers` | Using Superpowers | 스킬 우선 적용 원칙 |
| `verification-before-completion` | Verification Before Completion | 완료 주장 전 증거 기반 검증 |
| `write-a-skill` | Write a Skill | 새 스킬 작성 |
| `writing-plans` | Writing Plans | 구현 계획 문서 작성 |
| `writing-skills` | Writing Skills (TDD for Docs) | TDD 기반 스킬 문서 작성 |
| `zoom-out` | Zoom Out | 코드 고수준 맵 제공 |
| `graphify` | Graphify | 코드베이스/문서 → 지식 그래프 변환 및 쿼리 |
| `pretty-mermaid` | Pretty Mermaid | Mermaid 다이어그램 SVG/ASCII 렌더링 |
| `setup-matt-pocock-skills` | Setup Matt Pocock Skills | 엔지니어링 스킬을 위한 레포 초기 설정 |

> **제외 항목:** `codex-cli-runtime`, `codex-result-handling`, `gpt-5-4-prompting`은 `user-invocable: false` 내부 헬퍼 스킬로, Roo Code 모드로 추가하지 않았습니다.

## 업데이트

스킬이 추가/변경되면 `doc/add-skill.md` 절차를 따른 후
`.roomodes` 파일도 함께 업데이트하세요.
