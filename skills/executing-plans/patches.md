# esr Patch log: skills/executing-plans

Every change made to this Upstream skill on this branch, in the order esr applies them to the Upstream text. Written by esr; esr reads the block at the end on the next run, and asks about any entry it did not record itself.

The lines an entry replaces are kept only as a hash, never as text. To see a whole change, run git diff from the entry's Upstream commit to this branch, limited to this skill's folder.

## 1. fix (hygiene)

- Id: sha256:11c7fdaed459882a02996b745b38d4b50c794aeb0ba9faae0e734d1a3f1e31a2
- Reason: Model-proposed fix for l1-fnd-59d97314e475694efa1a9fc1; Model-proposed fix for l1-fnd-ad36adebbb06366eef4e0ca3
- Upstream commit: 2ce8aa15d05bd57213e6f746f953aafb7ded7a8b
- Resolves: rule Unvalidated task-number argument interpolated into a file path in scripts/task-done
- Resolves: rule raised weakness late\_safety\_rule in SKILL.md

Changes SKILL.md: 2 line(s) removed and 3 line(s) added, in 2 place(s).

Added:

    +
    +Sibling directories belong to other plans; leave them alone.
    +plan's workspace directory — the git history is the record now.

Changes scripts/task-done: 0 line(s) removed and 1 line(s) added, in 1 place(s).

Added:

    +case "$n" in ''|*[!0-9]*) echo "bad TASK_NUMBER: $n" >&2; exit 2 ;; esac

```esr-patches
{"entries":[{"entry":{"changes":[{"hunks":[{"edits":[{"add":"\nSibling directories belong to other plans; leave them alone.\n","at":3,"remove":0}],"old_bytes":170,"old_digest":"sha256:878e1121cea6bd28cbcea6d8017f8ede767277521a6f08bd2808f9fc08a855b1","old_lines":6},{"edits":[{"add":"plan's workspace directory \u2014 the git history is the record now.\n","at":3,"remove":2}],"old_bytes":318,"old_digest":"sha256:e044302adffd750afe43ceaae8c1268f5cbb1b6299748ec34f69091a27e4c030","old_lines":8}],"old_bytes":null,"old_digest":null,"op":"change","path":"SKILL.md"},{"hunks":[{"edits":[{"add":"case \"$n\" in ''|*[!0-9]*) echo \"bad TASK_NUMBER: $n\" >&2; exit 2 ;; esac\n","at":3,"remove":0}],"old_bytes":109,"old_digest":"sha256:c14c2c21ab2a3134fa745a1d7dd37b36b5c80b5a2fcb8e2eb26df20d58bd5305","old_lines":6}],"old_bytes":null,"old_digest":null,"op":"change","path":"scripts/task-done"}],"kind":"fix (hygiene)","reason":"Model-proposed fix for l1-fnd-59d97314e475694efa1a9fc1; Model-proposed fix for l1-fnd-ad36adebbb06366eef4e0ca3","resolved":[{"file":"scripts/task-done","rule":"Unvalidated task-number argument interpolated into a file path"},{"file":"SKILL.md","rule":"raised weakness late_safety_rule"}],"upstream_commit":"2ce8aa15d05bd57213e6f746f953aafb7ded7a8b"},"id":"sha256:11c7fdaed459882a02996b745b38d4b50c794aeb0ba9faae0e734d1a3f1e31a2"}],"skill":"skills/executing-plans","version":1}
```
