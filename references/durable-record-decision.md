# Durable Record Decision Guide

Use this reference when deciding whether, where, and how to preserve engineering context.

Durable records can be OpenSpec changes/specs, ADRs, design docs, issue tracker records, project notes, runbooks, or repository-specific governance files. Use the system the repository already has.

## Scope Selection

Before recording details or editing files in a parent workspace, identify the smallest workspace that owns the behavior or implementation.

Treat a child directory as an independent workspace when it has a strong boundary marker:

- Its own `AGENTS.md`, `CLAUDE.md`, `.cursor/rules`, or equivalent Agent entry.
- Its own `openspec/`, ADR directory, docs governance directory, or issue tracker mapping.
- Its own `.git` directory or git worktree.
- Its own release, build, CI, deployment, package, service, app, SDK, library, or plugin boundary.

When no strong marker exists, still prefer child-workspace ownership if several weaker markers appear together:

- Project root files such as `package.json`, `pnpm-workspace.yaml`, `Cargo.toml`, `go.mod`, `pyproject.toml`, or `pom.xml`.
- Local README, architecture docs, runbooks, tests, build commands, or release commands.
- A clear service, app, SDK, library, plugin, interface, or deployment boundary.

If ownership is uncertain, do the smallest useful investigation first. Do not write durable detail until the owner is clear.

## What Belongs In Parent vs Child

Use workspace-level durable records for:

- Cross-repository ownership, routes, contracts, shared configuration, deployment topology, or release policy.
- Incidents or decisions that affect multiple services or products.
- Team-wide Agent behavior, release discipline, or operational conventions.
- Lightweight indexes that point to child workspaces, key docs, relevant code paths, current status, and next entry points.

Use project-level durable records for:

- Internal behavior of one directly touched repository.
- Repository-specific implementation choices, validation evidence, and follow-ups.
- Service-local API, persistence, config, UI, or deployment details.
- Detailed investigation records, root cause, validation evidence, risks, rollback plans, and follow-up tasks for the behavior it owns.

Do not initialize a new durable record system for a repository that is only mentioned as a possible dependency.

## When To Create Or Update Records

Create or update a durable record when the task affects:

- Feature behavior, bug behavior, requirements, scope, or acceptance criteria.
- API, permissions, state flow, data model, business rules, metrics, customer delivery, or test strategy.
- Multiple modules, services, pages, roles, departments, systems, or Agent threads.
- Config, deployment, data structure, release source, or operational conventions.
- Any decision future teammates need to understand without chat history.

Durable records can stay lightweight or be skipped for:

- Simple questions, explanations, translations, or summaries.
- Tiny copy edits, pure formatting, and clearly low-risk mechanical changes.
- Read-only checks.
- Temporary exploration that produces no durable decision.

Decision rule: if a future teammate would struggle to understand the task without chat history, record it.

## Which Record System To Use

Prefer the repository's existing durable record system. Do not introduce a new
system just because this skill knows about one.

When multiple systems exist, choose by purpose:

- Use OpenSpec for scoped product or engineering changes that need proposal,
  design, task, requirement, acceptance-criteria, or spec evolution tracking.
- Use Spec Kit or a constitution/spec-driven system when the repository already
  uses it for project principles, specifications, and implementation planning.
- Use ADRs for durable architecture or technical decisions, especially when the
  important part is why one option was chosen over alternatives.
- Use issue trackers for execution state, bugs, assignment, triage, priority,
  milestones, and discussion that belongs with delivery management.
- Use design docs for broad problem framing, tradeoff analysis, proposals, or
  cross-team review before implementation.
- Use runbooks for repeatable operational procedures, incident handling,
  deployment checks, rollback steps, or environment-specific actions.
- Use README or project notes for lightweight human-facing usage, setup,
  migration, or adoption guidance.

If no durable record system exists:

- Do not initialize OpenSpec, Spec Kit, ADR directories, or issue structures
  automatically.
- Ask the user where durable context should live before creating a new system.
- If the user wants the lightest option, recommend a small Markdown note or ADR
  for decisions, and an issue or task list for execution state.
- If the work is a structured feature or behavior change and the user wants a
  specification workflow, offer OpenSpec or Spec Kit as options instead of
  choosing silently.

Before writing a durable record, state the proposed target and reason:

```text
Proposed durable record target: <system/path>
Reason: <why this system fits the task>
Please confirm before I create or update it.
```

If the user confirms a specific system, use it. If the user declines durable
recording, keep the decision thread-scoped and mention the risk in the final
handoff.

## Relationship Index Maintenance

Treat durable records as a retrieval graph, not just a note pile.

When creating or updating a record, maintain:

- Related stable specs, ADRs, docs, or rules.
- Related code paths, commands, scripts, APIs, schemas, config, charts, or modules.
- Related docs, PRDs, test plans, runbooks, customer notes, metrics definitions, or external references.
- Related changes, issues, incidents, PRs, follow-ups, blocked work, superseded work, or archived decisions.

Prefer precise paths and stable names over vague descriptions. If no related item exists, say so briefly instead of inventing links.

## Retrieval Hygiene

Durable records are not chat backups. Preserve reusable context:

- Final adopted decisions.
- Explicitly rejected options and why.
- Affected behavior and out of scope.
- Validation and residual risk.
- Follow-ups and handoff state.

Avoid low-value command logs, repeated background, unrelated code dumps, and unmarked stale ideas.

## Completion

Before closing a task:

- Check whether any durable rule belongs in a spec, ADR, doc, or tracker.
- Update relationship links so future searches can recover the right context.
- Keep low-value chat narration out of durable records.
- Archive or close completed records promptly after validation and backfill review when the repository supports it.
- Leave active records only when real work, validation, rollout, or adoption remains.
