# VeldoraHaven × EcoSmartFire (MAD Design Europe) Pricing Engine

**Date:** 2026-09-03
**Modeled on:** `pricing/PRICING-ENGINE-HANDOFF.md` (Auroom sauna engine) and `pricing/ROSHULTS-PRICING-ENGINE.md` — same discipline
(verified facts → cost architecture → commercial decision → per-SKU formula → blockers/next steps).
**Source doc:** `EcoSmartFire/ECOSMARTFIRE-MAD-MSRP-EUR-Price-List.pdf` — "MSRP Price List (EUR), Effective August 30, 2026, V300826" — 70 pages, ~410 sellable SKUs across ethanol burners, fireplace grates, fireplace inserts (Frame/Fire Pit Kits/Heritage/Flex — single-sided, corners, bay, peninsula, double-sided, island, bench), fire tables, fire pits, designer fireplaces, stools, and accessories (screens, trays, covers, safety, decorative, replacement parts).

---

## RELATIONSHIP STATUS

- Login/account access to EcoSmartFire (via MAD Design Europe, distributor) obtained 2026-09-03 from **Lincoln**.
- **Wholesale discount: 25% off MSRP**, effective as the starting tier.
- Discount is confirmed to **scale over time with sales volume** — exact tier thresholds not yet provided by Lincoln. See "Discount tier schedule" below for the placeholder structure.
- Supplier ships from **London, United Kingdom**. Shipping is quoted per-SKU, per-zone (Zone 1/2/3) in the MSRP price list and is a **separate line item**, not baked into product cost — see "Shipping" section.
- All MSRP prices in the source list are **exclusive of VAT**.

---

## PRICING STRATEGY

**Decision (2026-09-03):** Sell at MSRP initially, then benchmark against Danish retailer pricing for EcoSmartFire and align — MSRP is the honest starting point (it's what the brand and its other dealers already price at), and the wholesale discount becomes pure margin rather than something that has to be re-engineered into a markup. Once a Danish competitor's live price is checked, adjust the specific SKU/category up or down to stay aligned rather than leaving list price unexamined.

This mirrors how MSRP-driven brands (vs. quote-driven brands like Röshults) should be priced: don't re-derive a retail price from a margin target — take the brand's own retail signal and let the wholesale discount be the margin.

**Formula:**

```
Retail_price (Shopify, ex-VAT)  = MSRP (as published in the EcoSmartFire EUR price list)
Landed_cost                     = MSRP × (1 − current_discount_tier)
GM                               = (Retail_price − Landed_cost) / Retail_price
                                  = current_discount_tier   [since Retail_price = MSRP]
Shipping                         = passed through to customer at the SKU's published Zone 1/2/3 rate
                                    (not absorbed into product cost or margin)
```

At the current 25% tier: **GM = 25% flat across every SKU**, with zero per-SKU pricing work — margin scales automatically and silently as the discount tier improves, without ever having to reprice a product.

**Tax model (same as sauna and Röshults engines):**
- Shopify tax strategy: `ADD_TAXES_AT_CHECKOUT`
- `taxesIncluded: false` — Shopify variant price = ex-VAT retail price = MSRP as published
- Customer total (Denmark) = variant price × 1.25 (25% VAT)
- GM formula: `(Shopify_price − Landed_cost) / Shopify_price` — never divide by 1.25, MSRP is already ex-VAT

**Danish retailer alignment (action item, not yet done):**
1. Identify who sells EcoSmartFire (or the closest comparable premium ethanol/bio-fire brand) in Denmark.
2. Compare their live retail price per model against MSRP.
3. If a Danish retailer is meaningfully below MSRP on a given model/category, either match within a few % or hold at MSRP and lean on VeldoraHaven's positioning/service — don't reflexively race to the bottom, since margin at MSRP is already thin (25%) before this brand's discount scales up.
4. This is a `veldorahaven-competitor-intel` skill task — flagged as next step, not run yet.

---

## DISCOUNT TIER SCHEDULE (placeholder — confirm with Lincoln)

| Tier | Discount off MSRP | Volume threshold | GM at Retail = MSRP | Status |
|---|---|---|---|---|
| 1 | 25% | Starting tier (no minimum) | 25.0% | **CONFIRMED** |
| 2 | TBD | TBD | TBD | Placeholder — ask Lincoln for the actual schedule |
| 3 | TBD | TBD | TBD | Placeholder |
| 4 | TBD | TBD | TBD | Placeholder |

**Do not assume tier 2/3/4 numbers.** When Lincoln (or EcoSmartFire/MAD Design Europe) confirms the schedule, fill in the table above — no other part of this engine needs to change, since GM = discount tier is a direct pass-through when retail = MSRP.

---

## SHIPPING

The MSRP price list carries a per-SKU **Shipping Zone 1 / Zone 2 / Zone 3** column (in EUR, ex-VAT), sourced from the supplier's own shipping map (page 3 of the price list, "Products ship from London, United Kingdom"). Zones are shown on a colour-coded Europe map; exact country→zone assignment needs visual confirmation before building a Shopify shipping profile — from the map:
- **Zone 1** (darkest shading): appears to be Spain, Portugal, France, Italy
- **Zone 2** (mid shading): appears to be Germany, Netherlands, Belgium, Luxembourg, Austria, Switzerland, Denmark, Poland
- **Zone 3** (lightest shading): the remainder of covered mainland Europe (Nordics beyond Denmark, Eastern Europe, etc.)
- UK/Ireland shown greyed out (likely a separate/no-zone arrangement since goods ship *from* the UK)

**Do not build a live Shopify shipping profile on this guess** — confirm the exact zone list with MAD Design Europe/Lincoln first, same caution as the Röshults engine (never invent freight rates). Until confirmed, treat shipping as pass-through revenue/cost that nets to roughly zero — charge the customer the published zone rate, pay the same rate to the supplier.

---

## HOW TO PRICE A NEW ECOSMARTFIRE SKU

1. Look up the SKU's MSRP (ex-VAT) in the current price list (`EcoSmartFire/ECOSMARTFIRE-MAD-MSRP-EUR-Price-List.pdf`, or its successor once MAD Design Europe issues a new version — check the "Effective [date] Vxxxxxx" footer for currency).
2. Shopify variant price (ex-VAT) = that MSRP, unless the Danish-retailer alignment check (above) says otherwise for that model/category.
3. Landed cost = MSRP × (1 − current confirmed discount tier, currently 25%).
4. Shipping = the SKU's published Zone 1/2/3 rate, charged to the customer as shipping, not folded into the product price.
5. GM = the discount tier, automatically — no per-SKU math needed.
6. If a Danish retailer is found selling notably under MSRP, note it in `pricing/snapshots/` or this file rather than silently repricing, so the decision is traceable.

---

## CATALOG SCOPE (for context — not duplicated here)

The full SKU list, MSRP, and shipping rates already live authoritatively in the source PDF (~410 SKUs). Rather than hand-transcribing that into a second spreadsheet (high risk of transcription error at this volume, and it would immediately drift from the supplier's next price-list revision), this engine defines the **formula** that applies uniformly to every SKU: `Retail = MSRP`, `Cost = MSRP × (1 − discount tier)`. Categories covered:

- Ethanol Burners (9 models, several finish variants)
- Fireplace Grates (5)
- Fireplace Inserts: Frame (5), Fire Pit Kits (6), Heritage (3), Flex Single Sided / Left Corner / Right Corner / Bay / Peninsula / Double Sided / Island / Bench (30/30/30/30/30/23/23/23 SKU-rows respectively, incl. finish + decorative-box variants)
- Fire Tables (19 models × up to 12 finish/fuel variants each)
- Fire Pits (8 models × finish variants)
- Designer Fireplaces (11 models × colour variants)
- Stools (3)
- Accessories: Fireplace Screens (17), Fireplace Trays (15), Glass Cover Plates (5), Burner Covers (2), Protective Covers (10), Winter Storage Bags (6), All-Season Covers (16), Safety (15), Decorative (2)
- Replacement Items (13) and Replacement Parts (Fire Screens 7, Flex Wind Screens 8 — shipping POA, Indoor Trays 2)

When it's time to actually import products into Shopify, that's a separate catalog-build project (product selection, collection structure, imagery, copy) — this doc only defines the price math to apply once SKUs are chosen.

---

## OPEN ITEMS / BLOCKERS

- [ ] Discount tier schedule beyond 25% — needs Lincoln/MAD Design Europe confirmation.
- [ ] Shipping zone → country mapping — confirm from supplier, don't build a Shopify shipping profile off the map-image guess above.
- [ ] Danish retailer benchmark — not yet run. Use `veldorahaven-competitor-intel` skill when ready to select launch SKUs.
- [ ] Which EcoSmartFire categories/models VeldoraHaven will actually list (full catalog vs. curated subset) — not decided; this engine prices whatever is chosen, it doesn't choose for you.
