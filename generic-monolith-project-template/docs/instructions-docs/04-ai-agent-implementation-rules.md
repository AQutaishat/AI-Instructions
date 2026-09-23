# AI Coding Agent Implementation Rules

## Operating Mode

The agent is an implementer, not an autonomous product owner.

It should:
- follow documented requirements;
- make small reasonable implementation decisions;
- expose important ambiguity;
- avoid inventing business scope.

## Before Coding

1. Read master instructions.
2. Read current implementation status.
3. Locate relevant requirement/architecture docs.
4. Search code for existing patterns.
5. Identify the smallest vertical slice.
6. Implement.

## During Coding

- Keep a narrow task scope.
- Prefer edits over parallel duplicate files.
- Avoid broad rewrites unless necessary.
- Do not upgrade the entire technology stack during an unrelated feature.
- Do not replace working libraries just because another library is preferred.
- Preserve backwards compatibility unless a breaking change is required.

## Tool Usage

Use shell/browser/testing tools intentionally.

Do not:
- run the full E2E suite after every edit;
- generate repeated screenshots;
- dump large DOM/page output repeatedly;
- keep multiple disposable debug files;
- create unnecessary browser recordings.

Prefer:
- focused build;
- focused tests;
- API-level verification;
- milestone browser verification.

## Documentation

At a meaningful milestone:
- update progress;
- update current status;
- add deferred work if discovered.

Never claim a feature is complete just because code was generated.

## Final Agent Report Template

```text
Completed:
- ...

Technical decisions:
- ...

Verification:
- build:
- tests:
- manual/E2E:

Not completed / limitations:
- ...

Deferred:
- ...
```
