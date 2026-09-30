---
description: Review the current branch diff before commit or PR (read-only, writes REVIEW.md)
---
1. Apply the `pr-review-toolkit` skill. This workflow is read-only: do not edit source files, stage, commit, or push.
2. Determine the base branch (default `main`) and the Level from PLAN.md (default Level 2 if no PLAN.md).
// turbo
3. Run `git status --short` and `git diff --merge-base main --stat`.
// turbo
4. Run `git diff --merge-base main` and review changed files only, excluding lockfiles and generated output.
5. For each changed function, grep its callers and read targeted line ranges for context.
6. Run the lenses in order: security, correctness, silent failures, types, tests, performance, simplicity (ponytail), UI (ui-craft, only if UI changed).
7. Run the project's gates non-interactively (tests, type-check, lint, build), filtering output to errors and summary. Record each as passed / failed / not run.
8. Write `REVIEW.md` in the format defined by the skill. Every finding needs location, scenario, impact, and fix.
9. In chat: `REVIEW.md` link, verdict, and blockers one line each. Ask which findings to fix. Stop and wait.
