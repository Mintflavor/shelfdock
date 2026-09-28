# ShelfDock public repository working agreement

This repository (`Mintflavor/shelfdock`) contains public documentation, site content and release assets. Product source, operational configuration, private profiles, keys, OTPs and certificates belong outside this repository. The source repository is private (`Mintflavor/shelfdock-private`).

## Checkout and branch lifecycle

- Before dispatching work involving this repository, and again before reviewing its handoff or release documents, the orchestrator verifies the intended repository and branch, runs `git pull --ff-only origin <branch>` in the existing checkout, and records the resulting full commit hash. The worker also pulls its intended base before starting and reports base/head hashes. For a PR, refresh the exact head branch and `main` and compare with the remote PR. Do not review stale local files.
- Preserve local changes if a pull cannot fast-forward or the checkout is in use. Do not force-pull, reset, or stash someone else's changes. Resolve the condition before review and report the blocked refresh if it cannot be resolved.
- Keep one checkout of this public repository and one checkout of the private source repository per machine. Use task branches in the existing checkout for routine Windows and macOS work; switch branches after preserving local changes. Do not create extra clones or worktrees for routine tasks.
- Open a focused PR for tracked changes. After merge, the orchestrator verifies the merge and removes the completed local and remote task branches. Preserve uncommitted, unpushed and ignored work before cleanup.
- Keep `main`. Keep `gh-pages` while GitHub Pages serves from that branch; change the Pages source and verify the site before considering its removal.
- Release assets are uploaded only after the platform's exact package, checksum and contents are verified. Drafts remain unpublished until their stated acceptance gates pass. Record Windows and Mac results separately and never infer one platform's runtime result from the other.
