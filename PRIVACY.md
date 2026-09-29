# Privacy Policy

**Effective Date:** September 29, 2026

ShelfDock is designed with a strict privacy-first and local-first architecture. We believe your files and data belong entirely to you.

---

## 1. Information We Do Not Collect

ShelfDock does **not** collect, store, transmit, or sell your personal data:

- **No User Accounts:** There is no registration, login, or profile creation.
- **No Telemetry or Tracking:** No usage statistics, user tracking, or crash analytics are collected or sent to external servers.
- **No Advertisements:** ShelfDock contains no third-party ad networks or tracking SDKs.
- **No Cloud Content Storage:** ShelfDock does not upload or host your files or shelf items on any cloud server.
- **No Background Clipboard Monitoring:** ShelfDock never automatically monitors or records your clipboard history. Items appear on the shelf only when you explicitly paste or drag them in.

---

## 2. Data Storage and Handling

- **Local Storage:** Files placed on the shelf remain in their original locations on your device; ShelfDock only stores local references. Pairing credentials, encryption keys, and preferences are stored exclusively on your local machine using secure platform APIs (Windows DPAPI and macOS Keychain).
- **Peer-to-Peer Transfer:** File transfers between paired devices occur directly via peer-to-peer (libp2p) connections with end-to-end encryption (Noise / TLS). Pairing requires explicit, two-way confirmation via one-time passcodes (OTP).
- **Relay Processing:** When direct peer-to-peer connection is unreachable due to NAT/firewalls, transfers may be routed through an optional relay server. Relays only forward encrypted streams in-memory; they cannot decrypt, inspect, or retain your files or content.

---

## 3. Third-Party Services

- **Polar (Optional Sponsorship & Licensing):** When you choose to support development or activate a supporter license, ShelfDock communicates with the Polar public API (`api.polar.sh`) strictly to validate your license key. ShelfDock never collects, processes, or stores your payment details or credit card information. Payments are handled entirely by Polar under their own terms and privacy policy.

---

## 4. Updates and Inquiries

If this privacy policy is updated, changes will be published in this repository with an updated effective date.

For questions or security concerns, please open an issue on GitHub:
- [ShelfDock GitHub Issues](https://github.com/Mintflavor/shelfdock/issues)
