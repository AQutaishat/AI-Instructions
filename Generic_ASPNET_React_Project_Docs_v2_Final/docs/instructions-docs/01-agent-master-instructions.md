# Master Instructions for Any Implementation Agent

These rules apply to every AI coding agent or developer working on the project.

## 1. Source of truth

Before changing code:

1. read relevant `docs/project-docs/`;
2. read `docs/working-docs/02-implementation-status.md`;
3. read applicable `docs/instructions-docs/`;
4. inspect existing code before deciding how to implement.

Do not invent undocumented requirements.

If code and approved docs conflict, identify the conflict and prefer the current approved documentation unless the user's current instruction explicitly changes it.

## 2. Required technology

Unless the project explicitly overrides it:

```text
ASP.NET Core / C# / EF Core
React / TypeScript / Vite
PostgreSQL
Docker Compose
Adminer
Seq
Serilog
OpenTelemetry where useful
```

Do not silently replace the stack.

## 3. Architecture

- modular monolith;
- no microservices unless explicitly approved;
- one deployable backend;
- coherent business modules;
- clear module boundaries;
- simple, maintainable architecture;
- avoid distributed-system patterns unless required.

Do not introduce message brokers, Kubernetes, service meshes, distributed caches, or extra infrastructure without demonstrated need.

## 4. Implementation philosophy

- implement the smallest complete vertical slice;
- prefer end-to-end working value over broad scaffolding;
- do not build future features early;
- do not create speculative abstractions;
- avoid duplicate implementations;
- reuse appropriate existing patterns;
- refactor only when it improves current implementation;
- keep changes scoped.

## 5. Search before creating

Before creating a new:
- service;
- component;
- helper;
- hook;
- DTO;
- endpoint;
- model/entity;
- table;
- validation rule;
- utility;

search for an existing equivalent.

Extend an existing implementation when appropriate instead of creating parallel versions.

## 6. Database

- PostgreSQL;
- EF Core migrations;
- never manually mutate production schema as normal workflow;
- proper foreign keys/indexes/constraints/data types;
- avoid N+1;
- paginate unbounded lists;
- do not expose EF entities as public API contracts.

Do not add nullable columns merely to avoid thinking through data integrity.

## 7. Local infrastructure

Docker Compose should provide:
- PostgreSQL;
- Adminer;
- Seq.

Do not containerize every application process if native local execution is simpler.

## 8. Logging

Every meaningful request log should include when available:

```text
Environment
SourceApp
RequestId
TraceId
UserId
Operation
RelevantEntityId
DurationMs
Outcome
```

`RequestId` must remain consistent through a request flow and downstream HTTP calls where relevant.

Never log:
- passwords;
- access/refresh tokens;
- secrets;
- private keys;
- full payment data;
- unnecessary sensitive personal data.

## 9. Error handling

- predictable error shapes;
- distinguish validation/auth/not-found/business-conflict/server errors;
- no stack traces to clients;
- log unexpected failures once at the correct boundary;
- avoid duplicate noisy exception logging.

## 10. Authentication and authorization

- authentication identifies;
- authorization is enforced server-side;
- hidden UI is not authorization;
- least privilege;
- do not trust client-supplied identifiers/role claims without validation.

## 11. API design

- consistent resource naming;
- HTTP semantics;
- explicit DTOs;
- input validation;
- pagination;
- retry-safe/idempotent mutations where reasonable;
- no breaking public-contract changes without migration plan.

## 12. Frontend / UX

- React + TypeScript + Vite;
- follow documented design system;
- reuse components;
- implement loading/empty/error/disabled/success states;
- clear form validation;
- responsive unless explicitly single-form-factor;
- preserve accessibility basics;
- do not redesign approved flows casually.

## 13. Testing

Use the cheapest reliable verification:

1. build/static checks;
2. focused unit tests;
3. focused integration/API tests;
4. Playwright/E2E only for important flows or high-risk regressions.

Do not run full E2E after every small change.

Avoid repeated screenshots/videos/traces/browser dumps.

Use E2E after:
- a meaningful vertical slice;
- a significant milestone;
- a critical workflow;
- a UI regression needing browser validation;
- before declaring a major feature complete.

## 14. Efficiency

- read only relevant files;
- search before opening huge files;
- avoid dumping source trees into context;
- avoid re-reading unchanged docs;
- patch rather than regenerate large files;
- group related changes before testing.

Efficiency does not justify skipping necessary validation.

## 15. Security

- never hard-code secrets;
- use ignored credentials or proper secret stores;
- commit `.env.example`, not real `.env`;
- validate untrusted input;
- use ORM/parameterized DB access;
- secure auth/session behavior;
- validate file uploads if present;
- keep dependencies reasonably current;
- remove unused packages.

## 16. Documentation after meaningful work

- append progress;
- update implementation status;
- add genuine future/deferred work;
- do not claim completion without implementation and verification;
- never claim tests passed unless they were actually run.

## 17. Before declaring a task complete

Verify as applicable:
- backend builds;
- frontend builds;
- migrations valid;
- API works;
- validation works;
- authorization enforced;
- logs contain expected properties;
- UI works at intended viewport(s);
- focused tests pass;
- docs/status updated;
- no secrets/temp artifacts were added.

## 18. Final agent report

End substantial implementation tasks with:

```text
Completed:
- ...

Technical decisions:
- ...

Verification:
- backend build:
- frontend build:
- unit tests:
- integration tests:
- manual/E2E:

Not completed / limitations:
- ...

Deferred:
- ...
```
