# Process

Gated Development organizes agentic software work into a sequence of explicit execution gates.

## 1. Establish the system context

Before implementation, document:

- product vision;
- current architecture;
- important constraints;
- optimization mode;
- major known future decisions.

This gives the agent enough context to avoid locally-correct but globally-wrong choices.

## 2. Build a roadmap

The roadmap is a map, not a queue of permissions.

A milestone should group a meaningful product or engineering capability. It may contain several small tasks.

Example:

```text
M0 — Foundation
M1 — Core workflow
M2 — Invitations and onboarding
M3 — Prescription flow
M4 — Polish and demo completion
M5 — Production hardening
```

## 3. Define the current gate

Each task should declare:

- ID;
- objective;
- why it exists;
- current state;
- allowed changes;
- forbidden changes;
- expected behavior;
- acceptance criteria;
- validation;
- required report format.

See `templates/TASK.md`.

## 4. Execute only the current gate

The agent should be explicitly instructed not to implement future tasks, even when those tasks are visible.

Recommended prompt:

```text
Read AGENTS.md, the roadmap and the current task.
Implement only the current task.
Do not implement future milestones.
Respect all explicit non-goals and architecture constraints.
Run the required validation.
Report changed files, validation results and unresolved ambiguities.
```

## 5. Verify the exit criteria

The gate closes only after its acceptance criteria are satisfied.

Verification can include code-level checks and product-level behavior.

Example:

```text
Build passes
Typecheck passes
Both API hosts start
Trainer endpoint cannot access another trainer's student
No future billing code exists
```

## 6. Inspect repository state

Before a significant next milestone, inspect the real repository again.

Ask:

- Did the previous gate change assumptions?
- Did new coupling appear?
- Is a planned future task still the right next step?
- Should an architectural decision be recorded?

This prevents roadmap drift.

## 7. Open the next gate

Only after review should the next task become executable.

The lifecycle is therefore:

```text
Context
  ↓
Gate definition
  ↓
Execution
  ↓
Verification
  ↓
Repository inspection
  ↓
Plan adjustment
  ↓
Next gate
```

## Milestone vs task

A **milestone** defines a bounded capability.

A **task** defines one executable change within that milestone.

For small projects, a milestone may itself be executable. For larger or riskier work, break it into multiple tasks.

## Suggested task size

A good task is usually small enough that:

- the agent can explain the entire diff coherently;
- a human can review it without reconstructing the whole project;
- failure is easy to localize;
- rollback is straightforward;
- acceptance criteria are concrete.

The correct size is not measured in lines of code. It is measured in conceptual surface area.
