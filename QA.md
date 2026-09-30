# Release Acceptance — v0.2.4-beta (Public Beta)

Validation date: 2026-09-29 (Asia/Seoul). **Windows 11 x64 and macOS 13+ arm64 official public beta.**

## Completed & User-Confirmed Gates

- **Independent WAN P2P File Transfer (PASSED — USER CONFIRMED)**:
  - 8-digit OTP pairing v2 with SPAKE2 bilateral approvals, TLS WSS rendezvous routing.
  - Cross-network P2P transfer verified on independent real-world public networks via self-hosted Unraid Docker relay and libp2p Circuit Relay v2.
  - SHA-256 integrity verification, safe received file cache, and automatic cache cleanup on removal.
- **Real Cross-Application Drag & Explorer Integration (PASSED — USER CONFIRMED)**:
  - Drag-and-drop to and from Windows Explorer and desktop applications.
  - Multi-selection drag, copy-only non-destructive references, and original file preservation.
- **Multi-Monitor & High-DPI Scaling (PASSED — USER CONFIRMED)**:
  - 100%, 150%, and 200% mixed DPI scaling verified across multiple physical displays.
  - Negative origin coordinates and display disconnect/reconnect resilience; shelf and floating icon stay reachable.
- **Polar Sponsorship & License Deep-link (PASSED)**:
  - Settings -> About direct Polar checkout integration and custom URI protocol (`shelfdock://license?key=...`).
  - Automatic activation, background validation, silent offline fallback, and strict zero-telemetry invariant.
- **Windows Packaging & Store Readiness (PASSED)**:
  - Standalone portable ZIP (`ShelfDock-v0.2.4-beta-win-x64.zip`, SHA-256 `edcd4bc671ef14944ec13a38809252a7a35855728b8a0a7d454d1144bd3c9b37`).
  - Store MSIX upload package (`ShelfDock-0.2.4.0-win-x64.msixupload`, SHA-256 `30594e0cb57f3aeb66ef5de3a7291efca9dc6bce8a33632e9511807a97d87725`) with Partner Center Publisher ID `CN=AE66BB57-77A1-46B1-92B3-2860B0E12877`.
  - Zero sensitive source/debug leakage verified (0 leaks).
- **macOS Apple Silicon arm64 Native Beta (PASSED)**:
  - Swift & AppKit native UI aligned with Windows cards, rounded thumbnails, and action layout.
  - Clean arm64 package audit (455 extracted files, SHA-256 `7c7f3d8bef1dabc284aa721b72b4922d004b373f9a1abd19270212a4119ea9bc`).
  - Xcode Release suite (1 aggregate XCTest, 66 Polar checks) and native synthetic screenshot verification.

## Core Safety & Invariants

- **Non-Destructive Work Shelf**: Original files are never deleted or modified. Removing items from the shelf drops references only.
- **Zero Cloud & Zero Telemetry**: No accounts, no analytics, no advertising, and no automatic clipboard scrapers.
- **Opt-In Sharing**: Device sharing is disabled by default. Pairing requires manual 8-digit OTP exchange and bilateral confirmation on both physical machines.
- **Unsigned Beta Guidance**: Clear execution guidance provided for Windows SmartScreen ("More info" -> "Run anyway") and macOS Gatekeeper (Right-click -> "Open").

