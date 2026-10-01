# Screen Map and User Journeys

## Screen map

```text
Public
├── [Screen]
└── [Screen]

Authenticated
├── Dashboard
├── [Module]
│   ├── List
│   ├── Create
│   ├── Details
│   └── Edit
└── Settings
```

## Journey A — primary workflow

```text
Entry
→ Step
→ Step
→ Outcome
```

## Journey B — recovery

```text
Action
→ error
→ understandable message
→ data preserved
→ retry/recovery
```

## Validation

Major journeys should be verified:
- end to end;
- on realistic data;
- on relevant viewport sizes;
- in required locales.
