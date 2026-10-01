# Taw — AI / Coding-Agent Implementation Rules

These rules apply to Codex, Claude and other coding agents working on Taw.

## Establish current context first

Before substantial implementation:

- Read the relevant `docs/project-docs/` files.
- Read the applicable `docs/instructions-docs/` files.
- Read `docs/working-docs/02-implementation-status.md`.
- Inspect the backend/frontend code that will actually be changed.
- Read recent `01-progress.md` entries only when historical implementation detail is useful.

Do not assume a previous agent session accurately reflects current code.

## Implement approved scope instead of re-planning

If project docs already define the behavior clearly, implement it. Resolve ambiguity from existing docs/code first and ask only when the missing decision materially changes behavior.

Do not expand scope silently. Deferred ideas belong in `docs/working-docs/03-future-work.md`.

## Docker/local infrastructure

Use Docker Compose for reproducible supporting services such as:

- PostgreSQL.
- Seq.
- Adminer or equivalent DB inspection tool.

The API/frontend may run inside or outside Docker depending on the developer workflow.

## Testing strategy — necessary but economical

Testing is required, but do not run expensive full-browser/end-to-end cycles after every tiny code edit.

Use the cheapest reliable check for the current change:

- Unit tests for isolated business rules.
- Integration tests for API/database behavior.
- Focused manual/local verification for small UI changes.

Use Playwright/full E2E and screenshot-heavy verification **after a meaningful milestone, after several connected steps, or when a critical user journey has materially changed**.

Avoid:

- Re-running the entire Playwright suite after every small edit.
- Generating large numbers of screenshots/files for routine steps.
- Dumping verbose browser/page state unless needed to diagnose a failure.
- Re-reading/re-screenshotting a page after every trivial interaction if the action result is already deterministically known.

This is intended to reduce execution time, token usage and unnecessary artifacts without removing milestone-level quality verification.

## Critical E2E milestones

At meaningful milestones, verify the real running application for the golden path:

```text
Tenant/water station
→ water product
→ public store
→ guest order
→ admin sees order
→ assign driver
→ driver sees delivery/location
→ complete delivery
→ bottle transaction/balance updated
```

When the relevant modules exist, also milestone-test subscriptions and customer tracking.

## Screenshot policy

Capture screenshots only when they add value:

- major visual milestone
- responsive/RTL verification
- regression comparison
- bug evidence
- release candidate

A small representative set is preferred over screenshotting every step.

## Persisted-state verification

For critical flows, verify important server/database outcomes, for example:

- order persisted
- tenant isolation correct
- assignment persisted
- delivery status changed
- bottle transaction created

Screenshots do not replace state/assertion checks.

## Logging/observability

Respect the logging conventions in `01-programming-conventions.md` and the architecture document.

Logs should include when available:

- Environment
- SourceApp (`web`, `admin`, `mobile`, etc.)
- RequestId propagated across related HTTP calls
- TraceId
- TenantId
- UserId after authentication
- CustomerId where useful
- operation/endpoint

Never log secrets, passwords, OTP values or tokens.

## Documentation after implementation

After each meaningful implementation unit:

1. Append detailed factual work to `docs/working-docs/01-progress.md`.
2. Update `docs/working-docs/02-implementation-status.md` with the concise current phase/status.
3. Update `docs/working-docs/03-future-work.md` only when new deferred work is identified.
4. Change stable project docs only when implementation changes an approved fact/decision.
