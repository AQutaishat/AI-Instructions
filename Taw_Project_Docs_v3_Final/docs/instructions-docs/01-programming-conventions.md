# Taw — Programming and Project Conventions

These are the active implementation conventions for the project. They replace older conventions that were explicitly rejected.

## Documentation structure

Use this structure:

```text
docs/
├── project-docs/       # relatively stable product/technical reference
├── instructions-docs/  # implementation rules and procedures
├── working-docs/       # frequently updated during implementation
├── materials/          # source images, wireframes, external docs, raw references
└── credentials/        # local sensitive/production credentials; ignored by Git
```


## File numbering

Within each documentation folder, Markdown filenames use sequential prefixes:

```text
01-
02-
03-
...
```

The numbers indicate reading order only.

## Working documents

The key frequently updated working documents are:

- `docs/working-docs/01-progress.md` — detailed chronological implementation log.
- `docs/working-docs/02-implementation-status.md` — current concise status/phase summary.
- `docs/working-docs/03-future-work.md` — deferred ideas/features discovered during implementation.

After each meaningful implementation unit, the coding agent should:

1. Append factual detail to `01-progress.md`.
2. Refresh `02-implementation-status.md` so it accurately summarizes the current phase and completed/current/next work.
3. Add genuinely deferred scope to `03-future-work.md` when needed.

Do not pre-fill the progress log with roadmap items that have not happened.

## Read context before substantial implementation

Before changing a module:

- Read the relevant `project-docs`.
- Read applicable `instructions-docs`.
- Inspect the current backend/frontend code being changed.
- Read `implementation-status.md` for the current state.
- Read recent `progress.md` entries when implementation history matters.
- Read `future-work.md` only when scope/deferred decisions are relevant.

Do not rely solely on memory from a previous agent session.

## Scope discipline

Implement approved current scope directly. Do not add competitor/future features silently.

If useful but not current scope, record it in `docs/working-docs/03-future-work.md`.

## Product language

Current UI is water-specific. Generic internal terminology must not leak into user-facing copy.

Examples:

- Internal: `ReturnableContainer`
- UI: قارورة / قارورة فارغة / رصيد القوارير

## Architecture conventions

- Modular Monolith.
- Vertical feature slices.
- Explicit module boundaries.
- Avoid premature microservices.
- Shared PostgreSQL database/schema with `TenantId` initially.
- Tenant isolation is a security requirement.
- Business rules belong in application/domain code, not only frontend code.
- REST DTOs are explicit; do not expose EF entities as public API contracts.

## Database conventions

- PostgreSQL + EF Core migrations.
- Store timestamps in UTC and render in the tenant timezone.
- Preserve referenced business history; avoid destructive deletion of orders/transactions.
- Use concurrency protection where assignment/claim/update races are possible.
- Prefer snake_case database naming mapped from C# PascalCase if the repository convention adopts it.

## Logging and correlation

Structured logs must carry enough context to diagnose a request across the system.

Where available, every log scope should include:

- `Environment` — e.g. Development / Staging / Production.
- `SourceApp` — e.g. `web`, `admin`, `mobile` (driver/mobile), `mcp`, `worker` when relevant.
- `RequestId` / correlation ID — generated/accepted at the first HTTP boundary and propagated through downstream HTTP requests so related calls can be correlated.
- `TraceId` — OpenTelemetry/distributed trace identifier when available.
- `TenantId` — after tenant resolution.
- `UserId` — after authentication; omit/null before authentication.
- `CustomerId` when materially relevant.
- Endpoint/operation name.

The API should return or expose the request/correlation ID where useful for support/debugging, and propagate it on outgoing HTTP calls.

Never log passwords, OTP values, access/refresh tokens, private keys, client secrets or raw sensitive credentials.

## Error conventions

Return a stable machine-readable error code, localized/contextual user message, field errors where relevant, and trace/request identifiers for diagnostics. Never expose raw exception text to end users.

## Security conventions

- Backend authorization is mandatory even if the UI hides an action.
- Tenant boundaries are enforced server-side.
- A phone number alone is not sufficient proof for protected customer data.
- Secrets must come from ignored local credential files, environment variables, secret managers or deployment-platform secret stores.

## Credentials

`docs/credentials/` is intentionally the local project location for production/sensitive credentials and operational secret references **when a developer needs local copies**.

The folder must be excluded from Git except for safe documentation/template files. Production deployment should still prefer platform secret stores/environment variables over reading plaintext credential files at runtime.
