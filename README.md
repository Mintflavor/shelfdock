# ShelfDock

**A small place to put things between tasks.**

ShelfDock is a floating, always-on-top shelf for Windows. Collect files, screenshots, and text; drag them into the app where you need them.

[한국어](README.ko.md) · [User guide](USER-GUIDE.md) · [Releases](https://github.com/Mintflavor/shelfdock/releases) · [Report an issue](https://github.com/Mintflavor/shelfdock/issues)

## Availability

The first Windows 11 x64 beta is being validated. The release candidate remains a draft until the published [release checklist](QA.md) is complete. There is no public binary download yet.

Once available, download `ShelfDock-v0.2.0-beta-win-x64.zip` from Releases, extract the entire ZIP, and run `ShelfDock.exe`. No separate .NET installation or administrator rights are required. The beta is unsigned; Windows may not verify its publisher. Do not disable security protections.

New pairing uses an [8-character OTP](OTP-GUIDE.md), device comparison and approval on both PCs within 60 seconds. Update both devices; invitation links and QR are retired. Existing paired devices remain connected.

## What it does

- Optional persistent floating icon accepts drops and opens the shelf on click. Close returns to the icon.
- Self-host a Linux Docker relay on Unraid; see [Docker setup](RELAY-DOCKER.md).
- Open your shelf with `Ctrl+Alt+S` or the tray icon.
- Collect local files and text, or paste a screenshot.
- Select several files and drag them out together.
- Keep frequently used items pinned; undo removals during the current session.
- Restore the shelf after restarting. Choose English or Korean.
- Opt in to paired-device mirroring, metadata-first files and verified downloads. See [device and relay setup](P2P-GUIDE.md).

Your original files stay where they are. ShelfDock stores file references and allows Copy-only outgoing transfers. Removing an item does not delete its original. Optional auto-remove is off by default. A drop being accepted is not a guarantee that an upload has finished.

Sharing is off by default. When enabled, current and future local shelf contents are sent to paired devices. Public DHT discovery exposes network addresses and peer IDs; relays see traffic metadata, not plaintext content. There is no included public relay service. Actual external-network NAT/relay testing remains pending. No account, ads, telemetry, automatic clipboard monitoring, or automatic updates.

## Freeware, with private source

Free for personal, educational, and internal workplace use, with no expiry for this version. Complete unmodified official packages may be redistributed for free with all notices retained. Selling ShelfDock itself, bundling it in paid products, or distributing modified versions requires written permission. This repository contains documentation and releases, not application source code.

Read the [Freeware License Agreement](LICENSE.txt). Third-party components retain their own license terms. This project is not licensed under MIT, Apache, or GPL.

## Compatibility and feedback

Windows 11 x64 only for this beta. Folders, virtual mail attachments, mixed-type batch drags, multiple text drags, image-URL downloads, elevated target apps, and exclusive-fullscreen overlays are outside this version's support scope. See the [guide](USER-GUIDE.md) for limits and data storage.

Use Issues for reproducible bugs and focused feature requests. Never attach confidential files or the contents of your shelf. Support and future updates are best-effort.
