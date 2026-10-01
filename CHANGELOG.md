# Changelog

All future changes must be recorded here by version before delivery. Entries distinguish implemented behavior, validation, and pending work.

## 0.2.7-beta — 2026-10-01 (draft)

- **Centralized Localization & Unified String Tables**:
  - Unified bilingual (Korean/English) string tables introduced across Windows and macOS clients with shared semantic namespaces and dynamic format tokens (`{count}`, `{selected}`, `{peer}`, `{bytes}`, `{left}`, `{version}`, `{supporter}`).
  - Standardized Category B consensus terminology across both platforms:
    - Tray / menu commands: "ShelfDock 열기" / "Open ShelfDock", "ShelfDock 종료" / "Quit ShelfDock", "설정…" / "Settings…".
    - License dialog: "동의하고 시작" / "Accept and start", "ShelfDock 프리웨어 사용 약관" / "ShelfDock Freeware License".
    - Pairing OTP & Sharing: "8자리 코드 만들기" / "Create 8-character code", "이 창을 닫고 연결된 기기에서 먼저 공유를 켜세요." / "Close this window and enable sharing in Connected devices first.", "연결 완료. 양쪽 기기에서 승인과 저장을 확인했습니다." / "Paired. Both devices approved and confirmed saving.".
    - Floating drop icon & shelf controls: "화면에 플로팅 드롭 아이콘 항상 표시" / "Keep a floating drop icon on screen", "다운로드" / "Download", "닫기" / "Close", "숨기기" / "Hide", "백업에서 선반을 복원했습니다." / "Restored the backup shelf.".
- **Live Language Switching & Fault-Tolerant Fallback**:
  - macOS: dynamic live UI language switching without app restarts upon changing the language preference in Settings.
  - Crash-resilient safe fallback: missing keys or format discrepancies return original key strings safely without crashing or dropping user shelf items.
- **Package Digests**:
  - Windows 11 x64 Portable ZIP: `ShelfDock-v0.2.7-beta-win-x64.zip` (77,133,879 bytes, SHA-256 `1ebfe7ba15b787b5b31343cb65b145f51687a9bc482fd107bdbbb085cb56e44e`).
  - macOS Apple Silicon arm64 ZIP: `ShelfDock-v0.2.7-beta-macOS-arm64.zip` (21,355,705 bytes, SHA-256 `33a8e5c9007014c193e3747c731912b6a27ac3d4c6f206feba86b28155ddf6b9`).

## 0.2.6-beta — 2026-09-30 (public beta)

- **Double-Click File Execution**:
  - Double-clicking any file item on the shelf opens it directly in its default system application.
  - Remote items not yet downloaded are automatically fetched and SHA-256 integrity-verified before opening. Missing files and errors fail gracefully without app crashes or corrupting originals.
- **P2P LAN Auto-Connect**:
  - Optional local network (LAN) auto-connect: reciprocal peer discovery and automatic pairing over mDNS without requiring 8-digit OTP codes.
  - Bounded by 16-peer trust limit; requires explicit activation on both peers; disabling preserves existing connections.
- **OTP UX Alignment**:
  - Centered 8-digit OTP input field on both Windows and macOS.
  - Automatic uppercase alphanumeric filtering, auto-hyphen insertion (`XXXX-XXXX`), and smart backspace handling.
- **Device Unpair Confirmation & Peer Revocation**:
  - Added confirmation modal/alert before unpairing a device to prevent accidental disconnections.
  - Implemented `/shelfdock/unpair/1.0.0` protocol: unpairing notifies the remote peer, displaying a clear "Disconnected by remote device" status notice in the trusted devices list.
- **Cross-Platform UI Polish**:
  - Main window bottom-left status replaced with dynamic application version (e.g. `v0.2.6-beta`).
  - Floating icon badge displays item count (dark teal rounded badge, hidden when shelf is empty).
  - macOS: subtle 420ms rotation wiggle animation when dragging files over the floating icon or dropping items.
  - Layout cleanups: removed redundant explanatory text in Startup settings and OTP pairing dialogs.
- **Package Digests**:
  - Windows 11 x64 Portable ZIP: `ShelfDock-v0.2.6-beta-win-x64.zip` (74,835,330 bytes, SHA-256 `d05324fb7e74fe85dc06b6de064037e7b6f20e579616748dd3af7de5b9f917e4`).
  - macOS Apple Silicon arm64 ZIP: `ShelfDock-v0.2.6-beta-macOS-arm64.zip` (21,346,046 bytes, SHA-256 `3a8c26fba847f83c4a079956a79ce15870c82f536d467e12775ea26971fa46fd`).

## 0.2.4-beta — 2026-09-29 (public beta)

- **Official Public Beta Release**: Windows 11 x64 and macOS 13+ (Apple Silicon arm64) binaries published on GitHub Releases.
- **Polar Sponsorship & License Deep-link**:
  - Settings -> About tab direct Polar checkout link integration.
  - Custom URI deep-link protocol (`shelfdock://license?key=...`) for one-click supporter license activation.
  - Automatic background license validation with silent offline fallback; 100% freeware with zero paywalls.
- **macOS UI Alignment**:
  - Borderless draggable/resizable shelf header, rounded thumbnail cards, 5-action buttons (Download, Copy, Pin, Remove, Undo), and bilingual UI.
  - Clean arm64 package audit (455 extracted files, 0 leaks, SHA-256 `7c7f3d8bef1dabc284aa721b72b4922d004b373f9a1abd19270212a4119ea9bc`).
- **Windows Store & MSIX Infrastructure**:
  - MSIX packaging pipeline (`package-msix.ps1`), Partner Center Publisher ID `CN=AE66BB57-77A1-46B1-92B3-2860B0E12877`, transparent visual assets, MakePri multilingual resources, and zero sensitive leakage audit.
- **Hardware & Network Acceptance (PASSED — USER CONFIRMED)**:
  - Independent cross-network WAN P2P file transfers via self-hosted Unraid Docker relay and libp2p Circuit Relay v2.
  - Multi-monitor high-DPI mixed scaling (100%, 150%, 200%) and negative coordinate desktop positioning.
  - Real Windows Explorer and macOS Finder drag-and-drop operations.

## 0.2.3-beta — 2026-09-29

- Added Polar sponsorship integration to Settings -> About tab.
- Unauthenticated public client license key activation and validation via Polar API.
- Local persistent supporter status storage with personalized supporter greeting.
- Maintained strict freeware and zero-telemetry boundaries.

## 0.2.2-beta — 2026-09-28

- Connected devices UI v2: unified settings navigation, network/trust cards, and bilateral OTP sheets across Windows and macOS.
- Native startup registration: Windows Run registry key and macOS SMAppService support.
- macOS arm64 beta candidate packaging and checksum verification.

## 0.2.1-beta — 2026-09-26

- Cross-platform Windows and macOS 8-digit OTP pairing and bidirectional file transfer interoperability.
- Windows brand ICO assets, menu icons, and floating drop target alpha opacity fixes.
- Safe received file cache cleanup and retention policies.

## 0.2.0-beta — 2026-09-24

- Replaced invitation links/QR/legacy token IPC and network handler with eight-character OTP, shared SPAKE2 authentication, signed peer identity, matching verification number, both approvals and absolute 60-second expiry. Existing trust/file protocols remain compatible.
- Added cancellation, stale-session protection, retry throttle, bounded messages, failed-save rollback and explicit incomplete-final-ack recovery instructions. Routing is two public characters plus six random secret characters; no eight-secret-character claim.
- Windows OTP interface replaces link/QR controls; own legacy URL registration is removed. QRCoder and test QR decoder removed; new PAKE license notices included.
- Rendezvous 0.2.0 deployed: valid TLS on TCP 4000, certificate renewal and periodic reload, isolated memory-only backend, ShelfDock-only namespace, 60/65-second session controls, message limits, per-IP handshake/connection limits and global connection cap. Existing libp2p relay unchanged.
- PASSED: local Go networking/OTP tests, real WSS two-peer authentication from LAN, Windows workflow/OTP integration, certificate renewal dry-run, rejected foreign namespace and HTTP 429 burst limiting. Independent WAN, full native drag matrix, clean OS/DPI/performance and crypto audit remain pending. Self-contained publish, 38 Core safety checks, 19 Windows workflow checks plus OTP IPC assertions and package source/debug/secret guard passed. PAKE MIT option explicitly elected with upstream notices retained.

## 0.1.4-beta — 2026-09-24 (draft)

- Windows: explicitly removing a received file/image now deletes its app-owned Received cache and empty download folder after the shelf state is saved. Sender originals and exported copies are untouched.
- Undo restores deleted downloads as metadata for downloading again. Locked files are queued persistently and retried on restart; files referenced by another live item remain protected. Late download completion after removal discards the cache.
- Accepted-drop automatic cleanup retains the prior delayed policy because targets may still read the file. Existing retired caches are not mass-deleted retroactively.
- PASSED: 38 Core safety checks, 16 Windows workflow checks, self-contained publish and ZIP guard. Added deletion/undo/failed-save/locked-file/late-download/shared-reference coverage; Cache packaging avoids unrelated Go/invitation suites.
- User verified on 2026-09-24 for 0.1.3: Korean filenames, icon consistency, pinned ordering, missing-file styling, automatic settings, connection settings, and progress. This does not establish large-file native drag, WAN, clean-machine, DPI or performance acceptance.

## 0.1.3-beta — 2026-09-23 (draft)

- Shared peer: optional byte-progress IPC events for downloads; existing peer wire protocols remain v1. Verification completes only with a successful fetch reply.
- Windows settings now save automatically; connection changes are debounced and serialized, with startup failure rollback. Removed Save/Apply buttons.
- Remote outgoing drag requests download, SHA-256 verification and native file stream/path delivery in one gesture. Circular byte progress; no partial paths exposed. Explicit Download remains a fallback. Targets may wait during reception; real Explorer/browser large-file acceptance is NOT RUN.
- Pinned items appear first; missing local files use pale red backgrounds refreshed while visible. Header/empty-state icon uses the application icon.
- Explicit UTF-8 peer IPC fixes Korean/emoji filenames on legacy-codepage Windows. Remote name refresh preserves cached state and pinning.
- OTP feasibility reviewed in OTP-REVIEW.md; OTP is not implemented and invitation formats remain unchanged.
- PASSED: 30 Core safety checks, 2 related Go checks, self-contained publish and packaging guard. Added 16 passing focused Windows workflow checks, including actual 16MiB peer download/native IStream delivery, progress, Unicode IPC, styling, pin order and automatic settings.

## 0.1.2-beta — 2026-09-23 (draft)

- PC invitation URL opening/paste, explicit receiver confirmation, running-instance forwarding, QR generation and PNG saving; ten-minute single-use invitations. QR scanning is not included.
- Added QRCoder MIT notices and focused invitation checks (13); release build and 30 storage checks passed locally. Full CI intentionally not repeated.

## 0.1.1-beta — 2026-09-23 (draft)

- Optional always-on-top floating drop icon, hover/receipt wiggle, click-to-open, close/Esc return and saved position.
- Linux amd64 Docker relay package and Unraid deployment, persistent server identity, reloadable fail-closed allowlist, healthcheck and graceful restart.
- 30 Core, 23 Windows and 8 Go checks passed; private CI passed at ca49243. Real container relay transfer passed. Public DNS test from the same LAN is not independent external-NAT validation.

## 0.1.0-beta — 2026-09-23 (initial draft)

- Windows 11 x64 WPF/.NET 10 shelf: file references, PNG captures, Unicode text, native Copy-only drag, pinning, opt-in auto-remove, session undo, atomic persistence/recovery and scoped seven-day cache cleanup.
- Tray and configurable shortcut, Korean/English UI, first-run proprietary freeware terms, bundled runtime, dependency notices and manual unsigned ZIP distribution.
- Go/libp2p trusted-device pairing, metadata-first file sharing, SHA-256 reception, mDNS/DHT, configurable Circuit Relay v2, Windows DPAPI identities, revocation and remote-item suppression.
- Packaged IPC/public-DHT smoke verification and shutdown reentrancy fix (5972429, 1ba4995, 4d5c74a). External-network, clean-machine, DPI and sustained-performance acceptance remained open.
