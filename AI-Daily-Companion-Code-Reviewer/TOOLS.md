# TOOLS.md -- Code Reviewer Operational Notes

Tools and reliable review commands are documented here as they are discovered.

The Code Reviewer is not the primary implementation agent.

Do not run repository-changing commands unless explicitly assigned a clearly scoped fix task by CEO, CTO, or Board.

Do not stage, commit, push, merge, delete, or modify files during ordinary review.

Do not store secrets, tokens, passwords, private keys, or private user data in this file.

## Documentation Standard

When documenting a reliable review command, include:

- command
- purpose
- working directory
- expected result
- common failure modes
- safety considerations

## Safe Review Evidence Requests

When asking another agent for evidence, request concise, auditable output.

Useful evidence types:

- assigned issue
- branch name
- base commit
- head commit
- changed-file list
- diff stat
- acceptance criteria
- tests run
- test result
- manual validation notes
- documentation changes
- privacy/security impact statement
- scope exclusions
- known risks
- reviewer focus request

## Read-Only Repository Inspection Commands

Use read-only commands when permitted by the review task.

Examples:

    pwd
    git status --short
    git branch --show-current
    git rev-parse HEAD
    git rev-parse origin/main
    git diff --stat
    git diff --name-status
    git diff --check
    git show --stat --oneline HEAD
    find app -maxdepth 3 -type f | sort
    find tests -maxdepth 3 -type f | sort
    find docs -maxdepth 3 -type f | sort

Expected use:

- verify branch and repository state
- inspect changed-file scope
- detect whitespace or conflict-marker issues
- understand affected modules
- prepare evidence-based review comments

Safety:

- do not stage files
- do not commit
- do not push
- do not delete files
- do not run cleanup/reset commands
- do not print secrets or local private files

## Test Commands

Run tests only when safe and relevant to the review.

Common examples:

    python3 -m unittest discover
    python3 -m unittest tests.test_config_loader
    python3 -m unittest tests.test_run_mvp
    python3 -m unittest tests.test_startup_health
    python3 -m unittest tests.test_pr_gate_check

Expected use:

- verify submitted evidence
- reproduce targeted test results
- assess regression risk

Safety:

- record exact command and result
- do not claim tests passed unless run
- note missing or skipped tests
- avoid commands that require secrets, external services, or private hardware unless approved

## Review Diff Checklist

Inspect:

- files changed
- files deleted
- files added
- unexpected broad refactoring
- unrelated formatting churn
- dependency changes
- runtime behavior changes
- startup-health/logging changes
- test changes
- documentation changes
- secret-bearing filenames
- raw audio/transcript/log artifacts

## NPU / Accelerator Review Checklist

For NPU or accelerator reviews, request or verify:

- approved scope reference
- CTO routing/architecture reference
- affected workload
- accelerator backend
- fallback behavior
- degraded behavior
- startup-health impact
- privacy/logging impact
- hardware assumptions
- tests or smoke checks
- explicit non-goals
- evidence that optional hardware remains optional unless approved

Never accept performance claims without reproducible evidence.

Never approve dual-NPU MVP behavior without Board approval.

Never approve raw hardware logs, raw audio, or transcripts in review artifacts.

## Decision Checklist

Before choosing `APPROVE`, confirm:

- scope matches assigned issue
- acceptance criteria are satisfied
- tests are adequate or limitations are documented
- no serious privacy/security issue remains
- architecture boundaries are respected
- documentation impact is handled or routed
- QA/Privacy gates are handled where required
- no unrelated or deferred scope is bundled

Before choosing `REQUEST CHANGES`, confirm:

- findings are fixable within the assigned scope
- required changes are precise
- no Board/CTO/Privacy decision is required first

Before choosing `BLOCK`, confirm:

- serious governance, scope, architecture, privacy, security, or reviewability problem exists
- unblock owner and exact action are stated

## Safety Notes

Never request, print, commit, or expose:

- GH_TOKEN
- API keys
- passwords
- private keys
- real access tokens
- raw audio
- raw transcripts
- private logs
- local-only configuration files with secrets
- personal data

If sensitive content appears in a diff, do not quote it. Mask it and identify the pattern or file path only.

If authentication is needed, prefer Board/manual action over asking agents to expose credentials.

## Permission Boundary Pattern

If you cannot mutate an issue, create a durable review artifact if needed and ask the issue owner, CTO, CEO, or Board/Owner to relay the prepared comment.

Do not create a new issue unless traceability would otherwise be lost.