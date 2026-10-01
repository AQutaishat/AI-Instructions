# Credentials Folder

Reserved for local sensitive/production credentials when they must exist on a developer machine.

Examples:
- database credentials;
- OAuth client secrets;
- signing keys;
- deployment tokens;
- API keys;
- notification provider credentials.

## Git

Real credential files must never be committed.

The root `.gitignore` ignores this folder except safe README/template files.

## Runtime preference

Prefer:
- platform secret stores;
- environment variables;
- managed secrets.

## Logging

Never paste secrets into:
- progress docs;
- screenshots;
- test dumps;
- Seq;
- source code.
