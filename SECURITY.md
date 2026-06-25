# Security Policy

Agent Workflow Governance is a documentation and skill repository. It does not
ship a runtime service and does not process user data by itself.

Security still matters because workflow instructions can influence how agents
handle code, credentials, production systems, and durable records.

## Supported Scope

Please report issues related to:

- unsafe workflow guidance;
- instructions that could cause accidental destructive git operations;
- instructions that encourage exposing secrets;
- instructions that blur production, staging, or local boundaries;
- examples that accidentally include private or sensitive information.

## Out Of Scope

The following are outside the direct scope of this repository:

- vulnerabilities in Codex, Claude Code, Cursor, Gemini CLI, or other agent
  runtimes;
- vulnerabilities in user projects that install this skill;
- organization-specific release or deployment failures caused by private rules
  outside this repository.

## Reporting

For now, please open a GitHub issue with a minimal description if the issue is
not sensitive.

If the report contains sensitive details, avoid posting secrets, tokens, private
repository names, customer data, or production infrastructure details in public.
Open a minimal issue asking for a private contact path instead.

## Secret Handling

Do not contribute:

- API keys;
- tokens;
- certificates;
- private repository names;
- customer identifiers;
- production hostnames;
- internal incident details.

If such information is accidentally committed, rotate the secret immediately and
remove it from git history before publishing.
