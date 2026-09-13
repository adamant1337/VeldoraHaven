---
type: cache
status: active
source_of_truth:
  - theme/sections/vh-product-spec.liquid (implementation)
  - Shopify product metafields (spec.* namespace)
  - shopify/LIVE-LOCAL-RECONCILIATION.md
ttl: 14 days
last_verified: 2026-08-22
invalidate_when:
  - PDP architecture changes
  - spec.* metafields change (keys added/removed/retyped)
  - product data model changes
  - theme/sections/vh-product-spec.liquid changes
---

# Purpose

Compact map of the verified PDP data flow so agents don't re-discover it. **Not a source of
truth** — see above.

# Verified State

**Data flow**
```
PRODUCT → Shopify product data → spec.* PRODUCT METAFIELDS
        → sections/vh-product-spec.liquid (enabled_on: product; empty rows auto-hide)
        → PDP output: Specification table + Included / Not included + Delivery & installation
```

**Metafield namespace `spec.*`** (13 keys; drives the PDP):
`dim_external`, `dim_internal`, `capacity`, `materials`, `power`, `weight_kg`,
`certification`, `warranty` (→ Specification table) · `included`, `not_included`
(→ two lists, newline-split) · `lead_time`, `delivery_method`, `base_req`
(→ Delivery & installation). Types: single_line_text except `base_req/included/not_included`
= multi_line_text.

**Sections/snippets involved**: `sections/vh-product-spec.liquid` (renders spec.*), plus
stock Horizon `product-information`, `_product-media-gallery`, `product-recommendations`,
buy-buttons/variant-picker blocks in `templates/product.json`.

**Metaobjects**: none defined. **App blocks**: none on PDP (CookieYes is site-wide).

**Not part of VeldoraHaven PDP** (leftover from prior *epiccard* card-shop use — ignore):
`custom.*` product metafields (game/set/card_number/rarity/grading/etc., Danish labels).

# Authoritative vs presentation

- **Authoritative (data):** the `spec.*` product metafields in Shopify. Edit specs THERE.
- **Presentation only:** `vh-product-spec.liquid` (layout/styling of those fields).
- **NEVER manually duplicate** spec values into theme files, `products/`, or another doc —
  the metafields are the single source. `products/` may only *reference* them.

# Agent Usage

Before changing PDP behavior, agents (product-experience, liquid-engineer) read this cache
to know: specs come from `spec.*` metafields, rendered by `vh-product-spec.liquid`, empty
rows self-hide. Inspect `vh-product-spec.liquid` only for layout changes; inspect the
metafield definitions only if adding/removing a spec field.

# Invalidation Rules

Refresh **only this cache** on an `invalidate_when` trigger (esp. if `vh-product-spec.liquid`
or the `spec.*` keys change); re-verify keys against the section + metafield definitions and
bump `last_verified`. Do not refresh unrelated caches.
