---
description: Design and build a new page or screen with ui-craft — plan, generic check, build, screenshot critique
---
Follow every step in order. Do not skip steps 3, 4, 7 or 8.

1. Read PLAN.md and identify the target route or screen. State the register (Cinematic or Instrument) in one line.
2. Apply the `ui-craft` skill. Read `resources/generic-tells.md` and `resources/copy.md`. If Thai text is involved, read `resources/thai.md`.
3. Write a **Design Plan** into PLAN.md under this task:
   - Subject / audience / primary job (one line each)
   - Palette: 4–6 named hex values with roles
   - Type: families, roles, scale
   - Layout: one-sentence concept + ASCII wireframe for desktop and mobile + alignment
   - Signature: the one memorable element
   - Principles: 2–3 lines
4. **Generic check:** compare every plan axis against `generic-tells.md`. For each match not requested by the user, revise it and record `revised: X → Y because Z` in PLAN.md.
5. For a new Cinematic page, stop here and give the PLAN.md link; wait for the user's approval. For Instrument screens, continue unless the user asked to review the plan.
6. Build in this order: tokens → layout with realistic content → loading / empty / error states → interactions → motion last.
7. Open the page in the browser. Screenshot at 1280px and 375px. Check the console for errors.
8. **Critique** against the Design Plan and `resources/checklist.md`. Write the 3 biggest problems, ranked, into PLAN.md. Fix them.
9. Screenshot again once. Remove one accessory — the least necessary decoration. Confirm 0 console errors.
10. Append one line to `docs/design-log.md`: date, route, palette name, type, signature. Read this log at step 3 next time so new pages stay consistent within the product and don't repeat generic choices across products.
11. Report: PLAN.md link, 1 proof screenshot, at most 2 bullets (signature choice, anything skipped).
