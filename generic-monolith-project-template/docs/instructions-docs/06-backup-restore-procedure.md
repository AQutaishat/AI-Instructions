# Backup and Restore Procedure

Adapt commands to the deployed environment.

## Principles

- Backups must be restorable, not merely generated.
- Protect backups as sensitive data.
- Define retention according to project needs.
- Periodically perform a real restore test.
- Do not store production backups in the Git repository.

## PostgreSQL Backup Example

```bash
pg_dump   --format=custom   --no-owner   --file=backup.dump   "$DATABASE_URL"
```

## PostgreSQL Restore Example

Restore into a clean target database when practical:

```bash
pg_restore   --clean   --if-exists   --no-owner   --dbname="$TARGET_DATABASE_URL"   backup.dump
```

## Restore Verification

After restore:

- [ ] application can connect;
- [ ] migrations/schema version are expected;
- [ ] representative records exist;
- [ ] critical relationships are intact;
- [ ] authentication/user data behaves correctly;
- [ ] file/object references are valid if external storage is used;
- [ ] smoke test of critical workflow succeeds.

## Local Docker Data

Docker volumes are not a substitute for backups.

For disposable local development data, volumes may be recreated.
For important local fixtures or datasets, export them explicitly.
