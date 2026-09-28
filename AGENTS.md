# ShelfDock public repository working agreement

This repository (`Mintflavor/shelfdock`) contains public documentation, site content and release assets. Product source, operational configuration, private profiles, keys, OTPs and certificates belong outside this repository. The source repository is private (`Mintflavor/shelfdock-private`).

## Checkout and branch lifecycle

- Keep one checkout of this public repository and one checkout of the private source repository per machine. Use task branches in the existing checkout for routine Windows and macOS work; switch branches after preserving local changes. Do not create extra clones or worktrees for routine tasks.
- Open a focused PR for tracked changes. After merge, the orchestrator verifies the merge and removes the completed local and remote task branches. Preserve uncommitted, unpushed and ignored work before cleanup.
- Keep `main`. Keep `gh-pages` while GitHub Pages serves from that branch; change the Pages source and verify the site before considering its removal.
- Release assets are uploaded only after the platform's exact package, checksum and contents are verified. Drafts remain unpublished until their stated acceptance gates pass. Record Windows and Mac results separately and never infer one platform's runtime result from the other.
