# TOOLS.md -- Repository Cartographer Operational Notes

Tools and reliable repository inspection commands are documented here as they are discovered.

The Repository Cartographer is not an implementation agent.

Do not run repository-changing commands.

Do not stage, commit, push, merge, delete, or modify files during ordinary repository cartography.

Do not store secrets, tokens, passwords, private keys, or private user data in this file.

## Documentation Standard

When documenting a reliable inspection command, include:

- command
- purpose
- working directory
- expected result
- common failure modes
- safety considerations

## Safe Repository Evidence Requests

When asking another agent for evidence, request concise, auditable, privacy-safe output.

Useful evidence types:

- repository path
- branch name
- commit
- top-level tree
- changed-file list
- relevant file paths
- module names
- test file paths
- documentation paths
- source-of-truth candidates
- superseded artifacts
- deferred-scope references
- privacy-sensitive areas
- owner/action

Do not request raw logs, raw audio, raw transcripts, secrets, or private data.

## Read-Only Repository Inspection Commands

Use read-only commands when permitted by the mapping task.

Examples:

    pwd
    git status --short
    git branch --show-current
    git rev-parse --show-toplevel
    git rev-parse HEAD
    git rev-parse origin/main
    find . -maxdepth 2 -type f | sort
    find . -maxdepth 2 -type d | sort
    find docs -maxdepth 3 -type f | sort
    find app -maxdepth 3 -type f | sort
    find tests -maxdepth 3 -type f | sort

Expected use:

- verify repository context
- map top-level structure
- locate docs, tests, and app modules
- identify likely source-of-truth files
- support CTO routing

Safety:

- do not stage files
- do not commit
- do not push
- do not delete files
- do not run cleanup/reset commands
- do not print secrets or private local files

## Focused Search Commands

Use focused searches when relevant.

Examples:

    grep -R "startup_health" -n app tests docs
    grep -R "accelerator" -n app tests docs
    grep -R "hailo" -ni app tests docs
    grep -R "npu" -ni app tests docs
    grep -R "transcript" -ni app tests docs
    grep -R "audio" -ni app tests docs

Expected use:

- locate feature references
- identify likely affected files
- find test and documentation coverage
- support NPU/accelerator mapping
- support privacy and QA routing

Safety:

- do not print large raw outputs
- do not print secrets
- do not print raw transcripts or private logs
- summarize results when output is large or sensitive

## Source-of-Truth Mapping Checklist

When mapping docs or artifacts, classify:

- current source of truth
- supporting evidence
- historical context
- superseded
- draft
- experimental
- deferred
- unclear

Useful evidence:

- file path
- recent main-branch presence
- PR or issue reference
- explicit supersession statement
- current README/runbook reference
- linked Board/CTO/CEO decision

## NPU / Accelerator Mapping Checklist

For NPU or accelerator mapping, request or verify:

- accelerator-related modules
- startup-health probes
- config keys
- workload references
- routing references
- fallback behavior references
- degraded-mode references
- Hailo references
- onboard NPU/RK3588 references
- tests
- runbooks
- privacy-sensitive log/device metadata surfaces
- deferred NEO-40 / NEO-79 / INMP441 references

Do not infer implementation maturity without evidence.

Do not treat detection as workload acceleration.

## Privacy-Safe Mapping Rules

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

If sensitive content appears, mask it and identify only the file/path or pattern.

If privacy impact is unclear, route to Privacy Officer.

## Follow-up Recommendation Checklist

A good follow-up recommendation includes:

- proposed title or action
- rationale
- suggested owner
- acceptance criteria or completion condition
- why a new issue is or is not needed

Avoid vague follow-ups such as:

- "clean up docs"
- "improve architecture"
- "add more tests"
- "review privacy"

Make follow-ups bounded and owner-specific.

## Permission Boundary Pattern

If you cannot mutate an issue or create a durable artifact, ask the issue owner, CTO, CEO, or Board/Owner to relay the prepared comment.

Do not create a new issue unless traceability would otherwise be lost.