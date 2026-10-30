# esr review: skills/subagent-driven-development

Written by esr (`esr owner/repo`) from its own records. It never quotes the skill beyond what a finding's text holds; the summary and the claude review's findings below are model text.

- Upstream: obra/superpowers
- Upstream commit reviewed: 2ce8aa15d05bd57213e6f746f953aafb7ded7a8b
- Skill tree reviewed: 98c875856cf40765616a4565f09b437f0c58992b
- Date: 2026-10-30
- Choice: fix (re-checked and applied)

## What it does (claude review, model text)

    Runs an implementation plan in the current session. For each task it sends a
    fresh implementer subagent, then a task reviewer, then a fix loop if needed,
    and ends with a whole-branch review. Progress is tracked in a ledger file
    inside a git-ignored workspace in the repository, using three small bash
    helper scripts.

## What it could do (static profile)

- ships scripts: scripts/review-package, scripts/sdd-workspace, scripts/task-brief

## Public scores (outside opinions)

- public scores (outside opinions): Gen safe, Socket safe (0 alerts), Snyk low

## Findings

- critical prompt_injection (esr rules; rule reviewer-targeting in SKILL.md line 329): SKILL.md addresses a security reviewer to influence the verdict
- critical prompt_injection (esr rules; rule reviewer-targeting in references/fix-loop.md line 57): references/fix-loop.md addresses a security reviewer to influence the verdict
- low input_validation (claude review: model text, it can be wrong): The TASK\_NUMBER argument is never checked to be numeric. It goes straight into the default output file name ('$dir/task-${n}-brief.md') and into the awk regular expression that matches the task heading. A value containing path separators or '..' would write the brief outside the plan workspace, and regex metacharacters would change which plan text gets pulled out. The agent supplies this value from the plan, so the realistic impact is a misplaced or wrong brief file, not an attack.
- low prompt_injection (claude review: model text, it can be wrong): The fix investigation reports fetched text used as instructions at line 38 of task-reviewer-prompt.md.
- info other (claude review: model text, it can be wrong): The skill tells the agent to run the whole plan without checking in with the user and to settle conflicts, ambiguities and plan defects on its own, recording each decision as a 'Ruling:' line in the ledger. Subagents implement, run tests and commit with no human step in between. The skill names four stop conditions (irreversible or destructive operations, security-sensitive actions, side effects outside the worktree such as a merge, push or publish, and a hopelessly broken plan). It also requires every ruling to be listed for the user at the end. Even so, whether something counts as a stop condition is left to the agent, and plan content directly drives the commands that get run.

## Fix applied

- Fix label: hygiene
- Targets: low input\_validation
- Targets: low prompt\_injection
- Targets: info other
- After the fix: critical prompt\_injection (esr rules): – not addressed
- After the fix: critical prompt\_injection (esr rules): – not addressed
- After the fix: low input\_validation (claude review): \~ targeted, not re-verified
- After the fix: low prompt\_injection (claude review): \~ targeted, not re-verified
- After the fix: info other (claude review): \~ targeted, not re-verified
- Fix id: sha256:d6dbaa1e36679befe391c7f45d5f4f683b547028b47ec382358e1989ab10560c
- Changed: SKILL.md
- Changed: scripts/task-brief
- Changed: task-reviewer-prompt.md
- Fix offered: hygiene, checked
- critical prompt\_injection (esr rules): No fix. The claude review says this is what the skill is for. esr still flags it.
- critical prompt\_injection (esr rules): No fix. The claude review says this is what the skill is for. esr still flags it.

## Claude Code reported

During this run Claude Code reported these values, which differ from what esr expects. None of them lets the reviewer act; the review went ahead.

- Claude Code version: 2.1.312 is newer than 2.1.311, the version this esr was tested on
