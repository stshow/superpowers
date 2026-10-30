# esr review: skills/using-superpowers

Written by esr (`esr owner/repo`) from its own records. It never quotes the skill beyond what a finding's text holds; the summary and the claude review's findings below are model text.

- Upstream: obra/superpowers
- Upstream commit reviewed: 2ce8aa15d05bd57213e6f746f953aafb7ded7a8b
- Skill tree reviewed: 4c777432715fe58984d212a36aedc6a18472e512
- Date: 2026-10-30
- Choice: fix (re-checked and applied)

## What it does (claude review, model text)

    A bootstrap skill for the Superpowers skill package. It tells the agent to
    check for and invoke relevant in-package skills before responding or acting,
    and it gives per-harness reference notes that map generic skill actions
    (subagent dispatch, todos, file reads) onto each agent platform's tools.

## What it could do (static profile)

- no network hosts, tool grants, scripts or binaries found

## Public scores (outside opinions)

- public scores (outside opinions): Gen medium, Socket safe (0 alerts), Snyk low; BAD: Gen medium

## Findings

- low instruction_override (claude review: model text, it can be wrong): The description makes the skill trigger at the start of every conversation and requires a skill invocation before any response, including clarifying questions. The body uses forceful, non-negotiable wording ("ABSOLUTELY MUST", "YOU DO NOT HAVE A CHOICE", "You cannot rationalize your way out of this") and a 'Red Flags' table that pre-empts the agent's own judgment about whether a skill is needed. This changes the agent's default behaviour across all sessions. The skill also says that user instructions (CLAUDE.md, direct requests) take precedence and that a skill can be dropped if it does not fit, so it does not override the user. The steering only routes to skills in the same package.
- info persistence (claude review: model text, it can be wrong): The Codex reference tells the agent to add settings to the user's Codex config file (enable multi\_agent, set default subagent model and reasoning effort). For the backstop setting, the text says to ask the human partner to add it. These are agent-configuration changes that last beyond the session, but they are narrow and serve the stated subagent workflow.

## Fix applied

- Fix label: hygiene
- Targets: low instruction\_override
- Targets: info persistence
- After the fix: low instruction\_override (claude review): \~ targeted, not re-verified
- After the fix: info persistence (claude review): \~ targeted, not re-verified
- Fix id: sha256:1ad97e48c141e68068b3cfa15452a6682e7c094b4aeaf91cf71705fa6a25f634
- Changed: SKILL.md
- Changed: references/codex-tools.md
- Fix offered: hygiene, checked

## Claude Code reported

During this run Claude Code reported these values, which differ from what esr expects. None of them lets the reviewer act; the review went ahead.

- Claude Code version: 2.1.312 is newer than 2.1.311, the version this esr was tested on
