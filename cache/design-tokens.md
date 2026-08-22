---
type: cache
status: active
source_of_truth:
  - design-system/DESIGN-SYSTEM.md
  - brand/BRAND.md
  - theme/assets/veldora-custom.css (implementation)
ttl: 30 days
last_verified: 2026-08-22
invalidate_when:
  - design-system/DESIGN-SYSTEM.md changes
  - brand/BRAND.md changes
  - theme token implementation (veldora-*.css) changes
---

# Purpose

Compact digest of the verified VeldoraHaven design tokens for quick reuse. **Not a source
of truth** — see above. All values verified against `theme/assets/veldora-custom.css` (v28).

# Verified State

**Colors — `--vh-*`** (from veldora-custom.css, v28)
- `--vh-cream-pure #FAFAF8` — page background (body)
- `--vh-cream #F5F0E8` — warm cream; on-dark text, hero title
- `--vh-forest #1B4332` — primary green (header, nav)
- `--vh-forest-deep #0f2018` — deepest green (drawer, footer, story panel, dark CTAs)
- `--vh-forest-mid #2D6A4F` · `--vh-mid #7A9E87` (sage) · `--vh-mist #EAF2EC`
- `--vh-stone #2A2A22` — body text / headings on light
- `--vh-stone-mid #4A4A40` — secondary text, price
- `--vh-gold #C8A96E` — accent (logo, CTA hover, links, focus ring, vendor mark)
- `--vh-gold-light #dfc49a` — gold hover

**Typography**
- Heading/display: **Cormorant Garamond** (`--vh-serif`), light (200–300), letter-spacing −0.02em
- Body/UI: **Inter** (`--vh-sans`), 300/400/500; body 16px / line-height 1.75
- Authoritative decision: Cormorant = headings, Inter = body (ADR-0005)

**Component tokens**
- Radius: **0** everywhere · Shadows: **none** · Card border: none
- Buttons: uppercase 10px, letter-spacing 0.16em; **primary = ghost** (transparent + light
  border) → fills gold on hover; product submit = forest-deep → gold; cart checkout = solid gold
- Cards: serif title 20px/300; image zoom `scale(1.045)` / 0.7s
- Focus: `1px solid --vh-gold`, offset 3px · Section padding `clamp(56px,7vw,96px) clamp(20px,5vw,64px)`; spec container max 1100px
- Breakpoints (custom CSS): 768px (grids) · 749px (mobile nav/hero/footer)

**Visual language**: premium · editorial · architectural · luxury outdoor living. Cream
canvas + deep-forest chrome + gold accents; sharp corners; serif display over sans body;
restrained motion (scroll reveal, nav underline) honoring `prefers-reduced-motion`.

# Important Implementation Notes

- Brand layer applied over stock Horizon largely via **`!important`** (tech debt).
- **Color-scheme debt (R10):** `config/settings_data.json` schemes still carry Horizon
  **defaults** — legacy **blue** primary-button border/hover `#000f9f` (12×) and old cream
  `#f7f7f5` (3×) — **masked by the `!important` CSS above**, not reflected on the storefront.
- **Heading font at theme level is unset in v28** `settings_data.json` (no font overrides →
  Horizon schema defaults `anonymous_pro_n4` heading/accent, `work_sans_n4/n5` body). Cormorant
  is applied only via the custom-CSS `!important` layer (Google-hosted, weights 200–600).
- **R1 VERDICT (2026-08-22): authoritative typography = the custom-CSS layer; NO change made.**
  Do NOT set `type_heading_font` = Cormorant via font_picker: Shopify's library Cormorant lacks
  the 200/300 ultralight weights the brand uses (hero/product-title/story), and it would double-
  load fonts on top of the required Google `@import`. The theme-default mismatch is masked (mirror
  of R10 color debt), not a visible inconsistency. Cormorant/Inter render consistently across
  homepage, collection, PDP, cart, nav, headings, buttons, editorial. No Josefin remains (stale).

# Agent Usage

Visual/component/mobile agents read this before touching styling. Use these exact values;
do not re-derive from CSS unless the cache is expired or a value is contested.

# Invalidation Rules

Refresh **only this cache** on an `invalidate_when` trigger; re-verify against
`veldora-custom.css` + DESIGN-SYSTEM.md and bump `last_verified`. Never invent tokens.
