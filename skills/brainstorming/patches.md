# esr Patch log: skills/brainstorming

Every change made to this Upstream skill on this branch, in the order esr applies them to the Upstream text. Written by esr; esr reads the block at the end on the next run, and asks about any entry it did not record itself.

The lines an entry replaces are kept only as a hash, never as text. To see a whole change, run git diff from the entry's Upstream commit to this branch, limited to this skill's folder.

## 1. fix (security)

- Id: sha256:0456902700dd1e8cfc38515c8a038bef9f277f9431b091a575ef9f56db904a88
- Reason: Model-proposed fix for l1-fnd-ee3d87ab237a4c116d9ec6f3
- Upstream commit: 2ce8aa15d05bd57213e6f746f953aafb7ded7a8b
- Resolves: rule Default-on remote image beacon with version parameter in served pages in scripts/server.cjs

Changes scripts/server.cjs: 1 line(s) removed and 1 line(s) added, in 1 place(s).

Added:

    +const SUPERPOWERS_TELEMETRY_DISABLED = !isTruthyEnv(process.env.SUPERPOWERS_ENABLE_TELEMETRY) || TELEMETRY_DISABLE_ENV_VARS.some(name => isTruthyEnv(process.env[name]));

```esr-patches
{"entries":[{"entry":{"changes":[{"hunks":[{"edits":[{"add":"const SUPERPOWERS_TELEMETRY_DISABLED = !isTruthyEnv(process.env.SUPERPOWERS_ENABLE_TELEMETRY) || TELEMETRY_DISABLE_ENV_VARS.some(name => isTruthyEnv(process.env[name]));\n","at":3,"remove":1}],"old_bytes":362,"old_digest":"sha256:e839c7ffc426fd7e8fb49cc60c9a4f55fe51ef0454338e264375e57cd6777fb1","old_lines":7}],"old_bytes":null,"old_digest":null,"op":"change","path":"scripts/server.cjs"}],"kind":"fix (security)","reason":"Model-proposed fix for l1-fnd-ee3d87ab237a4c116d9ec6f3","resolved":[{"file":"scripts/server.cjs","rule":"Default-on remote image beacon with version parameter in served pages"}],"upstream_commit":"2ce8aa15d05bd57213e6f746f953aafb7ded7a8b"},"id":"sha256:0456902700dd1e8cfc38515c8a038bef9f277f9431b091a575ef9f56db904a88"}],"skill":"skills/brainstorming","version":1}
```
