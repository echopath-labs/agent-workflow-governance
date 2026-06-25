# Agent Workflow Governance

Lightweight workflow guardrails for AI-assisted engineering.

This repository provides a Codex-compatible skill for teams using coding agents
such as Codex, Claude Code, Cursor, Gemini CLI, or similar tools.

It focuses on:

- workspace ownership;
- durable engineering records;
- git hygiene;
- impact review;
- risk control;
- context handoff;
- closeout discipline.

It does not attempt to solve long-term Agent memory, context ownership, or
project cognition. Those are separate context governance problems.

## Why This Exists

Coding agents are good at implementing code. Long-running teams still need a
repeatable way to keep agent-assisted work:

- scoped;
- reviewable;
- recoverable;
- auditable;
- safe to hand off.

This skill gives agents a minimal workflow layer for important engineering
changes without importing company-specific release, deployment, or operations
rules.

## Repository Structure

```text
skills/
  agent-workflow-governance/
    SKILL.md
    agents/
      openai.yaml
    references/
      durable-record-decision.md
      git-lifecycle.md
      impact-review.md
      risk-and-context.md
```

## Install

Copy or symlink the skill folder into your Codex skills directory:

```bash
mkdir -p ~/.codex/skills
ln -s "$(pwd)/skills/agent-workflow-governance" ~/.codex/skills/agent-workflow-governance
```

Then use:

```text
$agent-workflow-governance
```

or ask your coding agent to use Agent Workflow Governance for an important
engineering change.

## What The Skill Does

The skill helps an Agent:

1. identify the owning workspace or repository;
2. decide whether durable records are needed;
3. preserve existing user changes;
4. choose branches deliberately;
5. keep edits scoped;
6. run focused validation;
7. review existing-behavior impact;
8. update durable records when appropriate;
9. close out with branch, git, validation, risk, and handoff state.

## What The Skill Does Not Do

This skill does not:

- define your release process;
- deploy to production;
- rewrite project memory;
- replace OpenSpec, ADRs, issues, or docs;
- infer Kubernetes, GitLab CI, image, rollback, or customer-data procedures;
- store long-term Agent memory.

For release, rollback, CI/CD, shared environment, or customer-data operations,
use your project-specific checklist.

## Relationship To EchoPath

This project is part of the EchoPath Labs research and dogfooding ecosystem.

It covers Workflow Governance:

```text
How should the Agent work?
```

EchoPath focuses on Context Governance:

```text
What should the Agent remember, where does it belong, and how can it be recovered later?
```

The two layers are complementary but intentionally separate.

## License

MIT
