# UI Component Standards

Specifications for core interface components ensuring consistency, defensive UX, and high cognitive speed.

## 1. Buttons & Actions
- **Primary CTA**: Exactly one prominent action per view or dialog (`bg-accent text-accent-ink`).
- **Secondary & Ghost**: Subdued supporting actions using subtle border (`border border-border`) or transparent background (`hover:bg-surface-hover`).
- **Height & Padding**: Uniform heights across button rows (`h-9` or `h-10`). Minimum click target ≥ 40px for mobile ergonomics.
- **Loading State**: Button displays inline spinner and retains fixed width; disables pointer events (`pointer-events-none opacity-80`).

## 2. Navigation Bar
- **3-Zone Layout**:
  - Left: Brand mark / SVG logo + title
  - Center: Primary route navigation pills
  - Right: Utilities, theme toggle, and user profile / actions
- **Sticky & Blurred**: Fixed height (`h-14` or `h-16`), sticky with subtle backdrop blur (`backdrop-blur-md bg-ground/80 border-b border-border`).
- **Anti-Slop**: No version tags, no framework badges, no green pulsating "connected" dots.

## 3. Modals & Dialogs
- **Triple Dismissal**: Must close via top-right close icon, backdrop overlay click, and `Escape` key press.
- **Action Grouping**: Primary action and explicit Cancel button placed side by side.
- **Destructive Actions**: Placed in a separate visual zone; require 2-step confirmation with destructive styling (`bg-danger text-white`).

## 4. Data Tables & Lists
- **Density & Legibility**: Pinned header row (`sticky top-0 bg-surface`), subtle row divider (`border-b border-border`), tabular numbers for all numeric/monetary columns.
- **Horizontal Scrolling**: Wrapped in responsive overflow container with sticky first column (ID or Key Entity).
- **Mobile Fallback**: Below 768px, gracefully switch from wide table to stacked card view.

## 5. Form Controls & Inputs
- **Explicit Labels**: Every input has a visible label (`text-xs font-medium text-ink-muted`) and clear placeholder.
- **Numeric Inputs**: Allow empty string while typing instead of aggressively resetting to `0`.
- **States**: Defined visual styles for idle, hover, active, focus-visible (`ring-2 ring-accent/30`), and error (`border-danger`).
- **Native Selects & Date Pickers**: Apply theme-aware styling and set `color-scheme: light dark` so native picker overlays match application theme.
