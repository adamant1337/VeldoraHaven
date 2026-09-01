# VeldoraHaven Pricing Engine — Phase 1 Mutation Report

**Date:** 2026-08-27  
**Phase:** 1 — Group A Black finish price increases  
**Status:** COMPLETE  

---

## Summary Counts

| Metric | Count |
|---|---|
| Variants authorized (Group A) | 33 |
| Pre-flight mapped unambiguously | 33 |
| Drift detected | 0 |
| Attempted | 33 |
| Successfully changed | 33 |
| Verified by independent read-back | 33 |
| Failed | 0 |
| Skipped | 0 |
| BLOCKED (untouched) | 6 |
| KEEP (untouched) | 33 |
| API errors | 0 |

---

## Pre-Flight & Drift Check

All 33 Group A target variants were mapped unambiguously by Shopify variant GID. Every live price matched the approved Phase 0C baseline at time of pre-flight. Zero drift detected. Mutations proceeded without exclusions.

---

## Snapshot

**Location:** `pricing/snapshots/snapshot-20260827-120000.json`  
**Contents:** All 72 core sauna variants with pre-mutation prices, proposed prices, GIDs, mutation group classification.  
**Validated:** Yes — written before first mutation; cross-checked against live Shopify data.

---

## Mutations Applied — Old → New (all EUR ex-VAT)

### Halo — Outdoor Barrel Sauna (`gid://shopify/Product/11190367125846`)

| # | Variant | Variant ID | Old Price | New Price | Status |
|---|---|---|---|---|---|
| 1 | Halo Cosy 120 / BB / DIY | 55032448155990 | €6,400 | **€6,700** | VERIFIED |
| 2 | Halo Cosy 150 / BB / DIY | 55032448352598 | €7,500 | **€7,900** | VERIFIED |
| 3 | Halo Cosy 150 / BB / Pre | 55032448418134 | €9,300 | **€9,700** | VERIFIED |
| 4 | Halo Cosy 180 / BB / DIY | 55032448549206 | €7,800 | **€8,400** | VERIFIED |
| 5 | Halo Cosy 180 / BB / Pre | 55032448614742 | €9,600 | **€10,200** | VERIFIED |
| 6 | Halo Cosy 225 / BB / DIY | 55032453333334 | €7,900 | **€8,500** | VERIFIED |
| 7 | Halo Cosy 225 / BB / Pre | 55032453398870 | €11,000 | **€11,600** | VERIFIED |
| 8 | Halo Comfy 225 / BB / DIY | 55032453529942 | €8,900 | **€9,700** | VERIFIED |
| 9 | Halo Comfy 225 / BB / Pre | 55032453595478 | €11,200 | **€12,000** | VERIFIED |
| 10 | Halo Comfy 300 / BB / DIY | 55032453726550 | €9,600 | **€10,400** | VERIFIED |
| 11 | Halo Comfy 300 / BB / Pre | 55032453792086 | €12,000 | **€12,800** | VERIFIED |
| 12 | Halo Extra Comfy / BB / DIY | 55032453923158 | €10,700 | **€11,500** | VERIFIED |
| 13 | Halo Extra Comfy / BB / Pre | 55032453988694 | €13,500 | **€14,300** | VERIFIED |

### Luma — Outdoor Barrel Sauna with Porch (`gid://shopify/Product/11191458234710`)

| # | Variant | Variant ID | Old Price | New Price | Status |
|---|---|---|---|---|---|
| 14 | Luma Cosy 225 / BB / DIY | 55042157838678 | €7,500 | **€8,100** | VERIFIED |
| 15 | Luma Cosy 225 / BB / Pre | 55042157904214 | €9,000 | **€9,600** | VERIFIED |
| 16 | Luma Cosy 260 / BB / DIY | 55042157969750 | €8,100 | **€8,700** | VERIFIED |
| 17 | Luma Cosy 260 / BB / Pre | 55042158035286 | €9,600 | **€10,200** | VERIFIED |
| 18 | Luma Cosy 300 / BB / DIY | 55042158100822 | €8,400 | **€9,200** | VERIFIED |
| 19 | Luma Cosy 300 / BB / Pre | 55042158166358 | €10,000 | **€10,700** | VERIFIED |
| 20 | Luma Comfy 225 / BB / DIY | 55040046039382 | €8,500 | **€9,300** | VERIFIED |
| 21 | Luma Comfy 225 / BB / Pre | 55040046072150 | €10,500 | **€11,300** | VERIFIED |
| 22 | Luma Comfy 260 / BB / DIY | 55040046170454 | €8,800 | **€9,600** | VERIFIED |
| 23 | Luma Comfy 260 / BB / Pre | 55040046203222 | €10,800 | **€11,600** | VERIFIED |
| 24 | Luma Comfy 300 / BB / DIY | 55040046301526 | €10,400 | **€11,200** | VERIFIED |
| 25 | Luma Comfy 300 / BB / Pre | 55040046334294 | €12,400 | **€13,200** | VERIFIED |

### Nora — Outdoor Square Barrel Sauna (`gid://shopify/Product/11159107862870`)

| # | Variant | Variant ID | Old Price | New Price | Status |
|---|---|---|---|---|---|
| 26 | Nora 210 / BB / DIY | 55072233881942 | €9,000 | **€10,000** | VERIFIED |
| 27 | Nora 250 / BB / DIY | 55072234013014 | €10,000 | **€11,000** | VERIFIED |
| 28 | Nora 250 / BB / Pre | 55072234045782 | €12,000 | **€13,000** | VERIFIED |

### Sola — Square Barrel Sauna (`gid://shopify/Product/11198241407318`)

| # | Variant | Variant ID | Old Price | New Price | Status |
|---|---|---|---|---|---|
| 29 | Sola 140 / BB / DIY | 55072257999190 | €7,200 | **€7,800** | VERIFIED |
| 30 | Sola 140 / BB / Pre | 55072258031958 | €8,300 | **€8,900** | VERIFIED |
| 31 | Sola 210 / BB / DIY | 55072258130262 | €9,400 | **€10,400** | VERIFIED |
| 32 | Sola 210 / BB / Pre | 55072258163030 | €11,100 | **€12,100** | VERIFIED |
| 33 | Sola 250 / BB / DIY | 55072258261334 | €9,800 | **€10,800** | VERIFIED |

---

## BLOCKED Variants — Untouched

| Model | Finish | Delivery | Live Price (unchanged) | Blocker |
|---|---|---|---|---|
| Halo Cosy 120 | NW | Pre | €8,700 | No assembly cost in Auroom PDF |
| Halo Cosy 120 | BB | Pre | €9,000 | No assembly cost in Auroom PDF |
| Nora 210 | NW | Pre | €10,500 | No assembly cost in Auroom PDF |
| Nora 210 | BB | Pre | €10,500 | No assembly cost in Auroom PDF |
| Sola 250 | NW | Pre | €11,500 | No assembly cost in Auroom PDF |
| Sola 250 | BB | Pre | €11,500 | No assembly cost in Auroom PDF |

---

## Commercial Sanity Check (key spot-checks)

| Config | New Price | Landed Cost | GM | Pass |
|---|---|---|---|---|
| Halo Extra Comfy BB DIY (worst case) | €11,500 | €5,465 | 52.5% | ✓ |
| Luma Cosy 225 BB DIY | €8,100 | €3,805 | 53.0% | ✓ |
| Nora 210 BB DIY | €10,000 | €4,570 | 54.3% | ✓ |
| Sola 140 BB DIY | €7,800 | €3,415 | 56.2% | ✓ |
| Sola 140 BB Pre | €8,900 | €3,965 | 55.4% | ✓ |

All 33 confirmed ≥ 52.5% target GM. No discrepancies.

---

## Rollback Instructions

If restoration of any variant to its pre-Phase-1 price is required:

1. Open `pricing/snapshots/snapshot-20260827-120000.json`
2. Locate the variant by `variant_id`
3. Use `current_price` as the restore value
4. Apply via `productVariantsBulkUpdate` mutation targeting the relevant product
5. Read back to verify restoration

**Never reconstruct old prices from memory or formulas when this snapshot exists.**

---

## API Errors

None.

---

## Completion Checklist

- [x] Pre-flight mapping succeeded (33/33 unambiguous by GID)
- [x] Snapshot exists and validated (`snapshot-20260827-120000.json`)
- [x] Approved variants mutated (33/33)
- [x] Live Shopify values read back independently
- [x] Expected and actual values match (33/33)
- [x] Exceptions documented (0 drift, 0 failed, 6 blocked unchanged)
- [x] Report written

**Phase 1 Group A is COMPLETE.**

---

## What Remains (not authorized in this phase)

- Group C (6 BLOCKED variants): pending Silga/Auroom assembly cost for Halo Cosy 120, Nora 210, Sola 250
- Natural Wood pricing: approved KEEP, no action needed
- Heater/accessory products: separate phase
- Luma Cosy vs Halo Cosy positioning anomaly: flagged for commercial review
