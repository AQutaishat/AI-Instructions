# Domain Model

Document business concepts before or alongside implementation.

## Entity: `[EntityName]`

Purpose:

`[Why this entity exists.]`

Fields:

```text
Id
...
CreatedAt
UpdatedAt
```

Rules:
- `[Rule]`

Relationships:
- `[Relationship]`

## Value objects / enums

```text
Status
Type
Role
Priority
```

Define valid values and meaning.

## Business invariants

Examples:
- only owner may perform X;
- closed object cannot be edited;
- combination of fields must be unique;
- state transition A → C is invalid.

## Explicitly absent concepts

List things agents must not invent:

- `[Not in scope]`
- `[Not in scope]`
