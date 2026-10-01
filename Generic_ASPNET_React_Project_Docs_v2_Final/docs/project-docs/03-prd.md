# Product Requirements Document

## Actors

### `[Actor]`

Description:
`[Who is this actor?]`

Permissions:
- `[Permission]`
- `[Permission]`

## Functional requirements

Use stable IDs.

### FR-001 — `[Requirement name]`

Description:

`[Exact expected behavior.]`

Acceptance notes:
- `[Condition]`
- `[Condition]`

### FR-002 — `[Requirement name]`

`[Requirement details]`

## Non-functional requirements

### Performance

`[Expected usage and response constraints.]`

### Security

- server-side authorization;
- input validation;
- secure secret handling;
- no credential leakage in logs;
- least privilege;
- safe handling of public identifiers/tokens if present.

### Localization

`[Languages / RTL / locale behavior.]`

### Accessibility

- semantic controls;
- keyboard support;
- visible focus;
- labels;
- adequate contrast.

### Observability

Logs should include when available:

```text
Environment
SourceApp
RequestId
TraceId
UserId
Operation
DurationMs
Outcome
```

Add relevant domain IDs when useful.

## Success metrics

- `[Metric]`
- `[Metric]`
