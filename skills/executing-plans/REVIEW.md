# esr review: skills/executing-plans

Written by esr (`esr owner/repo`) from its own records. It never quotes the skill beyond what a finding's text holds; the summary and the claude review's findings below are model text.

- Upstream: obra/superpowers
- Upstream commit reviewed: 2ce8aa15d05bd57213e6f746f953aafb7ded7a8b
- Skill tree reviewed: 1374506e051a95c35f04654ebde9c5d845d7c7cb
- Date: 2026-10-30
- Choice: fix (re-checked and applied)

## What it does (claude review, model text)

    Guides the agent through carrying out an implementation plan inline in the
    current session, one task at a time. Each task is driven by tests, progress
    is kept in a ledger file in a git-ignored workspace, and a single whole-
    branch code review happens at the end. Two helper scripts pull out each
    task's brief and run the task's test command before the result is recorded.

## What it could do (static profile)

- ships scripts: scripts/task-done, scripts/task-start

## Public scores (outside opinions)

- public scores (outside opinions): Gen safe, Socket safe (0 alerts), Snyk low

## Findings

- low input_validation (claude review: model text, it can be wrong): The task number argument is never checked to be numeric. It goes straight into the test-log path ("$dir/task-${n}-tests.log"), and the script truncates that file with the test output. If the value contains path separators or '..' segments, the log can be written outside the plan's workspace. The value comes from the agent, which reads it from a user-supplied plan, so in practice this is a hygiene problem and not an attack path.
- low other (claude review: model text, it can be wrong): The review reports a late safety rule at line 301 of SKILL.md. This safety rule is after the first 5,000 tokens. Claude Code can drop it when it compacts a conversation.

## Fix applied

- Fix label: hygiene
- Targets: low input\_validation
- Targets: low other
- After the fix: low input\_validation (claude review): \~ targeted, not re-verified
- After the fix: low other (claude review): \~ targeted, not re-verified
- Fix id: sha256:5cdab1f8294e9f4e286a033ce5cd91b6aef44a6423c544f368ee69e816ce3db3
- Changed: SKILL.md
- Changed: scripts/task-done
- Fix offered: hygiene, checked

## Claude Code reported

During this run Claude Code reported these values, which differ from what esr expects. None of them lets the reviewer act; the review went ahead.

- Claude Code version: 2.1.312 is newer than 2.1.311, the version this esr was tested on
