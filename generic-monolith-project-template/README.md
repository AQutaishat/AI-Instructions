# Generic Monolithic Project Template

Reusable project documentation and agent-instruction template for a standard monolithic application.

## Assumptions

- Monolithic backend architecture.
- No multi-tenancy.
- One primary relational database.
- PostgreSQL is the default database.
- Docker is used for local infrastructure.
- Adminer is used as the lightweight database client.
- Seq is used for centralized structured-log viewing.
- The application may have Web, Admin, and/or Mobile clients, but they consume the same backend/API.
- Secrets and production credentials are never committed to Git.

## Documentation Layout

```text
docs/
├── project-docs/        # Stable product and technical truth
├── instructions-docs/   # Rules for developers and AI coding agents
├── working-docs/        # Frequently updated implementation state
├── materials/           # Images, wireframes, source/reference materials
└── credentials/         # Local sensitive credentials; Git ignored
```

## Recommended Reading Order for Any Agent

1. `docs/instructions-docs/01-agent-master-instructions.md`
2. `docs/project-docs/01-product-vision.md`
3. `docs/project-docs/02-prd.md`
4. `docs/project-docs/03-domain-model.md`
5. `docs/project-docs/04-architecture.md`
6. `docs/project-docs/05-database-and-api.md`
7. `docs/project-docs/06-design-system-and-ux.md`
8. `docs/project-docs/07-screen-map-and-user-journeys.md`
9. `docs/project-docs/08-development-roadmap.md`
10. Remaining `instructions-docs`
11. `docs/working-docs/02-implementation-status.md`
12. `docs/working-docs/03-future-work.md`

## Documentation Discipline

After each meaningful implementation unit:

- append a concise entry to `docs/working-docs/01-progress.md`;
- update `docs/working-docs/02-implementation-status.md`;
- update `docs/working-docs/03-future-work.md` only when new deferred work is discovered;
- update stable `project-docs` only when the approved product or technical truth has actually changed.

Do not rewrite stable documentation merely to record implementation progress.
