---
description: Run the app locally, hand it over for user testing, and turn feedback into fixes or REQ changes
---
1. Make the run reproducible: `.env.example` documents every variable; README has install/run commands. Add or fix them if missing.
2. Follow AGENTS.md Port Hygiene (show PID and ask before terminating anything). Start the dev server as a background task; confirm the actual port from the server output.
3. Smoke check: the main route loads, 0 console errors. For UI, 1 proof screenshot.
4. Handover message (short):
   - `Preview: http://localhost:<port>`
   - What to test: each REQ in this slice → route + steps
   - Login: point to the seed/fixture file; never print credentials
   - Not verified by AI / known limitations
   - How to reply: "ok REQ-001", or describe the problem
5. STOP and wait for feedback.
6. Classify each feedback item:
   - **Bug** (violates an existing REQ) → add a fix task to the current slice.
   - **Change / new** (not covered by any REQ) → add or edit the REQ in PLAN.md (and docs/specs/ for Level 2.5+), log it in the Change log, add tasks.
   - **Accepted** → tick "User accepted".
   If an item is ambiguous, confirm the classification in one line before acting.
7. Return to `/build`.
8. When every REQ is user-accepted: stop dev servers I no longer need, run `/review`, then `/commit`, then ask whether to push.
