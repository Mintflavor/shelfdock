# ShelfDock v0.1.4-beta — draft

Windows 11 x64, self-contained, unsigned.

Explicitly removing a received file/image also deletes its owned AppData cache and empty download folder. Sender originals and exported copies stay untouched. Undo restores the item for re-download. Locked files retry on restart; another live shelf reference protects the cache. Downloads completing after removal are discarded.

Accepted-drop auto-remove retains the previous seven-day policy to protect applications still reading files. Old retired caches are not bulk-deleted retroactively.

Passed: 38 Core safety checks, 16 Windows workflow checks and packaging guard. User confirmed Korean filenames, icons, pins, missing-file styling, automatic settings, connection settings and progress in 0.1.3. Large-file native drag, WAN, clean Windows, DPI and performance acceptance remain pending. Release remains draft. No relay update needed.
