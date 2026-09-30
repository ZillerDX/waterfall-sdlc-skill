---
name: pr-review-toolkit
description: Use when reviewing a diff, branch, or pull request before merging or opening a PR, when the user asks "review this", "is this safe to merge", or during Phase 4 of PLAN.md. Audits security, correctness, silent failures, types, tests, performance, simplicity, and UI.
license: MIT
---

# PR Review Toolkit

Multi-lens review of **changed code only**. Read-only: never edit, stage, commit, or push during a review. Fixes happen only after the user picks which findings to address.

## Rules for every finding

A finding is reported only if it has all four:
1. **Location:** `path:line` in the diff (or the caller it breaks).
2. **Failure scenario:** the concrete input or sequence that goes wrong — not "might be an issue".
3. **Impact:** what the user/system experiences.
4. **Fix:** the smallest change that resolves it (ponytail).

No evidence → no finding. Pre-existing problems outside the diff are not findings; list at most 3 under "Outside scope" only if they are security or data-loss risks. Never pad the report — an empty section is a good result.

## Scope first

- Diff: `git diff --merge-base <base>` (base = `main` unless told otherwise) plus `git status` for untracked files. Exclude lockfiles, generated code, build output, snapshots from line-by-line review (still check lockfiles for new dependencies).
- Context: for each changed function, grep its callers and read targeted line ranges — not whole files.
- Level (from PLAN.md) sets depth:

| Level | Lenses |
|---|---|
| 1 | Correctness, Silent failures, Security quick scan |
| 2 / 2.5 | All lenses, targeted |
| 3 | All lenses in depth + dependency and secret scan + gate results |
| 4 | Review the spec/tickets against the diff; flag scope drift |

## Lenses (run in this order — security first)

### 1. Security & secrets (top invariant)
- Secrets, tokens, keys, or `.env` values in code, tests, fixtures, logs, commits.
- Injection: SQL/NoSQL built by string concat, shell commands with user input, `eval`, template injection, XSS (`innerHTML`, `dangerouslySetInnerHTML`, `[innerHTML]`, `@Html.Raw`).
- AuthN/AuthZ: new endpoint without auth, missing ownership check (IDOR), role checks only on the client.
- Secrets or third-party keys reachable from client bundles (AGENTS.md: backend proxying).
- CORS `*` with credentials, missing CSRF on cookie auth, path traversal, SSRF from user-supplied URLs, unsafe deserialization.
- New dependency: is it needed (ponytail ladder), maintained, and not typosquatted?

### 2. Correctness & edge cases
- Off-by-one, empty/null/zero/negative input, overflow, rounding (money: never float), timezone/DST, locale (Thai Buddhist year).
- Concurrency: races, double-submit, non-idempotent retries, missing transaction around multi-write.
- Behavior change for existing callers (signature, defaults, return shape).

### 3. Silent failures
Errors swallowed so failures look like success:

| Stack | Look for |
|---|---|
| TS/JS | empty `catch {}`, `.catch(() => {})`, un-awaited promises, `?? []` hiding API errors |
| C# | `catch { }`, `catch (Exception) { return null; }`, `async void`, `.Result`/`.Wait()` deadlocks |
| Python | `except: pass`, bare `except Exception` returning defaults, unchecked subprocess return codes |
| Dart/Flutter | `catchError` returning defaults, unawaited `Future`s |
| Swift/Kotlin | `try?` discarding errors, `runCatching` ignored, `!!` on external data |
| Any | fallback values that mask outages, missing logging on error paths, retries without limit |

### 4. Types & invariants
- Nullability at boundaries (API responses, DB rows, user input) validated, not cast.
- `any` / `dynamic` / `object` / unchecked casts introduced.
- Invalid states representable when a discriminated union / enum / sealed class would prevent them.
- Invariants enforced in one place (constructor, schema, DB constraint), not re-checked ad hoc.

### 5. Tests
- New logic has tests that fail if the logic breaks (assert behavior, not implementation).
- Tests cover the edge cases found in lens 2.
- Scope matches the Level gate (see ponytail "Checks by Level").
- Flag tests that can't fail: no assertions, asserting mocks only, snapshot-only for logic.

### 6. Performance (only where it matters)
N+1 queries, unbounded queries/loops, missing pagination, O(n²) on data that grows, work inside render/hot loops, missing index for a new query path, resource leaks (streams, connections, listeners, timers).

### 7. Simplicity
Apply the ponytail "Phase 4 review lens" — one line per finding with the lazier replacement. Do not re-list it here.

### 8. UI (only if the diff touches UI)
Apply `ui-craft` `resources/checklist.md`. Report only failures.

## Severity

- **Blocker:** security hole, data loss/corruption, crash on a realistic path, broken existing behavior, failing gate. Must fix before merge.
- **Should fix:** real bug on an edge path, missing test for new logic, silent failure without data loss, meaningful performance issue.
- **Consider:** simplification, clarity, minor hardening. Optional.

When unsure between two levels, pick the lower one and say why in the finding.

## Gates

Run what the project has (non-interactive, output filtered to errors/summary): tests, type-check, lint, build. Report each as passed / failed / **not run** with the reason. Never mark an unrun gate as passed (AGENTS.md: Honest Gate Reporting).

## Output

Write the full report to `REVIEW.md` (overwrite per review):

```markdown
# Review: <branch or PR> vs <base>
Level: <n> · Files: <n> · Verdict: Approve | Request changes | Needs discussion

## Gates
- Tests: passed | failed | not run (<reason>)
- Types / Lint / Build: …

## Blockers
1. `path:line` — <issue>. Scenario: <…>. Impact: <…>. Fix: <…>

## Should fix
…

## Consider
…

## Outside scope (security/data-loss only, max 3)
…
```

In chat (Zero-Echo): the `REVIEW.md` link, the verdict, and the blockers as one line each. Then ask which findings to fix.
