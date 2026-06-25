# Agent Workflow Governance

![License: MIT](https://img.shields.io/badge/license-MIT-green.svg)
![Skill](https://img.shields.io/badge/skill-Codex%20Skill-111827.svg)
![Agents](https://img.shields.io/badge/agents-Codex%20%7C%20Claude%20Code%20%7C%20Cursor%20%7C%20Gemini-2563eb.svg)

> 简体中文说明: [README.md](README.md)

Lightweight workflow guardrails for AI-assisted engineering agents.

This repository provides a Codex-compatible skill that helps coding agents work
with more discipline during real engineering changes. It is intended for teams
using Codex, Claude Code, Cursor, Gemini CLI, or similar AI coding agents.

The skill focuses on workflow governance:

```text
How should the Agent work?
```

It does not try to solve long-term agent memory, project cognition, or context
ownership:

```text
What should the Agent remember, where does it belong, and how can it be recovered later?
```

Those are separate context governance problems.

## Why This Exists

AI coding agents are already strong at implementation. Long-running engineering
teams still need repeatable guardrails so agent-assisted work remains:

- scoped;
- reviewable;
- recoverable;
- auditable;
- safe to hand off;
- respectful of existing user changes.

Without workflow governance, teams tend to accumulate common failure modes:

- changes are made in the wrong workspace;
- branch state is unclear;
- durable decisions are not recorded;
- existing behavior is changed accidentally;
- validation evidence is missing;
- handoff state is too vague for the next teammate or agent.

This skill gives agents a minimal workflow layer for important engineering
changes without importing company-specific release, deployment, or operations
rules.

## Who Should Use It

Use this skill if your team:

- works with AI coding agents on real repositories;
- uses multiple branches, workspaces, or repositories;
- expects agents to preserve existing user changes;
- wants clearer closeout reports;
- wants durable records for important decisions, risks, and follow-ups;
- does not want generic agents to invent project-specific release procedures.

It is especially useful for:

- feature implementation;
- bug fixes;
- refactors;
- dependency or configuration changes;
- API or integration changes;
- incident follow-up that produces durable rules or risks;
- handoff between humans and agents.

## What The Skill Does

The skill helps an agent:

1. identify the owning workspace or repository;
2. decide whether durable records are needed;
3. preserve existing user changes and unrelated dirty files;
4. choose branches deliberately;
5. keep edits scoped to the task;
6. run focused validation;
7. review existing-behavior impact;
8. update durable records when appropriate;
9. close out with branch, git, validation, risk, and handoff state.

## What The Skill Does Not Do

This skill does not:

- define your release process;
- deploy to production;
- replace OpenSpec, ADRs, issues, or project docs;
- rewrite project memory;
- store long-term agent memory;
- infer Kubernetes, GitLab CI, image, rollback, or customer-data procedures;
- decide company-specific compliance rules.

For release, rollback, CI/CD, shared environment, customer-data, or production
operations, use your project-specific checklist.

## Install

Recommended one-line install:

```bash
npx skills add https://github.com/echopath-labs/agent-workflow-governance --skill agent-workflow-governance
```

If you prefer manual installation, clone the repository directly into your Codex
skills directory:

```bash
mkdir -p ~/.codex/skills
git clone https://github.com/echopath-labs/agent-workflow-governance.git ~/.codex/skills/agent-workflow-governance
```

If already installed, update with:

```bash
git -C ~/.codex/skills/agent-workflow-governance pull
```

Restart your Codex session after installing the skill so it can be discovered.

## Usage

Invoke the skill directly:

```text
$agent-workflow-governance
```

Or ask your coding agent to use it for an important engineering change:

```text
Use Agent Workflow Governance for this bug fix.
```

```text
Use $agent-workflow-governance and make sure the final response includes branch,
validation, risk, and handoff state.
```

```text
Use Agent Workflow Governance before editing. First identify the owning workspace,
then check git status and relevant durable records.
```

The skill is designed to be lightweight. It does not force every small question
through a heavyweight process. It applies when the task affects code, config,
durable decisions, future teammates, customer-facing behavior, or long-term
project constraints.

## Durable Record Selection

Prefer the durable record system the repository already uses. Do not introduce a
new tool just because this skill mentions it.

| Record system | Best for |
| --- | --- |
| OpenSpec | Structured feature changes, requirements, designs, tasks, acceptance criteria, and spec evolution |
| Spec Kit | Existing constitution/spec-driven workflows for principles, specifications, and implementation plans |
| ADR | Architecture decisions, technical tradeoffs, and why option A was chosen over option B |
| Issue tracker | Bugs, execution state, priority, assignment, milestones, and delivery management |
| Design doc | Broad proposals, problem framing, tradeoff analysis, and cross-team review |
| Runbook | Repeatable operations, incident handling, deployment checks, and rollback steps |
| README / Project notes | Lightweight usage, setup, migration, adoption, or human-facing guidance |

If no durable record system exists, the agent should not silently initialize
OpenSpec, Spec Kit, or ADR directories. It should propose a target and reason,
then wait for user confirmation.

Detailed record-selection guidance lives in
[references/durable-record-decision.md](references/durable-record-decision.md).

## Expected Agent Behavior

When the skill is active, an agent should:

- inspect the actual repository boundary before editing;
- avoid broad context loading when a smaller context set is enough;
- check git status before changing files;
- avoid overwriting unrelated user changes;
- create or use a task branch when appropriate;
- keep edits focused;
- validate the change with task-relevant checks;
- review whether existing behavior may be affected;
- update durable records if the repository already uses a record system;
- close with clear state rather than vague summaries.

## Repository Structure

```text
SKILL.md
agents/
  openai.yaml
references/
  durable-record-decision.md
  git-lifecycle.md
  impact-review.md
  risk-and-context.md
```

### `SKILL.md`

The main skill entry. It contains the trigger metadata and the required workflow.

### `agents/openai.yaml`

Optional UI metadata for OpenAI Codex skill lists and chips.

### `references/`

Progressively loaded guidance. The agent should read only the reference needed
for the current task:

- [durable-record-decision.md](references/durable-record-decision.md): durable record ownership and update decisions.
- [git-lifecycle.md](references/git-lifecycle.md): branch, commit, merge, and primary-branch hygiene.
- [impact-review.md](references/impact-review.md): existing-behavior impact review.
- [risk-and-context.md](references/risk-and-context.md): high-risk operations and context-heavy work.

## Compatibility

The skill is written for Codex skill conventions, but the workflow principles can
be adapted to other coding agents that support custom instructions or reusable
workflow prompts.

Known target agents:

- Codex;
- Claude Code;
- Cursor;
- Gemini CLI;
- similar AI coding agents.

Agent-specific support may vary. Codex skill metadata is included in this
repository; other agents may require manual import into their own instruction or
rule systems.

## Open Source Boundary

This repository intentionally contains only generic workflow governance.

It should not contain:

- private company process;
- customer names;
- production credentials;
- deployment-specific secrets;
- proprietary release procedures;
- internal project memory;
- private context governance datasets.

If you adapt this skill for your team, keep project-specific release, compliance,
and production rules in your private workspace.

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md).

## Security

See [SECURITY.md](SECURITY.md).

## License

This project is licensed under the MIT License. See [LICENSE](LICENSE).
