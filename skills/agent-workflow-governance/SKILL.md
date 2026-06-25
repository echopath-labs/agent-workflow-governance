---
name: agent-workflow-governance
description: Use when planning, implementing, reviewing, closing out, or handing off important AI-assisted engineering work. Provides lightweight guardrails for workspace ownership, durable records, git hygiene, impact review, risk control, and context handoff across Codex, Claude Code, Cursor, Gemini CLI, or similar coding agents.
---

# Agent Workflow Governance

Use this skill as a lightweight workflow governance layer for AI-assisted engineering.

It governs how an Agent should work. It does not solve long-term Agent memory, context ownership, or project cognition by itself.

## Quick Gate

Before making changes, decide whether the task is important enough to require durable records and git discipline.

Use durable records plus git hygiene when the task includes:

- Feature work, bug fixes, optimizations, refactors, dependency changes, or configuration changes.
- API, auth, upload, download, storage, conversion, rendering, payments, deployment, or shared integration behavior.
- Branch management, commits, merges, releases, closeout, or primary-branch alignment.
- Incident investigation that produces a durable rule, risk, or follow-up.
- Any request that affects future teammates, future Agents, customer-facing behavior, production-like environments, or long-term project constraints.

Durable records may be skipped for:

- Pure read-only questions or simple command output.
- Short discussion where the user explicitly says not to implement yet.
- Local scratch checks that do not change code, config, docs, deployment state, or project facts.

If in doubt, propose a focused durable record using the repository's existing system, such as OpenSpec, ADR, issue tracker, design doc, or project notes. If no durable record system exists, do not initialize OpenSpec, Spec Kit, ADR directories, or issue structures silently. State the proposed target and reason, then wait for user confirmation.

## Required Workflow

1. Identify the actual repository or repositories involved. In multi-workspace trees, find the smallest child workspace that owns the behavior before editing files or recording durable details.
2. Check git status before editing each involved repository. Preserve user changes and unrelated dirty files.
3. Read the smallest relevant context set: workspace overview, governance entry, relevant specs or docs, and active changes if the repository has them.
4. Choose a branch deliberately. If new work starts from the repository's primary branch, remind the user to use a task branch before editing unless they explicitly want to continue on the current branch.
5. Keep edits scoped to the task. Do not mix unrelated cleanup, formatting, or historical fixes.
6. After changes, run focused validation and an existing-behavior impact review.
7. Update durable records with outcome, evidence, risks, follow-ups, and relationship links when a durable record exists. Ask before introducing a new durable record system.
8. Review human-facing docs. If the iteration changed workflow, API usage, release/build behavior, team rules, templates, or adoption guidance, update the short human-readable guide or explicitly record why no doc change is needed.
9. Finish with a clear state: branch, commits, uncommitted files, durable record status, validation evidence, remaining risk, and whether the repository was safely restored to its primary branch.

## References

Read only the reference needed for the current task:

- `references/durable-record-decision.md`: when deciding whether, where, and how to create durable records, including multi-workspace ownership and relationship-index maintenance.
- `references/git-lifecycle.md`: when creating branches, committing, merging, or aligning primary branches.
- `references/impact-review.md`: when completing any change that could affect existing behavior.
- `references/risk-and-context.md`: when handling high-risk operations, long-running work, or context-heavy tasks.

For release, rollback, image, Kubernetes, Helm, CI/CD, shared environment, customer data, or production operations, require a project-specific release or operations checklist. Do not invent one from this generic skill.
