# esr review: skills/systematic-debugging

Written by esr (`esr owner/repo`) from its own records. It never quotes the skill beyond what a finding's text holds; the summary and the claude review's findings below are model text.

- Upstream: obra/superpowers
- Upstream commit reviewed: 2ce8aa15d05bd57213e6f746f953aafb7ded7a8b
- Skill tree reviewed: 108961c080a6837ad8a188a553e593cc5e6df62d
- Date: 2026-10-30
- Choice: fix (re-checked and applied)

## What it does (claude review, model text)

    A debugging-method skill that tells the agent to find the root cause before
    proposing a fix, using four phases: investigation, pattern analysis,
    hypothesis and implementation. It ships reference notes on root-cause
    tracing, defense-in-depth and condition-based waiting, plus a bash script
    that runs test files one at a time to find which test creates unwanted
    files.

## What it could do (static profile)

- ships scripts: condition-based-waiting-example.ts, find-polluter.sh

## Public scores (outside opinions)

- public scores (outside opinions): Gen safe, Socket safe (0 alerts), Snyk low

## Findings

- low credential_access (claude review: model text, it can be wrong): The example for gathering evidence lists macOS keychains and code-signing identities ('security list-keychains', 'security find-identity -v'), checks whether an IDENTITY secret is in the environment, and runs codesign. The example prints only SET/UNSET, not the secret value. An agent that copies the pattern could still inspect keychain or identity state on the user's machine.
- low input_validation (claude review: model text, it can be wrong): The review reports an unquoted shell variable at line 38 of find-polluter.sh.
- info unsafe_execution (claude review: model text, it can be wrong): The script finds files under the current directory that match a pattern the caller gives. It runs 'npm test' on each one and hides the output. This runs the project's own test code and npm scripts, one file after another, until the named file or directory appears.

## Fix applied

- Fix label: hygiene
- Targets: low credential\_access
- Targets: low input\_validation
- After the fix: low credential\_access (claude review): \~ targeted, not re-verified
- After the fix: low input\_validation (claude review): \~ targeted, not re-verified
- After the fix: info unsafe\_execution (claude review): – not addressed
- Fix id: sha256:bf47a67f7d72199f85c12d095c1be674fb91d712e1491c974076180f551d6306
- Changed: SKILL.md
- Changed: find-polluter.sh
- Fix offered: hygiene, checked
- info unsafe\_execution (claude review): No fix. The claude review says this is what the skill is for.

## Claude Code reported

During this run Claude Code reported these values, which differ from what esr expects. None of them lets the reviewer act; the review went ahead.

- Claude Code version: 2.1.312 is newer than 2.1.311, the version this esr was tested on
