# esr review: skills/writing-skills

Written by esr (`esr owner/repo`) from its own records. It never quotes the skill beyond what a finding's text holds; the summary and the claude review's findings below are model text.

- Upstream: obra/superpowers
- Upstream commit reviewed: 2ce8aa15d05bd57213e6f746f953aafb7ded7a8b
- Skill tree reviewed: 660ede63b84ce5d07ef28cccc2973165e2ca06e2
- Date: 2026-10-30
- Choice: fix (re-checked and applied)

## What it does (claude review, model text)

    A guide for writing, editing and testing agent skills with a test-driven
    method: run baseline pressure scenarios on subagents, write the skill, then
    close loopholes. It ships reference documents and a small Node script that
    turns graphviz blocks in a skill's SKILL.md into SVG files.

## What it could do (static profile)

- reaches https hosts: agentskills.io, code.claude.com, mintcdn.com, platform.claude.com
- ships scripts: render-graphs.js

## Public scores (outside opinions)

- public scores (outside opinions): Gen medium, Socket safe (0 alerts), Snyk low; BAD: Gen medium

## Findings

- low mutable_dependency (esr rules; rule unpinned-install in references/anthropic-best-practices.md line 1082): references/anthropic-best-practices.md installs a package without pinning its version, so its code can change at any time
- low other (claude review: model text, it can be wrong): The mandatory per-skill deployment checklist tells the agent to commit the skill and push it to the user's fork, and suggests opening a PR upstream. This acts with the user's git identity and third-party hosting account. The skill requires this checklist for every skill, so the agent may push even when the user only asked for a local edit.
- low other (claude review: model text, it can be wrong): The skill tells the agent to micro-test wording with "a raw API call" per sample, at least 5 reps per variant plus a no-guidance control, on top of full pressure-scenario runs with subagents. If the agent has API access, this spends money on the user's model account through repeated calls. The skill sets no budget or limit on these calls.
- low instruction_override (claude review: model text, it can be wrong): The skill states an absolute rule: a skill written or edited before a failing test must be deleted and started over, with "No exceptions" even for small additions or documentation updates. It also calls the deployment checklist MANDATORY for each skill. An agent following this literally could discard edits the user asked for, or refuse a quick change the user wants. That would override the user's explicit request.
- info unsafe_execution (claude review: model text, it can be wrong): The script reads SKILL.md from any directory given on the command line, passes each dot block to the graphviz \`dot\` binary found on PATH, and writes SVG and dot files into a \`diagrams\` subdirectory it creates there. It uses execFileSync with an argument array, not a shell, and output names come from \`\\w+\` digraph names. So there is no shell injection, but it does run a system binary on content from another skill's file.
- info mutable_dependency (claude review: model text, it can be wrong): A "good example" in the reference document shows \`pip install pypdf\` with no version pin. It is illustrative text for authors and the skill never runs it. Skills written from this guidance may copy the unpinned install pattern.

## Fix applied

- Fix label: hygiene
- Targets: low mutable\_dependency
- Targets: low other
- Targets: low other
- Targets: low instruction\_override
- Targets: info mutable\_dependency
- After the fix: low mutable\_dependency (esr rules): ✓ gone (re-scanned)
- After the fix: low other (claude review): \~ targeted, not re-verified
- After the fix: low other (claude review): \~ targeted, not re-verified
- After the fix: low instruction\_override (claude review): \~ targeted, not re-verified
- After the fix: info unsafe\_execution (claude review): – not addressed
- After the fix: info mutable\_dependency (claude review): \~ targeted, not re-verified
- Fix id: sha256:deb09ab80f2cddffbf22fb6084c05984398731bac17fe2d62c6b0be86b19406b
- Changed: SKILL.md
- Changed: references/anthropic-best-practices.md
- Fix offered: hygiene, checked
- info unsafe\_execution (claude review): No fix. The claude review says this is what the skill is for.

## Claude Code reported

During this run Claude Code reported these values, which differ from what esr expects. None of them lets the reviewer act; the review went ahead.

- Claude Code version: 2.1.312 is newer than 2.1.311, the version this esr was tested on
