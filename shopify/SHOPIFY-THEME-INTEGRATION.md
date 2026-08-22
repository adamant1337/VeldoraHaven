# VeldoraHaven — Shopify Theme Integration

**Authoritative document for how the AI system interacts with the real Shopify theme.**
Audit date: 2026-08-22 (read-only). Governance rules:
[`../architecture/MASTER-ARCHITECTURE.md`](../architecture/MASTER-ARCHITECTURE.md).
Design tokens live in [`../design-system/DESIGN-SYSTEM.md`](../design-system/DESIGN-SYSTEM.md);
brand in [`../brand/BRAND.md`](../brand/BRAND.md).

## ⚠️ SOURCE OF TRUTH (updated R0, 2026-08-22)

**The LIVE published theme `205129482582` ("Copy of VeldoraHaven — v27") + Shopify
product metafields (`spec.*`) are authoritative.** The local clone and GitHub below are a
**stale 2026-08-02 snapshot** and are NOT the live site. Full analysis + reconciliation
plan: [`LIVE-LOCAL-RECONCILIATION.md`](LIVE-LOCAL-RECONCILIATION.md). Do not push local →
live; reconcile by pulling live → local first.

## Theme root & repository

| | |
| --- | --- |
| **Working copy (edit here)** | `C:\VeldoraHaven\theme\` |
| **Git remote** | `https://github.com/adamant1337/VeldoraHaven1.git` |
| **Branch** | `main` |
| **HEAD at clone** | `15eba70` — 2026-08-02 "Add LakeSaunaHeroPicture hero" |
| **Source of clone** | GitHub (verified identical to OneDrive canonical copy) |
| **Canonical OneDrive copy (DO NOT EDIT)** | `C:\Users\peter\OneDrive\Skrivebord\Shopify Theme Veldora\VeldoraHaven1\` |
| **Base theme** | Shopify **Horizon v3.5.1** (block-based / OS 2.0) |
| **Files** | 455 tracked |

> Do not edit the OneDrive copy or the surrounding `epiccard` repo. All AI work happens
> in `C:\VeldoraHaven\theme\`.

## Store connection & deployment

- **Shopify CLI:** installed, v3.94.3 (npm global). **No cached auth** — not logged into
  a store; store identity is not locally known.
- **No local theme link** (`.shopify/`, `shopify.theme.toml` absent).
- **Deployment is via the Shopify↔GitHub integration**, evidenced by auto-commits
  `"Update from Shopify for theme VeldoraHaven1/main"` in history. Pushing to GitHub
  `main` is what reaches Shopify — treat `main` as production-linked.

## Theme structure

`layout/ 2 · templates/ 18 · sections/ 42 · snippets/ 120 · blocks/ 95 · assets/ 124 ·
config/ 2 · locales/ 51`

- **Templates (JSON, OS 2.0):** index, product, collection, cart, blog, article, page,
  search, list-collections, 404, password, gift_card (liquid), plus page variants:
  about, contact, faq, how-it-works, returns, shipping.
- **Major sections:** hero, slideshow, layered-slideshow, marquee, media-with-content,
  featured-product, product-information, product-list, product-recommendations,
  product-hotspots, collection-list, collection-links, header(-group/-announcements),
  footer(-group/-utilities), cart-drawer-section, main-* (product/collection/cart/
  page/blog), predictive-search, custom-liquid.
- **Blocks:** 95 Horizon blocks, `_`-prefixed private blocks (e.g. `_card`,
  `_product-card*`, `_accordion-row`, `_collection-card`) composed inside sections.
- **Homepage (index.json):** hero → marquee → product-lists → media-with-content →
  text — an editorial, block-composed layout.

## Custom architecture (Veldora layer on top of stock Horizon)

Customizations are deliberately **thin and isolated** — this is the key integration fact:

| File | Role |
| --- | --- |
| `assets/veldora-custom.css` | **Primary brand override layer.** Injected once at `layout/theme.liquid:34` via `{{ 'veldora-custom.css' \| asset_url \| stylesheet_tag }}`. Defines `--vh-*` tokens and restyles header, nav, buttons, cards, product title, footer, focus, scrollbar — all with `!important`. |
| `config/settings_data.json` | Color schemes (scheme-1 = cream/stone/forest matches the CSS) and theme fonts. |
| `sections/footer-group.json` | Footer group customization. |
| `assets/accordion-custom.js` | Custom accordion behavior. |
| `assets/product-custom-property.js` | Custom product property behavior. |
| `LakeSaunaHeroPicture.png` | Brand hero image (root-level). |

**Design patterns present:** sharp corners everywhere (`border-radius:0`), no card
borders/shadows, uppercase micro-labels with wide letter-spacing, serif display type
over sans body, gold-on-forest primary buttons, subtle card image zoom on hover.

**Reusable components (stock Horizon, brand-styled):** product card (`_product-card*`
blocks + `section-rendering-product-card`), cards, cart drawer, predictive search,
accordions, slideshows, product-list.

## Known technical debt / risks

1. **Font conflict (medium):** theme settings set headings to **Josefin Sans 700**
   (`type_heading_font: josefin_sans_n7`), but `veldora-custom.css` force-overrides
   h1–h6/.heading to **Cormorant Garamond** via `!important`. Effective headings are
   Cormorant, but any heading element not caught by the override selectors will fall
   back to Josefin Sans → inconsistency. Decide one heading font and align settings +
   CSS.
2. **`!important` saturation (medium):** the entire brand layer relies on `!important`.
   It works but is brittle against Horizon updates and hard to override locally. Prefer
   migrating brand values into Horizon color-scheme/typography settings where possible.
3. **Cormorant loaded via `@import` from Google Fonts (low–medium perf):** blocking
   `@import` at top of CSS; a `preload`/`link` or theme font setting would be faster.
4. **GitHub = production link (high caution):** commits to `main` can reach the live
   store via the integration. Use branches + explicit user approval before touching
   `main`.
5. **OneDrive/nested-repo hazard (contained):** canonical copy sits inside an unrelated
   `epiccard` git repo on OneDrive. We work only in the clean `C:\VeldoraHaven\theme\`
   clone, so this no longer affects us — do not reintroduce it.

## Safe modification areas vs high-risk files

**Safer:** `assets/veldora-custom.css` (isolated override layer), new **custom sections/
snippets** we add, page-content JSON templates (about/faq/etc.), section settings via
theme editor.

**High-risk (change deliberately, review required):** `layout/theme.liquid`,
`config/settings_schema.json` / `settings_data.json`, stock Horizon `blocks/` and core
`sections/` (header/footer/cart/product), `assets/base.css`, `locales/*`. Editing stock
Horizon files complicates future theme updates.

## Agent ↔ theme ownership boundaries

| Agent | Owns (in theme) | Boundary |
| --- | --- | --- |
| brand-director | Design **direction**, `../brand/BRAND.md` | No direct Liquid edits |
| visual-designer | Visual system + component **specs**, `../design-system/` | Specifies; engineers implement |
| shopify-architect | Theme architecture & structural changes; `theme.liquid`, template/section structure, metafields, settings schema | Approves high-risk file changes |
| liquid-engineer | Liquid implementation across sections/snippets/blocks | Implements to spec; no redesign |
| component-builder | Reusable **custom** sections/snippets/components | Build-once, parameterize |
| homepage-director | `templates/index.json` + homepage sections | Homepage only |
| collection-experience | `templates/collection*.json`, collection sections/facets | Collection only |
| product-experience | `templates/product.json`, product sections/blocks | Product pages only |
| cart-aov-specialist | cart drawer/section, cart JS, merchandising | Cart + merchandising |
| mobile-specialist | Mobile audits & responsive fixes | Cross-cutting; coordinates edits |
| performance-engineer | Perf fixes (assets, `@import`, JS/CSS, images) | Cross-cutting |
| accessibility-specialist | A11y fixes (focus, ARIA, contrast, labels) | Cross-cutting |
| seo-specialist | Metadata, structured data, headings, alt text | Template/section fields |
| final-critic | Review only — APPROVE / REQUEST CHANGES / REJECT | No uncontrolled implementation |
| **orchestrator** | Coordinates conflicts, file locks (`../state/`), escalation | — |

Primary brand-styling changes route through `veldora-custom.css` (owned jointly by
visual-designer spec → liquid/component engineers), coordinated by the orchestrator via
file locks in [`../state/STATE.md`](../state/STATE.md).

## Git workflow (authoritative — ADR-0006)

`main` = **production** (GitHub↔Shopify integration). Never develop on `main`.

**Branch naming:** `feature/<task-name>` · `fix/<task-name>` · `performance/<task-name>`.

**Flow:** `TASK → BRANCH → IMPLEMENT → TEST → FINAL CRITIC → REPORT → USER APPROVAL → MERGE TO MAIN`.

1. Before work: `git status`, confirm branch/remote, record HEAD.
2. Branch off `main` using the pattern above.
3. Logically scoped commits — do **not** auto-commit every tiny change; no auto-merge.
4. **Never force-push. Never destructive reset. Never overwrite unrelated work.**
5. Merge to `main` only after explicit user approval (it reaches the live store).

## Testing workflow

- Static: `shopify theme check` (Theme Check) once CLI is authenticated; visual review
  against `../design-system/DESIGN-SYSTEM.md`; final-critic gate.
- Responsive/mobile + a11y review by the respective specialists.

## Shopify CLI workflow (when authorized)

- CLI present (v3.94.3). **Not authenticated; store unidentified.** To enable local
  preview/checks, the user must run `shopify auth login` / `shopify theme dev` in an
  interactive terminal and confirm the store.
- **Read-only until then. Do NOT push, publish, or modify the live theme.** No
  `shopify theme push --live`, no publish. Deployment currently flows through GitHub.
