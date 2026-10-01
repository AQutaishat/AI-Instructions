---
name: ai-agent-implementation-rules
description: Use when acting as a coding agent implementing work on a software project — governs context-gathering before implementation, testing economy, milestone end-to-end verification, screenshot policy, and scope discipline.
---

## When to use
At the start of any substantial implementation task, and while deciding how much testing/verification a change warrants.

## When not to use
Trivial one-line edits or pure Q&A where no project context is needed.

## Rules

### Establish context first
Before substantial implementation:
- Read the relevant project/reference docs (architecture, requirements, decisions).
- Read applicable rules/procedure docs for the project.
- Read the current implementation-status or task-tracking doc if one exists.
- Inspect the actual backend/frontend code being changed.
- Read recent progress-log entries only when historical detail is useful.
- Do not assume a previous session's notes accurately reflect current code — verify against the real code.

### Implement, don't re-plan
If project docs already define the behavior, implement it. Resolve ambiguity from existing docs/code first; ask the user only when a missing decision materially changes behavior.
Do not silently expand scope — deferred ideas go into a future-work/backlog doc rather than being built unasked.

### Local infrastructure
Use whatever local dev stack the project defines (containers for DB/logging/admin tooling are common). App services may run in or out of containers depending on developer workflow.

### Testing strategy — necessary but economical
Use the cheapest reliable check for the change size:
- Unit tests for isolated business rules.
- Integration tests for API/database behavior.
- Focused manual/local verification for small UI changes.
- Full end-to-end and screenshot-heavy verification only after a meaningful milestone, several connected steps, or a materially changed critical user journey.

Avoid: re-running the full E2E suite after every small edit; generating many screenshots for routine steps; dumping verbose browser/page state unless diagnosing a failure; re-screenshotting after every trivial interaction when the result is already deterministically known.

### Critical E2E milestone golden path
At meaningful milestones, verify the real running app end-to-end along the project's actual core user journey (e.g. create → process → complete, for whatever domain object the app centers on). Define this path once per project and re-run it at milestones rather than after every change.

### Screenshot policy
Capture screenshots only when they add value: major visual milestone, responsive/RTL verification, regression comparison, bug evidence, release candidate. Prefer a small representative set over screenshotting every step.

### Persisted-state verification
For critical flows, verify actual server/DB outcomes, not just UI appearance — screenshots do not replace state assertions.

### Logging
Respect the project's logging conventions (see `programming-conventions` skill). Never log secrets/passwords/OTP/tokens.

### Documentation after implementation
After each meaningful implementation unit:
1. Append factual detail to the project's progress log, if one exists.
2. Update the implementation-status doc with current phase/status.
3. Update a future-work/backlog doc only when new deferred work is identified.
4. Change stable reference docs only when implementation changed an approved fact/decision.

(See the `documentation-update-discipline` skill for this step in isolation.)
