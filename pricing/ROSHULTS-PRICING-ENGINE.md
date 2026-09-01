# VeldoraHaven × Röshults Pricing Engine

**Date:** 2026-09-01 (revised prices 2026-09-01)
**Modeled on:** `pricing/PRICING-ENGINE-HANDOFF.md` (the Auroom sauna pricing engine) — same discipline
(verified facts → cost architecture → commercial decision → per-SKU table → blockers), same target GM band (40–45%).

---

## PRICING STRATEGY

Röshults is positioned as premium outdoor living — not price-competed against Röshults.com direct.
VeldoraHaven sells curated design + direct delivery from Sweden, and the margin must cover freight,
payment fees, marketing, customer service, FX buffer, and affiliate/partner structures.

**Formula:**

```
Dealer_cost (EXW)  = Röshults net quote amount (post-30% discount)
Logistics_reserve  = €300 (Essentials) / €750 (Kitchen Islands) — internal estimate until real freight confirmed
Landed_cost        = Dealer_cost + Logistics_reserve
Retail_price       = Landed_cost ÷ (1 − target_margin)   [target: 40–45%]
```

**Tax model (same as sauna engine):**
- Shopify tax strategy: `ADD_TAXES_AT_CHECKOUT` (Denmark market)
- `taxesIncluded: false` — Shopify variant price = ex-VAT retail price
- Customer total (Denmark) = variant price × 1.25 (25% VAT)
- GM formula: `(Shopify_price − Landed_cost) / Shopify_price`

---

## VERIFIED FACTS

| Field | Value |
|---|---|
| Currency | EUR |
| Röshults trade discount | 30% off own retail list |
| Quote basis | EXW Jönköping, Sweden, EUR, no VAT |
| Payment terms | 50% at order confirmation, 50% before delivery |
| Quote validity | 3 months from quote date |
| Customer No. | 6471 |

**Logistics reserve is an internal assumption — not a confirmed freight rate.**
Niklas Sahlqvist (COO) has been asked for indicative DAP freight zone costs. Update reserves
to real numbers once confirmed. Do NOT build a Shopify shipping profile with invented rates.

---

## PER-SKU TABLE (4 entry-point SKUs)

| SKU | GID | Dealer cost (EXW) | Logistics reserve | Landed cost | Shopify price (ex-VAT) | Customer price (incl. DK 25% VAT) | GM |
|---|---|---|---|---|---|---|---|
| RH-ESSENTIALS-BLACK-GAS | `11217676566870` | €6,119.40 | €300 | €6,419 | **€10,995** | €13,744 | 41.6% |
| RH-ESSENTIALS-SS-CHARCOAL | `11217676534102` | €5,839.40 | €300 | €6,139 | **€10,495** | €13,119 | 41.5% |
| RH-KI5-BAR-SS316L | `11217676599638` | €24,734.50 | €750 | €25,485 | **€43,995** | €54,994 | 42.1% |
| RH-KI4-WALL-ANTHRACITE | `11217676632406` | €21,035.00 | €750 | €21,785 | **€36,995** | €46,244 | 41.1% |

All 4 are DRAFT, added to Outdoor Kitchens collection (`gid://shopify/Collection/700504277334`).

Source quotes (Customer No. 6471, quoted 2026-08-19, valid until ~2026-11-19):
- #9436 — Essentials SS Charcoal
- #9434 — Essentials Black Gas
- #9433 — KI5 Bar SS316L
- #9432 — KI4 Wall Anthracite

---

## PRICING RANGE (for reference — not live)

### Essentials Beluga Black (dealer cost €6,119 + €300 freight = €6,419 landed)
| Position | Ex. VAT | Incl. VAT | GM |
|---|---|---|---|
| Minimum | €9,995 | €12,494 | 35.8% |
| **Recommended ✓** | **€10,995** | **€13,744** | **41.6%** |
| Premium | €11,495 | €14,369 | 44.1% |
| High premium | €11,995 | €14,994 | 46.5% |

### Essentials Stainless Steel (dealer cost €5,839 + €300 = €6,139 landed)
| Position | Ex. VAT | Incl. VAT | GM |
|---|---|---|---|
| Minimum | €9,495 | €11,869 | 35.3% |
| **Recommended ✓** | **€10,495** | **€13,119** | **41.5%** |
| Premium | €10,995 | €13,744 | 44.2% |
| High premium | €11,495 | €14,369 | 46.6% |

### Kitchen Island 5M Bar (dealer cost €24,735 + €750 = €25,485 landed)
| Position | Ex. VAT | Incl. VAT | GM |
|---|---|---|---|
| Aggressive | €39,995 | €49,994 | 36.3% |
| Strong | €41,995 | €52,494 | 39.3% |
| **Recommended ✓** | **€43,995** | **€54,994** | **42.1%** |
| Premium | €45,995 | €57,494 | 44.6% |
| Luxury | €47,995 | €59,994 | 46.9% |

### Kitchen Island 4M Wall (dealer cost €21,035 + €750 = €21,785 landed)
| Position | Ex. VAT | Incl. VAT | GM |
|---|---|---|---|
| Aggressive | €33,995 | €42,494 | 35.9% |
| Strong | €35,495 | €44,369 | 38.6% |
| **Recommended ✓** | **€36,995** | **€46,244** | **41.1%** |
| Premium | €38,495 | €48,119 | 43.4% |
| Luxury | €39,995 | €49,994 | 45.5% |

---

## HOW TO PRICE FUTURE RÖSHULTS SKUs (reusable formula)

1. Get the Röshults Builder output or formal quote (gives post-30%-discount "Amount" = dealer cost).
2. Add logistics reserve: €300 for Essentials-class items, €750 for Kitchen Island-class items. Adjust once real freight is known.
3. Divide landed cost by (1 − 0.415) to hit ~41.5% GM, or adjust target within 40–45% range.
4. Round to a clean psychological price (e.g. €X,995 or €X,500).
5. Shopify variant price = ex-VAT. Customer price = variant × 1.25 for DK.
6. Create as DRAFT, tag `pending-assets` until Röshults marketing materials are in hand.
7. Do NOT build Shopify shipping profile until real freight zone rates confirmed from Niklas.

---

## PORTFOLIO ECONOMICS (4 SKUs, one of each)

| | Amount |
|---|---|
| Total revenue ex. VAT | €102,480 |
| Total dealer cost (EXW) | €57,728 |
| Total logistics reserves | €2,100 |
| Total landed cost | €59,828 |
| Gross profit | ~€42,652 |
| Blended GM | ~41.6% |

---

## DO NOT DO

- Do NOT add freight cost to the item price in Shopify (freight goes to checkout shipping profile)
- Do NOT build the shipping profile with invented rates — wait for Niklas freight quote
- Do NOT set products ACTIVE until: e-commerce webshop confirmation received + real photography in hand
- Do NOT expose Röshults dealer cost or discount % on the storefront
- Do NOT present any Röshults product with discount communication (%, crossed-out price, "deal") — hard constraint per marketing guidelines

---

*Companion to `pricing/PRICING-ENGINE-HANDOFF.md` (sauna engine). See
[[veldorahaven-roshults-timeline]] and [[veldorahaven-barrel-pricing]] memories for cross-reference.*
