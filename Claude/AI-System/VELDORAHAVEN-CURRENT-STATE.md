# VeldoraHaven — Current-State Baseline

**Authoritative snapshot of what exists today**, from two sources inspected 2026-08-22:
- **LIVE site** (customer-facing baseline): https://www.veldorahaven.com/ — inspected
  read-only via browser (homepage, /collections, a collection, a PDP).
- **LOCAL theme** (implementation): `C:\VeldoraHaven\theme\` (Horizon 3.5.1, HEAD `15eba70`).

Philosophy: this is the foundation to **elevate, not rebuild**. See KEEP/IMPROVE/REPLACE
verdicts in [`VELDORAHAVEN-IMPROVEMENT-ROADMAP.md`](VELDORAHAVEN-IMPROVEMENT-ROADMAP.md).

> ⚠️ **Key discrepancy (see §8): the local theme clone does NOT fully reflect the live
> site.** The live experience is richer than the theme files at HEAD imply — much of the
> premium content is data-driven (product metafields) and/or the published theme is ahead
> of GitHub `main`. Do not treat the local files as the complete source of the live site.

---

## 1. What already exists (live)

VeldoraHaven is a **genuinely premium, high-ticket European outdoor-living store** —
Auroom saunas, cold plunge, outdoor kitchens, baths/hot tubs, fire features. The live
site is well-considered, editorial, and trust-forward. This is strong source material.

## 2. Homepage (live)

- **Hero:** "OUTDOOR LIVING, ELEVATED. / Creating spaces worth living in" + confident
  editorial subcopy; two CTAs — *Explore collections*, *How it works*.
- **Category discovery:** Saunas · Cold Plunge · Outdoor Kitchens · Outdoor Baths — each
  with an editorial tagline + *Explore collection*.
- **USP / trust row:** Full Specifications · Scheduled Delivery · Warranty Managed ·
  Questions Answered (answered within one working day).
- **"The Veldora Haven Process":** 4 steps (Order → Manufacture & Dispatch → Scheduled
  Delivery → Warranty & Aftercare) — excellent high-ticket reassurance.
- **Journal:** 3 editorial articles (specification guides) — real content marketing.
- **About:** "A small number of products, chosen with care." — clear brand story.

## 3. Navigation (live)

Minimal: **drawer "Menu" + Search + Cart + logo**, even at desktop (1280px). Deliberately
luxury-minimal; discoverability of the full taxonomy behind one menu is worth evaluating.
Footer + policies present (privacy policy linked; cookie consent Accept/Decline banner).

## 4. Collections (live)

- Full taxonomy: Barrel Saunas, Cabin Saunas, Infrared Saunas, Saunas, Cold Plunge,
  Fire Features, Outdoor Baths & Hot Tubs, Outdoor Kitchens, Outdoor Furniture &
  Pergolas, Complete Bundles, Sauna Accessories.
- Collection page has **price filter (min/max) + sort dropdown + clean product cards**
  (e.g. Auroom Halo, Auroom Luma barrel saunas).

## 5. Product pages (live) — the strongest asset

The Auroom Halo PDP is comprehensive and high-ticket-appropriate:
- **Variant matrix:** Size (7 models w/ capacity) × Finish (Natural Wood / Brushed Black)
  × Delivery (DIY kit / Pre-assembled). Price, quantity, Add to cart, accelerated checkout.
- **Editorial storytelling:** "An Auroom Product" — materials, barrel-form rationale,
  weathering behavior.
- **Transparency:** Included as standard · Not included · Available options — exceptional
  for high-ticket clarity.
- **Logistics:** Assembly (2 adults, 4–6h), Base requirements, Delivery (48–72h call).
- **Specification table:** external dimensions, capacity, materials, power requirement,
  weight, CE certification, warranty.
- **Gap:** no visible customer reviews / social proof on the pages inspected.

## 6. Cart (live)

Not deeply inspected live (avoided cart mutation). Local theme provides cart drawer +
cart page + product-list recommendations. AOV/upsell mechanics appear minimal — to verify.

## 7. Brand & design system (implemented)

Extracted from `assets/veldora-custom.css` + `settings_data.json` (full detail in
[`../design-system/DESIGN-SYSTEM.md`](../design-system/DESIGN-SYSTEM.md)):
cream canvas `#F7F7F5`, forest chrome `#1B4332`/`#152E25`, gold accents `#C8A96E`, stone
text `#3D3D35`; Cormorant Garamond display + Inter body; sharp corners (radius 0), no
shadows; gold focus ring; card image zoom on hover. Coherent and premium.

## 8. Technical architecture & discrepancies

- **Base:** Shopify Horizon 3.5.1 (OS 2.0, block-based), 455 files, brand layer isolated
  in one CSS file injected at `theme.liquid:34`. Clean, DRY, maintainable.
- **PDP content is metafield-driven:** the rich specs/included/options/assembly text seen
  live is not in the theme files → it lives in Shopify product metafields. The theme
  provides the shell (`_product-details`, `product-information`, `text`, custom-liquid).
- **DISCREPANCY — local ≠ live (RESOLVED by R0, 2026-08-22):** confirmed root cause —
  development moved into **admin-duplicated themes (v25→v28)** and never flowed back to
  GitHub, so the live theme (`205129482582`, 2026-08-19) diverged from GitHub/local
  (`15eba70`, 2026-08-02). The live homepage is built from **custom `vh-*` sections**
  (`vh-category-cards`, `vh-trust-bar`, `vh-how-it-works`, `vh-journal`, `vh-brand-story`)
  that do not exist locally; the local homepage is the stock Horizon demo. The rich PDP is
  driven by **`spec.*` product metafields** rendered by `sections/vh-product-spec.liquid`.
  **Source of truth = live theme `205129482582` + Shopify metafields.** Full record:
  [`../shopify/LIVE-LOCAL-RECONCILIATION.md`](../shopify/LIVE-LOCAL-RECONCILIATION.md).
- **Known debt:** typography conflict (Josefin Sans setting vs Cormorant `!important`
  override — headings render inconsistently); `!important` saturation; 3.1 MB
  `LakeSaunaHeroPicture.png` in assets; render-blocking Google-Fonts `@import`; no JSON-LD
  in theme `meta-tags`; some contrast failures (footer/vendor). Full list in the roadmap.

## 9. Access limitations (stated honestly)

- Live site inspected **read-only via browser text/DOM**; no visual screenshot captured
  (pane not compositing) — visual-polish judgments are structural/copy-based, to be
  confirmed with a visual pass.
- **Shopify admin not accessed** (not authorized): cannot confirm published-theme version,
  metafield definitions, or app stack. Discrepancy resolution needs this.
- Cart/checkout not exercised (no mutation). Nothing about the live site is invented here.
