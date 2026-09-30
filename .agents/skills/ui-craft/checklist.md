# UI checklist (Step 3 critique / Phase 4 review)

Report only failures, ranked, one line each with file:line or screenshot region.

**Direction**
- [ ] Design plan exists in PLAN.md (subject, palette, type, wireframe, signature)
- [ ] No item from `generic-tells.md` without a brief-based reason
- [ ] One signature element; everything around it quiet
- [ ] One accessory removed after the first screenshot

**Structure**
- [ ] One Primary CTA per view/dialog
- [ ] Key status readable in < 3s
- [ ] Borders, labels, numbering, badges each encode real information
- [ ] Radius and elevation vary by hierarchy, not uniform everywhere

**Tokens**
- [ ] No raw hex/px in components
- [ ] Palette matches the plan; semantic colors only for state; color never the only signal
- [ ] Type from the scale; lines < 75ch; tabular numerals on data

**Copy**
- [ ] Buttons name the action; the same action keeps its name through the flow
- [ ] Errors say what happened and how to fix; empty states invite one action
- [ ] Real content, no lorem, no slogans (EN or TH)

**States & motion**
- [ ] Skeletons, empty, error states present; dynamic text truncates safely
- [ ] Destructive actions separated + 2-step confirm with Cancel
- [ ] 4 interaction states + visible focus; at most one ambient motion moment; reduced-motion respected

**Thai**
- [ ] Latin-first font stack with a Thai body font; `lang="th"`
- [ ] Thai line-height ≥ 1.5–1.6; no negative tracking; clipped containers padded; no tone marks cut in screenshot
- [ ] `nowrap` only on short controls; no parenthetical English

**Components & anti-slop**
- [ ] Buttons in a row share height, single-line
- [ ] Navbar 3 zones, nothing extra; modal dismissal rules followed
- [ ] 0 emoji icons, status pills, version/tech badges, dot-prefixed titles, dev commentary

**Verification (AGENTS.md)**
- [ ] 375 / 768 / 1280px checked; 0 console errors; 1 proof screenshot reported
