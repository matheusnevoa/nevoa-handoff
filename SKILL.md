---
name: nevoa-handoff
description: Create a compact, actionable handoff document so another agent can continue the current work without rediscovering context or reopening settled decisions.
disable-model-invocation: true
---

# Nevoa Handoff

Create a concise Markdown handoff document that allows a fresh agent to continue the current work with minimal rediscovery.

Save the document to the temporary directory of the user's operating system, not the current workspace.

Do not ask the user what the next session will be used for. Infer the next session objective from the current conversation, work state, and unresolved work. If the user explicitly provides a next-session focus, use it to tailor the handoff.

## Core principles

- Capture only the context necessary to continue the work.
- Preserve decisions that have already been made.
- Do not reopen or reinterpret settled decisions unless they are explicitly marked as unresolved.
- Clearly distinguish established context, decisions, assumptions, unresolved questions, and recommended next actions.
- Prefer references to existing artifacts over reproducing their contents.
- Do not include unnecessary conversation history.
- Do not invent missing context.

## Required structure

Use the following sections when applicable.

# Session Handoff

## Next Session Objective

State the most likely objective of the next session based on the current work.

Infer it without asking the user. If the user explicitly provided a next-session focus, use that instead.

## Current State

Summarize the current state of the work.

Include only information the next agent needs in order to continue effectively.

## Decisions Made

List important decisions that are already settled.

For each decision, capture the outcome and, only when useful, the reason behind it.

Do not present settled decisions as open questions.

## Constraints and Conventions

Capture relevant constraints, preferences, conventions, technical boundaries, or instructions that the next agent must preserve.

Examples include architecture constraints, repository conventions, implementation rules, user preferences, scope boundaries, and compatibility requirements.

## Relevant Artifacts

Reference existing artifacts instead of duplicating their contents.

Relevant artifacts may include specs, design documents, plans, ADRs, issues, pull requests, commits, diffs, source files, documentation, and external URLs.

For each artifact, include:

- its path or URL;
- a short explanation of why it matters to the next session.

Treat referenced artifacts as the source of truth for details already documented there.

## Work Completed

Summarize meaningful work already completed during the current session.

Avoid reproducing large outputs, diffs, or artifact contents.

## Open Questions

List only questions or uncertainties that remain genuinely unresolved.

Do not include items that have already been decided.

## Recommended Next Steps

Provide a short, ordered list of the most logical actions for the next agent.

Make the first step immediately actionable.

Do not repeat work that is already complete.

## Suggested Skills

List the skills the next agent should consider invoking through the Skill tool.

For each skill, include:

- the exact skill name;
- a one-line explanation of when or why it should be used.

Only suggest skills that are relevant to the next session.

## Security

Never include secrets or unnecessary sensitive information.

Redact or omit API keys, access tokens, passwords, private keys, credentials, secret-bearing connection strings, personal addresses, and unnecessary personally identifiable information.

When the existence of a sensitive value matters to the handoff, replace it with a descriptive placeholder instead of the real value.

Example:

`API_TOKEN=<configured in environment>`

## Output requirements

- Write the handoff in Markdown.
- Save it as `handoff.md` in the temporary directory of the user's operating system.
- Keep it compact and operational.
- Prefer concise bullets over long narrative sections.
- Do not duplicate information already documented in referenced artifacts.
- Optimize for continuation, not historical completeness.

The final handoff should let the next agent quickly understand:

1. what is being done;
2. where the work currently stands;
3. what has already been decided;
4. which artifacts are authoritative;
5. what remains unresolved;
6. what to do next.
