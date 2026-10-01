# Taw — Local Development Checklist

This file is a practical local-development checklist.

## Expected local environment

- Docker available.
- PostgreSQL container.
- Seq container.
- Adminer or equivalent development DB viewer.
- ASP.NET Core SDK.
- Node/npm tooling for React/Vite.

## Typical startup goal

A contributor/agent should be able to start required supporting services with Docker Compose and then run API/frontend in a predictable way.

## Minimum seed/demo data

Useful development seed data:

- Demo water station tenant.
- Owner.
- Employee/dispatcher.
- Two drivers.
- Several water products.
- Several customers/addresses.
- Orders across multiple statuses.
- Some bottle balances/transactions.
- One or more subscriptions after that module exists.

## Before accepting a meaningful UI milestone

For small edits, use focused verification. After several connected steps or a meaningful milestone:

- Run the actual application.
- Verify Arabic RTL.
- Verify representative mobile/desktop layout.
- Confirm no horizontal overflow.
- Check relevant API/database state.
- Review Seq logs for errors.
- Use Playwright/screenshots only when they materially add confidence; avoid generating artifacts after every small change.

## Golden-path local verification

```text
Tenant exists
→ Product visible in public store
→ Guest order succeeds
→ Admin sees order
→ Driver assignment persists
→ Driver sees delivery
→ Delivery completes
→ Bottle transaction persists
```
