# Specification: ZillerDX SDLC & Autonomous Engineering Suite (`zillerdx-sdlc-skill`)

## 1. Problem
The repository previously carried legacy Waterfall SDLC artifacts (`plugin.json`, references to waterfall methodologies and 5-phase monolithic gates) and omitted several core skills invoked by the new dispatcher (`ponytail`, `domain-modeling`, `commit-commands`, `wayfinder`). Additionally, the showcase landing page (`index.html`) and `README.md` documented the old waterfall paradigm rather than the modern 2026 spec-driven, slice-by-slice agentic pairing workflow.

## 2. Solution
Transform the repository into the definitive release package for **ZillerDX SDLC & Autonomous Engineering Suite**:
1. **Skill Suite Packaging**: Package all skills called by the master `AGENTS.md` (`ui-craft`, `ponytail`, `domain-modeling`, `pr-review-toolkit`, `commit-commands`, `wayfinder`) into `skills/` and `.agents/skills/`.
2. **Workflow Suite**: Package all 5 slice-loop workflows (`plan.md`, `build.md`, `preview.md`, `review.md`, `commit.md`) in `.agents/workflows/`.
3. **Repository Cleanup**: Purge dead and deprecated files (`plugin.json`, obsolete configs).
4. **Project & Remote Renaming**: Update package descriptors (`package.json`, workflow configs) and rename the GitHub remote repository to `zillerdx-sdlc-skill` via GitHub CLI (`gh repo rename`).
5. **Interactive Landing Page (`index.html`)**: Complete overhaul adhering to `ui-craft` standards — 3-tone electric blue/neutral palette, interactive 6-phase slice visualizer, terminal installation tabs (Antigravity, Claude Code, Cursor, Windsurf), token benchmark metrics, dark/light mode, and 0 console errors.
6. **Portfolio README (`README.md`)**: Complete rewrite with comprehensive architecture diagrams, technology stack, workflow runbooks, port hygiene rules, and usage examples.

## 3. Requirements (REQ Table)
| REQ | Requirement | Acceptance criteria |
|---|---|---|
| REQ-001 | Complete Skill Ecosystem Packaging | Given global skills (`ponytail`, `ui-craft`, `domain-modeling`, `commit-commands`, `pr-review-toolkit`, `wayfinder`), when synced to `skills/` and `.agents/skills/`, then all skills are present with valid frontmatter and passing CI validation. |
| REQ-002 | Repository Dead File Cleanup | Given obsolete artifacts (`plugin.json`), when deleted via `git rm`, then 0 references to `plugin.json` remain in config and manifests. |
| REQ-003 | Project & Remote Repository Renaming | Given `package.json`, `.github/workflows/deploy-pages.yml`, and GitHub remote, when renamed to `zillerdx-sdlc-skill`, then repo name and remote URLs resolve to `https://github.com/ZillerDX/zillerdx-sdlc-skill`. |
| REQ-004 | High-Fidelity Showcase Landing Page (`index.html`) | Given modern `ui-craft` and 2026 spec-driven system, when `index.html` is rewritten, then it presents the new architecture, includes interactive slice visualizer and terminal tabs, supports light/dark mode, and loads with 0 console errors. |
| REQ-005 | Portfolio Documentation Overhaul (`README.md`) | Given the updated system, when `README.md` is rewritten, then it documents the 6-phase slice loop, 7 product pillars, port hygiene, and installation guides without stale waterfall references. |
| REQ-006 | Automated Verification & Push Delivery | Given all changes, when gates run, then validate-skills CI passes, links resolve, and changes are committed and pushed cleanly to the renamed remote. |

## 4. Implementation Decisions
- **Styling**: Tailwind CSS CDN + custom CSS variables for dark/light themes, Lucide icons, Three.js canvas accent.
- **Port Hygiene**: Use port check before running local preview server.
- **Git Protocol**: Atomic conventional commits, no push before preview handover and user acceptance.

## 5. Testing Seams
- **CI Manifest & Frontmatter Validator**: Node test script in `.github/workflows/validate-skills.yml`.
- **Local Web Preview**: Web server on target port with Playwright verification (0 console errors, screenshot capture).
- **GitHub CLI**: `gh repo rename zillerdx-sdlc-skill -y`.

## 6. Out of Scope
- Creating new unrelated third-party skills.
- Modifying remote user profiles outside repository scope.

## 7. Open Questions
- None. Confirmation round presented in Phase 1 before execution.
