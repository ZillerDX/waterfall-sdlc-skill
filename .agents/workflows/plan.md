---
description: Turn a requirement into an approved PLAN.md with REQ acceptance criteria and vertical slices
---
1. Read AGENTS.md context files (PLAN.md, CONTEXT.md, docs/DECISIONS.md, docs/specs/). If an unfinished PLAN.md exists, ask whether to extend it or archive it to `docs/plans/<date>-<slug>.md`.
2. Restate the requirement in 2–3 lines. List gaps and ambiguities as ONE numbered round of questions, each with a recommended answer. Wait for answers; never answer for the user.
3. Triage the Level. Level 1 → say so and do the edit directly (no plan). Level 4 → switch to `/wayfinder`.
4. Verify any library/API assumptions via context7.
5. Write REQs (`REQ-001`…) each with Given/When/Then acceptance criteria. Level 2.5+: also write `docs/specs/<feature>.md` (Problem, Solution, REQ table, Implementation decisions, Testing seams, Out of scope, Open questions).
6. Split into vertical slices ordered by dependency then risk (riskiest first). Each slice lists its REQs; user-visible slices end with a "Preview checkpoint" task.
7. Fill PLAN.md using the skeleton in AGENTS.md §4, Approved: pending.
8. Report: PLAN.md link, REQ count, slice count, open questions. STOP for approval. On approval set `Approved: <date>`.
