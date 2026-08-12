# AGENTS.md Template

```md
# AGENTS.md

## Project mode
This project is currently optimized for: <demo-first | production-first | migration safety | hardening | other>.

## Stable architecture constraints
- ...
- ...

## Execution rules
- Implement only the task explicitly requested.
- Future roadmap items are context, not permission.
- Do not introduce infrastructure or abstractions not required by the current gate.
- Do not refactor unrelated areas.
- Preserve documented boundaries.
- Report ambiguity before changing a documented architecture decision.

## Validation rules
Before declaring completion:
- run relevant build/tests;
- run typecheck/lint where applicable;
- perform task-specific smoke checks;
- report failures instead of hiding them.

## Change reporting
At the end, report:
- files changed;
- outcome delivered;
- validation performed;
- deferred work;
- unresolved risks or ambiguity.
```

Use this file for stable project-level rules. Do not overload it with details that belong to one task only.
