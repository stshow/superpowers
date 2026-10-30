# esr review: skills/using-git-worktrees

Written by esr (`esr owner/repo`) from its own records. It never quotes the skill beyond what a finding's text holds; the summary and the claude review's findings below are model text.

- Upstream: obra/superpowers
- Upstream commit reviewed: 2ce8aa15d05bd57213e6f746f953aafb7ded7a8b
- Skill tree reviewed: d2b8357b922667a091bfe967840abf5ae84ce99c
- Date: 2026-10-30
- Choice: fix (re-checked and applied)

## What it does (claude review, model text)

    The skill gives an agent a procedure for setting up an isolated git
    workspace before feature work. It first checks for existing isolation, then
    prefers the platform's native worktree tool and falls back to `git worktree
    add`. After that it installs project dependencies and runs the project's
    tests to confirm a clean baseline.

## What it could do (static profile)

- no network hosts, tool grants, scripts or binaries found

## Public scores (outside opinions)

- public scores (outside opinions): Gen safe, Socket safe (0 alerts), Snyk low

## Findings

- low mutable_dependency (esr rules; rule unpinned-install in SKILL.md line 114): SKILL.md installs a package without pinning its version, so its code can change at any time
- low unsafe_execution (claude review: model text, it can be wrong): Whenever it finds the matching manifest files, the skill tells the agent to run the project's dependency installers and builds (npm install, cargo build, pip install -r requirements.txt, poetry install, go mod download) and then its test suite. It does not ask the user first. These commands run code the project controls, such as npm lifecycle scripts, Cargo build scripts, Python package builds and test code. They also download packages from public registries. In a repository the user does not fully trust, this could run arbitrary code with the user's privileges. The static scanner's unpinned-install lead points at the pip line. Those versions are set by the user's project, not by the skill.

## Fix applied

- Fix label: hygiene
- Targets: low unsafe\_execution
- After the fix: low mutable\_dependency (esr rules): – not addressed
- After the fix: low unsafe\_execution (claude review): \~ targeted, not re-verified
- Fix id: sha256:515e5dccdc354940dc6479cc5f5b973511b1feb0c2cc34f695d6c40535cb4513
- Changed: SKILL.md
- Fix offered: hygiene, checked
- low mutable\_dependency (esr rules): No fix. The claude review says this is what the skill is for.

## Claude Code reported

During this run Claude Code reported these values, which differ from what esr expects. None of them lets the reviewer act; the review went ahead.

- Claude Code version: 2.1.312 is newer than 2.1.311, the version this esr was tested on
