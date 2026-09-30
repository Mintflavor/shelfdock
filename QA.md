# Release Acceptance — v0.2.6-beta (Public Beta)

Validation date: 2026-09-30 (Asia/Seoul). **Windows 11 x64 and macOS 13+ arm64 official public beta.**

## Completed & User-Confirmed Gates

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
  - Standalone portable ZIP (`ShelfDock-v0.2.6-beta-win-x64.zip`, 74,835,330 bytes, SHA-256 `d05324fb7e74fe85dc06b6de064037e7b6f20e579616748dd3af7de5b9f917e4`).
  - Store MSIX upload package (`ShelfDock-0.2.6.0-win-x64.msixupload`) with Partner Center Publisher ID `CN=AE66BB57-77A1-46B1-92B3-2860B0E12877`.
  - Zero sensitive source/debug leakage verified (0 leaks).
- **macOS Apple Silicon arm64 Native Beta (PASSED)**:
  - Swift & AppKit native UI aligned with Windows cards, rounded thumbnails, and action layout.
  - Clean arm64 package audit (455 extracted files, `ShelfDock-v0.2.6-beta-macOS-arm64.zip`, 21,346,046 bytes, SHA-256 `3a8c26fba847f83c4a079956a79ce15870c82f536d467e12775ea26971fa46fd`).
  - Xcode Release suite (1 aggregate XCTest, 66 Polar checks), native synthetic screenshot verification, and CUA double-click & icon badge/wiggle tests.

## Core Safety & Invariants

- **Non-Destructive Work Shelf**: Original files are never deleted or modified. Removing items from the shelf drops references only.
- **Zero Cloud & Zero Telemetry**: No accounts, no analytics, no advertising, and no automatic clipboard scrapers.
- **Opt-In Sharing**: Device sharing is disabled by default. Pairing requires manual 8-digit OTP exchange and bilateral confirmation on both physical machines.
- **Unsigned Beta Guidance**: Clear execution guidance provided for Windows SmartScreen ("More info" -> "Run anyway") and macOS Gatekeeper (Right-click -> "Open").

