# Example: OpenSpec Change

Use this prompt when the repository already uses OpenSpec and the task changes product or engineering behavior.

```text
Use $agent-workflow-governance for this OpenSpec-backed change.

Change intent:
<describe the feature, bug behavior, or requirement change>

Please:
1. Confirm this repository already uses OpenSpec.
2. Check active OpenSpec changes before proposing a new one.
3. Identify the owner workspace for the behavior.
4. Propose the OpenSpec change target before writing durable records.
5. Keep the proposal focused on this behavior.
6. Link related specs, code paths, tests, and follow-ups.
7. Implement only after the scope is clear.
8. Run focused validation.
9. Close out with OpenSpec status, git status, validation, risk, and next step.
```

When not to use this:

- Do not initialize OpenSpec silently in a repository that does not already use it.
- Do not create broad OpenSpec changes for pure read-only questions.
- Do not store chat narration as durable specification content.
