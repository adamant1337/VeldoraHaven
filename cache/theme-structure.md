---
type: cache
status: active
source_of_truth:
  - shopify/SHOPIFY-THEME-INTEGRATION.md
  - shopify/LIVE-LOCAL-RECONCILIATION.md
  - theme/ (actual files where deeper detail is required)
ttl: 30 days
last_verified: 2026-08-22
invalidate_when:
  - theme structure changes
  - a major theme pull occurs
  - Shopify Horizon version changes
  - a major architectural refactor occurs
---

# Purpose

Compact retrieval aid so agents can orient in the VeldoraHaven theme without reading the
whole repo. **Not a source of truth** — see `source_of_truth` above.

# Verified State

**Identity** (verified vs Admin API + local files, 2026-08-22)
- Working draft theme: **VeldoraHaven — v28 Vendor + Footer** · ID **205283819862** (UNPUBLISHED)
- Live/published reference: ID **205129482582** ("Copy of VeldoraHaven — v27")
- Base: **Shopify Horizon 3.5.1** (OS 2.0, block-based)
- Local path: `C:\VeldoraHaven\theme` · git branch baseline: `fix/reconcile-local-live` (commit `1765603`)
- CLI store: `iqeb6u-5h.myshopify.com` (envs in `theme/shopify.theme.toml`)

**File counts** (approx): sections 51 · snippets 104 · blocks 93 · assets 117 · templates 13 · locales 51 · layout 2 · config 2.

**VH custom sections** (10, `sections/vh-*.liquid`): `vh-category-cards`, `vh-trust-bar`,
`vh-how-it-works`, `vh-journal`, `vh-brand-story`, `vh-product-spec`, `vh-collection-hero`,
`vh-collection-guide`, `vh-editorial`, `vh-category-links`. Custom snippet: `vh-coming-soon.liquid`.

**Key custom CSS/JS** (4, `assets/veldora-*`): `veldora-custom.css` (18.4 KB — brand layer,
injected at `layout/theme.liquid:34`), `veldora-footer.css`, `veldora-mobile.css` (luxury
mobile nav), `veldora-reveal.js` (scroll reveal).

**Important templates** (JSON/OS 2.0): `index` (custom vh-* homepage), `product` (+ vh-product-spec),
`collection` (+ filters), `cart`, `blog`/`article`, `page` + `page.contact`, `search`, `list-collections`, `404`, `password`, `gift_card.liquid`.

**Important snippets** (stock Horizon): `meta-tags`, `theme-styles-variables`, `fonts`,
`color-schemes`, `product-media-gallery-content`, `search-modal`, `header-actions`.

**Important config**: `config/settings_data.json` (color schemes, logo `shopify://shop_images/VeldoraHaven_Logo_Header.png`,
announcement, radius/borders/shadows = 0), `config/settings_schema.json` (theme_name Horizon 3.5.1).
App block: **CookieYes** consent embed (only material app block).

**High-risk areas** (change deliberately; review required): `layout/theme.liquid`,
`config/settings_schema.json` / `settings_data.json`, stock Horizon core `sections/` &
`blocks/` (header/footer/cart/product), `assets/base.css`, `locales/*`.

**Safe / common areas**: `assets/veldora-*.css|js` (isolated brand layer), the `vh-*` custom
sections/snippets, page-content JSON templates, section settings via theme editor.

# Agent Usage

Read this cache first to answer "what/where" questions (theme id, custom sections, file
homes, risk level). Only open the source-of-truth docs or actual theme files when the task
needs deeper detail, the cache is expired, or a high-risk change requires verification.

# Invalidation Rules

Refresh **only this cache** when any `invalidate_when` trigger fires (esp. after a
`shopify theme pull`). Re-verify counts + custom-file lists against `theme/` and bump
`last_verified`. Do not refresh unrelated caches.
