# TOOLS.md -- Product Owner Operational Notes

Tools and reliable operational commands are documented here as they are discovered.

The Product Owner is not an implementation agent.

Do not run repository-changing commands.

Do not stage, commit, push, merge, delete, or modify runtime files.

## Documentation Standard

For every tool or command, document:

- purpose
- when to use it
- required working directory
- expected output
- common failure modes
- safety considerations

Do not store secrets, tokens, passwords, private keys, or private user data in this file.

## Safe Product Evidence Requests

When asking another agent for evidence, request concise, auditable output.

Useful evidence types:

- product decision reference
- Board decision link
- issue ID
- issue status
- owner/action
- acceptance criteria
- user-facing behavior
- explicit non-goals
- branch or PR link when relevant
- test summary from QA or developer
- privacy review summary from Privacy Officer
- documentation artifact path
- current phase
- deferred scope

## Repository Inspection Notes

The Product Owner may request or perform non-invasive repository inspection when assigned.

Allowed read-only inspection examples:

    pwd
    git rev-parse --show-toplevel
    git branch --show-current
    ls
    find docs -maxdepth 3 -type f | sort
    find tests -maxdepth 2 -type f | sort

Expected use:

- understand current product context
- verify product documentation presence
- identify relevant artifacts
- ground product scope recommendations

Safety:

- do not stage files
- do not commit
- do not push
- do not delete files
- do not inspect or print secrets
- do not modify source code
- do not modify runtime configuration

## Product Scope Evidence Checklist

For scope recommendations, request:

- confirmed Board or CEO direction
- current issue objective
- explicit non-goals
- user-facing expected behavior
- affected workload or feature area
- owner and reviewer expectations
- privacy-sensitive surfaces
- QA-validatable acceptance criteria
- deferred or experimental scope

## NPU / Accelerator Product Checklist

For NPU or accelerator product work, request:

- target user benefit
- affected workload: STT, summary, sentiment, or status visibility
- required vs optional accelerator behavior
- degraded behavior when accelerator is missing or unhealthy
- user-facing setting or mode, if any
- QA acceptance scenario
- privacy-sensitive metadata/log surface
- explicit experimental-only scope, if applicable
- CTO architecture decision reference

Do not request raw hardware logs unless CTO and Privacy approve.

Do not request raw audio or transcripts.

## Issue Draft Quality Checklist

A good issue draft includes:

- clear title
- suggested owner
- background
- desired outcome
- scope
- out of scope
- acceptance criteria
- dependencies
- risks
- stop condition

A poor issue draft:

- mixes product and implementation ownership
- lacks non-goals
- lacks testable acceptance criteria
- assumes optional hardware
- creates a closure gate without a pass/fail condition
- duplicates an existing issue

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
- personal data

If authentication is needed, prefer Board/manual action over asking agents to expose credentials.

## Permission Boundary Pattern

If an agent cannot mutate an issue because of permissions:

1. Ask the current assignee, CEO, or Board/Owner to relay the prepared comment.
2. Preserve the source artifact path.
3. Continue only after the relay is visible in the target issue.
4. Do not create a new issue unless traceability would otherwise be lost.