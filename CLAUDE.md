# CLAUDE.md

이 repo 의 에이전트 지시서는 **`AGENTS.md` 로 통일**돼 있습니다 (Claude·Codex·Cursor 공통 정본).

👉 **먼저 `AGENTS.md` 를 읽으세요.**

- 내용을 여기 중복하지 않습니다(드리프트 방지).
- 🔴 이 레포는 **정적 호스팅**입니다. 자동 파이프라인이 계속 커밋을 넣으므로 `git pull --ff-only` 부터 합니다.

## 전 시스템 공통 강제 규칙 (무조건 준수)

아래 규칙은 `ai-automation-control` 이 관리하는 전 시스템 공통 정본이며, 이 레포의 다른 지시보다 우선한다.

> 🔒 이 규칙은 SessionStart 훅(`ai-automation-control/rules/hooks/required-read.sh`)이 이 세션에 **직접 주입**한다.
>
> 🔴 여기에 `@../ai-automation-control/…` 임포트를 **되살리지 않는다.** Claude Code 는 프로젝트 `CLAUDE.md` 의
> **레포 밖 임포트를 승인 없이 조용히 버린다** — v2.1.251 로더 실측 2026-08-31.
