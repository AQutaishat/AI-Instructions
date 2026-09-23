# Master Instructions for Any Implementation Agent

These rules apply to every AI coding agent or developer working on this project.

## 1. Source of Truth

Before changing code:

1. Read the relevant files under `docs/project-docs/`.
2. Read `docs/working-docs/02-implementation-status.md`.
3. Read any relevant implementation rules under `docs/instructions-docs/`.
4. Inspect the existing code before deciding how to implement a change.

Do not invent requirements that are not documented or clearly implied by the requested task.

If implementation and documentation conflict, stop and identify the conflict. Prefer the approved project documentation unless the current user instruction explicitly changes it.

## 2. Architecture

- Use a monolithic architecture.
- Do not introduce microservices unless explicitly requested.
- Keep one deployable backend application unless a separate frontend/mobile application is naturally required.
- Organize the monolith internally by coherent business/domain modules.
- Keep module boundaries clear even though everything is deployed together.
- Prefer simple, maintainable architecture over speculative abstraction.
- Avoid distributed-system patterns when an in-process solution is sufficient.
- Do not introduce message brokers, Kubernetes, service meshes, distributed caches, or extra infrastructure without a demonstrated requirement.

## 3. Implementation Philosophy

- Implement the smallest complete vertical slice that delivers user value.
- Prefer working end-to-end functionality over large amounts of scaffolding.
- Do not build future features early.
- Do not create abstractions solely because they might be needed later.
- Avoid duplicate implementations.
- Reuse existing patterns and components when they are still appropriate.
- Refactor only when it improves the current implementation or removes clear technical debt.
- Keep changes scoped to the requested task.

## 4. Existing Code

Before creating a new:

- service,
- component,
- helper,
- DTO,
- API endpoint,
- model,
- database table,
- utility,
- hook,
- validation rule,

search for an existing equivalent.

Modify or extend the existing implementation when appropriate instead of creating parallel versions.

## 5. Database

- PostgreSQL is the default relational database.
- Use migrations for schema changes.
- Never change production schema manually as the normal workflow.
- Use proper foreign keys, indexes, constraints, and data types.
- Do not add nullable columns merely to avoid thinking through data integrity.
- Prefer database constraints for invariants that the database can reliably enforce.
- Avoid N+1 queries.
- Paginate unbounded list endpoints.
- Never expose internal database entities directly as public API contracts unless deliberately designed that way.

## 6. Docker / Local Infrastructure

Local infrastructure should use Docker Compose where practical.

Default supporting services:

- PostgreSQL
- Adminer
- Seq

Do not containerize every application process merely for consistency if local native execution is faster and simpler for development.

## 7. Logging and Observability

Use structured logging.

Every meaningful request log should include, when available:

- `Environment`
- `SourceApp` — e.g. `Web`, `Admin`, `Mobile`, `Api`, `Worker`
- `RequestId` / correlation identifier
- `UserId` after authentication
- operation/event name
- relevant entity identifiers
- duration for important operations
- error details for failures

Use the same `RequestId` across the complete HTTP request flow and propagate it to downstream calls where relevant.

Never log:

- passwords,
- access tokens,
- refresh tokens,
- secrets,
- complete payment data,
- sensitive personal data unless explicitly required and properly protected.

Seq is the default local structured-log viewer.

## 8. Error Handling

- Return predictable API error shapes.
- Distinguish validation errors, authorization errors, not-found cases, business-rule conflicts, and unexpected server failures.
- Do not leak stack traces or infrastructure details to clients.
- Log unexpected failures once at the correct boundary; avoid duplicate noisy logging at every layer.
- Use meaningful domain/business errors rather than generic exceptions where practical.

## 9. Authentication and Authorization

- Authentication identifies the user.
- Authorization must be enforced server-side.
- UI hiding is not authorization.
- Follow least privilege.
- Never trust identifiers or role claims supplied by the client without server validation.
- Keep authorization rules close to the operations they protect.

## 10. API Design

- Keep APIs consistent.
- Use stable resource naming and HTTP semantics.
- Validate input.
- Use DTO/request/response contracts.
- Add pagination to potentially large collections.
- Make mutating operations safely retryable when reasonable.
- Do not break existing public contracts without a deliberate migration plan.

## 11. Frontend / UX

- Follow the documented design system.
- Reuse components.
- Implement loading, empty, error, disabled, and success states.
- Make forms usable with clear validation.
- Preserve accessibility basics: labels, keyboard navigation, semantic elements, adequate contrast.
- Build responsive interfaces unless the product explicitly targets one form factor.
- Do not redesign screens during implementation unless required.

## 12. Testing Strategy

Testing is required, but avoid wasteful over-testing.

Use the cheapest reliable test for the risk:

1. compile/build/static checks;
2. focused unit tests;
3. focused integration/API tests;
4. browser/E2E tests only for important user flows or high-risk regressions.

Do not run Playwright or full end-to-end testing after every small code change.

Do not repeatedly create screenshots, videos, traces, browser dumps, or large test artifacts.

Use browser/E2E validation:

- after a meaningful vertical slice,
- at a significant milestone,
- for a critical workflow,
- for a UI regression that cannot be validated cheaply another way,
- before declaring a major feature complete.

When a targeted test is sufficient, do not run the entire suite.

## 13. Token / Time Efficiency for AI Agents

- Read only the files needed for the current task.
- Search before opening very large files.
- Avoid dumping entire source trees into context.
- Avoid repeated browser screenshots.
- Avoid repeatedly re-reading unchanged documentation.
- Do not regenerate large files when a small patch is enough.
- Group related changes before testing.
- Verify after meaningful milestones, not every trivial edit.

Efficiency must never be used as an excuse to skip necessary validation.

## 14. Security

- Never hard-code secrets.
- Keep real credentials under `docs/credentials/` or a proper secret store; this folder must be Git ignored.
- Commit `.env.example`, never real `.env` files.
- Validate and sanitize untrusted input.
- Use parameterized database access / ORM protections.
- Apply secure authentication/session practices.
- Review file uploads for size/type/path risks if the project supports uploads.
- Keep dependencies reasonably current and remove unused packages.

## 15. Documentation Updates

After meaningful implementation work:

- append to `01-progress.md`;
- update `02-implementation-status.md`;
- add genuinely deferred items to `03-future-work.md`.

Do not mark something complete unless it is implemented and sufficiently verified.

Do not use fake completion markers or claim tests passed without running them.

## 16. Before Declaring a Task Complete

Verify, as applicable:

- solution builds;
- migrations are valid;
- changed API works;
- important validation paths work;
- authorization is enforced;
- logs contain expected structured properties;
- UI works in the intended viewport(s);
- relevant focused tests pass;
- documentation status is updated;
- no secrets or temporary artifacts were accidentally added.

Then summarize:

- what changed,
- important technical decisions,
- tests/verification performed,
- known limitations,
- deferred work.
