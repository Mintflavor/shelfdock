# Release Acceptance — v0.2.7-beta (Draft)

Validation date: 2026-10-01 (Asia/Seoul). **Windows 11 x64 and macOS 13+ arm64 release candidate.**

## Completed & User-Confirmed Gates

- **Centralized Localization & Unified String Tables (PASSED)**:
  - Unified bilingual (Korean/English) string tables across Windows and macOS clients with shared semantic namespaces.
  - Category B consensus wording applied and verified: "ShelfDock 열기" / "Open ShelfDock", "ShelfDock 종료" / "Quit ShelfDock", "설정…" / "Settings…", "동의하고 시작" / "Accept and start", "다운로드" / "Download", etc.
  - Safe fallback mechanisms and dynamic format token replacements verified without crashes.
  - macOS live language switching on settings change verified without requiring application restart.
- **Double-Click File Execution (PASSED)**:
  - Double-clicking any file item on the shelf launches the file directly in its default associated application.
  - Remote items not yet cached are safely fetched and SHA-256 verified before opening; missing files and invalid associations fail gracefully without crashing or altering originals.
- **P2P LAN Auto-Connect & Discovery (PASSED)**:
  - Reciprocal peer discovery and pairing over local network (mDNS) without requiring OTP entry.
  - Bounded by 16-peer trust limit; requires explicit activation on both peers; disabling preserves existing connections.
- **OTP UX Alignment & Bilateral Approvals (PASSED)**:
  - Centered 8-digit OTP input field on both Windows and macOS.
  - Automatic uppercase alphanumeric filtering, auto-hyphen insertion (`XXXX-XXXX`), and smart backspace handling.
- **Device Unpair Confirmation & Peer Revocation Protocol (PASSED)**:
  - Added confirmation modal/alert before unpairing a device to prevent accidental disconnections.
  - Implemented `/shelfdock/unpair/1.0.0` protocol: unpairing notifies the remote peer, displaying a clear "Disconnected by remote device" status notice in the trusted devices list.
- **Independent WAN P2P File Transfer (PASSED — USER CONFIRMED)**:
  - 8-digit OTP pairing v2 with SPAKE2 bilateral approvals, TLS WSS rendezvous routing.
  - Cross-network P2P transfer verified on independent real-world public networks via self-hosted Unraid Docker relay and libp2p Circuit Relay v2.
  - SHA-256 integrity verification, safe received file cache, and automatic cache cleanup on removal.
- **Real Cross-Application Drag & Explorer Integration (PASSED — USER CONFIRMED)**:
  - Drag-and-drop to and from Windows Explorer, macOS Finder, and desktop applications.
  - Multi-selection drag, copy-only non-destructive references, and original file preservation.
- **Multi-Monitor & High-DPI Scaling (PASSED — USER CONFIRMED)**:
  - 100%, 150%, and 200% mixed DPI scaling verified across multiple physical displays.
  - Negative origin coordinates and display disconnect/reconnect resilience; shelf and floating icon stay reachable.
- **Polar Sponsorship & License Deep-link (PASSED)**:
  - Settings -> About direct Polar checkout integration and custom URI protocol (`shelfdock://license?key=...`).
  - Automatic activation, background validation, silent offline fallback, and strict zero-telemetry invariant.
- **Windows Packaging & Store Readiness (PASSED)**:
  - Standalone portable ZIP (`ShelfDock-v0.2.7-beta-win-x64.zip`, 77,133,879 bytes, SHA-256 `1ebfe7ba15b787b5b31343cb65b145f51687a9bc482fd107bdbbb085cb56e44e`).
  - Store MSIX upload package (`ShelfDock-0.2.7.0-win-x64.msixupload`) with Partner Center Publisher ID `CN=AE66BB57-77A1-46B1-92B3-2860B0E12877`.
  - Zero sensitive source/debug leakage verified (0 leaks).
- **macOS Apple Silicon arm64 Native Release (PASSED)**:
  - Swift & AppKit native UI aligned with Windows cards, rounded thumbnails, and action layout.
  - Clean arm64 package audit (455 extracted files, `ShelfDock-v0.2.7-beta-macOS-arm64.zip`, 21,355,705 bytes, SHA-256 `33a8e5c9007014c193e3747c731912b6a27ac3d4c6f206feba86b28155ddf6b9`).
  - Bundle version format: strictly `0.2.7` without build numbers (`CFBundleShortVersionString` and `CFBundleVersion` both `0.2.7`).
  - Xcode Release suite, string table check suites, and zero sensitive leakage verified.

## Core Safety & Invariants

- **Non-Destructive Work Shelf**: Original files are never deleted or modified. Removing items from the shelf drops references only.
- **Zero Cloud & Zero Telemetry**: No accounts, no analytics, no advertising, and no automatic clipboard scrapers.
- **Opt-In Sharing**: Device sharing is disabled by default. Pairing requires manual 8-digit OTP exchange and bilateral confirmation on both physical machines.
- **Unsigned Beta Guidance**: Clear execution guidance provided for Windows SmartScreen ("More info" -> "Run anyway") and macOS Gatekeeper (Right-click -> "Open").

