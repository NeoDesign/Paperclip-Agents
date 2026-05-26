# TOOLS.md -- CTO Operational Notes

Tools and reliable operational commands are documented here as they are discovered.

The CTO Agent is not the primary implementation agent.

Do not run repository-changing commands unless explicitly authorized by Alexander / Board or CEO for a clearly scoped CTO task.

## Documentation Standard

For every tool or command, document:

- purpose
- when to use it
- required working directory
- expected output
- common failure modes
- safety considerations

Do not store secrets, tokens, passwords, private keys, or private user data in this file.

## Safe CTO Evidence Requests

When asking another agent for technical evidence, request concise, auditable output.

Useful evidence types:

- branch name
- base commit
- head commit
- changed-file list
- diff stat
- relevant file paths
- test command and result
- startup-health output with privacy-safe redaction
- accelerator detection result without sensitive logs
- privacy/secret scan result
- PR URL
- merge commit
- artifact paths
- clean-worktree status

## Repository Inspection Commands

Use repository inspection commands only when permitted by the issue scope.

Examples of read-only commands:

    git status --short
    git branch --show-current
    git rev-parse HEAD
    git rev-parse origin/main
    git diff --stat
    git diff --name-status
    find docs -maxdepth 3 -type f | sort
    find tests -maxdepth 2 -type f | sort

Expected use:

- understand current repository state
- verify file presence
- inspect changed-file scope
- prepare architecture plans
- prepare review requests

Safety:

- do not use broad cleanup commands
- do not stage files
- do not commit
- do not push
- do not delete files
- do not expose secrets

## PR / Merge Evidence Checklist

For PR readiness, request:

- PR link
- branch name
- approved commit
- number of changed files
- list of deletions
- test result
- diff quality result
- privacy/secret-safety confirmation
- statement that deferred scope is excluded
- statement that no unrelated architecture changes are bundled

For merge verification, request:

- latest origin/main commit
- approved commit ancestor check
- merge commit reference
- required artifact presence
- final clean-worktree evidence when cleanup is in scope

## NPU / Accelerator Evidence Checklist

For NPU or accelerator work, request:

- hardware target
- accelerator backend
- workload class
- routing policy
- fallback behavior
- startup-health impact
- degraded-state behavior
- tests or smoke checks
- privacy-safe logs only
- no raw audio or transcript leakage
- no secret-bearing device output

Never accept performance claims without reproducible evidence.

Never accept hardware availability as guaranteed unless the issue scope says so.

## Safety Notes

Never request or expose:

- GH_TOKEN
- API keys
- passwords
- private keys
- real access tokens
- raw audio
- raw transcripts
- private logs
- local-only configuration files with secrets

If authentication is needed, prefer Board/manual action over asking agents to expose credentials.

## Permission Boundary Pattern

If an agent cannot mutate an issue because of permissions:

1. Ask the current assignee, CEO, or Board/Owner to relay the prepared comment.
2. Preserve the source artifact path.
3. Continue only after the relay is visible in the target issue.
4. Do not create a new issue unless traceability would otherwise be lost.