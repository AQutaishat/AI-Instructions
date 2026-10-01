# Local Development Checklist

## First-time setup

- [ ] Install supported .NET SDK.
- [ ] Install Node.js/npm.
- [ ] Install Docker Desktop or compatible engine.
- [ ] Copy `.env.example` to local `.env`.
- [ ] Set local non-production credentials.
- [ ] Run `docker compose up -d`.
- [ ] Confirm PostgreSQL healthy.
- [ ] Confirm Adminer opens.
- [ ] Confirm Seq opens.
- [ ] Restore NuGet packages.
- [ ] Apply EF Core migrations.
- [ ] Restore npm packages.
- [ ] Start ASP.NET Core backend.
- [ ] Start React/Vite frontend.
- [ ] Verify health endpoint.
- [ ] Verify a structured log appears in Seq.

## Before starting work

- [ ] Pull/rebase latest code according to team workflow.
- [ ] Read implementation status.
- [ ] Confirm migration state.
- [ ] Ensure production credentials are not being used accidentally.

## Before committing

- [ ] Backend builds.
- [ ] Frontend builds.
- [ ] Relevant focused tests pass.
- [ ] No temporary screenshots/traces/dumps.
- [ ] No `.env` or secrets staged.
- [ ] No debug-only code.
- [ ] Working docs updated.

## Before accepting a meaningful milestone

- [ ] Critical flow works.
- [ ] API/database state correct.
- [ ] Logs contain no unexplained errors.
- [ ] Authorization checked.
- [ ] RTL/localization checked if applicable.
- [ ] Representative responsive widths checked.
- [ ] E2E used only if this milestone warrants it.
