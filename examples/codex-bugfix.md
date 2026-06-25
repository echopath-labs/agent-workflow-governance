# Example: Codex Bug Fix

Use this prompt when asking Codex to handle a real bug fix with workflow discipline.

```text
Use $agent-workflow-governance for this bug fix.

Problem:
<describe the bug and observed behavior>

Expected behavior:
<describe what should happen>

Please:
1. Identify the owning workspace or repository before editing.
2. Check git status and preserve unrelated user changes.
3. Read the smallest relevant context set.
4. Decide whether this needs a durable record.
5. Keep the fix scoped.
6. Run focused validation.
7. Review existing-behavior impact.
8. Close out with branch, git status, validation, risk, and handoff state.
```

Expected closeout shape:

```text
Branch:
<branch name>

Changed:
- <files or behavior changed>

Validation:
- <commands run and result>

Durable record:
- <updated / not needed / proposed target>

Risk:
- <remaining risk or none>

Handoff:
- <what the next human or agent should know>
```
