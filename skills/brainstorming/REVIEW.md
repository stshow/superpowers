# esr review: skills/brainstorming

Written by esr (`esr owner/repo`) from its own records. It never quotes the skill beyond what a finding's text holds; the summary and the claude review's findings below are model text.

- Upstream: obra/superpowers
- Upstream commit reviewed: 2ce8aa15d05bd57213e6f746f953aafb7ded7a8b
- Skill tree reviewed: 3d8a23691e919f5acfd31d45f76bdc168d24ca1b
- Date: 2026-10-30
- Choice: fix (re-checked and applied)

## What it does (claude review, model text)

    A brainstorming workflow that has the agent ask the user questions, lay out
    approaches and write an approved design document before any building starts.
    It can also start an optional local HTTP/WebSocket "visual companion" server
    that shows HTML mockups in the user's browser and records the user's clicks.

## What it could do (static profile)

- reaches http hosts: host, localhost
- reaches https hosts: github.com, primeradiant.com
- ships scripts: scripts/helper.js, scripts/server.cjs, scripts/start-server.sh, scripts/stop-server.sh

## Public scores (outside opinions)

- public scores (outside opinions): Gen safe, Socket safe (0 alerts), Snyk medium; BAD: Snyk medium

## Findings

- high malicious_diversion (esr rules; rule time-bomb in scripts/stop-server.sh line 23): scripts/stop-server.sh deletes files only after a certain date (time bomb)
- medium data_exfiltration (esr rules; rule dns-lookup-with-data in scripts/start-server.sh line 198): scripts/start-server.sh builds a DNS name from variable data, a known covert channel
- medium concealment (esr rules; rule log-delete in scripts/stop-server.sh line 109): scripts/stop-server.sh deletes log files
- medium undeclared_egress (claude review: model text, it can be wrong): By default, every companion page includes an \<img\> tag that loads a logo from an external host (primeradiant.com) and adds the plugin version as a query parameter. The code names this load as telemetry: it is skipped only when SUPERPOWERS\_DISABLE\_TELEMETRY, DISABLE\_TELEMETRY or CLAUDE\_CODE\_DISABLE\_NONESSENTIAL\_TRAFFIC is set. So whenever a mockup is shown, the user's browser contacts a third-party host, which reveals the user's IP address, when the companion is used, and the version. Neither SKILL.md nor visual-companion.md mentions this, and the review context lists no external services.
- low excessive_capability (claude review: model text, it can be wrong): For remote or containerised setups, the guide tells the agent to bind the companion server to all interfaces (--host 0.0.0.0). This makes the HTTP/WebSocket server reachable from the network. A per-session random key gates access, and the URL that carries the key is printed and shared.
- low path_handling (claude review: model text, it can be wrong): The review reports an unsafe temp file at line 123 of scripts/start-server.sh.
- low path_handling (claude review: model text, it can be wrong): stop-server.sh runs rm -rf on the session directory argument whenever it matches the glob /tmp/\*. The path is not normalised first, so a path that starts with /tmp/ but contains '..' segments passes the check and could point at a directory outside /tmp. To reach this code, a PID file in the given directory must name a live process whose command line holds the matching server instance id, which makes accidental misuse unlikely.
- low input_validation (claude review: model text, it can be wrong): The review reports an unquoted shell variable at line 291 of visual-companion.md.
- low secret_exposure (claude review: model text, it can be wrong): With --project-dir, the session key is saved inside the user's project in .superpowers/brainstorm/.last-token, and server-info and server.log also contain it. The skill only reminds the user to add .superpowers/ to .gitignore, and it separately tells the agent to commit design docs. If the directory is not ignored, the key file could be committed and shared.
- low prompt_injection (claude review: model text, it can be wrong): The fix investigation reports fetched text used as instructions at line 121 of visual-companion.md.
- info unsafe_execution (claude review: model text, it can be wrong): If the BRAINSTORM\_OPEN\_CMD environment variable is set, it runs through a shell (child\_process.exec) with the URL appended. The default platform launchers use execFile with argument arrays. The override only runs when --open is given and the bind is loopback.

## Fix applied

- Fix label: security
- Targets: medium undeclared\_egress
- After the fix: high malicious\_diversion (esr rules): – not addressed
- After the fix: medium data\_exfiltration (esr rules): – not addressed
- After the fix: medium concealment (esr rules): – not addressed
- After the fix: medium undeclared\_egress (claude review): \~ targeted, not re-verified
- After the fix: low excessive\_capability (claude review): – not addressed
- After the fix: low path\_handling (claude review): – not addressed
- After the fix: low path\_handling (claude review): – not addressed
- After the fix: low input\_validation (claude review): – not addressed
- After the fix: low secret\_exposure (claude review): – not addressed
- After the fix: low prompt\_injection (claude review): – not addressed
- After the fix: info unsafe\_execution (claude review): – not addressed
- Fix id: sha256:be0be04b315d531678fa543dc8be282020816ca1c6d22fc8feb09de12b27ad51
- Changed: scripts/server.cjs
- Fix offered: security, checked
- high malicious\_diversion (esr rules): No fix. The claude review says this is what the skill is for. esr still flags it.
- medium data\_exfiltration (esr rules): No fix. The claude review says this is what the skill is for. esr still flags it.
- medium concealment (esr rules): No fix. The claude review says this is what the skill is for. esr still flags it.
- low secret\_exposure (claude review): No fix by esr. Remove the secret and rotate it yourself.

## Claude Code reported

During this run Claude Code reported these values, which differ from what esr expects. None of them lets the reviewer act; the review went ahead.

- Claude Code version: 2.1.312 is newer than 2.1.311, the version this esr was tested on
