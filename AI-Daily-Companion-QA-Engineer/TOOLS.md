# TOOLS.md -- QA Engineer Operational Notes

Tools and reliable QA commands are documented here as they are discovered.

The QA Engineer is not an implementation agent.

Do not run repository-changing commands.

Do not stage, commit, push, merge, delete, or modify files during ordinary QA work.

Do not store secrets, tokens, passwords, private keys, or private user data in this file.

## Documentation Standard

When documenting a reliable QA command, include:

- command
- purpose
- working directory
- expected result
- common failure modes
- safety considerations

## Safe QA Evidence Requests

When asking another agent for evidence, request concise, auditable output.

Useful evidence types:

- assigned issue
- acceptance criteria
- branch name
- commit
- PR link
- changed-file list
- test command
- test result
- manual validation steps
- environment
- hardware availability
- expected behavior
- actual behavior
- privacy/security impact statement
- known limitations
- owner/action for defects

## Read-Only Repository Inspection Commands

Use read-only commands when permitted by the QA task.

Examples:

    pwd
    git status --short
    git branch --show-current
    git rev-parse HEAD
    git rev-parse origin/main
    git diff --stat
    git diff --name-status
    find app -maxdepth 3 -type f | sort
    find tests -maxdepth 3 -type f | sort
    find docs -maxdepth 3 -type f | sort

Expected use:

- verify environment
- inspect changed-file scope
- identify relevant tests
- confirm documentation or artifact presence

Safety:

- do not stage files
- do not commit
- do not push
- do not delete files
- do not run cleanup/reset commands
- do not print secrets or private local files

## Common Test Commands

Run tests only when safe and relevant to the assigned QA task.

Examples:

    python3 -m unittest discover
    python3 -m unittest tests.test_config_loader
    python3 -m unittest tests.test_run_mvp
    python3 -m unittest tests.test_startup_health
    python3 -m unittest tests.test_pr_gate_check

Expected use:

- validate acceptance criteria
- verify regressions
- reproduce developer test evidence
- confirm fixes

Safety:

- record exact command and result
- do not claim tests passed unless run
- document skipped tests and why
- avoid commands requiring secrets, external services, or unavailable hardware unless approved

## QA Result Checklist

A complete QA result should include:

- issue ID
- validation scope
- environment
- acceptance criteria matrix
- exact steps
- expected result
- actual result
- verdict per criterion
- automated tests run
- manual checks run
- defects
- risks and limitations
- recommended next action

## Defect Report Checklist

A useful defect report includes:

- summary
- severity
- repro steps
- expected behavior
- actual behavior
- environment
- branch/commit/PR
- affected acceptance criterion
- owner to fix
- required action
- evidence

## NPU / Accelerator QA Checklist

For NPU or accelerator validation, request or verify:

- approved scope reference
- CTO architecture/routing reference
- target workload
- accelerator backend
- hardware availability
- required vs optional accelerator behavior
- fallback behavior
- degraded behavior
- startup-health impact
- privacy/logging impact
- tests or smoke checks
- explicit non-goals
- evidence that optional hardware remains optional unless approved

Never accept performance or stability claims without reproducible evidence.

Never pass dual-NPU MVP behavior without Board approval.

Never copy raw hardware logs if they contain sensitive or machine-local data.

## Privacy-Safe Evidence Rules

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

If test output contains sensitive content, summarize safely and mask values.

If privacy impact is unclear, route to Privacy Officer.

## Permission Boundary Pattern

If you cannot mutate an issue, create a durable QA artifact if needed and ask the issue owner, CTO, CEO, or Board/Owner to relay the prepared comment.

Do not create a new issue unless traceability would otherwise be lost.