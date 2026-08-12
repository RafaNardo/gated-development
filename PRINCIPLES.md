# Principles

## 1. Global context, local authority

The agent may read the product vision, architecture, roadmap and future constraints. That does not mean it may implement all of them.

The current gate defines execution authority.

## 2. One task, one outcome

A task should end in a concrete, observable result. Avoid tasks such as "improve the architecture" or "finish the backend".

Prefer: "split the API surface into TrainerApi and StudentApi while keeping one shared DbContext."

## 3. Explicit non-goals

Agents often expand scope in ways that seem reasonable locally. Non-goals prevent this.

Examples:
- do not add billing;
- do not introduce Redis;
- do not create production auth;
- do not implement future AI features;
- do not refactor unrelated modules.

A strong task states both what success is and what success is not.

## 4. Future-aware, present-scoped

Known future decisions should influence boundaries today without forcing implementation today.

If an app will later split into two apps, organize actor-specific features to keep that future move cheap. Do not perform the split until a gate authorizes it.

## 5. No speculative refactors

Refactoring is allowed when it is necessary to complete the current task safely or when the task explicitly requests it.

"This could be cleaner" is not enough reason to widen a gate.

## 6. Verification belongs inside the gate

A task is not complete when code is written. It is complete when its exit criteria have been checked.

Typical validation:
- build;
- tests;
- typecheck;
- lint;
- migration checks;
- smoke test;
- a specific end-to-end behavior.

## 7. Re-plan from reality

A roadmap is written before the future exists. After each meaningful checkpoint, inspect the repository and refine upcoming gates based on the actual system state.

Do not blindly execute stale assumptions.

## 8. Declare the optimization mode

The agent should know what the project is optimizing for.

Examples:
- demo-first;
- production-first;
- migration safety;
- hardening;
- cost reduction;
- time-to-validation.

A demo-first project should not accidentally spend days on infrastructure nobody will see.

## 9. Separate architectural constraints from task instructions

Stable constraints belong in repository-level documentation such as `AGENTS.md` or architecture docs.

Task prompts should point to those constraints instead of re-inventing them every time.

## 10. Checkpoints are part of autonomy

Frequent checkpoints do not make an agent less useful. They make longer-term autonomy safer and more predictable.

A good autonomous workflow is not "run forever." It is "complete one bounded gate, verify, then continue with renewed context."
