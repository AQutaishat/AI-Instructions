# Taw / توّ — Project Documentation

This package is the consolidated project reference before implementation starts. It includes the early market analysis, product decisions, PRD, architecture, database/API direction, UX/design system, wireframe references, implementation rules, frequently updated working documents, publishing metadata, and legal drafts.

## Working product identity

- Brand: **Taw / توّ**.
- Candidate domain direction: **taw.delivery**; registrar availability/purchase is not asserted by this package.
- Current product: **water-only** SaaS for water stations/distributors.
- Current UI: water-specific throughout.
- Internal design: extensible enough not to block another delivery vertical later.
- Initial business model: free for a long adoption period.

## Documentation layout

```text
docs/
├── project-docs/       # stable product/technical reference
├── instructions-docs/  # programming, UX, agent and operational procedures
├── working-docs/       # frequently updated during implementation
├── materials/          # images, wireframes and source/reference files
└── credentials/        # local production/sensitive credentials; ignored by Git
```


## Recommended reading order

### Product and technical reference

1. `docs/project-docs/01-market-study-and-opportunity.md`
2. `docs/project-docs/02-product-vision-and-decisions.md`
3. `docs/project-docs/03-prd.md`
4. `docs/project-docs/04-domain-model.md`
5. `docs/project-docs/05-architecture.md`
6. `docs/project-docs/06-database-and-api.md`
7. `docs/project-docs/07-design-system-and-ux.md`
8. `docs/project-docs/08-screen-map-and-user-journeys.md`
9. `docs/project-docs/09-settings-offers-pages.md`
10. `docs/project-docs/10-development-roadmap.md`
11. `docs/project-docs/11-wireframe-reference.md`
12. `docs/project-docs/12-branding-and-naming.md`
13. `docs/project-docs/13-research-and-source-index.md`
14. `docs/project-docs/14-platform-publishing-metadata.md`
15. `docs/project-docs/15-privacy-statement.md`
16. `docs/project-docs/16-terms-and-conditions.md`

### Implementation instructions

1. `docs/instructions-docs/01-programming-conventions.md`
2. `docs/instructions-docs/02-ux-implementation-regulations.md`
3. `docs/instructions-docs/03-ai-agent-implementation-rules.md`
4. `docs/instructions-docs/04-local-development-checklist.md`
5. `docs/instructions-docs/05-backup-restore-procedure.md`

### Frequently updated working files

1. `docs/working-docs/01-progress.md` — detailed chronological implementation log.
2. `docs/working-docs/02-implementation-status.md` — concise current state and current phase.
3. `docs/working-docs/03-future-work.md` — deferred scope and future ideas.

## Documentation update discipline

After each meaningful implementation unit:

- append detail to `01-progress.md`;
- update `02-implementation-status.md`;
- update `03-future-work.md` only when new deferred scope is identified;
- change stable project docs only if the approved/product/technical truth actually changed.

## First implementation target

```text
Tenant/Water Station
→ Branding
→ Water Product
→ Public Store
→ Guest Order
→ Admin sees order
→ Assign driver
→ Driver sees delivery + map
→ Complete delivery
→ Record full/empty bottles
→ Bottle balance updated
```

Do not delay this flow to build future features.
