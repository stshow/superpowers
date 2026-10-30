# esr Patch log: skills/systematic-debugging

Every change made to this Upstream skill on this branch, in the order esr applies them to the Upstream text. Written by esr; esr reads the block at the end on the next run, and asks about any entry it did not record itself.

The lines an entry replaces are kept only as a hash, never as text. To see a whole change, run git diff from the entry's Upstream commit to this branch, limited to this skill's folder.

## 1. fix (hygiene)

- Id: sha256:f6508b8f09b1f6bad433bfbb73a7ff5b84ddfab8acbe3d143fe6df999eb4c4ec
- Reason: Model-proposed fix for l1-fnd-a25a75d9bef6cb29e20e8e82; Model-proposed fix for l1-fnd-60b2ea8fb0c28bc9aab8faee
- Upstream commit: 2ce8aa15d05bd57213e6f746f953aafb7ded7a8b
- Resolves: rule Illustrative diagnostics touch credential stores in SKILL.md
- Resolves: rule raised weakness unquoted\_shell in find-polluter.sh

Changes SKILL.md: 1 line(s) removed and 1 line(s) added, in 1 place(s).

Added:

    +   # Layer 3: Signing script (run only inside the CI job being debugged, never against the user's own keychain)

Changes find-polluter.sh: 2 line(s) removed and 3 line(s) added, in 2 place(s).

Added:

    +while IFS= read -r TEST_FILE <&3; do
    +  [ -n "$TEST_FILE" ] || continue
    +done 3<<< "$TEST_FILES"

```esr-patches
{"entries":[{"entry":{"changes":[{"hunks":[{"edits":[{"add":"   # Layer 3: Signing script (run only inside the CI job being debugged, never against the user's own keychain)\n","at":3,"remove":1}],"old_bytes":273,"old_digest":"sha256:5285cefbd837af9ed961dfde753aee59363fd55524702770abcf2df6c2815961","old_lines":7}],"old_bytes":null,"old_digest":null,"op":"change","path":"SKILL.md"},{"hunks":[{"edits":[{"add":"while IFS= read -r TEST_FILE <&3; do\n  [ -n \"$TEST_FILE\" ] || continue\n","at":3,"remove":1}],"old_bytes":111,"old_digest":"sha256:a0b4a9e89182bdafeeb1b55e07fbbec31b05bce4da7a73918a4999860cb22159","old_lines":7},{"edits":[{"add":"done 3<<< \"$TEST_FILES\"\n","at":3,"remove":1}],"old_bytes":133,"old_digest":"sha256:7378425197d8548bc3361de5ed5ac235e245f7edb46cdcdedd16132fafc0bab2","old_lines":7}],"old_bytes":null,"old_digest":null,"op":"change","path":"find-polluter.sh"}],"kind":"fix (hygiene)","reason":"Model-proposed fix for l1-fnd-a25a75d9bef6cb29e20e8e82; Model-proposed fix for l1-fnd-60b2ea8fb0c28bc9aab8faee","resolved":[{"file":"SKILL.md","rule":"Illustrative diagnostics touch credential stores"},{"file":"find-polluter.sh","rule":"raised weakness unquoted_shell"}],"upstream_commit":"2ce8aa15d05bd57213e6f746f953aafb7ded7a8b"},"id":"sha256:f6508b8f09b1f6bad433bfbb73a7ff5b84ddfab8acbe3d143fe6df999eb4c4ec"}],"skill":"skills/systematic-debugging","version":1}
```
