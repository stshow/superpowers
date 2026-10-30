# esr Patch log: skills/writing-skills

Every change made to this Upstream skill on this branch, in the order esr applies them to the Upstream text. Written by esr; esr reads the block at the end on the next run, and asks about any entry it did not record itself.

The lines an entry replaces are kept only as a hash, never as text. To see a whole change, run git diff from the entry's Upstream commit to this branch, limited to this skill's folder.

## 1. fix (hygiene)

- Id: sha256:9ea762b30c2f9192d509136d109ce549cd481e94f5f94e1df71550cde998661b
- Reason: Model-proposed fix for sf-0001, l1-fnd-b9b2fdb71f927f5d7c685bac; Model-proposed fix for l1-fnd-9c3a1a67dd68a4c2500e6d89; Model-proposed fix for l1-fnd-3ad7d53d3107854448b4e1b6; Model-proposed fix for l1-fnd-e56e9192f39923b2c3bbca78
- Upstream commit: 2ce8aa15d05bd57213e6f746f953aafb7ded7a8b
- Resolves: rule Absolute process rule that can conflict with the user's explicit request in SKILL.md
- Resolves: rule Checklist item that pushes to a remote with the user's identity in SKILL.md
- Resolves: rule Repeated paid model calls are part of the testing workflow, with no cost limit in SKILL.md
- Resolves: rule Unpinned install shown as recommended example in references/anthropic-best-practices.md
- Resolves: rule unpinned-install in references/anthropic-best-practices.md

Changes SKILL.md: 5 line(s) removed and 4 line(s) added, in 3 place(s).

Added:

    +This applies to NEW skills AND EDITS to existing skills. It disciplines your own drafts and never overrides the user: don't discard or refuse a change the user explicitly asked for.
    +1. **One fresh-context sample per call** — a single-shot subagent, or a raw API call only if the user asked for one; stop at 5 reps per variant plus the control. System prompt = the realistic context the guidance will live in (the full skill or prompt template, not the guidance in isolation); user message = a task that tempts the failure.
    +3. **5 reps per variant.** Single samples lie.
    +- [ ] Commit skill to git; push to your fork or open a PR only if the user asked for it

Changes references/anthropic-best-practices.md: 1 line(s) removed and 1 line(s) added, in 1 place(s).

Added:

    +"Install required package: `pip install pypdf==5.1.0`

```esr-patches
{"entries":[{"entry":{"changes":[{"hunks":[{"edits":[{"add":"This applies to NEW skills AND EDITS to existing skills. It disciplines your own drafts and never overrides the user: don't discard or refuse a change the user explicitly asked for.\n","at":3,"remove":1}],"old_bytes":196,"old_digest":"sha256:2bda43dd1404a99bd771b2d8e6f7730ad1fff8268f246e97e720bc97978252d7","old_lines":7},{"edits":[{"add":"1. **One fresh-context sample per call** \u2014 a single-shot subagent, or a raw API call only if the user asked for one; stop at 5 reps per variant plus the control. System prompt = the realistic context the guidance will live in (the full skill or prompt template, not the guidance in isolation); user message = a task that tempts the failure.\n","at":3,"remove":1},{"add":"3. **5 reps per variant.** Single samples lie.\n","at":5,"remove":1}],"old_bytes":1052,"old_digest":"sha256:a27401c7775fc87e2697157d3e8443507d8293e9d9690b695894f1f44a7c2f48","old_lines":9},{"edits":[{"add":"- [ ] Commit skill to git; push to your fork or open a PR only if the user asked for it\n","at":3,"remove":2}],"old_bytes":222,"old_digest":"sha256:a67211492dc68690270133157a86aecdaab03e5533d24e936bba4e226b7f2e3a","old_lines":8}],"old_bytes":null,"old_digest":null,"op":"change","path":"SKILL.md"},{"hunks":[{"edits":[{"add":"\"Install required package: `pip install pypdf==5.1.0`\n","at":3,"remove":1}],"old_bytes":162,"old_digest":"sha256:d27eae60303fe8c0c744ff64da1b9d90b1f57f0b649237610227486dc179ddfc","old_lines":7}],"old_bytes":null,"old_digest":null,"op":"change","path":"references/anthropic-best-practices.md"}],"kind":"fix (hygiene)","reason":"Model-proposed fix for sf-0001, l1-fnd-b9b2fdb71f927f5d7c685bac; Model-proposed fix for l1-fnd-9c3a1a67dd68a4c2500e6d89; Model-proposed fix for l1-fnd-3ad7d53d3107854448b4e1b6; Model-proposed fix for l1-fnd-e56e9192f39923b2c3bbca78","resolved":[{"file":"SKILL.md","rule":"Absolute process rule that can conflict with the user's explicit request"},{"file":"SKILL.md","rule":"Checklist item that pushes to a remote with the user's identity"},{"file":"SKILL.md","rule":"Repeated paid model calls are part of the testing workflow, with no cost limit"},{"file":"references/anthropic-best-practices.md","rule":"Unpinned install shown as recommended example"},{"file":"references/anthropic-best-practices.md","rule":"unpinned-install"}],"upstream_commit":"2ce8aa15d05bd57213e6f746f953aafb7ded7a8b"},"id":"sha256:9ea762b30c2f9192d509136d109ce549cd481e94f5f94e1df71550cde998661b"}],"skill":"skills/writing-skills","version":1}
```
