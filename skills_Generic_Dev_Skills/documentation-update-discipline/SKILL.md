---
name: documentation-update-discipline
description: Use immediately after completing any meaningful implementation unit — keeps progress log, implementation status, and future-work docs in sync with what was actually done.
---

## When to use
Right after finishing a meaningful piece of implementation work (a feature slice, a fixed bug, a completed milestone step) — not after every trivial edit.

## When not to use
Trivial edits (typos, formatting) or mid-task, before a unit of work is finished.

## Steps
1. **Append** factual, dated detail of what was actually done to the project's progress log. This is a chronological log — do not pre-fill it with roadmap items that haven't happened yet.
2. **Update** the implementation-status doc so it accurately and concisely reflects the current phase and completed/current/next work (this file should stay short and current, not historical).
3. **Update** a future-work/backlog doc only when genuinely new deferred scope or ideas were identified during the work — do not add speculative items otherwise.
4. **Change stable reference/architecture docs only** if the implementation changed an actually approved product/technical decision — these are not working logs.

## Anti-patterns to avoid
- Silently letting the implementation-status doc go stale after a milestone.
- Recording roadmap/future intentions as if they already happened.
- Editing stable reference docs casually instead of working/progress docs.
