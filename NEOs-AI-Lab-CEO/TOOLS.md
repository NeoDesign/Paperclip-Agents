# TOOLS.md -- CEO Operational Notes

Tools and reliable operational commands are documented here as they are discovered.

The CEO Agent is not the primary implementation agent. Do not run repository-changing commands unless explicitly authorized by Alexander / Board.

## Documentation Standard

For every tool or command, document:

- purpose
- when to use it
- required working directory
- expected output
- common failure modes
- safety considerations

Do not store secrets, tokens, passwords, private keys, or private user data in this file.

## CEO Evidence Requests

When asking another agent for technical evidence, request concise, auditable output.

Useful evidence types:

- branch name
- base commit
- head commit
- changed-file list
- diff stat
- test command and result
- privacy/secret scan result
- PR URL
- merge commit
- artifact paths
- clean-worktree status

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

For merge verification, request:

- latest `origin/main` commit
- approved commit ancestor check
- merge commit reference
- required artifact presence
- final clean-worktree evidence when cleanup is in scope

## Safety Notes

Never request or expose:

- `GH_TOKEN`
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

1. Ask the current assignee or Board/Owner to relay the prepared comment.
2. Preserve the source artifact path.
3. Continue only after the relay is visible in the target issue.
4. Do not create a new issue unless traceability would otherwise be lost.