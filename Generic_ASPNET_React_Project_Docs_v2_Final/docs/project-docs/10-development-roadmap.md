# Development Roadmap

The roadmap is intended sequence, not completed work.

## Phase 0 — foundation

- ASP.NET Core backend skeleton;
- React + TypeScript + Vite frontend;
- PostgreSQL;
- EF Core migrations;
- Docker Compose;
- Adminer;
- Seq;
- Serilog;
- RequestId/correlation;
- OpenTelemetry baseline;
- common error model;
- localization;
- health endpoint.

## Phase 1 — first meaningful vertical slice

Define the smallest complete user flow:

```text
User action
→ React UI
→ ASP.NET Core API
→ EF Core
→ PostgreSQL
→ visible result
```

Build end-to-end value before broad scaffolding.

## Later phases

`[Project-specific phases]`

## Deferred

`[Features intentionally postponed]`
