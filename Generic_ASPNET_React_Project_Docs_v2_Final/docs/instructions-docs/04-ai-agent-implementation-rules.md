# AI Coding Agent Implementation Rules

## Operating mode

The agent is an implementer, not an autonomous product owner.

It should:
- follow approved requirements;
- make small implementation decisions;
- surface important ambiguity;
- avoid inventing scope.

## Before coding

1. read Master Instructions;
2. read Implementation Status;
3. locate relevant requirement/architecture docs;
4. search code for existing patterns;
5. identify the smallest vertical slice;
6. implement.

## During coding

- narrow scope;
- edit rather than create duplicate files;
- avoid broad rewrites;
- do not upgrade the entire stack during unrelated work;
- do not replace working libraries just because another is preferred;
- preserve backwards compatibility unless change is intentionally breaking.

## Tool usage

Use shell/browser/testing deliberately.

Do not:
- run full Playwright suite after every edit;
- create repeated screenshots;
- repeatedly dump DOM/page output;
- keep disposable debug files;
- create unnecessary recordings/traces.

Prefer:
- focused builds;
- focused tests;
- API/database verification;
- milestone browser verification.

## Persisted-state verification

Screenshots are not enough.

For critical flows verify:
- API response;
- DB state;
- authorization;
- state transitions;
- audit/history when applicable.

## Documentation

At meaningful milestone:
- update progress;
- update implementation status;
- add deferred items if discovered.

Never claim completion because code merely exists.

## Final report

Use the template defined in Master Instructions.
