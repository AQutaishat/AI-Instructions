---
name: programming-conventions
description: Use when writing or reviewing backend/frontend code for a project — applies general architecture, database, logging, error, and security conventions so new code matches a consistent standard.
---

## When to use
Before and during any non-trivial implementation task (new endpoint, module, migration, service, etc.), and when reviewing code for consistency with project standards.

## When not to use
UI-only styling work (see ux-implementation-regulations) or one-off scripts that never ship.

## Rules

### Documentation structure
A useful convention: separate stable reference docs, rules/procedure docs, frequently-updated working logs, raw source materials, and local secrets (git-ignored) into distinct folders. Number files sequentially within a folder to indicate reading order only.

### Before substantial implementation
1. Read relevant stable reference docs (architecture, requirements, decisions).
2. Read applicable rules/procedure docs.
3. Inspect the actual current backend/frontend code being changed (do not rely on memory of a prior session).
4. Read the current implementation-status doc, if one exists.
5. Read recent progress-log entries if history matters.

### Scope discipline
- Implement only approved current scope. Do not silently add speculative/future features.
- Record useful-but-out-of-scope ideas in a future-work/backlog doc.

### Product language
- User-facing copy should use the product's actual domain terminology, in the target language(s), not raw internal/technical names.
- Example pattern: an internal generic entity name (e.g. `ReturnableContainer`) should be translated to the domain-appropriate user-facing term in the relevant language, not shown verbatim.

### Architecture
- Prefer a modular structure with vertical feature slices and explicit module boundaries (Modular Monolith is a reasonable default) over premature microservices.
- If multi-tenant, enforce tenant isolation consistently (e.g. a `TenantId` on shared tables) — this is a security requirement, not just a data-modeling detail.
- Business rules live in application/domain code, not only the frontend.
- API DTOs are explicit; never expose ORM entities directly as API contracts.

### Database
- Use migrations for all schema changes.
- Store timestamps in UTC; render in the user's/tenant's local timezone.
- Preserve business history — avoid destructive deletes of transactional/audit-relevant records.
- Use concurrency protection wherever assignment/claim/update races are possible.
- Pick one naming convention (e.g. snake_case in DB mapped from the language's native casing) and apply it consistently.

### Logging and correlation
Structured logs should carry, where available: environment, source app/service name, a request ID (propagated across downstream HTTP calls), a trace ID, a tenant ID (post tenant-resolution, if multi-tenant), a user ID (post-auth, null before), and the endpoint/operation name.
- Expose/return the correlation ID where useful for support.
- Never log passwords, OTP values, access/refresh tokens, private keys, client secrets, or raw credentials.

Example (one structured log entry):
```json
{"env":"prod","app":"api","requestId":"r-123","traceId":"t-456","tenantId":"acme","userId":null,"operation":"POST /orders","msg":"order rejected"}
```

### Errors
- Return a stable machine-readable error code, a localized/contextual user message, field errors when relevant, and trace/request IDs.
- Never expose raw exception text to end users.

Example:
```json
{"code":"ORDER_OUT_OF_STOCK","message":"<localized user message>","fieldErrors":{"quantity":"Only 3 left"},"requestId":"r-123"}
```

### Security
- Backend authorization is mandatory even when the UI hides an action.
- Enforce tenant/ownership boundaries server-side.
- A single weak identifier (e.g. a phone number alone) is not sufficient proof for accessing protected data.
- Secrets come only from ignored local credential files, environment variables, secret managers, or deployment-platform secret stores — never hardcoded.
