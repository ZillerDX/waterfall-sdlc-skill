---
name: ui-craft
description: Use when designing or building any user-facing UI — new pages or screens, components, layouts, styling, theming, dashboards, landing pages, forms, navbars, UI copy (Phase 3 of PLAN.md) — or when reviewing UI for visual quality, UX states, accessibility, or Thai typography (Phase 4).
license: MIT
---

# UI Craft

Goal: interfaces that look like a senior designer made them for *this* product — not like generated output. Quality comes from process (direction → plan → generic check → build → look → cut), not from adding effects. More effects almost always make it look more generated.

## Scope

- **Owns:** visual direction, layout, tokens, typography, color, motion, UI states, component UX, UI copy.
- **Does not own:** component logic, data fetching, state architecture → `ponytail`.
- **Yields to:** AGENTS.md (Safety, User Directive, Correctness). The brief's own words win — if the user asks for a specific look, build exactly that. A project's existing design system wins over everything here: extend it, never replace it.

## Step 0 — Register (per route)

| | Cinematic | Instrument |
|---|---|---|
| For | Landing, marketing, brand, showcase | Apps, dashboards, tools, admin, trading views |
| Goal | A distinct identity; one memorable moment | Clarity, density, 3-second comprehension |
| Distinctiveness from | Signature element, type, composition | Type choice, density, precise alignment, one small signature detail — never effects over data |

## Step 1 — Direction before code

Required for new pages/screens. Skip for small edits to existing UI (follow the local system instead).

1. **Ground it.** One line each: subject, audience, primary job of the screen. Take visual vocabulary from the subject's own world (its materials, tools, documents, vernacular) — that's where distinct choices come from. Use real content from the brief; write specific copy, never lorem or slogans.
2. **Plan** (write into PLAN.md under the task, not in chat):
   - Palette: 4–6 named hex values with roles.
   - Type: 1–2 families (clearly distinct if two) + a scale.
   - Layout: one-sentence concept + ASCII wireframe for desktop and mobile; state alignment.
   - Signature: the one element people will remember.
   - Principles: 2–3 lines on what makes this screen specific.
3. **Generic check.** Read `resources/generic-tells.md`. For each axis ask: *would I produce this for any similar brief?* If yes, change it and note `revised: X → Y because Z`.
4. Then build.

## Step 2 — Build laws

1. **Hierarchy.** One Primary CTA per view/dialog; everything else secondary or ghost. Weight ladder: primary action > key metric > section title > body > caption.
2. **Limited color.** Palette from the plan. Semantic state colors (success, warning, danger, info, market up/down) only encode state, never decorate. Never rely on color alone.
3. **Type carries personality.** Chosen per brief, not the same default every project. Tight scale, intentional weights. Lines under ~75 characters. Tabular numerals on data.
4. **Scannable.** Key status readable in 3 seconds; critical figures pop, scaffolding recedes.
5. **Whitespace is structure.** Tight within groups, generous between sections, never cramped against borders.
6. **Restraint.** Boldness in one place — the signature. Everything around it quiet and disciplined. Cut decoration that doesn't serve the brief.
7. **Structure is information.** Borders, dividers, numbering, eyebrows, labels, badges appear only when they encode something true about the content (numbering only for real sequences).
8. **Motion answers people.** Motion that shows what changed after an action is welcome. Ambient motion: at most one orchestrated moment per page. No fade-up on every section, no hover lift on every card.

Build order: tokens → layout with real content → states (loading/empty/error) → interaction → motion last.

## Step 3 — Look and cut

Required for new pages/screens, at the end of Phase 3:

1. Open in the browser; screenshot at 1280px and 375px.
2. Compare against the plan and `resources/checklist.md`. Write the 3 biggest problems, ranked.
3. Fix them. Re-screenshot once.
4. Remove one accessory — the least necessary decoration.
5. Max 2 critique rounds. Report 1 proof screenshot (AGENTS.md).

A screenshot catches what reading code never will: crowding, weak hierarchy, misaligned baselines, clipped Thai marks.

## Defensive UI (every screen)

- **Loading:** skeletons at final dimensions; no full-page spinner for content.
- **Empty:** one-line reason + one action. **Error:** what failed + how to fix; keep user input.
- **Truncation:** dynamic text truncates with full value in tooltip/`title`.
- **Destructive:** separated from primary; 2-step confirm with explicit Cancel.
- **Tables:** horizontal scroll with sticky ID column; card stack under 768px.
- **Deltas:** arrow = direction of change, color = good/bad. `--up`/`--down` are tokens.
- **Quality floor (don't announce it):** responsive to 375px, visible `:focus-visible`, 4.5:1 contrast, labeled inputs, ≥40px targets, `prefers-reduced-motion` respected.

## Anti-slop guards

- No emoji as icons/status/bullets; one icon family, uniform stroke and size.
- No connection/status pills or pulsing dots; connectivity surfaces only as an error when it fails.
- No version tags, build numbers, or tech-stack badges in UI.
- No dot-prefixed titles, meaningless corner icons, or developer commentary in copy.
- No parenthetical English in Thai labels.
- Everything in `resources/generic-tells.md` unless the brief asks for it.
- Every app ships an SVG favicon and logo mark derived from its domain.

## Load on demand

| Need | File |
|---|---|
| Step 1 generic check, Step 3 critique | `resources/generic-tells.md` |
| Any UI copy, labels, errors, empty states | `resources/copy.md` |
| Token structure, type scale, radius, motion, dark mode | `resources/tokens.md` |
| Buttons, navbar, modal, select, date, inputs, forms, tables | `resources/components.md` |
| Any Thai text | `resources/thai.md` |
| Cinematic signature elements, 3D, atmosphere | `resources/cinematic.md` |
| New layout with no local precedent | `resources/references.md` |
| Step 3 and Phase 4 review | `resources/checklist.md` |

## With ponytail

- Native controls first, themed. Custom select/date only from the project's headless library.
- Dependencies for effects (Three.js, animation libs) need a user request or a Cinematic signature that truly requires them; otherwise CSS/SVG.

## Output

Code first. Plan and critique live in PLAN.md. In chat, at most two lines: the signature choice and anything intentionally skipped.
