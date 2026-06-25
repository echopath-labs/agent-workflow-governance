# Contributing

Thank you for considering a contribution to Agent Workflow Governance.

This repository is intentionally small. The goal is to provide generic workflow
guardrails for AI-assisted engineering without turning the skill into a private
company process manual.

## Contribution Scope

Good contributions include:

- clearer workflow wording;
- better agent closeout guidance;
- safer git hygiene guidance;
- improved impact review prompts;
- examples that remain generic and vendor-neutral;
- compatibility notes for different coding agents;
- typo, formatting, and readability fixes.

Avoid contributions that add:

- company-specific deployment procedures;
- customer-specific rules;
- private repository names;
- production credentials or secret handling details;
- proprietary incident response steps;
- long-term memory or context governance internals;
- broad marketplace or product-positioning material unrelated to this skill.

## Design Principles

Keep the skill:

- concise;
- agent-readable;
- progressively disclosed;
- practical for real engineering changes;
- independent of any single project management or specification system.

`SKILL.md` should stay lean. Put conditional or detailed guidance in
`references/` and link to it from `SKILL.md`.

## Local Validation

Before opening a pull request, check:

1. `SKILL.md` has valid YAML frontmatter.
2. `name` and `description` still clearly explain when the skill should trigger.
3. `agents/openai.yaml` still matches the skill's purpose.
4. New guidance does not introduce private team rules.
5. New guidance does not conflict with the MIT license or this contribution
   boundary.

## Pull Request Guidance

In your pull request, explain:

- what workflow problem the change addresses;
- which file changed;
- whether the change affects agent behavior;
- whether the change is generic or project-specific.

Project-specific workflow rules should usually live in your private fork or
workspace, not in this public baseline.
