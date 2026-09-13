# VeldoraHaven — Google Shopping Campaign Brief

**Created:** 2026-08-31  
**KPIs unlocked:** F1, F9  
**Phase:** 1 exit / Phase 2 launch prep  
**Status:** READY FOR USER EXECUTION — do not launch before GA4 purchase event verified (queue #16)

---

## CAMPAIGN STRUCTURE

### Campaign 1 — Performance Max (primary)

**Goal:** Drive EU purchase volume across all barrel sauna product lines  
**Budget:** €1,400/mo (70% of total paid budget)  
**Geo:** Denmark, Germany, Netherlands, France — **exclude United States, Canada, Australia**  
**Products:** All 4 active barrel saunas (Halo, Luma, Nora, Sola)  
**Language targeting:** English (covers all 4 markets at Phase 1 — DE/NL/FR English copy is acceptable initially)

**Asset groups (set up 2 at minimum):**
1. **Barrel Saunas — lifestyle** — hero imagery, outdoor wellness copy
2. **Barrel Saunas — product specs** — dimension/spec-focused copy, "DIY kit" / "pre-assembled" callouts

**PMax asset requirements:**
- Headlines (15): mix of product name + spec + geo ("Outdoor Barrel Sauna Denmark", "Auroom Luma — Ships to Germany", "Premium Barrel Sauna Kit — EU Delivery")
- Descriptions (4): feature benefits, delivery confidence, consultation offer
- Images: at least 3 landscape (1200×628), 3 square (1200×1200) — use Auroom product images
- Logos: VeldoraHaven wordmark (horizontal)
- Sitelinks: /collections/barrel-saunas, /pages/faq, /pages/consultation, /pages/trade

### Campaign 2 — Standard Shopping (brand protection)

**Goal:** Capture branded searches ("VeldoraHaven", "Auroom sauna buy")  
**Budget:** €200/mo  
**Geo:** Same 4 EU markets  
**Products:** All active products  
**Priority:** LOW (runs beneath PMax)

---

## GEO TARGETING — DETAIL

| Country | Why | Priority |
|---|---|---|
| Denmark | Primary market, EUR pricing, correct fit | P1 |
| Germany | Largest EU economy, high outdoor living spend, Auroom name resonates | P1 |
| Netherlands | High disposable income, garden culture, compact market | P2 |
| France | Large market, lower language fit but worth testing | P3 |

**Exclusions (REQUIRED):** United States, Canada, Australia, New Zealand, United Kingdom (post-Brexit VAT complexity)

---

## PRODUCT FEED REQUIREMENTS

**Method:** Install Shopify Google & YouTube app (free, Shopify App Store)  
**Feed fields to verify:**
- `id` — Shopify product ID (auto-populated)
- `title` — must include model name + "outdoor barrel sauna"
- `description` — must match PDP meta description (EU-targeted, ≤5000 chars)
- `price` — EUR (confirm store currency is EUR)
- `availability` — in_stock for active products
- `google_product_category` — Home & Garden > Lawn & Garden > Outdoor Power Equipment > Other (use 121 or closest match)
- `shipping` — configure EU shipping rates in Shopify + GMC

**Custom labels (recommended for Shopping segmentation):**
- `custom_label_0`: product family (Halo / Luma / Nora / Sola)
- `custom_label_1`: price tier (premium / ultra-premium)
- `custom_label_2`: configuration (diy-kit / pre-assembled)

---

## CONVERSION TRACKING

**Required before launch:**
- GA4 purchase event → import as Google Ads conversion action
- Value: use actual order value (not fixed)
- Attribution: data-driven (default for PMax)
- Conversion window: 30 days (appropriate for high-consideration €6K–€15K purchases)

---

## NEGATIVE KEYWORD SEED LIST

Add to all campaigns as campaign-level negatives (Standard Shopping) or listed exclusions (PMax via audience signals):

**US/non-EU terms:**
- backyard, yard, deck (US terminology)
- free shipping usa, usa, united states, canada

**Low-intent / DIY-cheap:**
- cheap, discount, clearance, sale, coupon, promo code
- plans, blueprints, build your own, how to build
- free sauna

**Unrelated:**
- steam room, jacuzzi, hot tub (separate categories)
- infrared (separate product type, not in current range)
- gym, commercial (separate use case)

---

## BUDGET ALLOCATION

| Campaign | Monthly Budget | Notes |
|---|---|---|
| PMax — barrel saunas | €1,400 | Primary volume driver |
| Standard Shopping — brand | €200 | Brand protection, low cost |
| **Total** | **€1,600/mo** | Phase 2 test budget |

*Scale to €2,500–€3,500/mo if ROAS ≥ 3x sustained over 30 days.*

---

## TARGET ROAS

**Starting point:** 3x (€3 revenue per €1 ad spend)  
**Rationale:** At €8,000 AOV and 3x tROAS, cost per conversion = ~€2,667. At 15% gross margin on ad-attributed sales, that's marginally positive but builds brand data. Adjust upward to 4–5x once conversion history is established (minimum 30–50 conversions).

**Do not set target ROAS in PMax for first 30 days** — let the algorithm learn without a constraint. Switch to tROAS bidding once ≥30 conversions are recorded in the campaign.

---

## LAUNCH CHECKLIST (user)

- [ ] GA4 property verified + purchase event firing (queue #16)
- [ ] Google Ads account created (ads.google.com)
- [ ] Billing set to EUR + EU payment method
- [ ] Shopify Google & YouTube app installed + product feed approved in Google Merchant Center
- [ ] Merchant Center: business information (VAT number, shipping policy, return policy) completed
- [ ] PMax asset group built with EU copy + correct geo exclusions
- [ ] Negative keyword list uploaded to Standard Shopping
- [ ] Conversion tracking imported from GA4
- [ ] Daily budget cap set (€53/day for PMax, €7/day for Standard)

---

*Brief is for user execution. Do not attempt to set up Google Ads directly via any tool.*
