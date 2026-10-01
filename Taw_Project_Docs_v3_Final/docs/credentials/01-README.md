# Taw — Local Credentials Folder

This folder is intentionally reserved for **real sensitive/production credentials and local operational secret references** when they must exist on a developer machine.

Examples:

- production connection strings
- API keys
- OAuth client secrets
- service-account credentials/files
- signing keys/certificates
- WhatsApp provider credentials
- SMS/OTP provider credentials
- Firebase/admin private credentials
- cloud deployment tokens
- database admin credentials

## Git rule

Real credential files in this folder must **never** be committed to Git.

The root `.gitignore` should ignore `docs/credentials/*` while allowing this safe README/template to remain tracked if desired.

## Runtime rule

Production applications should prefer deployment-platform secrets, environment variables or a managed secret store. This folder is primarily a local secure reference/staging location, not the preferred runtime secret source.

## Logging rule

Never paste secrets into progress logs, implementation-status, screenshots, test dumps or Seq logs.
