# esr review: skills/diagnosing-superpowers

Written by esr (`esr owner/repo`) from its own records. It never quotes the skill beyond what a finding's text holds; the summary and the claude review's findings below are model text.

- Upstream: obra/superpowers
- Upstream commit reviewed: 2ce8aa15d05bd57213e6f746f953aafb7ded7a8b
- Skill tree reviewed: effb02c345170011be4470c73b99530de43182a7
- Date: 2026-10-30
- Choice: fix (re-checked and applied)

## What it does (claude review, model text)

    Helps a user find out why a 'superpowers' coding-agent session went wrong.
    It reads the session transcripts on disk, sends parallel analyst subagents
    to report evidence with path:line citations, and writes a report. If the
    user asks, it also searches or files GitHub issues on the superpowers
    repository and builds a scrubbed diagnostic bundle.

## What it could do (static profile)

- reaches https hosts: api.github.com, github.com

## Public scores (outside opinions)

- public scores (outside opinions): Gen safe, Socket safe (0 alerts), Snyk medium; BAD: Snyk medium

## Findings

- low prompt_injection (claude review: model text, it can be wrong): The analyst and matcher subagents read raw session transcripts. These contain tool results, fetched web content and other untrusted text, and the subagents run shell commands to do so. Only the redaction policy, which the scrub agents use, says to treat transcript content as evidence and not as instructions. The analyst prompts have no such rule, so hostile text inside a diagnosed transcript could steer an analyst subagent.
- low secret_exposure (claude review: model text, it can be wrong): A bundle exported at the 'full' redaction level keeps every tool-result body from the session, and the scrubbing is done by an LLM. The skill itself says scrubbing can miss things. Credentials or personal data from the user's sessions could therefore end up in an archive meant for sharing. Mitigations are present: the bundle is built only on request, a scrub audit must return CLEAN, archiving needs approval, and the user is told to review every file.
- low undeclared_egress (claude review: model text, it can be wrong): Step 5 runs when report section 7 says involvement is 'possible' or 'likely', not only when the user asks. It searches GitHub issues for the symptoms, using gh or an unauthenticated curl request to the GitHub search API. The search terms come from the private session content, so some of it leaves the machine before the user approves anything. Only filing an issue has an approval gate.

## Fix applied

- Fix label: hygiene
- Targets: low prompt\_injection
- Targets: low undeclared\_egress
- After the fix: low prompt\_injection (claude review): \~ targeted, not re-verified
- After the fix: low secret\_exposure (claude review): – not addressed
- After the fix: low undeclared\_egress (claude review): \~ targeted, not re-verified
- Fix id: sha256:c774ef75e2b67ec4c649230895839cc5d18220c9663d58ea6ad4e16e06133166
- Changed: prompts/analyst-common.md
- Changed: references/github-issues.md
- Fix offered: hygiene, checked
- low secret\_exposure (claude review): No fix by esr. Remove the secret and rotate it yourself.

## Claude Code reported

During this run Claude Code reported these values, which differ from what esr expects. None of them lets the reviewer act; the review went ahead.

- Claude Code version: 2.1.312 is newer than 2.1.311, the version this esr was tested on
