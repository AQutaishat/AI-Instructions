# Taw — Backup and Restore Working Guide

This procedure should be refined when deployment infrastructure is selected.

## Principle

A backup plan is not considered complete until a restore has been tested.

## Before production schema/configuration changes

1. Verify current deployment version.
2. Create/verify database backup.
3. Back up critical deployment configuration if changed.
4. Apply EF Core migration.
5. Deploy application.
6. Run health checks.
7. Validate critical user flow.
8. Monitor logs/telemetry.

## Restore test

Before relying on production backups, perform at least one controlled restore into a non-production environment and verify:

- Database can be restored.
- Application starts.
- Tenant data is accessible only to correct tenant.
- Orders/customers/products exist as expected.
- Migrations are compatible.

## Secrets

Backups of configuration must not lead to secrets being committed to Git.

Use deployment secret storage/environment variables/secret managers.
