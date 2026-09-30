# ShelfDock

**A small shelf for the things you need between tasks.**

ShelfDock is a lightweight desktop shelf for Windows and macOS. Collect files, screenshots, and text on the shelf, then drag them out wherever you need them.

[한국어](README.ko.md) · [User guide](USER-GUIDE.md) · [Privacy policy](PRIVACY.md) · [Releases](https://github.com/Mintflavor/shelfdock/releases) · [Report an issue](https://github.com/Mintflavor/shelfdock/issues)

## Availability

The official public beta (`v0.2.4-beta`) is available for **Windows 11 x64** and **macOS arm64 (Apple Silicon)** on [GitHub Releases](https://github.com/Mintflavor/shelfdock/releases/tag/v0.2.4-beta).

- **Windows 11 x64**: Download `ShelfDock-v0.2.4-beta-win-x64.zip`, extract completely, and run `ShelfDock.exe`. No separate .NET installation or administrator rights are required. If prompted by Windows SmartScreen, click *More info* -> *Run anyway*.
- **macOS (Apple Silicon)**: Download `ShelfDock-v0.2.4-beta-macOS-arm64.zip`, extract, and launch `ShelfDock.app`. If blocked by Gatekeeper, right-click (or Control+click) `ShelfDock.app` in Finder and select *Open*.
- Device-to-device sharing uses an [8-character OTP](OTP-GUIDE.md) with mutual two-way approval within 60 seconds. All transfers are end-to-end encrypted (Noise / TLS).

## What it does

- **Drop in, drag out**: Drop files and text onto the shelf, or paste screenshots directly from your clipboard (`Ctrl+V` / `Cmd+V`). Drag them out wherever you need them.
- **Floating drop target**: An optional floating icon stays on screen, accepts drops, and opens the shelf when clicked. Closing the shelf returns it to the icon.
- **Quick access**: Open your shelf anytime with `Ctrl+Alt+S` (macOS: `Cmd+Opt+S`) or via the tray/menu bar icon.
- **Batch selection**: Select multiple items and drag them out together in a single gesture.
- **Pin & Undo**: Pin frequently used items to keep them at hand; undo accidental removals anytime before quitting.
- **Session restore**: Your shelf is restored after restarting. Both English and Korean are supported.
- **Private P2P sharing**: Optionally mirror your shelf across paired devices, with metadata-first transfers and verified downloads. See [device and relay setup](P2P-GUIDE.md).
- **Self-hosted relay**: Run your own Linux Docker relay on Unraid or any server; see [Docker setup](RELAY-DOCKER.md).

Your original files stay where they are. ShelfDock stores file references and allows Copy-only outgoing transfers. Removing an item from the shelf never deletes the original file.

Automatic removal after an accepted drop is off by default. A successful drop means the destination accepted the data; background reading or uploading in the target app may still be in progress.

Sharing is off by default. When enabled, current and future local shelf contents are shared with paired devices. Public DHT discovery may expose network addresses and peer IDs; relays see traffic metadata, never plaintext file contents. There is no included public relay service.

**No accounts. No ads. No telemetry. No automatic clipboard monitoring or updates.**

## Freeware, closed-source

ShelfDock is completely free for personal, educational, and internal workplace use, with no expiration for this version. Complete unmodified official packages may be redistributed freely with all notices retained.

Commercial sale of ShelfDock itself, bundling it into paid products, or distributing modified versions requires prior written permission. Source code is closed; this repository contains distribution documents and release assets only.

Read the [Freeware License Agreement](LICENSE.txt). Third-party components retain their own license terms.

## Compatibility and feedback

Windows 11 x64 and macOS 13+ (Apple Silicon arm64) for this beta. Folders, virtual mail attachments, mixed-type batch drags, multiple text drags, image-URL downloads, elevated target apps, and exclusive-fullscreen overlays are outside this version's support scope. See the [guide](USER-GUIDE.md) for limits and data storage.

Use GitHub Issues to report reproducible bugs or request specific features. Never attach confidential files or private shelf contents. Support and future updates are provided on a best-effort basis.

