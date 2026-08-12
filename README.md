# Gated Development

> **Global context. Local authority. Explicit gates.**

Gated Development is a milestone-driven methodology for building software with AI coding agents.

It emerged from a practical problem: modern coding agents are extremely capable, but broad prompts often make them do too much at once. They may implement future features prematurely, introduce infrastructure that is not needed yet, refactor unrelated areas, or make architectural decisions before the product has earned that complexity.

Gated Development addresses this by separating **what the agent is allowed to understand** from **what the agent is allowed to change**.

The agent receives the whole map — product vision, architecture, roadmap, future constraints — but only one key at a time: the current task or milestone.

## Core idea

```text
Vision
  ↓
Architecture constraints
  ↓
Roadmap
  ↓
Current milestone
  ↓
Current task
  ↓
Build / Test / Review
  ↓
Next gate
```

A future decision may influence today's architecture without becoming today's implementation.

For example, a team may already know that one mobile application will eventually be split into two apps. The current task does not need to perform that split. It only needs to avoid coupling the code in a way that would make the future split unnecessarily expensive.

This is the distinction at the heart of Gated Development:

> **Future-aware. Present-scoped.**

## Why this exists

This methodology was shaped while building a real product with AI coding agents. The project began with one business model and later went through a substantial product pivot involving new actors, a new domain model, different API boundaries and a new user experience.

The first instinct was to give the agent a large prompt describing the whole target state. That worked partially, but the agent repeatedly "hit the post": it understood the goal, yet broad scope made implementations less predictable, harder to review and more likely to include premature decisions.

The workflow changed. Instead of asking for the transformation all at once, the work was divided into narrowly-scoped milestones and tasks. Each task explicitly described:

- the objective;
- the current context;
- what changes were allowed;
- what changes were forbidden;
- non-goals;
- acceptance criteria;
- validation commands;
- the expected final report.

Most importantly, the agent was told **not to implement future milestones**, even though those milestones were visible in the roadmap.

The difference was immediate: smaller diffs, less architectural drift, easier reviews, clearer failures and much more predictable agent behavior.

This repository exists to turn that working pattern into a reusable methodology.

## Principles

1. **Global context, local authority** — agents should understand the system broadly, but receive narrow execution permission.
2. **One task, one outcome** — each task should produce one observable, reviewable result.
3. **Explicit non-goals** — say what must *not* be implemented.
4. **Future-aware architecture** — known future constraints may shape today's boundaries without authorizing future work.
5. **No speculative refactors** — refactor only when required by the current gate or explicitly planned.
6. **Verification is part of the task** — build, test, typecheck and behavioral checks belong inside the gate.
7. **Re-plan from reality** — future tasks should be refined from the repository's actual state, not from assumptions made several milestones ago.
8. **Optimization mode must be declared** — demo-first, production-first, migration-first, hardening-first, etc.

Read the full rationale in [PRINCIPLES.md](PRINCIPLES.md) and the execution model in [PROCESS.md](PROCESS.md).

## Repository structure

```text
gated-development/
├── README.md
├── MANIFESTO.md
├── PRINCIPLES.md
├── PROCESS.md
├── CONTRIBUTING.md
├── docs/
│   ├── origin-story.md
│   └── linkedin-post-ptbr.md
├── templates/
│   ├── AGENTS.md
│   ├── MILESTONE.md
│   ├── TASK.md
│   └── DECISION.md
└── examples/
    └── product-pivot.md
```

## Minimum viable adoption

You do not need new tooling to use Gated Development. A repository can start with four files:

```text
AGENTS.md
ROADMAP.md
CURRENT_TASK.md
DECISIONS.md
```

The agent receives all four, but its execution prompt points to exactly one task.

A minimal task prompt can be as small as:

```text
Read AGENTS.md, ROADMAP.md and CURRENT_TASK.md.
Implement only the current task.
Do not implement future milestones.
Respect all explicit non-goals.
Run the required validation commands.
At the end, report files changed, validation performed and unresolved ambiguities.
```

The quality comes primarily from the structure of the task definition, not from prompt length.

## When it works well

Gated Development is especially useful for:

- greenfield products;
- large product pivots;
- legacy modernization;
- framework or runtime migrations;
- vulnerability remediation;
- architecture refactors;
- cloud migrations;
- proof-of-concepts;
- production hardening.

It is tool-agnostic. The same principles can be used with Codex, Claude Code, GitHub Copilot or other coding agents.

## What it is not

Gated Development is not a replacement for engineering judgment, code review, testing or architecture design.

It is also not about maximizing agent autonomy.

The goal is the opposite:

> **Make autonomous execution controlled, reviewable and predictable.**

## Status

This repository is an early public draft of a methodology extracted from real-world usage. The vocabulary, templates and examples are expected to evolve as the approach is tested across more projects.
