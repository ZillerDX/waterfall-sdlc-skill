---
name: commit-commands
description: Use when committing, staging, splitting changes into commits, writing commit messages, preparing to push, or cleaning up merged branches — including Phase 5 (Delivery) of PLAN.md.
license: MIT
---

# Commit Commands

Atomic, safe commits in Conventional Commits 1.0.0 format. Local commits are cheap and reversible; anything that leaves the machine or deletes history needs the user's approval.

## Safety (checked before every commit)

1. **Secrets:** scan staged changes for keys, tokens, passwords, private keys, connection strings, `.env*` files. Found → unstage, stop, report (redacted). Confirm `.gitignore` covers secret files (AGENTS.md §5).
2. **Stage by path, never blindly.** No `git add -A` / `git add .` without first reviewing `git status`. Exclude build output, local config, editor files, `REVIEW.md` and other scratch artifacts.
3. **Non-interactive only.** No `git add -p`, `git commit` without `-m`/`-F`, or `git rebase -i` — they hang. For hunk-level splits, write a patch and use `git apply --cached <patch>`.
4. **Never** `--no-verify`, never `--amend` or rebase commits that are already pushed, never force-push a shared branch.
5. **Gates:** run tests/type-check/lint for the changed area first. Failing gate → no commit unless the user asks for a WIP checkpoint on a private branch (AGENTS.md 3-strike rule). Report unrun gates honestly.

## Atomic splitting

One commit = one reason to change. Split when the diff mixes:
- behavior change + formatting/rename (`style`/`refactor` first, then the change)
- feature + unrelated fix
- dependency bump + code using it (bump in `build`/`chore` only if it stands alone; otherwise together)
- migration + application code (keep together if the app breaks without it)

Every commit should build and pass tests on its own. Tests go with the code they test. PLAN.md checkbox updates go in the commit that completes the task.

## Message format

```
<type>(<scope>)!: <subject>

<body — why, not what; wrapped at 72>

<footers>
```

| Type | For |
|---|---|
| feat | New user-facing capability |
| fix | Bug fix users could hit |
| perf | Faster/leaner, same behavior |
| refactor | Structure change, same behavior |
| test | Tests only |
| docs | Docs only |
| style | Formatting only, no meaning change |
| build | Build system, dependencies, packaging |
| ci | CI configuration |
| chore | Tooling/maintenance that fits nothing above |
| revert | Reverts a commit (`revert: <original subject>` + `Refs: <sha>`) |

- **Scope:** the area touched (`auth`, `orders`, `ui`, `api`) — match scopes already in `git log`.
- **Subject:** imperative, lowercase start, no period, ≤ 50 characters preferred, 72 hard max. Specific: `fix(orders): prevent double submit on slow network`, never `fix: bug`, `update files`, `misc changes`.
- **Body:** when the why isn't obvious — the problem, the reason for this approach, trade-offs. Skip for self-explanatory commits.
- **Breaking change:** `!` after the type/scope **and** a `BREAKING CHANGE: <what breaks and how to migrate>` footer.
- **Footers:** `Refs: #123`, `Closes #123` if the repo uses an issue tracker.
- **Language & style:** follow the repo's existing history (`git log --oneline -20`). Default English.
- No tool or AI advertisements in messages.

## Push & branches (approval required)

- Push only when the user asks. Show `git log --oneline @{u}..HEAD` (or the branch's new commits) first.
- On the default branch of a repo with a remote, ask once before committing directly; suggest a feature branch (`feat/<short-name>`).
- Branch cleanup: list local branches merged into the base (`git branch --merged <base>`), excluding the base and current branch. Delete with `git branch -d` only after the user confirms the list. Never `-D`, never delete remote branches unless explicitly asked.

## Phase 5 delivery

After the final commit of a PLAN.md: record key decisions in `docs/DECISIONS.md` (one line each: date, decision, reason) and include it in the last commit. Report the commit list in chat as one line per commit.
