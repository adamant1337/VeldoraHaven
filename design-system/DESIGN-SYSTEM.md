# VeldoraHaven — Design System

Authoritative for design **tokens** and component/pattern conventions. Brand meaning &
voice live in [`brand/BRAND.md`](../brand/BRAND.md). Owned by
`veldorahaven-visual-designer` (with `veldorahaven-component-builder` for component APIs).

> ✅ **AUTHORITATIVE (R0, 2026-08-22):** tokens below are extracted from the **live/v28
> theme** via the Admin API — `assets/veldora-custom.css` (v28, 18.4 KB), `veldora-footer.css`,
> `veldora-mobile.css`, `config/settings_data.json` of theme `205283819862` (v28 working
> draft; live `205129482582` is near-identical). Verify against files after the CLI pull
> ([`../shopify/THEME-DEV-WORKFLOW.md`](../shopify/THEME-DEV-WORKFLOW.md)). Never invent.

## Principles

Restrained, editorial, architectural. Strong type hierarchy, deliberate whitespace,
minimal ornament, sharp corners (radius 0), no shadows. Purposeful motion only, with
`prefers-reduced-motion` honored. Extend this system — never fork it. The brand layer
lives in `assets/veldora-custom.css` (+ `veldora-footer.css`, `veldora-mobile.css`),
applied over stock Horizon largely via `!important` (tech debt — see below).

## Color — `--vh-*` tokens (live/v28, authoritative)

| Token | Hex | Role |
| --- | --- | --- |
| `--vh-forest` | `#1B4332` | Primary green — header, nav |
| `--vh-forest-deep` | `#0f2018` | Deepest green — drawer, footer, story panel, dark CTAs |
| `--vh-forest-mid` | `#2D6A4F` | Mid green |
| `--vh-gold` | `#C8A96E` | Accent — logo, CTA hover, links, focus ring, vendor mark |
| `--vh-gold-light` | `#dfc49a` | Gold hover-light |
| `--vh-cream` | `#F5F0E8` | Warm cream — on-dark text, hero title |
| `--vh-cream-pure` | `#FAFAF8` | Page background (body), trust bar |
| `--vh-mist` | `#EAF2EC` | Soft green tint |
| `--vh-stone` | `#2A2A22` | Body text / headings on light |
| `--vh-stone-mid` | `#4A4A40` | Secondary text, price |
| `--vh-mid` | `#7A9E87` | Muted sage |

Image tokens: `--vh-hero-img`, `--vh-story-img` (Shopify CDN URLs). Logo:
`shopify://shop_images/VeldoraHaven_Logo_Header.png` (48px / 36px mobile).

> ⚠️ **Color-scheme debt:** the theme's `settings_data.json` color schemes still carry
> Horizon **defaults** — old cream `#f7f7f5`, and **blue primary-button borders/hover
> `#000f9f`** — which are *masked* by the `!important` CSS above but are wrong underneath.
> Roadmap R10 migrates real values into the schemes and removes the override reliance.

## Typography — AUTHORITATIVE (decision 2026-08-22)

## Typography — AUTHORITATIVE (decision 2026-08-22)

- **Display / headings / editorial → `'Cormorant Garamond', Georgia, serif`** (`--vh-serif`).
  Weights 300/400/500/600 (+ italic 300/400).
- **Body / UI / supporting text → `'Inter', system-ui, sans-serif`** (`--vh-sans`).
  Theme settings: body `inter_n4` (400), subheading `inter_n5` (500).

Observed sizes/treatment: product title 32px/300; card heading 17px/400 serif; price
13px/300; nav & buttons 11px uppercase, letter-spacing 0.08–0.1em; vendor label
10px/0.12em uppercase; footer heading 10px/0.15em uppercase. Headings letter-spacing
−0.01em.

### Josefin Sans usage audit (before removal — do NOT blind-delete)

- **Named in exactly one place:** `config/settings_data.json` →
  `type_heading_font: josefin_sans_n7`. Not referenced by name in any liquid/CSS/JS.
- **But it is the live heading font engine-wide.** Horizon maps `type_heading_font` →
  `--font-heading--family` (`snippets/theme-styles-variables.liquid:164`), which is the
  default font for many blocks: `product-title`, `collection-title`, `price`, `sku`,
  `product-description`, `text`, `_announcement`, blog-post titles — plus the Shopify
  **account UI** (`--shopify-account-font-heading`). `type_font_h1: heading` (Josefin);
  `h2/h3: primary` (Inter).
- **Current reality:** `veldora-custom.css` forces Cormorant on literal `h1–h6/.heading`
  via `!important`, but block-rendered headings using the font *variable* still render
  in **Josefin** → visible inconsistency.
- **Regression risk of deleting the setting:** HIGH — headings on product/collection/
  blog cards and account pages would break/fallback. **Correct fix (P1, not now):** set
  `type_heading_font` = Cormorant Garamond at the theme level (theme editor / settings_
  data), which flows Cormorant into `--font-heading--family` everywhere, lets us drop
  most `!important` font rules, and removes the render-blocking `@import`. Owner:
  shopify-architect (setting) + liquid-engineer (CSS cleanup).

## Buttons (v28)

Radius **0**, uppercase, 10px, letter-spacing 0.16em, weight 400, padding `15px 36px`.
- **Primary = ghost:** transparent + `1px rgba(245,240,232,0.45)` border, light text →
  hover fills `--vh-gold` with `--vh-forest-deep` text.
- **Secondary:** transparent + fainter light border → hover brightens.
- **Product form submit:** `--vh-forest-deep` bg + cream text → hover `--vh-gold` bg.
- **Cart checkout:** solid `--vh-gold` bg + `--vh-forest-deep` text.

## Cards (v28)

No border, no shadow, transparent bg, radius **0**. Media radius 0 `overflow:hidden`;
image zoom on hover `scale(1.045)` / `0.7s cubic-bezier(.25,.46,.45,.94)`. Serif title
**20px / weight 300**, color `--vh-stone` → hover `--vh-forest`. Info padding `16px 0 28px`.
**Price:** labels hidden, `--vh-stone-mid` 13px/300, letter-spacing 0.1em; sale shows
struck regular at 38% opacity.

## Vendor mark (v28 — Auroom)

`.product__vendor`: Cormorant serif, 17px/300, uppercase, letter-spacing 0.12em,
`--vh-gold`, gold bottom hairline. The "Vendor" half of v28's name.

## Custom sections (live/v28)

`vh-category-cards` (4-col, 540px tiles, gradient overlay, image zoom, serif 30px names),
`vh-trust-bar` (4-col USP row on cream-pure, hairline dividers), `vh-brand-story` (2-col:
image + forest-deep text panel), `vh-how-it-works`, `vh-journal`, `vh-product-spec`
(renders `spec.*` metafields), `vh-collection-hero`, `vh-collection-guide`, `vh-editorial`,
`vh-category-links`. All responsive (2-col / 1-col at ≤768px).

## Border radius & shadows

Radius **0** globally; shadows **none**.

## Spacing & layout

- `page_width`: **`wide`**. Section padding pattern `clamp(56px,7vw,96px) clamp(20px,5vw,64px)`.
- Container max-width (spec section) `1100px`. Base spacing = Horizon defaults (`TBD`).

## Breakpoints

Custom CSS breakpoints: **768px** (grids → 2/1 col) and **749px** (mobile nav/hero/footer).
Horizon defaults otherwise.

## Motion (v28)

Card/category image zoom; nav underline slide-in (gold, 0.28s); scroll reveal
(`.vh-reveal`, translateY 28px + fade, 0.7s, staggered delays). **`prefers-reduced-motion`
disables all** transforms/reveals. Hero = full-bleed image with dark gradient overlay,
centered light serif title.

## Focus / a11y treatment

`:focus-visible` → `1px solid --vh-gold`, offset 3px. Custom scrollbar 3px. Mobile: custom
gold hamburger with "MENU" label, editorial serif drawer links (28px) on `--vh-forest-deep`.

## Components (conventions)

Reusable, configurable (theme-editor schema), responsive, accessible, performant. Build
once, parameterize, reuse — no near-duplicate variants. Custom `vh-*` sections above +
stock Horizon components (header, cart drawer, predictive search, product-list, facets).
Each component's public API (settings/blocks) is documented by the component-builder.

## Accessibility & mobile floor

WCAG 2.1 AA contrast on all role pairs; visible focus; comfortable touch targets; mobile
must feel as premium as desktop. Enforced by the accessibility & mobile specialists.

## Status

- [x] Real tokens/components extracted from live/v28 via Admin API (2026-08-22).
- [ ] Verify against files after CLI pull of v28; confirm Horizon spacing base unit.
- [ ] Resolve Cormorant vs Josefin heading-font conflict (R1) + color-scheme debt (R10).
- [x] Logo recorded: `shopify://shop_images/VeldoraHaven_Logo_Header.png`.
