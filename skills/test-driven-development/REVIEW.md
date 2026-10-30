# esr review: skills/test-driven-development

Written by esr (`esr owner/repo`) from its own records. It never quotes the skill beyond what a finding's text holds; the summary and the claude review's findings below are model text.

- Upstream: obra/superpowers
- Upstream commit reviewed: 2ce8aa15d05bd57213e6f746f953aafb7ded7a8b
- Skill tree reviewed: 847144cf0824095922c0d4875648b9fa74877e1a
- Date: 2026-10-30
- Choice: keep

## What it does (claude review, model text)

    An instruction-only skill that makes the agent follow strict test-driven
    development: write a failing test, watch it fail, write minimal code to
    pass, refactor, and run the project's whole test suite. A reference file
    gives rules for writing good tests and mocks.

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
