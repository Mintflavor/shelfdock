# Changelog

## 0.1.2-beta — release candidate

- PC invitation links with explicit confirmation and running-instance delivery.
- Generate QR codes and save lossless PNG invitations; no QR scanning/import.
- 13 focused invitation checks and release packaging passed. Relay allowlisting is unchanged.
- See [invitation guide](INVITATIONS.md).


## 0.1.1-beta — release candidate

- Optional persistent floating drop icon, subtle drag animation, click/close navigation and saved position.
- Linux amd64 Docker relay package, Unraid guide, reloadable device allowlist and persistent identity.
- 61 automated checks pass. Actual container relay transfer passes; independent external-network acceptance remains pending.


## 0.1.0-beta — release candidate

- Always-on-top Windows shelf with tray access and a configurable global shortcut.
- Local file references, PNG captures, and plain text.
- Copy-only native transfers, pinning, optional auto-remove, and session undo.
- Atomic state persistence, previous-snapshot recovery, and scoped PNG cleanup.
- English/Korean UI and first-run freeware license consent.
- Opt-in trusted-device pairing, live metadata/text mirroring, lazy SHA-256-verified files and small-capture reception.
- LAN discovery, public DHT lookup, hole-punch support, configurable Circuit Relay v2 and an allowlisted Windows relay executable.
- Persistent local removals, independent received copies, scoped received-cache cleanup and dependency license/source notices.

Unsigned. External-network NAT/DHT/relay, clean-machine and mixed-DPI acceptance gates remain open; see QA.md. The release is a draft until those gates pass.
