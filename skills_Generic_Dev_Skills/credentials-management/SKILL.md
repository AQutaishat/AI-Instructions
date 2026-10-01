---
name: credentials-management
description: Use when handling, storing, or referencing API keys, OAuth secrets, DB passwords, or other credentials for a project — where they must live, what must never be committed or logged, and an inventory template to follow.
---

## When to use
Whenever a task involves adding a new external integration (DB, OAuth provider, cloud/storage, maps, push notifications, messaging/SMS, deployment platform) that requires secret values, or when reviewing code/config for accidental secret exposure.

## When not to use
Non-secret configuration (feature flags, public URLs, ports) — those can live in tracked config.

## Where credentials live locally
Keep a local, git-ignored staging folder (e.g. `docs/credentials/` or `.secrets/`) for real sensitive/production credentials on a developer machine. Examples: production connection strings, API keys, OAuth client secrets, service-account files, signing keys/certificates, messaging/SMS/OTP provider credentials, cloud admin credentials, deployment tokens, DB admin credentials.

## Git rule
Real credential files must never be committed. Root `.gitignore` should ignore the credentials staging folder while allowing safe README/template files to remain tracked.

Example `.gitignore` entries:
```gitignore
docs/credentials/*
!docs/credentials/README.md
!docs/credentials/*.template.md
.secrets/
*.local.md
```

## Runtime rule
Production applications must prefer deployment-platform secrets, environment variables, or a managed secret store as the actual runtime source — the local credentials folder is a local reference/staging area only, not the runtime secret source.

## Logging rule
Never paste secrets into progress logs, implementation-status docs, screenshots, test dumps, or log aggregators.

## Adding a new credential type
1. Maintain a safe credentials template listing the sections your project's integrations need (DB, OAuth/cloud, storage, maps, push, messaging/SMS, AI/MCP providers, deployment).
2. Make a **local, git-ignored copy** (e.g. `production-credentials.local.md`) and fill real values only there — never fill real secrets directly into the tracked template.
3. Confirm the actual runtime code reads the secret from environment variables/secret manager, not by parsing this local file at runtime.
