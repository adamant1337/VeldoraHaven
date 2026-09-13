# VeldoraHaven Pricing Engine — Phase 1 Handoff

**Date:** 2026-08-27  
**Current phase:** Phase 0 COMPLETE — Phase 1 pending  
**Stop Gate 3:** ACTIVE — zero Shopify mutations executed  
**Artifact (Phase 0C matrix):** https://claude.ai/code/artifact/166aaa68-ddb0-4f12-82ce-606ed506ebbb  
**Artifact (Phase 0B health report):** https://claude.ai/code/artifact/21cdd905-2929-4172-bb2c-d0deebc1ac40

---

## CURRENT STATE

Phase 0 (audit, correction, commercial decision) is complete. All supplier costs verified. Tax model confirmed live. Black finish commercial decision made. 33 Black finish price mutations are ready in Group A. 33 Natural configurations remain KEEP. 6 configurations are BLOCKED pending supplier assembly cost.

**Phase 1 job:** snapshot → validate → apply Group A mutations → readback → report.

---

## VERIFIED SHOPIFY FACTS

| Field | Value |
|---|---|
| Currency | EUR |
| Shop `taxesIncluded` | `false` |
| Denmark market tax strategy | `ADD_TAXES_AT_CHECKOUT` |
| Variant `taxable` | `true` (all sauna variants) |
| Price lists | None (no market overrides) |

**Critical interpretation:**
> Shopify variant price = ex-VAT retail price.  
> Customer total (Denmark) = variant price × 1.25  
> Do NOT treat stored prices as incl. VAT.

**GM formula:**
```
GM = (Shopify_price − Landed_cost) / Shopify_price
```
Never divide by 1.25 — variant price is already ex-VAT.

---

## VARIANT ARCHITECTURE (VALIDATED — DO NOT RESTRUCTURE)

```
72 core sauna variants = 18 models × 4 configs (NW DIY / NW Pre / BB DIY / BB Pre)
  Halo:  28 variants (7 models × 4)
  Luma:  24 variants (6 models × 4)
  Nora:   8 variants (2 models × 4)
  Sola:  12 variants (3 models × 4)
```

---

## APPROVED COST ARCHITECTURE

### Logistics reserve (internal assumption — not a quoted freight rate)
- DIY: €600
- Pre-assembled: €850

### GM thresholds (sauna-only)
- Target: 52.5%
- Floor: 45%

### Landed cost formula
```
Landed = Base_EXW + Finish_EXW_uplift + Assembly_EXW + Logistics_reserve
```

---

## SUPPLIER COST DATA (ALL SUPPLIER-VERIFIED FROM AUROOM PDFS)

### Natural EXW base costs

| Model | Code | EXW |
|---|---|---|
| Halo Cosy 120 | R-190-120 | €1,840 |
| Halo Cosy 150 | SR-150 | €2,070 |
| Halo Cosy 180 | SR-180 | €2,250 |
| Halo Cosy 225 | SR-225 | €2,460 |
| Halo Comfy 225 | R-225 | €2,580 |
| Halo Comfy 300 | R-300 | €2,980 |
| Halo Extra Comfy | RC-300 | €3,990 |
| Luma Cosy 225 | SRT-225 | €2,550 |
| Luma Cosy 260 | SRT-260 | €2,720 |
| Luma Cosy 300 | SRT-300 | €2,920 |
| Luma Comfy 225 | RT-225 | €2,660 |
| Luma Comfy 260 | RT-260 | €2,850 |
| Luma Comfy 300 | RT-300 | €3,060 |
| Nora 210 | KT-210 | €3,150 |
| Nora 250 | KT-250 | €3,390 |
| Sola 140 | K-140 | €2,280 |
| Sola 210 | K-210 | €3,060 |
| Sola 250 | K-250 | €3,300 |

### Black EXW uplifts (from Auroom Q4 2026 price list)

| Model | Uplift | Tier |
|---|---|---|
| Halo Cosy 120 | +€490 | 1 |
| Halo Cosy 150 | +€540 | 1 |
| Halo Cosy 180 | +€590 | 2 |
| Halo Cosy 225 | +€655 | 2 |
| Halo Comfy 225 | +€820 | 3 |
| Halo Comfy 300 | +€875 | 3 |
| Halo Extra Comfy | +€875 | 3 |
| Luma Cosy 225 | +€655 | 2 |
| Luma Cosy 260 | +€725 | 2 |
| Luma Cosy 300 | +€795 | 3 |
| Luma Comfy 225 | +€820 | 3 |
| Luma Comfy 260 | +€835 | 3 |
| Luma Comfy 300 | +€875 | 3 |
| Nora 210 | +€820 | 3 |
| Nora 250 | +€875 | 3 |
| Sola 140 | +€535 | 1 |
| Sola 210 | +€820 | 3 |
| Sola 250 | +€875 | 3 |

### Assembly costs (from Auroom assembly pricing PDF, Aug 2024)

| Model | Assembly cost |
|---|---|
| Halo Cosy 120 | **BLOCKED — not in Auroom PDF** |
| Halo Cosy 150 | €300 |
| Halo Cosy 180 | €320 |
| Halo Cosy 225 | €340 |
| Halo Comfy 225 | €370 |
| Halo Comfy 300 | €390 |
| Halo Extra Comfy | €430 (listed as Deluxe 300) |
| Luma Cosy 225 | €340 |
| Luma Cosy 260 | €350 |
| Luma Cosy 300 | €360 |
| Luma Comfy 225 | €370 |
| Luma Comfy 260 | €380 |
| Luma Comfy 300 | €390 |
| Nora 210 | **BLOCKED — not in Auroom PDF** |
| Nora 250 | €520 |
| Sola 140 | €300 |
| Sola 210 | €340 |
| Sola 250 | **BLOCKED — not in Auroom PDF** |

---

## APPROVED COMMERCIAL DECISIONS

### Natural (NW) prices: KEEP ALL
All Natural configurations are currently above the 52.5% GM target (56–66% range).  
No Natural price changes are needed or approved.

### Black finish: TIERED RETAIL PREMIUM (ex-VAT)

| Tier | EXW uplift range | Customer retail premium (ex-VAT) | Customer sees (incl. DK VAT) |
|---|---|---|---|
| 1 | €490–€540 | +€600 | +€750 |
| 2 | €590–€725 | +€800 | +€1,000 |
| 3 | €795–€875 | +€1,000 | +€1,250 |

Premium is identical for DIY and Pre-assembled within each model.

All resulting Black GMs verified above 52.5% target. Worst case: Halo Extra Comfy BB DIY at exactly 52.5%.

### Pre-assembled pricing: KEEP RETAIL STRUCTURE
Retail Pre-assembled premiums are already model-specific and well above margin floor.  
Assembly cost for margin calculations: use verified Auroom assembly costs above.

---

## MUTATION GROUPS

### GROUP A — Safe to apply (33 configurations)
All Black finish increases. Supplier costs verified. Margins ≥ 52.5% target. No catalogue conflicts.

| # | Model | Fin | Del | Current (ex-VAT) | Recommended (ex-VAT) | Danish (incl.VAT) | Delta | GM |
|---|---|---|---|---|---|---|---|---|
| 1 | Halo Cosy 120 | BB | DIY | €6,400 | **€6,700** | €8,375 | +€300 | 56.3% |
| 2 | Halo Cosy 150 | BB | DIY | €7,500 | **€7,900** | €9,875 | +€400 | 59.4% |
| 3 | Halo Cosy 150 | BB | Pre | €9,300 | **€9,700** | €12,125 | +€400 | 61.2% |
| 4 | Halo Cosy 180 | BB | DIY | €7,800 | **€8,400** | €10,500 | +€600 | 59.0% |
| 5 | Halo Cosy 180 | BB | Pre | €9,600 | **€10,200** | €12,750 | +€600 | 60.7% |
| 6 | Halo Cosy 225 | BB | DIY | €7,900 | **€8,500** | €10,625 | +€600 | 56.3% |
| 7 | Halo Cosy 225 | BB | Pre | €11,000 | **€11,600** | €14,500 | +€600 | 62.9% |
| 8 | Halo Comfy 225 | BB | DIY | €8,900 | **€9,700** | €12,125 | +€800 | 58.8% |
| 9 | Halo Comfy 225 | BB | Pre | €11,200 | **€12,000** | €15,000 | +€800 | 61.5% |
| 10 | Halo Comfy 300 | BB | DIY | €9,600 | **€10,400** | €13,000 | +€800 | 57.2% |
| 11 | Halo Comfy 300 | BB | Pre | €12,000 | **€12,800** | €16,000 | +€800 | 60.2% |
| 12 | Halo Extra Comfy | BB | DIY | €10,700 | **€11,500** | €14,375 | +€800 | 52.5% |
| 13 | Halo Extra Comfy | BB | Pre | €13,500 | **€14,300** | €17,875 | +€800 | 57.0% |
| 14 | Luma Cosy 225 | BB | DIY | €7,500 | **€8,100** | €10,125 | +€600 | 53.0% |
| 15 | Luma Cosy 225 | BB | Pre | €9,000 | **€9,600** | €12,000 | +€600 | 54.2% |
| 16 | Luma Cosy 260 | BB | DIY | €8,100 | **€8,700** | €10,875 | +€600 | 53.5% |
| 17 | Luma Cosy 260 | BB | Pre | €9,600 | **€10,200** | €12,750 | +€600 | 54.5% |
| 18 | Luma Cosy 300 | BB | DIY | €8,400 | **€9,200** | €11,500 | +€800 | 53.1% |
| 19 | Luma Cosy 300 | BB | Pre | €10,000 | **€10,700** | €13,375 | +€700 | 53.9% |
| 20 | Luma Comfy 225 | BB | DIY | €8,500 | **€9,300** | €11,625 | +€800 | 56.1% |
| 21 | Luma Comfy 225 | BB | Pre | €10,500 | **€11,300** | €14,125 | +€800 | 58.4% |
| 22 | Luma Comfy 260 | BB | DIY | €8,800 | **€9,600** | €12,000 | +€800 | 55.4% |
| 23 | Luma Comfy 260 | BB | Pre | €10,800 | **€11,600** | €14,500 | +€800 | 57.6% |
| 24 | Luma Comfy 300 | BB | DIY | €10,400 | **€11,200** | €14,000 | +€800 | 59.5% |
| 25 | Luma Comfy 300 | BB | Pre | €12,400 | **€13,200** | €16,500 | +€800 | 60.8% |
| 26 | Nora 210 | BB | DIY | €9,000 | **€10,000** | €12,500 | +€1,000 | 54.3% |
| 27 | Nora 250 | BB | DIY | €10,000 | **€11,000** | €13,750 | +€1,000 | 55.8% |
| 28 | Nora 250 | BB | Pre | €12,000 | **€13,000** | €16,250 | +€1,000 | 56.7% |
| 29 | Sola 140 | BB | DIY | €7,200 | **€7,800** | €9,750 | +€600 | 56.2% |
| 30 | Sola 140 | BB | Pre | €8,300 | **€8,900** | €11,125 | +€600 | 55.5% |
| 31 | Sola 210 | BB | DIY | €9,400 | **€10,400** | €13,000 | +€1,000 | 56.9% |
| 32 | Sola 210 | BB | Pre | €11,100 | **€12,100** | €15,125 | +€1,000 | 58.1% |
| 33 | Sola 250 | BB | DIY | €9,800 | **€10,800** | €13,500 | +€1,000 | 55.8% |

### GROUP B — Manual commercial review
None. All pricing decisions resolved by tiered system.

### GROUP C — Blocked (4 configurations remaining; Halo Cosy 120 unblocked 2026-09-03)
Missing Auroom assembly cost. Do not price until supplier confirms.

| Model | Finish | Delivery | Blocker |
|---|---|---|---|
| Nora 210 | NW | Pre | No assembly cost in Auroom PDF |
| Nora 210 | BB | Pre | No assembly cost in Auroom PDF |
| Sola 250 | NW | Pre | No assembly cost in Auroom PDF |
| Sola 250 | BB | Pre | No assembly cost in Auroom PDF |

**Action required:** Request assembly pricing for Nora 210, Sola 250 from Silga/Auroom.

**Halo Cosy 120 Pre-assembled — unblocked 2026-09-03 (commercial decision, not a supplier confirmation):**
user reviewed the live prices (NW Pre €8,700, BB Pre €9,000 — both already live and selling) and
decided to keep them, assuming an assembly cost in line with the other small models (Cosy 150
€300, Cosy 180 €320, Sola 140 €300) rather than waiting on the Auroom PDF figure. Using an
assumed €300 assembly cost: NW Pre landed = 1,840 + 300 + 850 = €2,990 → GM 65.6% at €8,700;
BB Pre landed = 1,840 + 490 + 300 + 850 = €3,480 → GM 61.3% at €9,000. Both comfortably above
the 52.5% target. Treat €300 as a working assumption, not a verified Auroom cost — replace with
the real figure if/when Silga/Auroom confirms it, same as Nora 210 and Sola 250 above.

---

## ROLLBACK REQUIREMENTS

Before applying any mutation in Phase 1, the Phase 1 agent must:

1. Read all 72 current variant prices from Shopify and persist to a snapshot file
2. Persist variant GIDs (not just product GIDs) for exact targeting
3. Store snapshot before any mutation begins
4. Apply mutations one product at a time, reading back each changed value
5. On any error: halt immediately, do not continue with remaining mutations
6. Rollback procedure: restore snapshot values using the same productVariantsBulkUpdate mutation

Snapshot file location (to be created by Phase 1): `C:\VeldoraHaven\pricing\snapshots\snapshot-[timestamp].json`

---

## CATALOGUE NOTES (not blockers)

**Positioning anomaly — Luma Cosy vs Halo Cosy (not a margin issue):**
- Halo Cosy 225 NW DIY = €7,700 | Luma Cosy 225 NW DIY = €7,300
- Luma EXW is actually higher (€2,550 vs €2,460) yet retails lower
- Luma Cosy should arguably command a premium over Halo Cosy given the porch/glass design
- Not fixed in Phase 0 — flagged for future commercial review

---

## DO NOT DO (in Phase 1 or any future session)

- Do NOT change tax settings or Markets configuration
- Do NOT apply Group C (BLOCKED) prices — they have no verified landed cost
- Do NOT change Natural Wood prices — all are above target and approved KEEP
- Do NOT interpret stored Shopify prices as VAT-inclusive
- Do NOT expose supplier EXW costs or internal GM data on the storefront
- Do NOT restructure the Size × Finish × Delivery variant architecture
- Do NOT mutate heater/option/accessory product pricing

---

## NEXT PHASE — PHASE 1 (New chat)

**First action in the new chat:**
1. Load this handoff file
2. Read current Shopify variant prices for all 72 configurations (verify no changes since snapshot)
3. Persist snapshot JSON to `pricing/snapshots/`
4. Apply Group A mutations (33 Black finish increases) using `productVariantsBulkUpdate`
5. Read back all 33 changed values and verify
6. Produce mutation report

**Shopify products:**
- Halo: `gid://shopify/Product/11190367125846`
- Luma: `gid://shopify/Product/11191458234710`
- Nora: `gid://shopify/Product/11159107862870`
- Sola: `gid://shopify/Product/11198241407318`

**Phase 1 must NOT:**
- Apply any price without first creating the snapshot
- Apply Group C (BLOCKED) items
- Change any Natural Wood price

---

*Stop Gate 3 remains active. This file is the authoritative handoff. The Phase 0C artifact contains the full 72-row annotated matrix.*
