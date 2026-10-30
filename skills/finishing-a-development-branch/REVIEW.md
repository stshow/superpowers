# esr review: skills/finishing-a-development-branch

Written by esr (`esr owner/repo`) from its own records. It never quotes the skill beyond what a finding's text holds; the summary and the claude review's findings below are model text.

- Upstream: obra/superpowers
- Upstream commit reviewed: 2ce8aa15d05bd57213e6f746f953aafb7ded7a8b
- Skill tree reviewed: 3b1205aa5038c71946077dd63b9e71b447729e70
- Date: 2026-10-30
- Choice: keep

## What it does (claude review, model text)

    Guides the agent through finishing a development branch. It runs the test
    suite, works out whether it is in a normal repo or a git worktree, shows a
    fixed menu (merge locally, push and open a PR, or keep the branch), carries
    out the user's choice with git, and removes only the worktrees it created.

## What it could do (static profile)

- no network hosts, tool grants, scripts or binaries found

## Public scores (outside opinions)

- public scores (outside opinions): Gen safe, Socket safe (0 alerts), Snyk low

## Findings

- none

## Fix applied

- none

## Claude Code reported

During this run Claude Code reported these values, which differ from what esr expects. None of them lets the reviewer act; the review went ahead.

- Claude Code version: 2.1.312 is newer than 2.1.311, the version this esr was tested on
