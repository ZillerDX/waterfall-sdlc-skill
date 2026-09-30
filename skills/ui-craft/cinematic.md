# Cinematic signature elements

A Cinematic page gets exactly one signature — the memorable thing — and everything else stays quiet. The hero opens with the most characteristic thing in the subject's world, in whatever form fits: a headline set as an active typographic object, a real product view, an image, a live demo, an interaction.

## Pick one signature
- **Type as the image:** oversized display set with intent (scale, weight, width, cropping) — no accented single word.
- **Real product:** an actual, interactive slice of the product with real data.
- **Subject artifact:** a rendered object from the subject's world (a ticket, a chart tape, a receipt, a floor plan).
- **One orchestrated motion:** a single page-load sequence or scroll reveal that explains something.
- **3D:** only if the subject is spatial or the user asked (rules below).

Then check: is the signature specific to this brief, or one of the tells in `generic-tells.md`?

## Atmosphere (use at most one, only if it supports the signature)
- Subtle texture or grid drawn from the subject.
- A single soft light source behind the signature in dark mode.
- A top-edge inset highlight on floating panels in dark mode (`inset 0 1px 0 rgb(255 255 255 / 0.06)`).

Glassmorphism, spotlight cursor glow, gradient text, button shimmer, and glow shadows are listed tells — use only when the brief asks.

## Three.js rules (when 3D is justified)
- ES module import at a pinned version (verify via context7); the legacy `three.min.js` build isn't shipped in current releases.
- Lazy-load after first paint; pause off-screen and when the tab is hidden; cap devicePixelRatio at 2; dispose on unmount.
- Colors from tokens; update on theme change.
- `prefers-reduced-motion` → one static frame or a poster image.
- The page must be fully readable without the canvas.

## Composition
- Break the grid once, deliberately, at the signature. Elsewhere, align rigorously.
- Vary section rhythm (full-bleed, narrow text column, dense detail) instead of repeating one card block.
- Left alignment for reading content; centering only for short, isolated statements.
