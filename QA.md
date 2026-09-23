# Release acceptance — 0.1.1-beta candidate

Validation date: 2026-09-23 (Asia/Seoul). **Public binary release is held as a draft.**

## Completed

- Release WPF build: zero warnings / zero errors.
- 30 storage and transfer-policy regression checks passed, including pending remote items, local removal suppression, undo and received-cache boundaries.
- 23 Windows/WPF integration checks passed: actual FileDrop/UnicodeText/Bitmap payloads, generated PNG ownership, preferred Copy effect, invalid batch rejection, missing-file rejection, rendered layout, C# IPC against two packaged peer processes (startup, pairing, verified Unicode file reception, revocation), and real WPF window shutdown with sharing disabled.
- 8 Go integration tests passed: authenticated pairing/revocation, live catalog/lazy file integrity and independent removal, unpaired access denial/bounded frames, persistent DPAPI identity, local Circuit Relay transfer/allowlist rejection, isolated DHT address lookup, and safe received filenames. DHT tests use a private loopback bootstrap; relay tests use three loopback nodes. These do not exercise real NAT.
- Separate opt-in public DHT smoke test passed on 2026-09-23: a fresh ephemeral peer reached the public routing table within the 45-second bound. This confirms bootstrap access from this PC only, not cross-network discovery, NAT traversal or public relay transfer. Run with `SHELFDOCK_PUBLIC_DHT_SMOKE=1` and `go test ./network/internal/peer -run TestPublicDHTBootstrap -count=1 -v`.
- First-run license consent was visually inspected: acceptance is required and persists.
- Real UI: Korean text paste, English language change, settings/help and shelf rendering; state restored after restarting.
- New paired-device dialog visually inspected in Korean, with sharing off by default and explicit current/future shelf sharing and networking disclosure.
- Private GitHub Actions build and packaging passed for the initial P2P candidate. Final revision validation is tracked in the private Actions history.
- Runtime is bundled. The running process loaded coreclr.dll from its application directory. The system-wide dotnet installation has .NET 8, not .NET 10; the SDK used to build is workspace-local.
- Package guard rejected a Core PDB on its first run. Release symbols were disabled and the clean candidate passed the source/debug/data artifact guard.
- Native notification icon replaces Windows Forms to avoid loading a second UI framework.
- After this change, a five-second local sample measured 134.6 MiB working set, 79.0 MiB private memory, and 0.469% processor-normalized average CPU. This is one measurement, not a sustained performance guarantee.
- Executable is unsigned, correctly documented. SHA-256 is supplied for integrity, not identity.

## 0.1.1 additions

- User reports real cross-application drag working. The specific destination apps and edge-case matrix were not provided; record this as user validation, not an automated Explorer/Chrome/Edge certification.
- Floating icon: persisted opt-in setting, topmost independent drop window, copy-only routed drops, hover/receipt wiggle respecting OS animation preferences, click to open, close/Esc to return, move and position restore, disable and quit cleanup. Eight additional WPF assertions bring the Windows/native/IPC suite to 23 checks.
- The Unraid Docker relay was built and started as non-root with read-only rootfs and persistent state. A forced circuit-relay integration test transferred and verified a Unicode fixture through the actual container and rejected an unallowlisted reservation.
- Container stop exited with code 0; restarting preserved the relay Peer ID. TCP healthcheck passed. One idle sample was approximately 5.4 MiB and 0% CPU; not a capacity benchmark.
- A bounded, reloadable allowlist denies new access on invalid/missing/empty configuration. A new Go regression test covers reload and fail-closed behavior.
- Forced relay transfer through the configured public DNS address also passed from this PC. This may use NAT loopback and does not establish reachability from an independent external network. App identities and actual deployment addresses are kept outside the public repository.

## Required before publishing the draft

- [ ] Two separate public networks: DHT-assisted discovery, configured public relay reservation, relay-only file transfer, reconnect after changed IP, restrictive NAT, source offline and interrupted download. An Unraid relay is deployed and its public DNS address was tested from this PC; an independent external-network test remains pending. This gate remains mandatory.
- [ ] Paired-device end-to-end WPF UI and sustained process-tree memory/CPU with sharing enabled. Earlier local-only performance measurements do not cover the Go process.

- [x] Real cross-application drag: user-confirmed working. Detailed destination/version matrix remains unrecorded.
- [ ] New floating-icon native drop in the user's workflow (routed Windows payload tests pass).
- [ ] Native drag Escape/rejection leaves all items; accepted drag auto-removes only unpinned items and Undo restores them.
- [ ] Word and browser text input accept text; rejected targets can use Copy/Paste.
- [ ] Two monitors with 100%, 150%, 200% DPI, negative origins and disconnect/reconnect; shelf stays reachable.
- [ ] Fresh Windows 11 x64 VM without SDK or .NET: extract, accept license, use, quit and restart.
- [ ] Sustained idle and typical-use performance; measure warm shortcut-to-visible latency against 200ms target.
- [ ] Verify tray double-click/context menu/Quit and hotkey conflict/change/recovery in an interactive session.

The current Windows UI tool refuses a drag whose endpoint is another application's window. That prevented real cross-application drag tests; it is a tooling restriction, not evidence of application compatibility or incompatibility. Automated payload tests are not a substitute.

## Manual fixture procedure

1. Create a source folder with two harmless text files and one PNG. Record SHA-256 values; create an empty target folder.
2. Drag from Explorer to ShelfDock, then into the target folder. Compare original and target hashes and verify originals still exist.
3. Repeat with browser file inputs on a local test page; no cloud upload is required.
4. Enable auto-remove; try accepted, cancelled and rejected drops, pinned items and Ctrl+Z.
5. Test display configurations and a clean VM. Record app/browser/Windows versions and results here.
6. Once all gates pass, update public availability text and QA record, then publish the existing release as a prerelease. Do not create a duplicate release or expose the private source repository.

## User confirmation — 2026-09-24

Confirmed for 0.1.3: Korean filenames, icon consistency, pinned sorting, missing-file styling, automatic settings, connection settings and progress. Large-file native drag/WAN/clean Windows/DPI/performance remain unconfirmed. 0.1.4 passed 38 Core and 16 Windows workflow checks plus release packaging; explicit received-cache deletion still needs user confirmation.
