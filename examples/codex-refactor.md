# Example: Codex Refactor

Use this prompt when asking Codex to refactor code without mixing unrelated changes.

```text
Use $agent-workflow-governance for this refactor.

Goal:
<describe the refactor goal>

Constraints:
- Preserve existing behavior unless I explicitly approve behavior changes.
- Do not mix formatting-only churn with logic changes.
- Keep unrelated dirty files untouched.

Please:
1. Identify the owning workspace or repository.
2. Check git status before editing.
3. Explain the refactor boundary before making changes.
4. Run tests or focused validation that prove behavior is preserved.
5. Review existing-behavior impact.
6. Update durable records only if the refactor changes architecture, ownership, API behavior, or future maintenance rules.
7. Close out with changed files, validation, risk, and follow-up state.
```

Durable record guidance:

- Use an ADR if the refactor changes an architecture decision.
- Use OpenSpec or Spec Kit only if the repository already uses them and the refactor changes requirements, design, or acceptance criteria.
- Use project notes or README only if the refactor changes how humans use, build, or maintain the project.
