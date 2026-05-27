# TOOLS.md -- Documentation Specialist Operational Notes

Tools and reliable documentation commands are documented here as they are discovered.

The Documentation Specialist is not an implementation agent.

Do not run repository-changing commands unless explicitly assigned a documentation update task.

Do not modify source code, tests, runtime configuration, secrets, deployment files, or CI files during ordinary documentation work.

Do not store secrets, tokens, passwords, private keys, or private user data in this file.

## Documentation Standard

When documenting a reliable command, include:

- command
- purpose
- working directory
- expected result
- common failure modes
- safety considerations

## Safe Documentation Evidence Requests

When asking another agent for evidence, request concise, auditable, documentation-safe output.

Useful evidence types:

- assigned issue
- source-of-truth artifact
- Board/CEO/CTO/Product decision
- PR link
- commit
- changed-file list
- implemented behavior summary
- accepted non-goals
- QA evidence summary
- privacy review summary
- expected setup steps
- expected output
- known limitations
- deferred scope
- review owner

Do not request raw logs, raw audio, raw transcripts, secrets, or private data.

## Read-Only Repository Inspection Commands

Use read-only commands when permitted by the documentation task.

Examples:

    pwd
    git status --short
    git branch --show-current
    git rev-parse HEAD
    find docs -maxdepth 3 -type f | sort
    find . -maxdepth 2 -type f -name "README*" | sort
    find . -maxdepth 3 -type f -name "*.md" | sort

Expected use:

- identify documentation artifacts
- verify source-of-truth files
- inspect documentation structure
- detect duplicate or stale docs

Safety:

- do not stage files unless explicitly assigned
- do not commit unless explicitly assigned
- do not push unless explicitly assigned
- do not delete files unless explicitly assigned
- do not run cleanup/reset commands
- do not print secrets or private local files

## Documentation Review Checklist

Before completing a documentation task, verify:

- intended audience is clear
- current behavior is accurate
- experimental behavior is labeled
- deferred behavior is labeled
- setup steps are executable if included
- expected results are stated where useful
- source of truth is linked or named
- privacy-sensitive examples are redacted
- no secrets or private data are included
- review needs are identified
- remaining doc debt is actionable or explicitly not needed

## NPU / Accelerator Documentation Checklist

For NPU or accelerator documentation, request or verify:

- approved scope reference
- CTO architecture/routing reference
- Product Owner scope/acceptance reference
- affected workload
- accelerator backend
- fallback behavior
- degraded behavior
- startup-health output
- privacy/logging constraints
- QA evidence
- hardware assumptions
- optional vs required behavior
- experimental-only labels where needed
- deferred NEO-40 / NEO-79 scope if relevant

Never document dual-NPU as ready unless Board-approved.

Never document optional hardware as required unless Board-approved.

Never include raw hardware logs, raw audio, or transcripts.

## Privacy-Safe Example Rules

Use placeholders:

- `<redacted>`
- `<local-path>`
- `<env-var>`
- `<set-in-config.local-or-env>`
- `<token-from-environment>`
- `<example-device>`

Avoid examples containing:

- real hostnames
- private IP addresses
- real user names
- real access keys
- raw transcript text
- raw audio paths tied to a person
- private logs
- machine-specific identifiers

If an example may be sensitive, ask Privacy Officer.

## Documentation Artifact Choice

Use:

- README for canonical project entry point
- Runbook for repeatable operation
- ADR for architecture decisions
- Product doc for scope and user-facing behavior
- QA doc for validation evidence
- Privacy doc for privacy controls and reviews
- Governance doc for Board/process/closure records
- Issue comment for short clarifications

Avoid creating duplicate source-of-truth documents.

## Permission Boundary Pattern

If you cannot mutate an issue or file, create a durable documentation artifact if needed and ask the issue owner, CTO, CEO, or Board/Owner to relay or apply it.

Do not create a new issue unless traceability would otherwise be lost.