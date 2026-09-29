# PLAN: Waterfall SDLC & Modern Agentic Skill System 2.0 Overhaul
> **Issue / Ticket**: Full-Loop Upgrade: Webpage Redesign, Skill Sync, Portfolio README | **Level**: Level 3 (System-Track)
> **Live State**: Phase 5/5 — Git Packaging, Portfolio README & QA Handover | **Status**: COMPLETED

## Phase Decomposition Matrix

### Phase 1: Specifications, Domain Architecture & DevSecOps Threat Model
- **Goal**: Lock requirements, scope skill updates, establish UI visual hierarchy and threat model.
- **Skills & MCPs**: `claude-mem`, `domain-modeling`, `frontend-design`, `context7`.
- **Execution Checklist**:
  - [x] 1.1 Memory and repository inventory audit (`AGENTS.md`, `skills/`, `index.html`, `README.md`, `plugin.json`).
  - [x] 1.2 Lock versioning scheme (`v2.0.0`) and updated feature contracts (PLAN.md engine, SOLID/OOP, NIST SSDF, 12-step QA/CI/CD).
  - [x] 1.3 Shift-Left Security: Ensure zero external vulnerable CDN scripts, static local client-side assets only, CSP compliance.
- **Exit Gate**: Plan locked, scope defined, security boundaries validated.

### Phase 2: Core Architecture & Skill Package Synchronization
- **Goal**: Sync the latest production skills and metadata ready for workspace distribution.
- **Skills & MCPs**: `ponytail`, `csharp-tooling`, `angular-modern`, `frontend-design`.
- **Execution Checklist**:
  - [x] 2.1 Sync `skills/frontend-design/SKILL.md` with latest 5 Rules of Clean Design from config.
  - [x] 2.2 Sync `skills/csharp-tooling/SKILL.md` with .NET 10 LTS & C# 14 standards.
  - [x] 2.3 Verify `skills/angular-modern/SKILL.md` and `skills/waterfall-sdlc/SKILL.md`.
  - [x] 2.4 Update `plugin.json` and `package.json` to version `2.0.0`.
- **Exit Gate**: All skills updated, manifests valid and in sync.

### Phase 3: High-Fidelity Frontend & UI/UX Engineering (`index.html`)
- **Goal**: Re-engineer `https://zillerdx.github.io/waterfall-sdlc-skill/` adhering to the 5 Rules of Clean Design.
- **Skills & MCPs**: `frontend-design`.
- **Execution Checklist**:
  - [x] 3.1 Layout & Hierarchy: 1 dominant primary CTA ("Install System"), 3-zone sticky navbar, bento grid layout.
  - [x] 3.2 3-Tone Color Palette: Electric Cobalt accent (`#2563eb`), Subdued secondary tint (`#eff6ff`), Neutral grounds (`zinc-50`/`white`).
  - [x] 3.3 Light Mode Default + Dark Mode Toggle: Default to crisp Light Mode with persisted Sun/Moon toggle.
  - [x] 3.4 5 Rules of Clean Design & Defensive UX: Generous whitespace (`gap-6`/`gap-8`), Gestalt proximity, tabular numbers for metrics.
  - [x] 3.5 Professional Iconography: Cohesive SVG vector icons (Heroicons/Lucide); zero Unicode emojis on UI.
  - [x] 3.6 1-Click Installation Terminal: Multi-client tabs (Antigravity/Gemini CLI, Claude Code, Cursor, Windsurf).
- **Exit Gate**: Responsive HTML5/Tailwind standalone landing page, 0 console errors, interactive features verified.

### Phase 4: Headless Verification, CI & Multi-Lens Review
- **Goal**: Local web verification, Playwright milestone inspection, and multi-lens code review.
- **Skills & MCPs**: `pr-review-toolkit`, `playwright` (milestone visual proof).
- **Execution Checklist**:
  - [x] 4.1 Local web preview test on target port (PowerShell port cleanup + live preview).
  - [x] 4.2 Headless Playwright audit: 1280px desktop, verify 0 uncaught console errors, capture 1 milestone proof screenshot.
  - [x] 4.3 Multi-lens review pass: Check 5 Rules compliance, contrast ratios, and responsive breakpoints.
- **Exit Gate**: 0 console errors, visual proof validated, zero broken links.

### Phase 5: Git Packaging, Portfolio README & QA Handover
- **Goal**: Create portfolio-grade `README.md`, atomic Conventional Commits, push to GitHub `main`.
- **Skills & MCPs**: `commit-commands`, `github-mcp-server`, `claude-mem`.
- **Execution Checklist**:
  - [x] 5.1 Rewrite `README.md` to Portfolio-Grade standard (7 Product Pillars, zero emoji Mermaid diagrams).
  - [x] 5.2 Atomic Conventional Commit (`feat(release): v2.0.0 full-loop overhaul`).
  - [x] 5.3 Push to `origin main` to trigger GitHub Pages CD workflow.
  - [x] 5.4 Persist deployment state and release notes to `claude-mem`.
- **Exit Gate**: Pushed to GitHub main, live URL verified, memory synced.
