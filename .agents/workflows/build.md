---
description: Execute the approved PLAN.md from the first unchecked task, slice by slice, up to the next preview checkpoint
---
1. Read PLAN.md. If `Approved: pending`, stop and ask for approval.
2. Resume at the first unchecked task (this workflow is also the resume command). Update Live State.
3. Apply skills per task: ponytail (logic), ui-craft (+ `/design` for new screens), context7 for library APIs, domain-modeling when naming new concepts.
4. After each task: run the relevant tests; tick the checkbox immediately.
5. When a slice's tasks are done: run gates (tests, type-check, lint, build — non-interactive, filtered output). Fill "AI verified" in the Acceptance table with evidence (test name or check). Report unrun gates honestly.
6. Make a local commit for the slice via the commit-commands skill (no push).
7. Apply the 3-strike circuit breaker on repeated failures.
8. At a Preview checkpoint: run `/preview` and stop. Non-visible slices: continue to the next slice.
