# esr Patch log: skills/using-superpowers

Every change made to this Upstream skill on this branch, in the order esr applies them to the Upstream text. Written by esr; esr reads the block at the end on the next run, and asks about any entry it did not record itself.

The lines an entry replaces are kept only as a hash, never as text. To see a whole change, run git diff from the entry's Upstream commit to this branch, limited to this skill's folder.

## 1. fix (hygiene)

- Id: sha256:59ba7dc6aff91b27e7b21275f6080dccffe8346f0e1dd07992dc71e0f602cf26
- Reason: Model-proposed fix for l1-fnd-db74e1db172d555fd82b204d; Model-proposed fix for l1-fnd-b0e8f14b4a811b4f467cf202
- Upstream commit: 2ce8aa15d05bd57213e6f746f953aafb7ded7a8b
- Resolves: rule Always-on metadata trigger combined with coercive steering language in SKILL.md
- Resolves: rule Reference guidance edits a persistent agent configuration file in references/codex-tools.md

Changes SKILL.md: 1 line(s) removed and 1 line(s) added, in 1 place(s).

Added:

    +User instructions still take precedence over this rule (see User Instructions below).

Changes references/codex-tools.md: 1 line(s) removed and 1 line(s) added, in 1 place(s).

Added:

    +Multi-agent tools need this in the Codex config (`~/.codex/config.toml`); do not edit that file yourself, and tell your human partner it is needed if the tools are missing:

```esr-patches
{"entries":[{"entry":{"changes":[{"hunks":[{"edits":[{"add":"User instructions still take precedence over this rule (see User Instructions below).\n","at":3,"remove":1}],"old_bytes":183,"old_digest":"sha256:727e2573619ae58163a1701ace9b10e272ef024cbc22c6d1ccc955e3f1151b24","old_lines":7}],"old_bytes":null,"old_digest":null,"op":"change","path":"SKILL.md"},{"hunks":[{"edits":[{"add":"Multi-agent tools need this in the Codex config (`~/.codex/config.toml`); do not edit that file yourself, and tell your human partner it is needed if the tools are missing:\n","at":2,"remove":1}],"old_bytes":122,"old_digest":"sha256:43449e9d4efb2b745d86e2f777949db3d0c6ade036faa05f44abc030f7b1560e","old_lines":6}],"old_bytes":null,"old_digest":null,"op":"change","path":"references/codex-tools.md"}],"kind":"fix (hygiene)","reason":"Model-proposed fix for l1-fnd-db74e1db172d555fd82b204d; Model-proposed fix for l1-fnd-b0e8f14b4a811b4f467cf202","resolved":[{"file":"SKILL.md","rule":"Always-on metadata trigger combined with coercive steering language"},{"file":"references/codex-tools.md","rule":"Reference guidance edits a persistent agent configuration file"}],"upstream_commit":"2ce8aa15d05bd57213e6f746f953aafb7ded7a8b"},"id":"sha256:59ba7dc6aff91b27e7b21275f6080dccffe8346f0e1dd07992dc71e0f602cf26"}],"skill":"skills/using-superpowers","version":1}
```
