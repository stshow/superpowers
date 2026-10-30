# esr review: skills/requesting-code-review

Written by esr (`esr owner/repo`) from its own records. It never quotes the skill beyond what a finding's text holds; the summary and the claude review's findings below are model text.

- Upstream: obra/superpowers
- Upstream commit reviewed: 2ce8aa15d05bd57213e6f746f953aafb7ded7a8b
- Skill tree reviewed: f4a6749898702895ea4fd57c7f186cf43205b99a
- Date: 2026-10-30
- Choice: fix (re-checked and applied)

## What it does (claude review, model text)

    The skill tells the agent to send a general-purpose code reviewer subagent
    to check completed work, using a filled-in template (code-reviewer.md). The
    template gives the subagent a description of the change, the plan or
    requirements, and a git commit range. The subagent returns findings sorted
    by severity and a verdict on whether the work is ready to merge.

## What it could do (static profile)

- no network hosts, tool grants, scripts or binaries found

## Public scores (outside opinions)

- public scores (outside opinions): Gen safe, Socket safe (0 alerts), Snyk low

## Findings

- critical prompt_injection (esr rules; rule reviewer-targeting in SKILL.md line 85): SKILL.md addresses a security reviewer to influence the verdict
- low path_handling (claude review: model text, it can be wrong): The review reports an unsafe temp file at line 52 of code-reviewer.md.
- low path_handling (claude review: model text, it can be wrong): The fix investigation reports an unsafe temp file at line 52 of code-reviewer.md.
- low prompt_injection (claude review: model text, it can be wrong): The fix investigation reports fetched text used as instructions at line 30 of code-reviewer.md.

## Fix applied

- Fix label: hygiene
- Targets: low path\_handling
- Targets: low prompt\_injection
- After the fix: critical prompt\_injection (esr rules): – not addressed
- After the fix: low path\_handling (claude review): \~ targeted, not re-verified
- After the fix: low path\_handling (claude review): – not addressed
- After the fix: low prompt\_injection (claude review): \~ targeted, not re-verified
- Fix id: sha256:05593f603c646b7952bd3898f29a61b2ea98c08b84a502433d88c3fef4a81f48
- Changed: code-reviewer.md
- Fix offered: hygiene, checked
- critical prompt\_injection (esr rules): No fix. The claude review says this is what the skill is for. esr still flags it.
- low path\_handling (claude review): No fix. The fix did not apply to the files.

## Claude Code reported

During this run Claude Code reported these values, which differ from what esr expects. None of them lets the reviewer act; the review went ahead.

- Claude Code version: 2.1.312 is newer than 2.1.311, the version this esr was tested on
