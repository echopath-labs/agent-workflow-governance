# Git Lifecycle Guide

Use this reference when creating branches, committing, merging, pushing, aligning primary branches, or closing out an iteration.

## Preflight

Run git status in every involved repository before editing.

Record mentally or in durable notes when relevant:

- Current branch.
- Whether the branch tracks a remote.
- Uncommitted changes and whether they are yours.
- Relevant remote state when pushing, merging, or releasing.

Never revert, overwrite, reformat, or stage user changes unless the user explicitly asks.

## Primary Branch Naming

For new repositories, prefer `main` as the default primary branch.

For existing repositories, respect the repository's current primary branch, whether it is `master`, `main`, or a project-specific release branch. Do not rename branches without an explicit migration request and a plan covering remotes, CI, branch protection, release scripts, and documentation.

When saying a repository is aligned, refer to its primary branch instead of assuming one name.

## Branch Choice

Common prefixes:

- `feature/` for new capabilities.
- `fix/` for normal bug fixes.
- `hotfix/` for urgent production fixes.
- `release/` for release preparation or release-source synchronization.
- `chore/` for tooling, docs, or maintenance.

Reuse the current branch when it already matches the task and has no conflicting unrelated work.

Create or request a new branch when the current branch is the repository's primary branch, unrelated, dirty with other work, or already tied to another release.

Do not create branches just to appear organized. The branch must clarify ownership, scope, or release intent.

## New Iteration Reminder

When the user starts a new feature, bug fix, refactor, dependency update, or configuration change, check the current branch before editing.

If the current branch is the repository's production primary branch, usually `master` or `main`, remind the user that new work should usually start from a task branch unless one of these is true:

- The user explicitly asked to work directly on the current branch.
- The project governance entry defines a different branch policy.
- The task is a tiny read-only check or documentation-only inspection that does not edit files.

Do not automatically create or switch branches when doing so could disrupt unrelated work. Report the current branch, suggest a branch name, and ask for confirmation when branch intent is ambiguous.

## Release And Shared Environment Work

For repositories that release to shared environments, respect the repository's own release rules.

Do not infer production, staging, Kubernetes, CI/CD, rollback, image, or customer-data procedures from this generic skill. If a project-specific release checklist exists, use it. If none exists, stop and ask for explicit instructions before triggering high-risk release actions.

## Commit Rules

Commit only related files. Inspect staged diff before commit.

Use concise messages:

- `feat: ...`
- `fix: ...`
- `hotfix: ...`
- `chore: ...`
- `docs: ...`

Avoid one commit that mixes code, unrelated formatting, durable-record archive churn, and deployment source updates unless they are inseparable for the same closeout.

## Merge And Closeout

Before merging to the primary branch or saying the primary branch is aligned:

- Compare intended branch commits with the target branch.
- Confirm focused tests or checks.
- Confirm durable records have final evidence and remaining risk.
- Confirm human-facing docs are updated when the iteration changed workflow, usage, release/build behavior, templates, or team rules.
- Check git status after merge.

## Closeout Branch Restore

At the end of a completed iteration, evaluate whether to restore the repository to its actual primary branch.

Restore only when all of these are true:

- The working tree is clean.
- The completed work has been committed and integrated into the primary branch, or the task branch no longer needs to remain active.
- The current branch is not needed for validation, follow-up patches, rollback, customer verification, or release source comparison.
- If a release happened, the deployment succeeded and the live environment or release source of truth is confirmed to match the primary branch.

Do not restore when any of these are true:

- There are uncommitted changes.
- The task branch has unmerged, unpushed, or unverified commits that still matter.
- Production deployment, live-state validation, or primary-branch alignment is still pending.
- The user intends to continue work on the current branch.
- The repository's primary branch is unknown.

When restore is safe, switch to the repository's actual primary branch and report the final branch. For multi-repository work, summarize each repository separately.
