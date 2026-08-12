# Origin Story

Gated Development was not designed as a theoretical process first. It emerged from a product that was being built quickly with AI coding agents.

## The situation

The project started as a consumer fitness application. It already had a working mobile app, backend, database, offline workout execution, nutrition flows and an AI coach.

Then the product direction changed substantially.

Instead of serving end users directly, the product pivoted toward a B2B2C platform for personal trainers and their students. That meant introducing new actors, changing ownership rules, redesigning the domain, splitting API responsibilities, rethinking branding and preserving only selected parts of the original product.

Technically, this was not a small feature request. It was a controlled product rewrite on top of a working codebase.

## What did not work well

Large prompts describing the entire target state produced useful output, but not consistently useful change sets.

The coding agent often understood the destination while still making locally-reasonable decisions that created review friction:

- implementing future features early;
- carrying old domain assumptions into the new product;
- adding infrastructure that was not needed for the demo;
- mixing product decisions with technical refactors;
- widening the scope beyond what was easy to verify.

The issue was not lack of capability. It was too much execution freedom at once.

## The change

The work was reorganized into small milestones and even smaller executable tasks.

The agent still received the full product context and roadmap, but each execution prompt explicitly limited authority to one task.

Every task started to include:

- a single objective;
- relevant current-state context;
- allowed changes;
- explicit forbidden changes;
- non-goals;
- acceptance criteria;
- validation steps;
- a required completion report.

One instruction became particularly important:

> Do not implement future milestones.

This sounds obvious, but making it explicit changed the agent's behavior.

## What improved

The resulting changes became easier to reason about.

Reviews were smaller. Failures were easier to localize. The agent stopped trying to solve problems that belonged to later phases. Architecture became more intentional because future constraints could be documented without automatically becoming implementation scope.

A useful pattern appeared:

> Let the agent know the whole future, but authorize only the present.

For example, the product team knew a single demo mobile app might eventually split into separate trainer and student apps. Instead of doing the split immediately, the current task only required boundaries that would make the future split cheap. Later, when the real repository state justified doing the split sooner, the roadmap could be adjusted.

That is also an important part of the methodology: milestones are not immutable. After meaningful checkpoints, the actual repository is inspected again and future work is refined from reality.

## Why publish this

AI coding agents are becoming capable enough that prompt quality alone is no longer the main challenge.

The harder problem is execution management:

- how much context should the agent receive?
- how much authority should it have?
- how do we keep architectural direction without overbuilding?
- how do we review autonomous work without turning every run into a large forensic exercise?

Gated Development is an attempt to document one practical answer.

It is intentionally simple. It does not require an orchestration platform or a new programming model. The first version is mostly disciplined documentation, explicit gates and frequent verification.

The methodology may evolve, but its origin remains practical: a real product moved faster and with less drift once agent execution became deliberately bounded.
