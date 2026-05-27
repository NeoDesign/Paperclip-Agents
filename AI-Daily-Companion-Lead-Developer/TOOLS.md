# TOOLS.md -- Lead Developer Operational Notes

Tools and local project commands are documented here as they are discovered.

The Lead Developer may use implementation tools only for assigned, scoped tasks.

Do not use repository-changing commands outside the approved task scope.

Do not store secrets, tokens, passwords, private keys, or private user data in this file.

## Documentation Standard

When documenting a reliable command, include:

- command
- purpose
- working directory
- expected result
- common failure modes
- safety considerations

## Safe Repository Inspection Commands

Use read-only commands before implementation to understand current state.

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

- confirm working directory
- confirm branch
- inspect worktree status
- identify changed-file scope
- avoid overwriting unrelated work

Safety:

- do not run cleanup/reset/delete commands unless explicitly authorized
- do not print secrets
- do not inspect local secret files unnecessarily
- do not stage unrelated files

## Git Safety Commands

Before implementation:

    git status --short
    git branch --show-current
    git rev-parse HEAD

Before handoff:

    git diff --name-status
    git diff --stat
    git diff --check

Expected use:

- verify changed files
- verify diff quality
- detect whitespace or conflict-marker issues
- prepare review handoff

Safety:

- do not run broad `git add -A` unless the task explicitly allows all changed files
- prefer staging explicit files
- never commit local secret files
- never commit raw audio, transcripts, private logs, or machine-local artifacts

## Test Commands

Use targeted tests for the changed area.

Common examples:

    python3 -m unittest discover
    python3 -m unittest tests.test_config_loader
    python3 -m unittest tests.test_run_mvp
    python3 -m unittest tests.test_startup_health

Expected use:

- run targeted tests after implementation
- run broader tests when shared behavior changes
- record exact command and result in handoff

Safety:

- do not claim tests passed unless run
- document skipped tests and why
- document missing coverage

## PR / Review Handoff Evidence

For Code Review handoff, provide:

- objective
- assigned issue
- branch name, if available
- base commit, if available
- changed files
- diff summary
- tests run
- test result
- manual validation notes
- documentation changes
- privacy/security implications
- known risks
- reviewer focus areas
- explicit non-goals

## NPU / Accelerator Implementation Evidence

For NPU or accelerator work, provide:

- approved scope reference
- CTO architecture/routing reference
- affected workload
- affected files
- fallback behavior
- startup-health impact
- privacy/logging impact
- test evidence
- hardware assumptions
- degraded behavior
- explicit non-goals

Never claim accelerator performance without reproducible evidence.

Never treat optional hardware as required unless approved.

Never include raw hardware logs if they contain sensitive or machine-local data.

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

If authentication is needed, prefer Board/manual action over asking agents to expose credentials.

## Permission Boundary Pattern

If you cannot mutate an issue, create a durable handoff artifact if needed and ask the issue owner, CTO, CEO, or Board/Owner to relay the prepared comment.

Do not create a new issue unless traceability would otherwise be lost.