# Example: ADR Decision

Use this prompt when the important output is a durable technical decision.

```text
Use $agent-workflow-governance for this architecture decision.

Decision topic:
<describe the architecture or technical decision>

Context:
<describe the constraints, current system, and why the decision matters>

Options:
- Option A: <summary>
- Option B: <summary>
- Option C: <summary, if any>

Please:
1. Identify the owning workspace or repository.
2. Check whether an ADR system already exists.
3. If no ADR system exists, propose where the decision should be recorded and wait for confirmation.
4. Compare options with tradeoffs, not just pros and cons.
5. Record the selected decision, rejected alternatives, consequences, validation needs, and follow-ups.
6. Link related docs, specs, code paths, issues, or tests.
7. Close out with durable record location and remaining risk.
```

Minimal ADR shape:

```text
# ADR: <decision title>

Status:
Accepted | Proposed | Superseded

Context:
<why this decision exists>

Decision:
<what was chosen>

Alternatives:
- <rejected option and why>

Consequences:
- <expected impact>

Follow-ups:
- <validation or implementation work>
```
