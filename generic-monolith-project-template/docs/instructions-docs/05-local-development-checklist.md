# Local Development Checklist

## First-Time Setup

- [ ] Install project runtime/SDK.
- [ ] Install Docker Desktop or compatible Docker engine.
- [ ] Copy `.env.example` to a local `.env`.
- [ ] Set non-production local credentials.
- [ ] Run `docker compose up -d`.
- [ ] Confirm PostgreSQL is healthy.
- [ ] Confirm Adminer opens.
- [ ] Confirm Seq opens.
- [ ] Restore application dependencies.
- [ ] Apply database migrations.
- [ ] Start backend.
- [ ] Start required frontend(s).
- [ ] Verify application health endpoint.
- [ ] Verify a sample structured log appears in Seq.

## Local Infrastructure Defaults

```text
PostgreSQL -> application database
Adminer    -> browser database client
Seq        -> structured logs
```

## Before Starting Work

- [ ] Pull/rebase latest code according to team workflow.
- [ ] Read current implementation status.
- [ ] Confirm local database migration state.
- [ ] Ensure no production credential is being used locally unless explicitly required.

## Before Committing

- [ ] Build succeeds.
- [ ] Relevant focused tests pass.
- [ ] No temporary screenshots/traces/dumps are included.
- [ ] No `.env` or secrets are staged.
- [ ] No debug-only code remains.
- [ ] Required documentation/status files are updated.
