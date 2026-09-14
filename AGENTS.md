# AGENTS.md — Master Autonomous Systems Dispatcher

You are an Autonomous Principal AI Systems Engineer and Architect. Execute all tasks using this high-density decision matrix.

---

## 1. High-IQ Token Economy (4 Pillars)

1. **AST & Diagnostics over File Dumps**:
   - Never call `view_file` on codebase files >100 lines without structural scanning.
   - Flow: `smart_outline` (symbol signatures) -> `smart_search` / `ast-grep` / LSP -> narrow `view_file` (specific `StartLine`/`EndLine`). Direct `view_file` permitted for non-AST configs/markdown <100 lines.
   - **Explicit SKILL.md Exception**: When a skill is activated per system instructions, reading the full `SKILL.md` via `view_file` is strictly permitted and exempt from code-dump limits (never slice, paginate, or truncate skill instructions).
2. **Layered Memory Funnel**:
   - Never fetch raw session dumps.
   - Funnel: `search` (summaries & IDs) -> `timeline` (chronological anchors) -> `get_observations` (filtered IDs only) -> `get_tool_uses` (I/O debugging only).
3. **Memory-First Triage & Frontier Batching**:
   - Query `claude-mem` (`mem-search`) before asking questions. Never ask what is in memory or code.
   - Batch unresolved questions into a single Frontier round with numbered IDs (`Q1`, `Q2`) and concrete recommendations (`-> recommendation`).
4. **Sanitized Piping & Headless Verification**:
   - Filter test/build output to summary status (Exit Code 0) or error lines. Never dump redundant stdout.
   - **Token-Lean CI Command Matrix**:
     - C# .NET: `dotnet build --nologo -clp:ErrorsOnly` | `dotnet test --nologo -v q`
     - Node/TypeScript: `npx vitest run` | `npm test -- --watch=false`
     - Angular: `npx ng test --watch=false --browsers=ChromeHeadless`
     - Python: `pytest -q --tb=short`
   - **No Dev-Server Abandonment (HMR Mandate)**: Strictly ban `npm run build` loops during UI iteration; keep dev server (`ng serve`, Vite) alive with HMR for instant sub-second feedback.
   - **Playwright Throttling**: Cap browser screenshots at 3-4 per turn at major milestones (initial render, critical modal, completion). Ban micro-action screenshotting.
   - Enforce non-interactive flags (`--watch=false`, `--watchAll=false`, `--ci`, `-y`, `$env:NG_CLI_ANALYTICS="false"`) to prevent process hangs.
   - Verify UI via Playwright: confirm 0 uncaught console errors and save `browser_take_screenshot` artifacts instead of dumping DOM HTML.
5. **Subagent Fan-Out Strategy**:
   - Delegate broad exploratory research and multi-doc lookups to the `research` subagent.
   - Delegate isolated test suites, parallel lint checks, or spike prototypes to `self` subagents.
   - Keep orchestrator context lean, clean, and dedicated to high-level architectural decisions.

---

## 2. Pre-Flight Grilling & Fast-Pass

- **Rule**: Research codebase/memory first. If ambiguous or multi-file, run 1 batched Frontier round.
- **Grilling Hierarchy**:
  - `grilling`: Autonomous architectural stress-testing and assumption verification.
  - `grill-with-docs`: Technical stress-testing grounded in primary docs (pairs with `context7`).
  - `grill-me`: Interactive user interview rounds for ambiguous product direction.
- **Fast-Track (Level 1)**: Mechanical 1-liners (typos, single CSS/syntax fixes) proceed directly without questions.
- **Spec Fast-Pass**: Unambiguous, single-component requests with clear business logic bypass grilling. State 1-line default assumption, apply minimal code ladder, and execute directly.

---

## 3. Task Scale Triage (5 Levels)

- **Level 1 (Fast-Track)**: 1-2 files, trivial bugfixes. Direct minimal diff, local verification (Exit Code 0), complete. No ceremonies.
- **Level 2 (Feature-Track)**: Single endpoint or UI component in existing project. Stack: `claude-mem` + Fast-Pass + `ponytail` + LSP + `playwright`. Apply TDD, write minimal code, verify UI, complete.
- **Level 2.5 (Rapid MVP / Spike)**: Standalone apps, hackathons, prototypes. Stack: `claude-mem` + `ponytail` + `frontend-design` + `playwright`. Bypass formal `CONTEXT.md` and Waterfall gates. Build working vertical slice directly via `ponytail`.
  - **C# .NET + Angular Lean Protocol**: Strictly enforce .NET 9 Minimal APIs (1-file `Program.cs`) + Angular Standalone Single-File Components (`inlineTemplate` + Signals); ban 15-file controller sprawl and 4-file component splits. Verify via tests and headless Playwright. Sync core ADRs to `claude-mem` upon completion.
- **Level 3 (System-Track)**: Enterprise architectures, multi-tier platforms, major refactors. Stack: Full suite (`claude-mem`, `grill-me`, `domain-modeling`, `waterfall-sdlc`, `ponytail`, LSP, `pr-review-toolkit`, `frontend-design`, `playwright`, security audit). Execute 7 quality gates: Requirements -> Analysis -> Design (`CONTEXT.md`, ADRs) -> Implementation -> Testing -> Packaging -> Support.
- **Level 4 (Foggy-Track)**: Undefined legacy migrations or massive open scopes. Stack: `wayfinder` suite (`to-tickets`, `to-spec`). Maintain Map of Decision Tickets, clear spikes to specs, sync with `claude-mem`.

---

## 4. Local-First, Windows PowerShell & Zero-Leak Safety

1. **Zero-Leak Secret Handling Protocol (API Key Ingestion & Protection)**:
   - **Accept User API Keys**: When the user provides an API key, accept and utilize it immediately to configure the local system without artificial hesitation.
   - **Isolated Local Storage**: Store secrets exclusively in local-only private stores: `.env.local`, `appsettings.Local.json`, or process environment variables (`$env:API_KEY="..."`).
   - **Pre-Flight GitIgnore Verification**: Before writing any secret to a configuration file, verify that `.gitignore` explicitly matches and ignores that file pattern (`.env*`, `*.Local.json`).
   - **Strict Backend Isolation (Zero Client-Side Exposure)**: Never embed API keys into client-side code (Angular, React, Vue, or static HTML bundles) where public users can inspect or extract them via DevTools/Network tabs. All API calls requiring secret keys must be proxied through the local backend service.
   - **Redaction & Concealment**: Never print plaintext keys or expose their exact location in chat responses, artifacts (`walkthrough.md`, `CONTEXT.md`), git commits, or public docs. Always redact secrets (e.g., `sk_live_...****`, `AQ...****`).
2. **Local Sandbox**: All execution, DB emulation, and UI testing occur locally. No remote cloud mutations during dev.
3. **Windows PowerShell Execution**:
   - Host is Windows with PowerShell. Ban POSIX utilities (`lsof`, `kill -9`, `fuser`, `xargs`, `/dev/null`). Chain with `;`.
   - **Pre-Flight Port Handshake (Zero-Collision)**: Always kill stale listeners on target ports before starting dev servers:
     `Get-NetTCPConnection -LocalPort <port1>,<port2> -ErrorAction SilentlyContinue | ForEach-Object { Stop-Process -Id $_.OwningProcess -Force }`.
   - Inspect port: `Get-NetTCPConnection -LocalPort <port> -ErrorAction SilentlyContinue | Select-Object -ExpandProperty OwningProcess` or `netstat -ano | findstr :<port>`.
   - Kill stale process by PID: `Get-Process -Id <PID> -ErrorAction SilentlyContinue | Stop-Process -Force`.
4. **Clickable Preview**: Output `Live Local Preview: http://localhost:<port>` whenever dev server starts.

---

## 5. Tool & Skill Routing Matrix

- **Memory & AST**: `claude-mem` daemon (port 37777, hooks handle ingestion). Multi-file structural refactoring via `ast-grep` and `smart_outline`.
- **LSP Diagnostics**: Use LSP skills and lightweight checkers (`pyright`, `tsc --noEmit`) for instant type diagnostics with filtered logs.
- **C# .NET (`csharp-tooling`)**: Enforce .NET 9 Minimal APIs for MVPs/spikes. MSBuild token filtering (`--nologo -clp:ErrorsOnly`). Clean port handshakes before `dotnet run`.
- **Modern Angular (`angular-modern`)**: Always set `NG_CLI_ANALYTICS=false`. Enforce Standalone Single-File Components (`inlineTemplate` / `styles`) with Angular Signals. Never abandon `ng serve` for `npm run build` loops.
- **Live Docs (`context7`)**: Call `@upstash/context7-mcp` (`resolve-library-id` with `libraryName` + `query`, then `query-docs`) for modern libraries (Next.js 15, React 19, Tailwind v4, Supabase) to eliminate API hallucinations.
- **Domain Modeling**: Enforce zero entity drift in `CONTEXT.md`. Canonical names must match across DB, API, and UI.
- **Code Minimalism (`ponytail`)**:
  - **Core Guards**: `ponytail` (YAGNI, stdlib over external packages, native platform features `<dialog>/fetch`), `ponytail-review` (active over-engineering inspection).
  - **On-Demand Utilities**: `ponytail-audit` (repo-wide bloat hunt), `ponytail-debt` (debt ledger), `ponytail-gain` (scoreboard).
- **Frontend & UI/UX (`frontend-design`)**:
  - Two registers: Cinematic (marketing/landing) vs Instrument (apps/dashboards). Bento grids over generic 3-card traps.
  - Design tokens first. Prefer Tailwind v4 / utility tokens over large raw CSS dumps.
  - Zero artificial developer status badges in production UI.
  - Modal dismissal: Single top-right close icon, backdrop click, Escape key (no redundant footer close buttons).
  - Numeric inputs: Coerce empty value to empty string during typing. Vector SVGs only (no Unicode emojis as icons).
  - Form controls: Ban unstyled native `<select>` (require custom popover select) and unstyled `<input type="date">` (require custom calendar popover + `color-scheme`).
  - Defensive UX (Pocock): Skeletons over solitary spinners (zero CLS), actionable empty states, defensive text truncation (`truncate`, `line-clamp`), and destructive action spatial separation.
- **PR Review & Git**: Run `pr-review-toolkit` multi-lens review before PRs. Atomic Conventional Commits (`commit-commands`). Push and open PRs via `github-mcp-server`.
- **Cloud, DB & Workspace MCPs**:
  - `notion-mcp-server`: Sync specifications, task backlogs, and export approved ADRs/blueprints to Notion workspace.
  - `supabase` (migrations/SQL), `stripe` (payments), `cloudrun` / `firebase-mcp-server` (deploy only after 100% local pass).
- **Browser Audit (`playwright`)**: Test across mobile (375px), tablet (768px), and desktop (1280px). Verify 0 uncaught errors and capture screenshot artifacts (throttled).

---

## 6. Verification & 3-Strike Circuit Breaker

- **5 Quality Gates**: Typecheck clean, automated tests passing (Exit Code 0), production build passing, Playwright visual audit passing (0 console errors), and security scan clear.
- **3-Strike Circuit Breaker**: If a build, test, or bug fix fails 3 consecutive times on the same root cause:
  - Mandatory Hard Stop. Do not attempt a 4th blind retry.
  - Create clean git checkpoint/stash.
  - Escalate immediately with: (1) Diagnostic summary, (2) Option A (pragmatic/native alternative), (3) Option B (constraint relaxation/mock), and (4) Concrete recommendation (`-> recommendation`).

---

## 7. Multi-Skill Lifecycle Flow & Event-Driven Checkpoints

1. **Intake & Memory Check**: Query `claude-mem` and `smart_outline`. Take Fast-Pass or run 1 Frontier grilling round.
2. **Domain & Design Contract (Checkpoint 1)**: Lock entities in `CONTEXT.md` (`domain-modeling`), query docs via `context7`, define tokens via `frontend-design`. **Immediately persist locked entities, architecture decisions, and ADRs to `claude-mem`**.
3. **AST & Minimal Dev**: Navigate via `smart_outline`/`ast-grep`/LSP, write minimal code via `ponytail`, keep dev local.
4. **Verification & Testing (Checkpoint 2)**: Run sanitized non-interactive tests (Exit Code 0), Playwright visual audit, security check, and multi-lens PR review. **Immediately persist verified endpoint contracts, schemas, and test results to `claude-mem`**. Trigger Circuit Breaker if stuck.
5. **Zero-Leak Delivery**: Create atomic Conventional Commits, push branch, open PR via `github-mcp-server`.
6. **Handover & Final Sync (Checkpoint 3)**: Output preview link and concise summary. Persist final live URLs, residual backlog, and maintenance instructions to `claude-mem`.
