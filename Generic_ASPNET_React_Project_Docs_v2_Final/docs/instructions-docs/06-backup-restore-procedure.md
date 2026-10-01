# Backup and Restore Procedure

Adapt after production hosting is selected.

## Principles

- backups must be restorable;
- protect backups as sensitive data;
- define retention;
- perform real restore tests periodically;
- never store production backups in Git.

## PostgreSQL backup

```bash
pg_dump \
  --format=custom \
  --no-owner \
  --file=backup.dump \
  "$DATABASE_URL"
```

## Restore

```bash
pg_restore \
  --clean \
  --if-exists \
  --no-owner \
  --dbname="$TARGET_DATABASE_URL" \
  backup.dump
```

## Verification

After restore:

- [ ] application connects;
- [ ] schema/migration version expected;
- [ ] representative records exist;
- [ ] critical relationships intact;
- [ ] authentication/user data behaves correctly;
- [ ] external file/object references valid if applicable;
- [ ] smoke test succeeds.

## Docker data

Docker volumes are not backups.

Disposable local data may be recreated.
Important local fixtures/datasets should be exported explicitly.
