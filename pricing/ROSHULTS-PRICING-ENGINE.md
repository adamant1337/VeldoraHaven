# VeldoraHaven × Röshults Pricing Engine

**Date:** 2026-09-01
**Modeled on:** `pricing/PRICING-ENGINE-HANDOFF.md` (the Auroom sauna pricing engine) — same discipline
(verified facts → cost architecture → commercial decision → per-SKU table → blockers), different
formula, because the supplier relationship is structurally different.

**Current phase:** 4 entry-point SKUs built (DRAFT, unpublished). Freight not yet incorporated —
BLOCKED pending Niklas Sahlqvist (Röshults COO) freight-by-zone quote.

---

## WHY THIS FORMULA IS NOT THE SAUNA FORMULA

The sauna engine computes `GM = (Shopify_price − Landed_cost) / Shopify_price` against a target of
52.5%, because Auroom's EXW price is a true **factory production cost** — VeldoraHaven is free to set
any retail margin on top of it.

Röshults is a different relationship: Röshults quotes a **30% trade discount off their own published
retail price list** — the same list price Röshults sells at directly on roshults.com. The discount
*is* the entire dealer margin, not a floor to build further margin on top of. Applying the sauna's
52.5%-style markup on top of the discounted cost would price VeldoraHaven's kitchens far above
Röshults' own direct-to-consumer prices — not credible, and likely a MAP (minimum advertised price)
violation for an authorized dealer of a brand that also sells DTC.

**Decision (confirmed 2026-09-01):** Retail price = parity with Röshults' own suggested retail
(the pre-discount "Unit Price" line total on each quote). No markup on top. Margin = the 30% trade
discount, minus freight and payment/operational costs once known.

---

## VERIFIED FACTS

| Field | Value |
|---|---|
| Currency | EUR |
| Shop `taxesIncluded` | `false` (same as sauna) |
| Denmark market tax strategy | `ADD_TAXES_AT_CHECKOUT` |
| Röshults quote basis | EXW Jönköping, Sweden, EUR, no VAT (export quote) |
| Röshults payment terms | 50% at order confirmation, 50% before delivery |
| Röshults quote validity | 3 months from quote date |

**Critical interpretation (same rule as sauna engine):** Shopify variant price = ex-VAT retail price.
Customer total (Denmark) = variant price × 1.25. Do not treat stored prices as VAT-inclusive.

---

## COST ARCHITECTURE

```
Dealer_cost (EXW)  = Röshults_retail_list_price × (1 − 0.30)
Retail_price        = Röshults_retail_list_price   (parity — no markup)
Landed_cost          = Dealer_cost + Freight_to_customer   ← Freight = BLOCKED, see below
Effective_margin     = (Retail_price − Landed_cost) / Retail_price
                     = 30% minus (Freight_to_customer / Retail_price) minus opex
```

Before freight is known, `Effective_margin` is not final — treat the 30% figure per SKU below as
gross-before-freight, not the number the business actually nets.

---

## FREIGHT — BLOCKED, NOT YET IN THE FORMULA

Röshults quotes customer freight "per project and delivery address" under Incoterms DAP — no rate
card exists yet. Decision already made on structure: freight will be **calculated separately at
checkout**, not baked into the item price (fair to nearby vs. far customers; standard for freight-class
items like a 192kg kitchen island), using a Shopify shipping profile scoped to the Outdoor Kitchens
collection with (loosely) 3 distance zones from Jönköping, Sweden.

**Do not build the shipping profile or any zone rate numbers yet.** Shipping profiles are live
storefront-wide the moment they're configured — unlike DRAFT products, there's no safe unpublished
state for shipping rates. Wait for real DAP figures from Niklas before configuring anything.

**Next action:** once the user has spoken to Niklas and has indicative DAP freight for representative
zones (e.g. Denmark/Nordics, Central/Western EU, Southern/Eastern EU) for a heavy item like the KI4/KI5
islands, build the zone shipping profile and re-run `Effective_margin` per SKU to confirm all 4 SKUs
still clear a reasonable floor (no floor number agreed yet — TBD alongside the freight conversation).

---

## PER-SKU TABLE (4 entry-point SKUs, built 2026-09-01)

| SKU | Product GID | Röshults retail (=VH price, ex-VAT) | Dealer cost (EXW, after 30%) | Gross margin (pre-freight) |
|---|---|---|---|---|
| RH-ESSENTIALS-SS-CHARCOAL | `gid://shopify/Product/11217676534102` | €8,342 | €5,839.40 | 30.0% |
| RH-ESSENTIALS-BLACK-GAS | `gid://shopify/Product/11217676566870` | €8,742 | €6,119.40 | 30.0% |
| RH-KI5-BAR-SS316L | `gid://shopify/Product/11217676599638` | €35,335 | €24,734.50 | 30.0% |
| RH-KI4-WALL-ANTHRACITE | `gid://shopify/Product/11217676632406` | €30,050 | €21,035.00 | 30.0% |

All 4 are DRAFT, added to the Outdoor Kitchens collection, tagged `pending-contract`, zero images.

Source quotes (Customer No. 6471, quoted 2026-08-19, valid until ~2026-11-19): #9436 (Essentials SS),
#9434 (Essentials Black), #9433 (KI5 Bar), #9432 (KI4 Wall). Matching Röshults Builder configurator
spec sheets (renders + dimensions) held on file for PDP content once contract is signed.

---

## HOW TO PRICE FUTURE RÖSHULTS SKUs (reusable formula)

1. Get the quote or Röshults Online Builder output for the configuration (gives both the pre-discount
   "Unit Price" list and the post-30%-discount "Amount").
2. Sum the pre-discount Unit Price lines → that is the VeldoraHaven retail price (ex-VAT), no markup.
3. Sum the discounted Amount lines → that is the dealer cost, for internal margin tracking only
   (never expose on the storefront).
4. Do not add freight to the item price. Once the zone shipping profile exists, freight is a separate
   checkout line.
5. Create as DRAFT, tag `pending-contract` until the contract is signed, no images until Röshults
   marketing materials are released.

---

## DO NOT DO

- Do NOT apply the sauna's 52.5%/45% GM thresholds to Röshults SKUs — wrong formula for this
  supplier relationship (see WHY section above)
- Do NOT set these products ACTIVE until: contract signed + freight resolved + real photography in hand
- Do NOT build shipping rate numbers without a real Niklas freight quote
- Do NOT expose Röshults dealer cost/discount % on the storefront
- Do NOT mark up above Röshults' own retail price without an explicit new user decision (MAP risk)

---

*Companion to `pricing/PRICING-ENGINE-HANDOFF.md` (sauna engine). See
[[veldorahaven-roshults-timeline]] and [[veldorahaven-barrel-pricing]] memories for cross-reference.*
