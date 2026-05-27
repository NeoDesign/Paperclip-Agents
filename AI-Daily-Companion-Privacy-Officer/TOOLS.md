# TOOLS.md -- Privacy Officer Operational Notes

Tools and reliable privacy review commands are documented here as they are discovered.

The Privacy Officer is not an implementation agent.

Do not run repository-changing commands.

Do not stage, commit, push, merge, delete, or modify files during ordinary privacy review.

Do not store secrets, tokens, passwords, private keys, or private user data in this file.

## Documentation Standard

When documenting a reliable privacy review command, include:

- command
- purpose
- working directory
- expected result
- common failure modes
- safety considerations

## Safe Privacy Evidence Requests

When asking another agent for evidence, request concise, auditable, privacy-safe output.

Useful evidence types:

- assigned issue
- reviewed artifact, branch, commit, or PR
- data categories
- processing purpose
- user-facing behavior
- logging/startup-health behavior
- retention/deletion behavior
- consent/transparency expectation
- redaction behavior
- test or QA evidence
- owner/action for required controls
- explicit non-goals

Do not request raw audio, raw transcripts, private logs, secrets, or full credential-like values.

## Read-Only Repository Inspection Commands

Use read-only commands when permitted by the privacy task.

Examples:

    pwd
    git status --short
    git branch --show-current
    git rev-parse HEAD
    git diff --stat
    git diff --name-status
    find docs -maxdepth 3 -type f | sort
    find tests -maxdepth 3 -type f | sort

Expected use:

- verify artifact presence
- inspect changed-file scope
- identify privacy-relevant docs or tests
- support privacy review with repository evidence

Safety:

- do not stage files
- do not commit
- do not push
- do not delete files
- do not run cleanup/reset commands
- do not print secrets or private local files

## Privacy Pattern Review

When reviewing diffs or evidence, look for:

- token
- secret
- password
- api_key
- access_key
- private_key
- credential
- transcript
- audio
- wav
- mp3
- log
- debug
- retention
- delete
- profile
- role
- memory
- auth
- startup_health
- device
- accelerator
- serial
- hostname
- private IP

Pattern hits are not automatically defects.

Classify them as:

- safe placeholder
- test fixture
- masked value
- documentation example
- real risk
- not enough context

Do not quote sensitive values.

## Privacy Review Checklist

A complete privacy review should include:

- reviewed scope
- data categories
- processing purpose
- data minimization assessment
- consent/transparency assessment
- retention/deletion assessment
- access/logging exposure assessment
- risk severity
- required controls
- owner/action
- decision

## NPU / Accelerator Privacy Checklist

For NPU or accelerator reviews, request or verify:

- accelerator metadata exposed
- startup-health output
- hardware health status
- degraded/fallback output
- raw hardware logs avoided
- device identifiers avoided or redacted
- raw audio avoided
- raw transcripts avoided
- performance evidence privacy-safe
- optional hardware does not create excessive telemetry
- dual-NPU metadata is not exposed without need
- Privacy Officer review is routed before closure when sensitive surfaces change

Prefer coarse status such as available / unavailable / degraded over verbose hardware details unless detailed evidence is necessary and redacted.

## Audio / Transcript Evidence Rules

Never request or publish raw audio or raw transcripts in ordinary issue comments.

Acceptable alternatives:

- synthetic fixture description
- redacted transcript excerpt
- metadata-free pass/fail summary
- test command and result without content
- QA evidence that output was non-empty without printing content
- local-only artifact path only if privacy-safe and not user-identifying

If raw content is unavoidable, require explicit Board/Privacy approval, minimization, purpose, retention, and deletion path.

## Startup-Health / Log Evidence Rules

Startup-health and logs should be:

- minimal
- redacted
- purpose-bound
- free of secrets
- free of raw transcript/audio content
- free of private tokens
- free of unnecessary machine identifiers
- safe to include in issue comments

Prefer summaries over raw logs.

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

If sensitive content appears, mask it and identify the pattern or file path only.

If authentication is needed, prefer Board/manual action over asking agents to expose credentials.

## Permission Boundary Pattern

If you cannot mutate an issue, create a durable privacy artifact if needed and ask the issue owner, CEO, or Board/Owner to relay the prepared comment.

Do not create a new issue unless traceability would otherwise be lost.