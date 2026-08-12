# Task Template

```md
# <TASK-ID> — <Short title>

## Objective
What single outcome must this task produce?

## Why
Why is this task needed now?

## Current state
Relevant facts about the repository before execution.

## Allowed changes
- ...

## Forbidden changes / non-goals
- ...
- Do not implement future tasks.
- Do not refactor unrelated areas.

## Expected behavior
Describe observable behavior after completion.

## Acceptance criteria
- [ ] ...
- [ ] ...
- [ ] ...

## Validation
Run:

```text
<build command>
<test command>
<typecheck/lint command>
```

Perform smoke check:
- ...

## Report format
At the end, report:
- files changed;
- what was implemented;
- validation commands and results;
- anything intentionally deferred;
- unresolved ambiguity or risk.
```

## Authoring guidance

A task is too broad when its acceptance criteria describe several independent user-visible outcomes or architectural changes.

When in doubt, split it.

The agent should be able to answer "what was this task for?" with one sentence.
