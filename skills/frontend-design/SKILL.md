---
name: frontend-design
description: Master studio design system and UI engineering standards. Fuses aesthetic rigor (tokens, 2 registers, 4-state motion) with defensive software engineering (skeletons, empty states, truncation, destructive safety) and ruthless anti-slop production guards.
license: MIT
---

# Master Frontend Design & UI Engineering

The unified studio standard for high-fidelity web applications and marketing interfaces. Fuses aesthetic polish with defensive software engineering. Execute every UI task using this decision contract.

---

## 1. The Two Design Registers

Determine the project register before writing markup:

1. **Cinematic Register (Marketing, Landing Pages, Brand Portals)**:
   - **Purpose**: Visual impact, brand authority, narrative pacing, conversion.
   - **Ground & Atmosphere**: Tinted tones (warm stone, deep slate, subtle radial glows). Never stark `#ffffff` or flat `#000000`.
   - **Layout**: Asymmetric compositions, editorial whitespace, proof-driven metrics, client trust bars.
   - **Anti-Monotony Guard**: Absolute ban on the generic "centered title + 3 identical icon cards" trap. Use Bento grids, interactive sandbox previews, or split narrative pacing.

2. **Instrument Register (Web Apps, Dashboards, Product Interfaces)**:
   - **Purpose**: High information density, cognitive clarity, low latency, rapid operation.
   - **Typography**: Clean grotesque system sans (`Inter`, `Geist`, `SF Pro`) + monospace tabular numbers (`font-variant-numeric: tabular-nums`).
   - **Ground & Atmosphere**: Neutral tinted grays, structured 1px borders (`1px solid var(--border)`), high-contrast data rows.
   - **Layout**: Fixed toolbars, compact padding, pinned data tables, density-respecting mobile drawers.

---

## 2. Design Tokens & Visual Hierarchy

Lock design tokens in CSS variables or Tailwind config before writing markup. Ban raw arbitrary hex/px values.

### Anti-Cliche Palette Archetypes
Do not default exclusively to "Obsidian Black + Neon Cyan Glow". Choose deliberately:
1. **Monochrome Precision (Default Instrument)**: Neutral zinc/slate grounds, crisp 1px borders (`hsl(220, 15%, 20%)`), single purposeful accent (Signal Orange `hsl(24, 95%, 53%)` or Electric Cobalt `hsl(221, 83%, 53%)`).
2. **Warm Editorial (Default Marketing)**: Alabaster ground (`hsl(36, 33%, 97%)`), stone surface, espresso ink (`hsl(24, 10%, 12%)`), terracotta accent (`hsl(14, 75%, 50%)`).
3. **Deep Bronze / Architectural Charcoal**: Warm charcoal ground (`hsl(30, 8%, 10%)`), bronze borders (`hsl(38, 30%, 25%)`), warm sand text.

### Tinted Ground & Radius Formula
- **Ground is never white, ink is never black**:
  - Light mode: Ground `hsl(210, 20%, 98%)`, Surface `hsl(0, 0%, 100%)`, Ink Primary `hsl(215, 25%, 12%)`, Ink Muted `hsl(215, 15%, 45%)`.
  - Dark mode: Ground `hsl(220, 25%, 8%)`, Surface `hsl(220, 20%, 12%)`, Ink Primary `hsl(210, 20%, 95%)`, Ink Muted `hsl(215, 15%, 60%)`.
- **Radius Nesting Formula**: Inner element radius must nest harmoniously inside outer container radius:
  `r_inner = max(0, r_outer - padding)`.

---

## 3. Strict Vector Iconography & Typography Discipline

1. **Zero Unicode Emojis**: Absolute ban on emojis (🚀, 💡, 🔥, ⚙️) as interface icons, navigation items, or statuses. Always use clean inline SVGs or vector icon sets (Lucide, Radix, Heroicons) with explicit sizes (`width={20} height={20}`) and `flex-shrink: 0`.
2. **Semantic Icon Discipline**: Ban decorative filler icons in card corners. Every icon must carry clear, functional semantic meaning.
3. **Directional Delta Accuracy**: Decreases, savings, and latency drops MUST use downward indicators (`-` or `down-arrow SVG`). Never use upward arrows for reductions. Increases and earnings use upward indicators (`+` or `up-arrow SVG`).
4. **Readable Line Length (Prose Clamping)**: Long-form text and subtitles MUST clamp to readable line lengths (`max-w-prose` / 65–75ch). Never allow paragraphs to stretch unconstrained across 1920px viewports.
5. **Motion Physics & Spring Curves**:
   - Modal reveals & entrances: `transition: transform 300ms cubic-bezier(0.16, 1, 0.3, 1), opacity 250ms ease-out;`
   - Micro-interactions (hover, press): `transition: all 150ms cubic-bezier(0.2, 0.8, 0.2, 1);`
   - Ban linear or uncurved transitions.
6. **Complete 4-State Micro-Interactions**:
   Interactive controls MUST define: (1) **Idle**, (2) **Hover** (lift `-1px`, brightness +5%), (3) **Active** (depression `+0.5px`, scale `0.98`), and (4) **Focus-Visible** (`ring-2 ring-primary ring-offset-2`).

---

## 4. Defensive Engineering & State Architecture (Pocock Discipline)

1. **Defensive Text Truncation**: All dynamic user-generated content (asset tags, usernames, emails, model names) must anticipate extreme lengths. Guard containers with `truncate`, `line-clamp-2`, or `break-words` with `title` tooltips. Dynamic content must never blow out card bounds.
2. **Zero-Layout-Shift Loading (Skeleton Shimmer over Spinners)**:
   - Ban solitary, centering full-screen spinners for page content areas.
   - Use skeleton pulse/shimmer blocks matching the exact dimensions of final content to eliminate Cumulative Layout Shift (CLS).
3. **Actionable Empty States**:
   - When a dataset is empty or search yields 0 items, never render blank dead space or raw "No data" text.
   - Render a deliberate empty container: contextual vector icon + clear 1-line explanation + primary call-to-action button (e.g. "Clear filters", "Register new asset").
4. **Destructive Action Safety**:
   - Spatial separation: Never place a destructive button (Delete, Revoke, Terminate) directly adjacent to a primary commit action without visual distinction and padding.
   - Require a 2-step confirmation dialog or popover before executing destructive mutations.
5. **Defensive Responsive Tables**:
   - Wrap multi-column tables in `overflow-x-auto` with sticky identifier columns. On viewports <768px, transform wide rows into mobile card stacks.

---

## 5. Anti-Slop Production Guards & Form Discipline

1. **Zero-Status-Badge Rule**: Absolute ban on environment chips, server locations, port numbers, activity pills, and pulsing status dots in UI headers (e.g. "Prod / US-East", "Memory Engine Active", "Frontend: Online", "Port 3000", "Live", "v1.0.0"). Replace exclusively with authentic application navigation, user switchers, and command palettes (`Ctrl+K`).
2. **Zero Meta-Commentary in UI Copy**: Never place developer implementation notes, bugfix explanations, or test self-praise in customer-facing UI (e.g. "will not get stuck on 0", "fixed modal bug"). All copy must read as authentic user guidance.
3. **Dashed Border Discipline**: Dashed borders (`border-dashed`) are strictly reserved for file upload dropzones. Data cards, summary panels, and results use crisp 1px solid borders.
4. **Modal Dismissal Hierarchy**: Exactly one top-right close icon (`X`), backdrop click dismissal, and Escape key listener. Do not place redundant "Cancel" buttons in modal footers alongside primary actions.
5. **Zero-Stuck Numeric Input Bug Prevention**: When binding `<input type="number">` or currency inputs, prevent undeletable 0 values: handle empty state explicitly (`value === '' ? '' : val`) and coerce empty string in change handlers.
6. **Ban on Unstyled Native Select (`<select>`)**: Native `<select>` triggers OS-level popup menus (sharp 90° square corners on Windows, harsh OS-blue selection highlight, rigid system fonts, zero tokenized dark radii). Always build custom accessible select components featuring:
   - Tokenized surface and subtle border (`bg-zinc-800 border-zinc-700/80 rounded-md`).
   - Smooth micro-animated vector chevron (`rotate-180` on open).
   - Floating popover card with nested border radius (`r_inner`), subtle backdrop blur (`backdrop-blur-md`), elevated shadow (`shadow-xl`), and keyboard/click-outside dismissal.
   - 4-state item hover and active styling with a discrete vector checkmark SVG for the active option.
7. **Ban on Unstyled Native Date Picker (`<input type="date">`)**: Default browser date pickers render stark white, sharp rectangular calendar widgets.
   - Baseline: Set `color-scheme: dark` (or light matching theme) in CSS.
   - Studio Standard: Replace with custom calendar popovers: input field displaying formatted date with vector calendar SVG icon, quick clear button, popover card matching tokens (`rounded-xl`, `border-zinc-700`, `bg-zinc-900`), month/year navigator chevrons, muted monospace weekday header (`Su Mo Tu We Th Fr Sa`), 7-column grid with rounded pill/circle date buttons, and "Today" / "Clear" action presets.

---

## 6. Pre-Flight Visual Reasoning Checklist

Before marking any UI task complete, verify:
- [ ] 0 Unicode emojis used as icons or buttons.
- [ ] 0 infrastructure status badges (e.g. "Prod / US-East", "Port 3000", "Active", pulsing dots) or developer commentary in UI.
- [ ] 0 unstyled native `<select>` dropdowns (using custom styled popover select with tokens & chevrons).
- [ ] 0 unstyled native `<input type="date">` browser pickers (using custom calendar popover and `color-scheme` guard).
- [ ] Hero sections avoid generic 3-card monotony; use Bento grids or split previews.
- [ ] Loading states use skeleton shimmers; empty states include actionable CTAs.
- [ ] Dynamic user text includes defensive truncation (`truncate`/`line-clamp`); paragraphs clamp to `max-w-prose`.
- [ ] Destructive actions have spatial separation and 2-step confirmation.
- [ ] Decreases/savings use downward indicators (down-arrow SVG or -), never upward arrows.
- [ ] 0 decorative meaningless icons in card corners.
- [ ] Ground and ink use tinted tokens, not raw black and white; outer/inner radii obey nesting formula.
- [ ] All interactive controls define 4 complete visual states with spring motion curves.
- [ ] Modal dismissal follows the single-close hierarchy.
- [ ] Responsive across mobile (375px), tablet (768px), and desktop (1280px) with 0 uncaught console errors.
