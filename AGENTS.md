# ShelfDock public repository working agreement

This repository (`Mintflavor/shelfdock`) contains public documentation, site content and release assets. Product source, operational configuration, private profiles, keys, OTPs and certificates belong outside this repository. The source repository is private (`Mintflavor/shelfdock-private`).

## Checkout and branch lifecycle

- Before dispatching work involving this repository, and again before reviewing its handoff or release documents, the orchestrator verifies the intended repository and branch, runs `git pull --ff-only origin <branch>` in the existing checkout, and records the resulting full commit hash. The worker also pulls its intended base before starting and reports base/head hashes. For a PR, refresh the exact head branch and `main` and compare with the remote PR. Do not review stale local files.
- Preserve local changes if a pull cannot fast-forward or the checkout is in use. Do not force-pull, reset, or stash someone else's changes. Resolve the condition before review and report the blocked refresh if it cannot be resolved.
- Keep one checkout of this public repository and one checkout of the private source repository per machine. Use task branches in the existing checkout for routine Windows and macOS work; switch branches after preserving local changes. Do not create extra clones or worktrees for routine tasks.
- Open a focused PR for tracked changes. After merge, the orchestrator verifies the merge and removes the completed local and remote task branches. Preserve uncommitted, unpushed and ignored work before cleanup.
- Keep `main`. Keep `gh-pages` while GitHub Pages serves from that branch; change the Pages source and verify the site before considering its removal.
- Release assets are uploaded only after the platform's exact package, checksum and contents are verified. Drafts remain unpublished until their stated acceptance gates pass. Record Windows and Mac results separately and never infer one platform's runtime result from the other. Never upload `.msix` or `.msixupload` files to GitHub Releases; public releases distribute portable ZIPs and their SHA-256 digests only (Store packages are reserved for Microsoft Store submission). Never perform external internet or WAN testing; all tests are confined to local LAN, loopback, or mock environments.

## Pre-release note guidelines

When promoting a draft release to a public pre-release (or publishing releases), the release notes must remain concise, professional, and strictly user-focused:
1. **App Introduction (앱 소개 축약)**: Keep to a single 1-2 sentence core philosophy (local-first, 100% freeware, zero-telemetry, zero cloud). Do not repeat the entire feature list or specifications already covered in README or landing pages.
2. **What's New (사용자 가치 우선 주요 변경사항)**: List 3-5 key highlights focused strictly on "how user workflow improved", using user-facing terms (e.g. "한국어/영어 UI 지원", "앱 안정성 개선") rather than internal implementation jargon ("통합 다국어 스트링 테이블 도입", "무중단 안전 폴백 메커니즘").
3. **Collapsible Technical & Secondary Details (<details> 접기 활용)**:
   - **Download & Launch Guide (보안 경고 안내)**: Place OS unsigned executable launch instructions (SmartScreen / Gatekeeper right-click bypass) inside a `<details>` tag.
   - **Checksums (SHA-256 체크섬 표 간소화)**: Checksum tables must be placed inside a `<details>` collapsible section (assets already include `SHA256SUMS.txt`).
4. **Complete Elimination of Internal QA / Test Notes (내부 테스트 메모 완전 삭제)**: Never include internal developer QA checklists, verification status ("NOT RUN", "PASSED"), ad-hoc signing disclaimers, prompt dumps, or test matrices in public release notes.

## Public documentation hygiene and legacy pruning

When releasing a new version or promoting a pre-release:
- Audit all files in the public repository to ensure they match the active release.
- Delete obsolete one-off release notes (e.g. `RELEASE-*.md`) and retired protocol memos (e.g. `INVITATIONS.md`, `OTP-REVIEW.md`).
- Replace historical draft disclaimers ("binary held as draft", "untested on external WAN") with verified acceptance results once passed.
- Ensure `CHANGELOG.md`, `USER-GUIDE.md`, `QA.md`, and `P2P-GUIDE.md` reflect multi-platform support and confirmed real-world validation.
- Audit and synchronize the GitHub Pages site (`gh-pages` branch `index.html`) on every version bump and release: verify header version tag (`header-version`), hero/card download buttons, package notices, fallback JavaScript variables (`activeVersion`, `activeTag`, `activePackageName`), and bilingual translation dictionaries (`translations.ko` / `translations.en`) match the active release.


