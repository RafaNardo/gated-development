# Example — Product Pivot with Gated Development

This example is intentionally generic and based on a real type of product transition.

## Scenario

A working mobile product has:
- one Expo app;
- one ASP.NET Core API;
- PostgreSQL;
- offline workout logging;
- nutrition flows;
- an AI assistant.

The business pivots from a direct-to-consumer fitness app to a B2B2C platform with two actors:
- Trainer;
- Student.

The target architecture may later include two mobile apps and two API surfaces.

A broad request such as:

```text
Rewrite this product for trainers and students, split the APIs, prepare two apps,
rework the domain, keep the useful features and remove the old methodology engine.
```

contains too many independent decisions for one safe execution gate.

## Gated version

### M0 — Foundation
Goal: neutralize the old product assumptions while keeping the technical baseline working.

Tasks:
- M0-001: audit and preserve reusable infrastructure;
- M0-002: rename solution/packages;
- M0-003: introduce separate API surfaces;
- M0-004: establish actor-separated mobile feature boundaries;
- M0-005: introduce the new core domain.

Each task is executable independently.

### Example task

```md
# M0-003 — Split API surfaces

## Objective
Create TrainerApi and StudentApi hosts that share the same Domain,
Application, Infrastructure and DbContext.

## Allowed
- add two API hosts;
- move endpoint registration as required;
- share application/infrastructure projects.

## Forbidden
- do not create separate databases;
- do not create microservices;
- do not implement trainer dashboard features;
- do not implement student onboarding;
- do not change mobile navigation;
- do not begin M0-004.

## Acceptance criteria
- both API hosts build;
- both start locally;
- OpenAPI surfaces are separate;
- both use the same database/infrastructure;
- no future product feature is introduced.
```

The agent knows the future product shape, but cannot jump to it.

## Future-aware boundary example

Suppose the demo currently uses one app, but two apps are expected later.

The task may require:

```text
features/trainer/* must not import features/student/*
features/student/* must not import features/trainer/*
actor-specific API clients remain separate
shared contains only neutral primitives/infrastructure
```

That is a future-aware decision.

It does **not** authorize creating two apps yet.

## Checkpoint

After M2, the team inspects the actual repository and realizes the actor experiences have diverged enough that splitting the apps now is cheaper than continuing with the original demo plan.

The roadmap is updated.

This is not a failure of planning. It is the intended process:

> plans provide direction; repository state opens the next gate.
