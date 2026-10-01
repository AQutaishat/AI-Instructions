---
name: local-development-checklist
description: Use when setting up or verifying a local development environment (containerized services, seed data, or pre-milestone checks) — a practical checklist for getting an app running and validated locally.
---

## When to use
When a fresh environment needs to be brought up, when seeding demo data, or before accepting a meaningful UI/feature milestone.

## When not to use
Production deployment or CI setup — use the project's deployment docs and backup-restore-procedure instead.

## Expected local environment
- Container runtime (e.g. Docker) available.
- Database container.
- Structured-logging viewer container (e.g. Seq, or equivalent), if the project uses one.
- A lightweight DB viewer/admin tool.
- Backend runtime/SDK for the project's language.
- Frontend tooling (Node/npm or equivalent) if applicable.

## Startup goal
Start required supporting services via a compose file or equivalent, then run the API/frontend predictably (in or out of containers per developer workflow).

## Minimum seed/demo data
Seed enough realistic data to exercise the core domain end-to-end, generally including:
- One or more top-level accounts/tenants (if multi-tenant).
- An admin/owner user and at least one non-admin user role.
- Several representative core-domain records (products, items, entities the app manages).
- Several customer/end-user records.
- Records spanning multiple statuses/states the app defines.
- Any secondary domain objects (transactions, balances, subscriptions) once those modules exist.

## Before accepting a meaningful UI milestone
Use focused verification for small edits. After several connected steps or a real milestone:
1. Run the actual application.
2. Verify any required localization/RTL behavior, if the project needs it.
3. Verify representative mobile/desktop layout.
4. Confirm no horizontal overflow.
5. Check relevant API/database state.
6. Review logs for errors.
7. Use E2E tooling/screenshots only when they materially add confidence — avoid generating artifacts for every small change.

## Golden-path local verification
Define one representative end-to-end path through your project's core domain (e.g. create → process → complete) and re-run it as the smoke test for local setup, rather than testing every feature individually.
