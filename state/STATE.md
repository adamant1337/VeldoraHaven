# VeldoraHaven — Live State

_Last updated: 2026-08-23 — roadmap R0/R1/R2/R5(partial)/R7(partial) complete; R3 next_

## Active tasks

```yaml
- task_id: AI-ARCH-001
  title: Establish agent system + source-of-truth scaffolding
  status: complete
- task_id: THEME-INT-001
  title: Confirm + clone theme, read-only integration audit, extract real tokens
  status: complete
  notes: theme at C:\VeldoraHaven\theme (HEAD 15eba70, main)
- task_id: AUDIT-001
  title: Master store audit (live + local), baseline scores, roadmap
  status: complete
  baseline_score: 70/100
- task_id: R0
  title: Reconcile local <-> live + set up dev workflow
  status: complete (CLI pull pending user auth)
  branch: fix/reconcile-local-live
  finding: source of truth = LIVE 205129482582 + spec.* metafields; local/GitHub stale (Aug 2)
  decision: v28 (205283819862) = working draft; live (205129482582) = reference
  captured: real design tokens + custom-source knowledge via Admin API
  outputs: shopify/LIVE-LOCAL-RECONCILIATION.md, shopify/THEME-DEV-WORKFLOW.md, theme/shopify.theme.toml
  pull: COMPLETE 2026-08-22 — v28 verified (byte-match) + committed as baseline on fix/reconcile-local-live
  next_action: R0 complete.
- task_id: R1
  title: Typography audit (roadmap P0)
  status: complete — NO CHANGE REQUIRED. Custom-CSS layer already authoritative
    (Cormorant/Inter), correct across all surfaces. See ADR (typography).
- task_id: R2
  title: Hero + fonts perf (roadmap P0)
  status: complete. Hero PNG→CDN-resized WebP (~90% smaller), preload/preconnect
    added. Branch perf/r2-lcp-optimization (theme repo). Merged into
    integration/dev-preview.
- task_id: R5
  title: JSON-LD structured data (roadmap P1)
  status: partial-complete. Product + Organization JSON-LD already existed via
    Horizon (`structured_data` filter, header.liquid) — kept as-is. Added
    BreadcrumbList (new, `snippets/breadcrumb-json-ld.liquid`). FAQPage
    explicitly skipped — no real FAQ content exists anywhere on the site;
    do not add until real content exists.
- task_id: R7
  title: Cart AOV (roadmap P2)
  status: partial-complete, scope-narrowed. No real accessory/care/install
    products exist in Shopify (checked — Sauna Accessories collection empty,
    zero matches store-wide) — upsell half is blocked on missing product data,
    a merchandising decision, not implementable without inventing products.
    Implemented the trust half only: `sections/vh-cart-trust.liquid` reassurance
    strip (secure checkout / delivery process / contact), added to
    templates/cart.json.
- task_id: BARREL-SAUNA-FAMILY
  title: Complete + polish the Barrel Sauna product family (Halo/Luma/Nora/Sola)
  status: complete. Outside strict roadmap numbering but foundational — this
    IS the roadmap's "first real implementation phase." Covers Nora/Sola
    content authored from verified Auroom sheets, all 4 products built/fixed
    in Shopify (variants, spec.* metafields, images, publication, inventory
    tracking), variant-image mapping for all 4, PDP buy-box trust fix,
    Barrel Saunas collection buying-guide + comparison table, homepage
    category-card typography pass (numbered index + italic accent + gold
    rule), collections-index entrance motion, sticky-add-to-cart disabled,
    spec section converted to a dropdown, repeated price near buy buttons,
    variant-picker label font fixed, Infrared Saunas removed from nav +
    collections index. All on theme-repo branch `integration/dev-preview`,
    pushed to Shopify dev theme v28 (unpublished). See memory
    `veldorahaven-nora-sola-products.md`.
  next_action: R3 (Reviews / social proof) is next in roadmap priority order —
    R4 (premium polish) and R6 (contrast AA) still pending in P1 too.
    R8-R13 (P2/P3) not started except R7 above.
```

## Theme snapshot

```yaml
root: C:\VeldoraHaven\theme
remote: https://github.com/adamant1337/VeldoraHaven1.git
branch: main
head: 15eba70
base_theme: Shopify Horizon 3.5.1
```

## File-ownership locks

_None active._

```yaml
# template
# - file: ; owner: ; task_id: ; locked: true
```

## Blockers / cautions

- `main` is **production-linked** via the Shopify↔GitHub integration — no pushes to
  `main` without explicit user approval.
- Shopify CLI present but **not authenticated**; store not identified. Read-only until
  the user logs in. See [`../shopify/SHOPIFY-THEME-INTEGRATION.md`](../shopify/SHOPIFY-THEME-INTEGRATION.md).
- **Local theme ≠ live site** (live homepage/PDP richer; likely published-theme-ahead
  and/or metafield-driven). Reconcile (roadmap R0) before any implementation.
