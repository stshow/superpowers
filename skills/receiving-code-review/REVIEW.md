# esr review: skills/receiving-code-review

Written by esr (`esr owner/repo`) from its own records. It never quotes the skill beyond what a finding's text holds; the summary and the claude review's findings below are model text.

- Upstream: obra/superpowers
- Upstream commit reviewed: 2ce8aa15d05bd57213e6f746f953aafb7ded7a8b
- Skill tree reviewed: b5e154fc3ec7a6a0b1e710eebacc2168620cc428
- Date: 2026-10-30
- Choice: keep

## What it does (claude review, model text)

    An instruction-only skill that tells the agent how to handle code review
    feedback: check suggestions against the codebase, ask about unclear items,
    push back with technical reasons, and avoid empty agreement. It also says
    how to reply to inline GitHub review comments.

## What it could do (static profile)

- no network hosts, tool grants, scripts or binaries found

## Public scores (outside opinions)

- public scores (outside opinions): Gen safe, Socket safe (0 alerts), Snyk medium; BAD: Snyk medium

## Findings

- none

## Fix applied

- none
- Fix offered: none
- No fix needed. esr found no weakness to fix.

## Claude Code reported

During this run Claude Code reported these values, which differ from what esr expects. None of them lets the reviewer act; the review went ahead.

- Claude Code version: 2.1.312 is newer than 2.1.311, the version this esr was tested on
