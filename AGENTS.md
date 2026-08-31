# AGENTS.md — 인스타 법무·정책 지원 (ai-instagram-legal) 에이전트 지시서 정본

> 이 레포의 에이전트 지시서는 **이 파일 하나가 정본**이다 (Claude·Codex·Cursor 공통).
> `CLAUDE.md` 는 포인터일 뿐이다 (내용 중복 금지).
> 신설 2026-08-31 — 관리 대상 17개 중 **유일하게 지시서가 없던 레포**였다(허브 필독 훅 시험에서 드러남).

## 0. 이 레포는 무엇인가

**GitHub Pages 정적 호스팅.** 두 가지만 산다:

| | 무엇 | 누가 넣나 |
|---|---|---|
| **법무 문서** | `index.html`(개인정보처리방침) · `data-deletion.html` · `oauth-callback.html` | 사람 (드물게) |
| **공개 자산** | `img/`(카드뉴스·어필리에이트 카드) · `vid/`(릴스) | 🤖 **자동 파이프라인** |

공개 URL: `https://devgster.github.io/ai-instagram-legal/`

🔴 **여기서 아무것도 만들지 않는다.** 카드도 영상도 글도 다른 레포가 만들어 **결과만** 여기 올린다.
코드가 없다 — 빌드도 테스트도 없다.

## 1. 🔴🔴 먼저 알아야 할 것 — 자동 커밋이 계속 쌓인다

이 레포에는 **사람이 안 건드려도 커밋이 늘어난다.** 두 파이프라인이 여기 직접 push 한다:

| 넣는 쪽 | 코드 | 무엇을 |
|---|---|---|
| `ai-affiliate-agent` | `deals/hosting.py` | `img/affiliate/` 카드 |
| `ai-instagram-agent` | `publisher/hosting.py` | `img/` 카드뉴스 |

🔴 **그래서 이 레포에서 `git status` 가 깨끗하다고 믿지 않는다.** 작업 시작 전에 `git pull --ff-only`
(RULE-007) 를 반드시 하고, 커밋할 때는 **내가 만든 경로만 적어서** add 한다 (RULE-004).
뭉텅이 스테이징은 훅(`guard-git-add-all.py`)이 막는다.

🔴 **알려진 미해결 문제 (대표님 판단 대기):** 위 두 hosting.py 는 **launchd 의 python subprocess** 로
push 하므로 **Claude Bash 훅을 지나가지 않는다.** 즉 관리 대상 레포인데 **RULE-001 승인 마커 없이
커밋이 나간다.** 훅이 뚫린 것이 아니라 **훅이 보는 지점을 안 지나가는 구조**다.
정본 등재는 `ai-automation-control/HANDOFF.md` — 여기서 임의로 고치지 않는다.

## 2. 🔒 법무 문서는 함부로 고치지 않는다

`index.html` · `data-deletion.html` · `oauth-callback.html` 는 **Meta 앱 심사에 제출된 문서**이고
`oauth-callback.html` 은 **실제 OAuth 리다이렉트 대상**이다.

- 🔴 문구·URL·시행일을 바꾸면 **심사 상태나 로그인 흐름에 영향**을 줄 수 있다. **대표님 지시가 있을 때만** 고친다.
- 🔴 고칠 때는 무엇이 바뀌는지와 심사 영향 가능성을 **먼저 보고**하고 승인을 받는다 (RULE-002 — 외부 공개 게이트).
- 개인정보 처리 문구를 실제 동작보다 **좁게** 적지 않는다 (거짓 고지가 된다).

## 3. 🔒 지우지 않는다

`img/` · `vid/` 의 자산은 **이미 발행된 게시물이 참조하는 공개 URL** 이다.
지우면 살아 있는 게시물의 이미지가 깨진다. **정리·삭제는 대표님 지시가 있을 때만** 하고,
그때도 참조 여부를 먼저 확인한다.

## 4. 커밋·push

GLOBAL-RULES 를 따른다. 특히:

- **RULE-001** push 전 검토 + 승인 마커 (`git rev-parse HEAD > .git/push-review-approved` 후 별도 명령으로 push)
- **RULE-004** 내 작업만 — 🔴 자동 파이프라인이 넣은 파일을 내 커밋에 담지 않는다
- **RULE-005** DEVLOG 즉시 기록 — 이 레포엔 아직 `DEVLOG.md` 가 없다. 사람이 의미 있는 변경을 하면 그때 만든다
- **RULE-008** push 성공 후 옵시디언 상태 갱신

## 5. 읽지 않는 것

`img/` `vid/` 의 바이너리 — 명시 요청 없이 열지 않는다 (수백 건이고 내용이 파일명에 다 있다).
