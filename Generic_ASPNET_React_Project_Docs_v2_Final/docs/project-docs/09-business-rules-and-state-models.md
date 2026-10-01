# Business Rules and State Models

Centralize rules here so backend, frontend, and tests do not diverge.

## State model: `[Entity]`

States:

```text
Draft
Active
Closed
Completed
Cancelled
```

Replace with real states.

## Allowed transitions

| From | To | Allowed | Notes |
|---|---|---:|---|
| Draft | Active | Yes | |
| Active | Completed | Yes | |
| Completed | Active | No | |

## Rules

### BR-001
`[Rule]`

### BR-002
`[Rule]`

## Derived values

Prefer calculating derived values instead of storing duplicate truth.

Example:

```text
IsExpired = current_time > ExpiresAt
```

## History

Define which changes require audit/history preservation.

## Deletion

Explicitly define:
- hard delete;
- soft delete;
- archive;
- immutable history.
