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

## 2. The 5 Rules of Clean Design (Core Aesthetic Laws)

Every layout, component, and screen MUST adhere strictly to the 5 Foundational Rules of Clean Design:

### Rule 01: Prioritize Hierarchy ("If everything is important, nothing is important")
- **Single Dominant Action**: Exactly one **Primary CTA** per view/dialog (bold, high-contrast, visually grounded).
- **Secondary & Tertiary Demotion**: Supporting actions must be subdued into Secondary (soft gray tint) or Ghost/Outline buttons. Never compete with the Primary action using two saturated colored buttons in the same container.
- **Visual Weight Ladder**: Size, weight, and contrast must guide the eye naturally: `Primary Action > Key Value/Data Metric > Section Title > Body Text > Helper/Muted Caption`.

### Rule 02: Limit Colors ("Too many colors create visual noise")
- **The 3-Tone Rule (Primary + Secondary + Neutral)**:
  - **1 Primary Accent**: The brand voice (e.g. Electric Cobalt, Signal Indigo, or Deep Navy). Used strictly for active states, primary buttons, and focal indicators.
  - **1 Secondary Tint**: A soft, subdued tint or shade of the primary color (used for active pill backgrounds, badge surfaces, subtle highlights).
  - **Neutral Grounds**: Tinted zinc/slate for background canvas (`zinc-50`), card surfaces (`white`), and subtle 1px borders (`zinc-200/80`).
- **Absolute Ban on Rainbow Clutter**: Never decorate individual cards or dashboard metrics with arbitrary different colors (e.g. purple card next to pink card next to yellow card). Color must communicate state or focus, never pure decoration.

### Rule 03: Keep Typography Consistent ("Too many sizes & different fonts create chaos")
- **Single Cohesive Type Family**: Use at most 1 primary system sans font family (e.g. `Inter`, `Geist`, `SF Pro`, paired with high-legibility Thai font `Prompt`/`Sarabun`).
- **Disciplined Type Scale**: Never use arbitrary font sizes. Restrict strictly to standard steps:
  - Display / Hero: `28px` – `36px` (`font-bold`, `tracking-tight`)
  - Section Headings: `18px` – `20px` (`font-semibold`)
  - Body & Form Controls: `14px` (`font-normal` or `font-medium`, `leading-normal`)
  - Captions, Meta, & Badges: `12px` (`font-medium`, `text-zinc-500`)
- **Tabular Numerics for Data**: All monetary, timer, and counter numbers MUST use `font-variant-numeric: tabular-nums` or `font-mono` to prevent jitter during updates.

### Rule 04: Design for Easy Scanning ("Make important information easy to find in seconds")
- **The 3-Second Comprehension Law**: A user scanning a dashboard or report must grasp system status, current queue, or total revenue in under 3 seconds without hunting.
- **The Pop-Out Effect**: Make critical figures prominent (large bold numerals, distinct badges, high-contrast status cards) while muting surrounding scaffolding.
- **Scan-Friendly Layouts**: Use F-pattern and Z-pattern visual structures, clear row borders, and pinned header rows in data tables.

### Rule 05: Whitespace is Not Empty Space ("It's what makes your design readable and structured")
- **Whitespace is an Active Structural Tool**: Generous padding and margins are what create order, rhythm, and clarity.
- **Gestalt Proximity**:
  - Tightly group related items (e.g. label + input: `gap-1.5` to `gap-2`).
  - Generously space distinct sections and unrelated cards (`gap-6` to `gap-8`, padding `p-6` to `p-8`).
- **Ban Cramped & Claustrophobic Cards**: Never crowd text, inputs, and buttons against card borders. Maintain comfortable internal card padding (`p-6` on desktop, `p-4` on mobile).

---

## 3. Crafted Elegance & Sensory Depth (Artistic Rigor)

Functional minimalism without artistry results in sterile, rigid, and lifeless interfaces. Modern flagship interfaces (Linear, Vercel, Stripe, Raycast) achieve high appeal by infusing clean engineering with **sensory depth, atmospheric lighting, and bespoke typography**:

### 1. Three.js & Interactive 3D Centerpieces ("Ban Naked Heroes")
- **Mandatory Visual Centerpiece**: Flagship landing pages and developer showcases MUST NOT consist solely of naked text and buttons. Every premier showcase MUST feature a dynamic **Visual Centerpiece**:
  - **Three.js Ambient 3D Canvas**: Integrate **Three.js** (`three.min.js`) to render silky, lightweight 3D elements behind or beside the Hero section:
    - Interactive geometric wireframes (icosahedrons, floating architectural rings, or knot meshes).
    - Constellation node graphs or dynamic wave particle fields that subtly rotate and gracefully respond to user cursor movement (`mousemove` parallax).
    - Canvas must be lightweight, throttled to 60fps, GPU-friendly, and gracefully adapt its materials/wireframe colors to Light Mode (`#2563eb`, `#93c5fd`) vs Dark Mode (`#60a5fa`, `#3b82f6`).
  - **Interactive Terminal / IDE Sandbox Mockup**: As an alternative or paired centerpiece, provide an authentic, interactive IDE mockup featuring line numbers, glowing status tabs, active prompt cursors, and syntax highlighting.

### 2. Bespoke Typographic Personality (`Plus Jakarta Sans` & `JetBrains Mono`)
- **Primary Display & Interface Typography**: Standardize on **`Plus Jakarta Sans`** (Google Fonts variable font) for all headlines, navigation, and interface controls.
  - Apply negative letter-spacing on display headings: `tracking-[-0.025em]` to `tracking-[-0.035em]`. This provides the tight, confident, geometric editorial character seen in world-class design systems.
  - Pair with high-legibility Thai web fonts (`Prompt` or `Sarabun`) when rendering multilingual content.
- **Specular Gradient Text Masks**: Display titles in Dark Mode MUST NOT be stark, flat white text. Use subtle vertical specular gradient text masks:
  `bg-gradient-to-b from-white via-zinc-100 to-zinc-400 bg-clip-text text-transparent`.
- **Code, Data & Terminal Typography**: Standardize on **`JetBrains Mono`** (Google Fonts) or `Geist Mono` for all code blocks, terminal lines, telemetry, and data counters (`font-mono`, `font-variant-numeric: tabular-nums`).

### 3. Atmospheric Lighting & Specular Sheen (Ban Flat Black Voids)
- **Ambient Lighting**: Dark mode is NEVER a flat black hole (`#000000` or `#09090b`). Infuse background grounds with multi-stop radial glows, subtle aurora mesh blurs (`blur-3xl`, opacity 15–25%), or delicate geometric grids.
- **Top-Edge Specular Highlights**: Every elevated card, modal, and bento panel in Dark Mode MUST feature top-edge specular illumination to simulate authentic physical materials:
  `border border-white/[0.08] shadow-[inset_0_1px_0_0_rgba(255,255,255,0.08)]`.

### 4. Spotlight Bento Glassmorphism & Cursor Glow
- **Spotlight Hover Tracking**: Bento grid cards must implement mouse-tracking spotlight lighting. Utilizing CSS custom properties (`--mouse-x`, `--mouse-y`), cast a soft radial gradient sheen that illuminates the card's borders and surface only near the user's cursor.
- **Multi-Layered Icon Badges**: Strictly ban placing icons into flat, solid, monochrome squares. Elevate all feature and section icons into **Multi-Layered Glass Badges**:
  `w-11 h-11 rounded-xl bg-gradient-to-br from-blue-500/15 to-indigo-500/5 border border-blue-500/25 flex items-center justify-center text-blue-400 shadow-[0_0_20px_rgba(37,99,235,0.15)]`.

### 5. Authentic Developer Brand Icons & Tactile Micro-Interactions
- **Official Developer Brand Vectors**: When highlighting tech stacks, runtimes, or tools, use authentic, pixel-perfect brand SVG vectors (Google, Claude, Cursor, Windsurf, .NET 10, Angular, TypeScript, Python, GitHub) instead of generic folder or wrench icons.
- **Lucide Iconography**: Use **Lucide Icons** as the standard vector symbol family for all actions, navigation, and features (stroke width `1.75` or `2`, consistent 20px/24px geometry).
- **Tactile Micro-Interactions**:
  - Primary buttons must feature a subtle light shimmer sweep: an angled overlay that glides across the button on hover (`group-hover:translate-x-full transition-transform duration-1000`).
  - Bento cards must feature smooth spring-like elevation lifts: `hover:-translate-y-1 hover:border-blue-500/40 hover:shadow-2xl transition-all duration-300`.

---

## 4. Mobbin Visual Intelligence Protocol (Real-World Ground Truth)

When designing new landing pages, dashboards, complex components, or user flows, the AI MUST NOT guess or improvise layout compositions in a vacuum. Utilize the Mobbin MCP server (`search_sections`, `search_screens`, `search_flows`) as the primary visual reference engine to anchor layouts in battle-tested world-class designs:

### 1. Pre-Flight Visual Reference Search
- **Component & Section Patterns**: Before building Hero sections, Bento Grids, Pricing Tables, Navbars, or Settings Panels, call `search_sections` with descriptive queries and `platform="web"` (e.g. `query: "developer tools landing page hero with dark bento grid"`, `output_destination: "code"`).
- **Full-Screen Architecture & Density**: For dashboard layouts, workspace consoles, or analytics views, call `search_screens` (e.g. `query: "Linear app desktop dashboard instrument layout"`, `platform: "web"`).
- **Multi-Step Interaction Flows**: For onboarding wizards, multi-stage forms, or checkout funnels, call `search_flows`.

### 2. The Reference Synthesis Law (Extract Architecture, Enforce Our Tokens)
- **Extract from Reference**:
  - Spatial rhythm, column proportions, and padding scale (`gap-6`/`gap-8`, `p-6`/`p-8`).
  - Asymmetric bento grid arrangements (e.g. 2-column or 3-column mixed spans: `col-span-2`, `row-span-2`).
  - Icon badge placement, micro-copy hierarchy, and metric badge styling.
- **Enforce Our Production Standards**:
  - **Map to Our 3-Tone Palette**: Strictly recolor the external reference into our project's 3-tone color tokens (Primary brand accent + secondary tint + neutral grounds). Never copy external arbitrary colors.
  - **Apply Standard Typography**: Standardize on `Plus Jakarta Sans` for display headlines (`tracking-[-0.03em]`) and `JetBrains Mono` for code/numbers.
  - **Infuse Crafted Elegance**: Add Three.js 3D ambient canvas, top-edge specular highlights (`inset 0 1px 0 rgba(255,255,255,0.08)`), and spotlight cursor tracking.
  - **Maintain Anti-Slop Discipline**: Enforce zero emojis, zero green online dots, and zero version tags regardless of whether the external reference has them.

### 3. Citation & QA Traceability
- When presenting UI plans, screenshots, or opening PRs, document the inspiration `mobbin_url` as a clickable markdown citation (e.g. `Inspiration Reference: [Mobbin Screen](https://mobbin.com/...)`) so reviewers and QA can verify design fidelity against the intended benchmark.

---

## 5. Design Tokens & Visual Hierarchy

Lock design tokens in CSS variables or Tailwind config before writing markup. Ban raw arbitrary hex/px values.

### Anti-Cliche Palette Archetypes
Do not default exclusively to "Obsidian Black + Neon Cyan Glow". Choose deliberately:
1. **Monochrome Precision (Default Instrument)**: Neutral zinc/slate grounds, crisp 1px borders (`hsl(220, 15%, 20%)`), single purposeful accent (Signal Orange `hsl(24, 95%, 53%)` or Electric Cobalt `hsl(221, 83%, 53%)`).
2. **Warm Editorial (Default Marketing)**: Alabaster ground (`hsl(36, 33%, 97%)`), stone surface, espresso ink (`hsl(24, 10%, 12%)`), terracotta accent (`hsl(14, 75%, 50%)`).
3. **Deep Bronze / Architectural Charcoal**: Warm charcoal ground (`hsl(30, 8%, 10%)`), bronze borders (`hsl(38, 30%, 25%)`), warm sand text.

### Light-Mode-First Mandate & Dual-Theme Tokens
- **Default Theme is Light Mode**: All newly generated interfaces and dashboards MUST default to clean, high-contrast, modern Light Mode. Support Dark Mode gracefully via class-based theming (`class="dark"`). Ban defaulting blindly to pitch-black/obsidian interfaces unless building terminal CLIs or media streaming players.
- **Light Mode Default Tokens**:
  - Canvas / Ground: Crisp neutral off-white (`bg-zinc-50` or `bg-slate-50`). Never pure hospital white across the whole viewport.
  - Card & Container Surface: Pure crisp white (`bg-white`), bordered with subtle 1px gray (`border-zinc-200/80` or `border-slate-200/80`), elevated with soft shadow (`shadow-sm` or `shadow-[0_1px_3px_rgba(0,0,0,0.05)]`).
  - Typography: Deep charcoal/zinc primary text (`text-zinc-900`), muted secondary labels (`text-zinc-500`).
  - Interactive Accents: Rich cobalt blue (`bg-blue-600 hover:bg-blue-700 text-white`), electric indigo (`bg-indigo-600`), or violet.
- **Dark Mode Support Tokens**:
  - Ground: Deep charcoal (`dark:bg-zinc-950`).
  - Surface: Elevated dark surface (`dark:bg-zinc-900`), subtle border (`dark:border-zinc-800`).
  - Typography: Crisp white primary (`dark:text-zinc-100`), muted secondary (`dark:text-zinc-400`).
- **Accessible Theme Toggle**: Every application MUST provide a clean, accessible Theme Toggle button (Sun / Moon vector SVG) in the Navbar utility area to seamlessly switch between Light and Dark modes.

### Tinted Ground & Radius Formula
- **Ground is never white, ink is never black**:
  - Light mode: Ground `hsl(210, 20%, 98%)`, Surface `hsl(0, 0%, 100%)`, Ink Primary `hsl(215, 25%, 12%)`, Ink Muted `hsl(215, 15%, 45%)`.
  - Dark mode: Ground `hsl(220, 25%, 8%)`, Surface `hsl(220, 20%, 12%)`, Ink Primary `hsl(210, 20%, 95%)`, Ink Muted `hsl(215, 15%, 60%)`.
- **Radius Nesting Formula**: Inner element radius must nest harmoniously inside outer container radius:
  `r_inner = max(0, r_outer - padding)`.

---

## 6. Strict Vector Iconography, App Favicon & Typography Discipline

1. **Zero Unicode Emojis**: Absolute ban on emojis (🚀, 💡, 🔥, ⚙️) as interface icons, navigation items, or statuses. Always use clean inline SVGs or vector icon sets (Lucide, Radix, Heroicons) with explicit sizes (`width={20} height={20}`) and `flex-shrink: 0`.
2. **Semantic Icon Discipline**: Ban decorative filler icons in card corners. Every icon must carry clear, functional semantic meaning.
3. **Dedicated App Favicon Standard**:
   - Every web application MUST define an authentic, system-matched vector Favicon in `<link rel="icon" type="image/svg+xml" href="...">` or `/favicon.svg`.
   - The favicon must visually reflect the specific application domain (e.g. Queue -> ticket/flow icon; Finance -> ledger/vault icon; Logistics -> box/route icon; Analytics -> spark/chart icon) instead of generic defaults or missing favicon errors.
4. **Cohesive System-Matched Iconography & Bespoke Brand Logo**:
   - All icons in an app must share a uniform style and family (Lucide, Heroicons, or Radix vector SVGs) with matching stroke width (`stroke-[1.75]` or `stroke-2`) and consistent sizing (`size-4` for compact, `size-5` for nav/buttons, `size-6` for headers).
   - **App Brand Logo**: Every app must feature a bespoke vector SVG icon matching the system identity, beautifully housed in a rounded squircle container (e.g. `rounded-xl bg-blue-600/10 text-blue-600 dark:bg-blue-500/20 dark:text-blue-400 p-2.5 shadow-sm`).
5. **Directional Delta Accuracy**: Decreases, savings, and latency drops MUST use downward indicators (`-` or `down-arrow SVG`). Never use upward arrows for reductions. Increases and earnings use upward indicators (`+` or `up-arrow SVG`).
6. **Readable Line Length (Prose Clamping)**: Long-form text and subtitles MUST clamp to readable line lengths (`max-w-prose` / 65–75ch). Never allow paragraphs to stretch unconstrained across 1920px viewports.
7. **Motion Physics & Spring Curves**:
   - Modal reveals & entrances: `transition: transform 300ms cubic-bezier(0.16, 1, 0.3, 1), opacity 250ms ease-out;`
   - Micro-interactions (hover, press): `transition: all 150ms cubic-bezier(0.2, 0.8, 0.2, 1);`
   - Ban linear or uncurved transitions.
8. **Complete 4-State Micro-Interactions**:
   Interactive controls MUST define: (1) **Idle**, (2) **Hover** (lift `-1px`, brightness +5%), (3) **Active** (depression `+0.5px`, scale `0.98`), and (4) **Focus-Visible** (`ring-2 ring-primary ring-offset-2`).

---

## 7. Defensive Engineering & State Architecture (Pocock Discipline)

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

## 8. Anti-Slop Production Guards & Form Discipline

1. **Zero-Status-Badge, Zero-Tech-Stack & Zero-Version-Clutter Rule**:
   - **Absolute ban on green online status dots** (`🟢`, `bg-emerald-500 rounded-full`, pulsing dots), connection status pills (e.g. "SignalR Connected", "WebSocket Live", "Online", "Connected", "Memory Engine Active", "FastAPI Dev", "Port 3000", "Live"), and arbitrary dot prefixes on section titles (e.g., ban `● คิวประจำโต๊ะบริการนี้`).
   - **Absolute ban on App Version tags & Tech Stack disclosures on UI**: Never render app version pills (e.g., `v1.0`, `v0.9.4`, `v2.0-beta`), build numbers, or framework/tech stack badges (e.g. "Powered by Next.js", "Built with .NET 10 + Angular", "FastAPI Backend", "Tailwind CSS", "Supabase Cloud") anywhere in user-facing headers, navbars, cards, hero banners, or footers.
   - **Rationale**: Real-time connectivity must work silently and defensively. Tech stack details, architecture specs, and release versions belong strictly in `README.md` and repository documentation. Exposing infrastructure telemetry or bragging about framework versions on UI degrades enterprise credibility and makes software look like an amateur tutorial project.
   - Replace exclusively with authentic application navigation, clean user switchers, and command palettes (`Ctrl+K`).
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
8. **Professional 3-Zone Navbar Layout Architecture**:
   - **Strict ban on messy, cluttered navbars**: Never cram version tags (`v1.0`), marketing taglines, or connection status dots into the navigation header.
   - All Navbars must follow the **3-Zone Clean Architecture**:
     - **Zone 1 (Brand - Left)**: App Logo Icon (bespoke vector SVG in a polished rounded squircle container) + App Name (`font-semibold tracking-tight text-zinc-900 dark:text-zinc-100 text-base`). Keep it clean and unburdened.
     - **Zone 2 (Navigation / Workspaces - Center)**: Clean segmented controls, tabs, or link items with subtle active pill highlight, uniform padding (`px-3 py-1.5`), explicit heights, and `whitespace-nowrap`.
     - **Zone 3 (Utilities & Actions - Right)**: Theme toggle switch (Light/Dark Sun/Moon SVG), Search trigger (`Ctrl+K`), Notifications, User profile/avatar, or Primary Action CTA. Perfectly aligned vertically (`items-center gap-3`), zero clutter, zero connection status dots.
   - **Navbar Dimensions & Glassmorphism**: Explicit height (`h-14` [56px] or `h-16` [64px]), sticky positioning (`sticky top-0 z-50`), subtle bottom border (`border-b border-zinc-200/80 dark:border-zinc-800/80`), and backdrop blur (`bg-white/80 dark:bg-zinc-950/80 backdrop-blur-md`).

---

## 9. Thai & Multilingual Typography & Button Layout Discipline

1. **Button Single-Line Law & Mandatory `whitespace-nowrap`**:
   - Interactive controls (buttons, tabs, filter pills, dropdown triggers) MUST enforce `whitespace-nowrap` (or `white-space: nowrap`).
   - **Never wrap button text into 2 or 3 lines** while adjacent buttons in the same row/toolbar remain single-line.
   - If text length is substantial, expand the button width naturally (`w-auto min-w-fit`) or wrap the whole toolbar gracefully with `flex-wrap gap-2`.
2. **Uniform Height in Action Groups & Toolbars**:
   - All buttons sharing a row, toolbar, or modal footer MUST share an **explicit, identical height** (e.g. `h-9` [36px], `h-10` [40px], or `h-11` [44px]) and `inline-flex items-center justify-center`.
   - Never allow one button to balloon vertically due to longer text, creating ragged, uneven heights.
3. **No Parenthetical Bilingual Clutter in Button Labels**:
   - When the interface language is Thai, **strictly ban appending English translations in parentheses inside button labels** (e.g. ban `เริ่มการเทรน (Train)` -> use clean `เริ่มการเทรน`; ban `จำลองจุดรบกวน (Inject Outliers)` -> use `จำลองจุดรบกวน`).
   - Stuffing English in parentheses doubles text width, destroys responsive layouts, and causes catastrophic multi-line wrapping.
   - For English translations, use clean HTML tooltips (`title="Inject Outliers"`) or use an authentic language toggle switch (`TH | EN`).
4. **Thai Font Metric & Baseline Discipline (Zero Clipped Tone Marks)**:
   - **Line-Height Guard**: Absolute ban on `leading-none` or `leading-tight` (line-height < 1.4) on Thai text. Thai vowels (สระบน/ล่าง: ิ, ี, ุ, ู) and tone marks (วรรณยุกต์: ่, ้, ๊, ๋) require vertical clearance. Always use `leading-normal` (1.5) or `leading-relaxed` (1.625) to prevent clipped marks.
   - **Tracking Guard**: Absolute ban on negative letter-spacing (`tracking-tight`, `tracking-tighter`, `letter-spacing: -0.025em`) on Thai strings. Negative tracking causes Thai vowels and tone marks to collide and shift baselines awkwardly. Use `tracking-normal`.
   - **Icon + Thai Text Alignment**: Always pair vector SVGs with Thai text using:
     ```html
     <button class="inline-flex items-center justify-center gap-2 h-10 px-4 rounded-lg whitespace-nowrap text-sm leading-normal">
       <svg class="size-4 shrink-0" ...></svg>
       <span>ข้อความภาษาไทย</span>
     </button>
     ```
     `shrink-0` on the SVG prevents icon distortion, and `items-center leading-normal` keeps the text and icon perfectly centered on the exact same baseline.
5. **Modern Thai Font Stack**:
   - Specify high-legibility Thai web fonts before generic fallbacks:
     `font-family: 'Prompt', 'Sarabun', 'Noto Sans Thai', system-ui, -apple-system, sans-serif;`

---

## 10. Pre-Flight Visual Reasoning Checklist

Before marking any UI task complete, verify:
- [ ] **Mobbin Visual Intelligence**: Layout composition, bento arrangement, or visual hierarchy grounded in real-world benchmark references via Mobbin MCP (when available).
- [ ] **Rule 01 (Hierarchy)**: Exactly 1 primary CTA per view; secondary/supporting actions clearly demoted.
- [ ] **Rule 02 (Limit Colors)**: Palette restricted to 1 primary accent + 1 secondary tint + neutral grounds (0 rainbow clutter).
- [ ] **Rule 03 (Consistent Typography)**: Strict disciplined type scale, 1 cohesive font family, tabular numbers for data.
- [ ] **Rule 04 (Design for Scanning)**: 3-second comprehension law met; key metrics prominently pop out.
- [ ] **Rule 05 (Whitespace as Structure)**: Generous padding and margins applied (`p-6` cards, `gap-6` to `gap-8` sections); 0 cramped layouts.
- [ ] **Crafted Elegance (Centerpiece)**: Visual Centerpiece present in Hero (Three.js 3D ambient canvas, rotating geometric wireframe, or interactive IDE/Terminal sandbox).
- [ ] **Crafted Elegance (Typography)**: Typography uses `Plus Jakarta Sans` with `tracking-[-0.03em]` on display headlines, gradient text masking in Dark Mode, and `JetBrains Mono` for code/numbers.
- [ ] **Crafted Elegance (Atmosphere)**: Dark Mode incorporates ambient lighting, subtle aurora glow, and top-edge specular highlights (`border border-white/[0.08] shadow-[inset_0_1px_0_0_rgba(255,255,255,0.08)]`).
- [ ] **Crafted Elegance (Glass & Spotlight)**: Bento grid cards implement spotlight cursor tracking (`--mouse-x`, `--mouse-y`) and multi-layered glass badges for icons.
- [ ] **Crafted Elegance (Brand Icons)**: Official developer brand SVG vectors used for toolings and runtimes.
- [ ] UI defaults to clean, high-contrast Light Mode (`bg-zinc-50`, `bg-white`) with Dark Mode support and an accessible Theme Toggle button.
- [ ] 0 green online status dots, pulsing connection pills, or developer badges (e.g. "SignalR Connected", "WebSocket Live", "Online") in user-facing UI.
- [ ] 0 arbitrary dot prefixes in section titles (e.g. ban `● คิวประจำโต๊ะบริการนี้`).
- [ ] 0 app version badges (e.g. "v1.0", "v2.0-beta") and 0 tech stack disclosures (e.g. "Powered by Next.js", "FastAPI Backend", "Tailwind CSS") on user-facing UI.
- [ ] Navbar adheres to the professional 3-Zone Architecture (Brand left, Navigation center, Utilities & Theme toggle right) with 0 marketing subtitle clutter.
- [ ] Application features a bespoke vector SVG Logo and dedicated domain-matched Favicon (`<link rel="icon" ...>`).
- [ ] All icons use a cohesive vector family (Lucide / Heroicons) with uniform stroke width and sizing.
- [ ] 0 buttons wrapping text into multi-line while siblings are single-line (`whitespace-nowrap` enforced).
- [ ] All buttons in the same toolbar/action group share identical explicit height (`h-9` or `h-10`) and baseline alignment.
- [ ] 0 parenthetical English clutter in Thai button labels (e.g. `เริ่มการเทรน` over `เริ่มการเทรน (Train)`).
- [ ] 0 `leading-none` / `leading-tight` or negative `tracking-tight` applied to Thai text (0 clipped tone marks, 0 baseline displacement).
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
