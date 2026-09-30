# Tokens

Verify framework class names against the installed Tailwind major via context7. Tokens are framework-neutral CSS custom properties.

## Deriving the palette (no fixed default)

1. List 3–5 materials, objects, or documents from the subject's world.
2. Pull 4–6 named hex values from them: ground, surface, ink, muted ink, accent, optional second accent.
3. Check: ink/ground ≥ 7:1 for body, muted ≥ 4.5:1, accent on ground ≥ 3:1 for UI.
4. Semantic colors (success/warning/danger/info, `--up`/`--down`) are separate and tuned to sit with the palette.
5. Dark mode is re-derived (lower-chroma surfaces, slightly desaturated accent), not a simple invert. Dark ground is never `#000`.
6. Check the result against `generic-tells.md` palettes.

## Token structure (values are placeholders — replace from the plan)

```css
:root {
  --ground: #…; --surface: #…; --border: #…;
  --ink: #…; --ink-muted: #…;
  --accent: #…; --accent-ink: #…;           /* text on accent */
  --success: #…; --warning: #…; --danger: #…;
  --up: var(--success); --down: var(--danger);
  --radius-control: 6px; --radius-card: 12px; --radius-panel: 16px;
  --space-1: 4px; --space-2: 8px; --space-3: 12px; --space-4: 16px;
  --space-6: 24px; --space-8: 32px; --space-12: 48px; --space-16: 64px;
}
.dark { /* re-derived values */ }
```

## Type scale

| Role | Instrument | Cinematic |
|---|---|---|
| Display | 24–30px | `clamp(2.5rem, 5vw, 4.5rem)` or larger if type is the signature |
| Section heading | 18–20px, 600 | 24–32px |
| Body / controls | 14px (16px on mobile inputs) | 16–18px |
| Caption / meta | 12px, `--ink-muted` | 13–14px |

Ratio-based scales (1.2 Instrument, 1.25–1.333 Cinematic) keep steps coherent. Serif body gets slightly more line-height than sans. Latin display may use −0.02 to −0.035em tracking; never Thai (see `thai.md`).

## Radius follows hierarchy

Different radius per level (control < card < panel), not one radius on everything. Nested: `r_inner = max(0, r_outer − padding)`. Zero radius is a valid choice when it fits the subject.

## Shadows

Elevation only where something truly floats (menus, dialogs, popovers). Resting cards separate with border or background step, not a shadow on each.

## Motion

```css
--ease-out: cubic-bezier(0.16, 1, 0.3, 1);   /* entrances, dialogs: 200–300ms */
--ease-snappy: cubic-bezier(0.2, 0.8, 0.2, 1); /* press/toggle: 120–150ms */
@media (prefers-reduced-motion: reduce) {
  *, *::before, *::after { animation-duration: 0.01ms !important; transition-duration: 0.01ms !important; }
}
```

Interactive controls define idle, hover, active, focus-visible. Hover feedback is subtle (color/background step), not a lift on everything.

## Theme toggle

Instrument apps: in the navbar utility zone, initial from `prefers-color-scheme`, persisted. Cinematic: optional.
