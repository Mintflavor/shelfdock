# Changelog

All future changes must be recorded here by version before delivery. Entries distinguish implemented behavior, validation, and pending work. Platform-specific unreleased work must name its branch; never mark a draft as a public release.

## 0.2.0-beta — 2026-09-24 (draft)

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
