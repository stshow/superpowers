# esr review: skills/writing-plans

Written by esr (`esr owner/repo`) from its own records. It never quotes the skill beyond what a finding's text holds; the summary and the claude review's findings below are model text.

- Upstream: obra/superpowers
- Upstream commit reviewed: 2ce8aa15d05bd57213e6f746f953aafb7ded7a8b
- Skill tree reviewed: cc97fa00eb2ccd4f283e34eb2ba06a48e1e679f7
- Date: 2026-10-30
- Choice: keep

## What it does (claude review, model text)

    An instruction-only skill that has the agent write a detailed implementation
    plan (bite-sized TDD tasks, file structure, interfaces, review focus) from a
    spec, save it as a markdown file under docs/superpowers/plans, and then hand
    off to an in-package execution skill once the user has reviewed it.

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
