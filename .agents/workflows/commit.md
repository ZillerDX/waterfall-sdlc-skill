---
description: Create safe, atomic Conventional Commits from the current changes (local only, no push)
---
1. Apply the `commit-commands` skill.
// turbo
2. Run `git status --short`, `git branch --show-current`, and `git log --oneline -20` to learn the current branch and the repo's message style.
3. If on the default branch and a remote exists, ask once whether to commit here or create a feature branch. Wait for the answer.
// turbo
4. Run `git diff` and `git diff --cached` to see all changes.
5. Scan the changes for secrets and files that shouldn't be committed. If any are found, stop and report them (redacted).
6. Run the project's tests, type-check, and lint for the changed area non-interactively. If a gate fails, stop and report; do not commit.
7. Group the changes into atomic commits. Show the plan in chat: one line per commit (`type(scope): subject` + files).
8. For each planned commit: stage by explicit path (or `git apply --cached` for hunk splits), verify with `git diff --cached --stat`, then `git commit -m "<subject>" -m "<body>"`.
// turbo
9. Run `git log --oneline -n <number of new commits>` and `git status --short` to confirm a clean result.
10. Report the new commits one line each. Do not push. Before offering to push, check that every REQ in PLAN.md is user-accepted and REVIEW.md verdict is not "Request changes"; if not, state what's missing instead of offering to push. If all checks pass, ask whether to push.
