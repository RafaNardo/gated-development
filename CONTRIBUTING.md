# Contributing

Gated Development is intentionally lightweight and tool-agnostic.

Contributions are welcome when they improve one of these areas:

- task/milestone authoring;
- reviewability;
- validation strategy;
- agent handoff;
- repository checkpointing;
- examples from real software work;
- adaptations for migration, security remediation or production hardening.

## Contribution principles

Please prefer concrete examples over abstract terminology.

When proposing a new rule, explain:
- what problem it addresses;
- how it changes agent behavior;
- what trade-off it introduces;
- whether it is a stable principle or a situational technique.

Avoid coupling the methodology to one vendor, model or IDE unless the contribution is explicitly an integration example.

## Vocabulary

- **Gate**: the currently-authorized unit of execution.
- **Task**: one bounded executable change.
- **Milestone**: a coherent capability containing one or more tasks.
- **Global context**: product/architecture/roadmap knowledge visible to the agent.
- **Local authority**: the subset of changes the current gate allows.
- **Non-goal**: an explicit statement of what must not be implemented now.
- **Checkpoint**: review of the actual repository state before opening the next meaningful gate.
