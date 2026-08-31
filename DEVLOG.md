# DEVLOG — 인스타 법무·정책 지원 (ai-instagram-legal)

이 레포에서 **사람이 한 변경**을 기록한다. 🔴 자동 파이프라인(`hosting.py` 두 개)이 넣는
`img/`·`vid/` 커밋은 여기 적지 않는다 — 그건 산출물이지 변경이 아니다. 최신 항목을 맨 위에 둔다.

## 2026-08-31 · 지시서 — 관리 대상 17개 중 유일하게 지시서가 없던 레포였다
- 발단: 허브 필독 훅(`required-read.sh`) 17개 레포 시험에서 이 레포만 영수증이 `AGENTS#-` 로 나왔다. **`CLAUDE.md`·`AGENTS.md` 가 둘 다 없었다** — 관리 대상인데 GLOBAL-RULES 도 레포 지시도 걸리지 않는 상태였다. 옵시디언 볼트에 「🟡 임포트가 안 걸린다」로 이미 적혀 있었으나 고쳐지지 않고 있었다.
- 무엇을 했나: `AGENTS.md`(정본) · `CLAUDE.md`(포인터) · 이 `DEVLOG.md` 신설. 훅 재시험에서 영수증이 `AGENTS#7fb805` 로 바뀐 것을 확인했다.
- 🔴 지시서에 박은 것 중 제일 중요한 것: **이 레포는 사람이 안 건드려도 커밋이 늘어난다.** `ai-affiliate-agent/deals/hosting.py` 와 `ai-instagram-agent/publisher/hosting.py` 가 직접 push 한다. 그래서 ①작업 전 `git pull --ff-only` ②커밋은 **내 경로만** 지정 ③`git status` 가 깨끗하다고 믿지 않는다. ②는 같은 날 신설한 훅(`guard-git-add-all.py`)이 기계로 막는다.
- 🔴 **미해결(대표님 판단 대기)**: 위 두 hosting.py 는 launchd 의 python subprocess 라 **Claude Bash 훅을 지나가지 않는다** — 관리 대상 레포인데 RULE-001 마커 없이 커밋이 나간다. 훅이 뚫린 게 아니라 **훅이 보는 지점을 안 지나가는 구조**다. 정본 등재는 `ai-automation-control/HANDOFF.md`.
- 🔒 법무 문서 3종(`index.html`·`data-deletion.html`·`oauth-callback.html`)은 **Meta 앱 심사 제출본이자 실제 OAuth 리다이렉트 대상**이라 대표님 지시가 있을 때만 고치도록 못박았다. `img/`·`vid/` 는 **살아 있는 게시물이 참조하는 공개 URL** 이라 삭제도 지시가 있을 때만.
- 배운 점: ⭐ **「지시서가 없는 레포」는 조용하다.** 잘못된 지시서는 읽으면 티가 나지만, 없는 지시서는 아무 신호도 내지 않는다. 17개를 한 줄로 훑는 훅을 만들고 나서야 보였다 — **전수 검사가 있어야 「없는 것」이 보인다.**
- 태그: 인스타법무, 지시서, 호스팅, 자동커밋, RULE-001
