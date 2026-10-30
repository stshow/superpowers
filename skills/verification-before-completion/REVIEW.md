# esr review: skills/verification-before-completion

Written by esr (`esr owner/repo`) from its own records. It never quotes the skill beyond what a finding's text holds; the summary and the claude review's findings below are model text.

- Upstream: obra/superpowers
- Upstream commit reviewed: 2ce8aa15d05bd57213e6f746f953aafb7ded7a8b
- Skill tree reviewed: a4cb0b69aaefeab540947a7f1642bdaad810e37a
- Date: 2026-10-30
- Choice: keep

## What it does (claude review, model text)

    A process-discipline skill that tells the agent to run fresh verification
    commands (tests, linters, builds, VCS diffs) and read their output before it
    claims work is complete, fixed or passing, or before it commits or opens a
    PR.

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
