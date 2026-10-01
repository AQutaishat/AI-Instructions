# Generic ASP.NET Core + React Project Documentation Template

This package is the reusable baseline for future software projects built with coding agents such as Codex, Claude, ChatGPT, Cursor agents, or similar tools.

It is intentionally **domain-neutral**, but the technology baseline is intentionally fixed:

```text
Backend:
ASP.NET Core
C#
EF Core

Frontend:
React
TypeScript
Vite

Database:
PostgreSQL

Local infrastructure:
Docker Compose
Adminer
Seq

Observability:
Serilog structured logging
OpenTelemetry where useful
```

Use this package as the starting point for new projects, then fill the project-specific product/domain documents.

---

## Core assumptions

Unless a future project explicitly overrides these rules:

- architecture is a modular monolith;
- ASP.NET Core is the backend;
- React + TypeScript + Vite is the web frontend;
- PostgreSQL is the primary relational database;
- EF Core migrations manage schema changes;
- Docker Compose runs local supporting infrastructure;
- Adminer is the lightweight local database client;
- Seq is the default local structured-log viewer;
- Serilog is used for structured application logging;
- OpenTelemetry is used where tracing/metrics add value;
- no multi-tenancy unless the project explicitly requires it;
- one primary backend/API serves Web/Admin/Mobile clients;
- secrets are never committed to Git.

---

## Documentation layout

```text
docs/
├── project-docs/       # stable approved product/technical truth
├── instructions-docs/  # rules for developers and coding agents
├── working-docs/       # frequently updated implementation state
├── materials/          # images, wireframes, PDFs, reference files
└── credentials/        # sensitive/local credentials; Git ignored
```

---

## Recommended reading order for any coding agent

1. `docs/instructions-docs/01-agent-master-instructions.md`
2. relevant files under `docs/project-docs/`
3. `docs/working-docs/02-implementation-status.md`
4. relevant remaining `docs/instructions-docs/`
5. inspect the actual code to be changed
6. read recent progress only when historical details matter

The agent must not rely only on memory from a previous session when current files exist.

---

## Stable project documents

```text
01-project-overview.md
02-product-vision-and-scope.md
03-prd.md
04-domain-model.md
05-architecture.md
06-database-and-api.md
07-design-system-and-ux.md
08-screen-map-and-user-journeys.md
09-business-rules-and-state-models.md
10-development-roadmap.md
11-wireframe-reference.md
12-branding-and-naming.md
13-research-and-source-index.md
14-platform-publishing-metadata.md
15-privacy-statement.md
16-terms-and-conditions.md
```

---

## Working documents

### `01-progress.md`

Chronological factual implementation record.

### `02-implementation-status.md`

Short current snapshot of what actually works now.

### `03-future-work.md`

Ideas deliberately not part of current approved implementation scope.

---

## Documentation update discipline

After each meaningful implementation unit:

1. append factual work to `01-progress.md`;
2. refresh `02-implementation-status.md`;
3. add genuinely deferred work to `03-future-work.md`;
4. change stable project docs only when approved project truth changes.

Do not write roadmap items into progress before they are implemented.

---

## Core implementation philosophy

- implement the smallest complete vertical slice that produces real user value;
- prefer working end-to-end functionality over large scaffolding;
- search for existing patterns before creating new services/components/helpers/DTOs;
- avoid duplicate implementations;
- do not build future features early;
- do not create abstractions solely because they might be useful later;
- avoid broad rewrites during unrelated work;
- validate after meaningful milestones, not after every trivial edit.
