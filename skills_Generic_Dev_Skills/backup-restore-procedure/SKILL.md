---
name: backup-restore-procedure
description: Use before any production schema/configuration change, or when planning/testing database backup and restore — a step-by-step safety procedure and restore-test checklist.
---

## When to use
Before applying a production database migration or deployment configuration change, or when validating that backups are actually restorable.

## When not to use
Local/dev database changes or throwaway environments with no data worth keeping.

## Principle
A backup plan is not complete until a restore has been tested.

## Before production schema/configuration changes
1. Verify current deployment version.
2. Create/verify database backup.
3. Back up critical deployment configuration if it changed.
4. Apply the database migration.
5. Deploy the application.
6. Run health checks.
7. Validate the critical user flow.
8. Monitor logs/telemetry afterward.

## Restore test
Before relying on production backups, perform at least one controlled restore into a non-production environment and verify:
- Database can be restored.
- Application starts.
- Tenant/customer data is accessible only to the correct owner (if multi-tenant).
- Core domain records exist as expected.
- Migrations are compatible.

## Secrets
Backups of configuration must never lead to secrets being committed to Git. Use deployment secret storage, environment variables, or a secret manager instead.

## Note
Adapt this procedure to the project's actual deployment infrastructure once selected — it is a general-purpose template, not a finalized runbook for any specific stack.
