# esr Patch log: skills/using-git-worktrees

Every change made to this Upstream skill on this branch, in the order esr applies them to the Upstream text. Written by esr; esr reads the block at the end on the next run, and asks about any entry it did not record itself.

The lines an entry replaces are kept only as a hash, never as text. To see a whole change, run git diff from the entry's Upstream commit to this branch, limited to this skill's folder.

## 1. fix (hygiene)

- Id: sha256:5b086439ba330d32d859157040c741f31af69a9399bf863013ae5328a42a8295
- Reason: Model-proposed fix for l1-fnd-3638f25af3cd845b088d0918
- Upstream commit: 2ce8aa15d05bd57213e6f746f953aafb7ded7a8b
- Resolves: rule Automatic execution of project-defined install, build and test commands in SKILL.md

Changes SKILL.md: 1 line(s) removed and 1 line(s) added, in 1 place(s).

Added:

    +Auto-detect and run appropriate setup. These commands, and the Step 3 tests, run code that the project controls. If the user did not write the repository and has not said they trust it, run them only in a sandbox:

```esr-patches
{"entries":[{"entry":{"changes":[{"hunks":[{"edits":[{"add":"Auto-detect and run appropriate setup. These commands, and the Step 3 tests, run code that the project controls. If the user did not write the repository and has not said they trust it, run them only in a sandbox:\n","at":3,"remove":1}],"old_bytes":85,"old_digest":"sha256:d4890601f15f10845124059f5d2be37e90d018958a2c358769c5f826361f9a3b","old_lines":7}],"old_bytes":null,"old_digest":null,"op":"change","path":"SKILL.md"}],"kind":"fix (hygiene)","reason":"Model-proposed fix for l1-fnd-3638f25af3cd845b088d0918","resolved":[{"file":"SKILL.md","rule":"Automatic execution of project-defined install, build and test commands"}],"upstream_commit":"2ce8aa15d05bd57213e6f746f953aafb7ded7a8b"},"id":"sha256:5b086439ba330d32d859157040c741f31af69a9399bf863013ae5328a42a8295"}],"skill":"skills/using-git-worktrees","version":1}
```
