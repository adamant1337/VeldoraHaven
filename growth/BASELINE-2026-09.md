# VeldoraHaven — Live Commercial Baseline (G0.2)

**Audit date:** 2026-08-31  
**Auditor:** Primary session (Claude Sonnet 4.6)  
**Source:** Shopify MCP (live data) + repository audit  
**Purpose:** Establish ground truth before any growth activity begins. All values live-verified. Unknowns marked explicitly.

---

## 1. STORE BASICS

| Field | Value |
|---|---|
| Store name | Veldora Haven |
| Domain | www.veldorahaven.com |
| Contact email | info@veldorahaven.com |
| Shopify plan | Shopify (mid-tier) |
| Currency | EUR |
| Country / tax jurisdiction | Denmark |
| Tax model | ADD_TAXES_AT_CHECKOUT — ex-VAT prices, 25% DK VAT added at checkout |
| Timezone | CEST (Europe/Copenhagen) |

---

## 2. COMMERCIAL STATE — REVENUE

**Revenue to date: €0. Zero orders ever placed.**

| Month | Sessions | Visitors | Orders | Revenue | AOV | Conversion |
|---|---|---|---|---|---|---|
| 2026-02 | ~0 | ~0 | 0 | €0 | — | 0% |
| 2026-03 | ~0 | ~0 | 0 | €0 | — | 0% |
| 2026-04 | ~0 | ~0 | 0 | €0 | — | 0% |
| 2026-05 | 1 | 1 | 0 | €0 | — | 0% |
| 2026-06 | 49 | 49 | 0 | €0 | — | 0% |
| 2026-07 | 170 | 170 | 0 | €0 | — | 0% |
| 2026-08 | 898 | 832 | 0 | €0 | — | 0% |
| **TOTAL** | **1,118** | **~1,052** | **0** | **€0** | **—** | **0%** |

**Assessment:** Pre-launch. Store has never transacted. Traffic is growing (organic/direct only — no paid acquisition yet). August shows a 5× jump over July — likely organic search gaining traction.

**Referral source breakdown:** UNKNOWN — DATA REQUIRED (ShopifyQL `session_referrer_source` column not available via API; requires GA4 or Shopify Analytics dashboard access).

---

## 3. PRODUCT CATALOGUE

### 3.1 Active Products (sellable now)

| # | Product | Vendor | Type | Variants | Min Price | Status |
|---|---|---|---|---|---|---|
| 1 | Halo — Outdoor Barrel Sauna | Auroom Wellness | Barrel Sauna | 28 | €6,100 | ACTIVE ✓ |
| 2 | Luma — Outdoor Barrel Sauna with Porch | Auroom Wellness | Barrel Sauna | 24 | €7,300 | ACTIVE ✓ |
| 3 | Nora — Outdoor Square Barrel Sauna | Auroom Wellness | Barrel Sauna | 8 | €9,000 | ACTIVE ✓ |
| 4 | Sola — Square Barrel Sauna | Auroom Wellness | Barrel Sauna | 12 | €7,200 | ACTIVE ✓ |
| 5 | HUUM Electric Sauna Heater | HUUM | Sauna Heater | 5 | €1,130 | ACTIVE ✓ |
| 6 | HUUM Wood-Burning Sauna Heater | HUUM | Sauna Heater | 2 | €2,230 | ACTIVE ✓ |
| 7 | Harvia Electric Sauna Heater | Harvia | Sauna Heater | 5 | €640 | ACTIVE ✓ |
| 8 | Harvia Wood-Burning Sauna Heater | Harvia | Sauna Heater | 2 | €1,510 | ACTIVE ✓ |
| 9 | Wood-Burning Heater Installation Service | Auroom Wellness | Service | 1 | €180 | ACTIVE ✓ |

**Active total: 9 products / 87 variants**  
**Commercially sellable Auroom barrel saunas: 4 (Halo/Luma/Nora/Sola) = 72 variants**

### 3.2 Draft Products (in catalogue, not live)

| Product | Vendor | Type | Min Price | Blocker |
|---|---|---|---|---|
| Kaia — Garden Sauna Cabin | Auroom | Barrel Sauna | **€0** | Pricing not set |
| Sauna & Cold Plunge Bundle | Auroom Wellness | Bundle | €12,300 | DRAFT |
| VelAqua — Outdoor Wellness Shower | Auroom Wellness | Outdoor Shower | €5,200 | DRAFT |
| Auroom Arti — Compact Outdoor Designer Sauna | Auroom Wellness | Sauna | €7,500 | DRAFT |
| Auroom Terra — Modular Outdoor Sauna | Auroom Wellness | Sauna | €9,500 | DRAFT |
| Auroom Aurea — LED Outdoor Sauna | Auroom Wellness | Sauna | €11,000 | DRAFT |
| Premium Cold Plunge with Advanced Filtration | Auroom Wellness | Cold Plunge | €9,500 | DRAFT |
| Chiller-Equipped Cold Plunge Tub | Auroom Wellness | Cold Plunge | €5,500 | DRAFT |
| EcoSmart Fire Nova 850 | EcoSmart Fire | Fire Pit | €4,200 | DRAFT — prospective partner |
| EcoSmart Fire Nova 600 | EcoSmart Fire | Fire Pit | €2,400 | DRAFT — prospective partner |
| EcoSmart Fire Mix 850 | EcoSmart Fire | Fire Pit | €3,800 | DRAFT — prospective partner |
| EcoSmart Fire Mix 600 | EcoSmart Fire | Fire Pit | €2,400 | DRAFT — prospective partner |
| EcoSmart Fire Pod 40 | EcoSmart Fire | Fire Pit | €4,800 | DRAFT — prospective partner |
| EcoSmart Fire Pod 30 | EcoSmart Fire | Fire Pit | €3,400 | DRAFT — prospective partner |
| EcoSmart Fire Stix 8 | EcoSmart Fire | Fire Pit | €4,500 | DRAFT — prospective partner |
| EcoSmart Fire Stix | EcoSmart Fire | Fire Pit | €3,200 | DRAFT — prospective partner |
| Gloster Grand Sail — Modular Outdoor Sectional | Gloster | Outdoor Furniture | €12,000 | DRAFT — future target |
| Gloster Fern — Designer Outdoor Lounge | Gloster | Outdoor Furniture | €8,500 | DRAFT — future target |
| Luxury Outdoor Sectional Furniture Set | Zuo Modern | Outdoor Furniture | €5,500 | DRAFT |
| Luxury Aluminium Pergola 12×16ft | Aluminum Pergola Co. | Pergola | €7,500 | DRAFT |
| Bundle: Lounge + Pergola — Covered Terrace | Veldora Haven | Bundle | €14,800 | DRAFT |
| Bundle: Grill Island + Furniture | Veldora Haven | Bundle | €15,400 | DRAFT |
| Bundle: Sauna + Plunge + Shower | Veldora Haven | Bundle | €16,900 | DRAFT |
| Auroom Luma (old) | Auroom Wellness | Sauna | €6,500 | **ARCHIVED** |

**Draft total: 23 products** (including 8 EcoSmart — prospective partner only)

### 3.3 Pricing Gaps

| Model | Issue | Action Required |
|---|---|---|
| Kaia — S/L × NW/BB | All variants priced at €0 | Auroom pricing needed before publish |
| Halo Cosy 120 Pre-assembled (NW + BB) | Assembly cost missing | Request from Silga/Auroom |
| Nora 210 Pre-assembled (NW + BB) | Assembly cost missing | Request from Silga/Auroom |
| Sola 250 Pre-assembled (NW + BB) | Assembly cost missing | Request from Silga/Auroom |

**6 pricing configs BLOCKED** (Group C from pricing handoff).

---

## 4. COLLECTION ARCHITECTURE

| Collection | Handle | Products | Status | Notes |
|---|---|---|---|---|
| Barrel Saunas | barrel-saunas | 4 | ✓ Active | All 4 core Auroom products |
| Saunas | saunas | 7 | ✓ Active | Barrel + cabin + designer |
| Sauna Accessories | sauna-accessories | 4 | ✓ Active | HUUM + Harvia heaters |
| Cold Plunge | cold-plunge-ice-baths | 3 | ⚠ Draft products only | No active cold plunge for sale |
| Fire Features | fire-features | 8 | ⚠ Draft products only | All EcoSmart — prospective partner |
| Outdoor Furniture & Pergolas | outdoor-furniture-pergolas | 4 | ⚠ Draft products only | Gloster (future) + generic |
| Complete Bundles | complete-bundles | 4 | ⚠ Mostly draft | Bundle pages not live |
| Outdoor Baths & Hot Tubs | outdoor-baths-hot-tubs | 1 | ⚠ Draft only | VelAqua shower only |
| Cabin Saunas | cabin-saunas | 3 | ⚠ Draft only | Terra/Arti/Aurea — not active |
| **Outdoor Kitchens** | outdoor-kitchens | **0** | ❌ Empty | No products — image placeholder only |
| **Infrared Saunas** | infrared-saunas | **0** | ❌ Empty | No products |

**Critical finding:** Two collections are completely empty (Outdoor Kitchens, Infrared Saunas). Four collections contain only draft/non-active products — they appear in navigation but lead to no purchasable items.

---

## 5. TRUST INFRASTRUCTURE

| Page | Handle | Status | Quality |
|---|---|---|---|
| Shipping & Delivery | /pages/shipping-delivery | ✓ Published | Confirmed live |
| Returns & Cancellation | /pages/returns-cancellation | ✓ Published | Confirmed live |
| Warranty & Aftercare | /pages/warranty-aftercare | ✓ Published | Confirmed live |
| How It Works | /pages/how-it-works | ✓ Published | Confirmed live |
| Our Story | /pages/our-story | ✓ Published | Confirmed live |
| Contact Us | /pages/contact | ✓ Published | Confirmed live |
| Privacy Policy | /pages/privacy-policy | ✓ Published (Aug 3) | Confirmed live |
| Terms of Service | /pages/terms-of-service | ✓ Published (Aug 3) | Confirmed live |
| Partners | /pages/partners | ✓ Published (Aug 25) | Auroom confirmed; others prospective only |
| **FAQ** | — | ❌ **DOES NOT EXIST** | Not built |
| **Trade / B2B** | — | ❌ **DOES NOT EXIST** | Not built |
| **Consultation** | — | ❌ **DOES NOT EXIST** | Not built |
| **Financing / Affirm/Klarna info** | — | ❌ **UNKNOWN** | Not found in pages |

**Trust assessment:** Core legal and logistical trust pages are in place. Customer reassurance (FAQ, consultation path, financing explainer) is missing. Trade program has no public entry point.

---

## 6. JOURNAL (BLOG)

| Article | Published | Handle |
|---|---|---|
| Choosing an Outdoor Barrel Sauna: What to Look for Before You Buy | ✓ Jul 30, 2026 | best-outdoor-barrel-saunas-for-your-backyard-in-2026 |
| Cold Plunge: What Separates a Good System from an Expensive Tub | ✓ Jul 30, 2026 | cold-plunge-tubs-the-complete-buyers-guide |
| Outdoor Kitchen Specification: The Questions Worth Asking Before You Build | ✓ Jul 30, 2026 | how-to-design-the-perfect-outdoor-kitchen |
| Auroom Terra vs Arti: Which Outdoor Sauna Is Right for Your Garden? | ❌ DRAFT | auroom-terra-vs-arti-which-outdoor-sauna-is-right-for-your-garden |
| Inside the Auroom Aurea: Why LED Lighting Changes the Sauna Experience | ❌ DRAFT | inside-the-auroom-aurea-why-led-lighting-changes-the-sauna-experience |
| Barrel Sauna Buying Guide 2026: Auroom Luma vs Traditional Cedar | ❌ DRAFT | barrel-sauna-buying-guide-2026-auroom-luma-vs-traditional-cedar |

**Journal: 3 published, 3 draft. Blog exists (handle: outdoor-living). No publishing cadence established.**

**Note:** "Outdoor Kitchen Specification" article exists but Outdoor Kitchens collection is empty — no products to link to.

---

## 7. SUPPLIER STATUS

| Supplier | Products in Store | Status | Publicly Represented As |
|---|---|---|---|
| Auroom Wellness | 4 ACTIVE barrel saunas + service | ✓ CONFIRMED authorized retailer | Partner on /pages/partners ✓ |
| HUUM | 2 ACTIVE heaters | Supplier — partnership status UNKNOWN | Vendor on product page |
| Harvia | 2 ACTIVE heaters | Supplier — partnership status UNKNOWN | Vendor on product page |
| EcoSmart Fire | 8 DRAFT fire pits | ⚠ PROSPECTIVE — NOT confirmed | DRAFT only — not published |
| Gloster | 2 DRAFT furniture | FUTURE TARGET — not started | DRAFT only — not published |
| Aluminum Pergola Co. | 1 DRAFT pergola | UNKNOWN — generic brand | DRAFT only — not published |
| Zuo Modern | 1 DRAFT furniture | UNKNOWN | DRAFT only — not published |

**Protocol check:** EcoSmart Fire and Gloster products remain DRAFT. No prospective partner is publicly represented as confirmed. ✓

---

## 8. SEO STATE

| Area | Status | Evidence |
|---|---|---|
| Product SEO titles/descriptions | UNKNOWN — DATA REQUIRED | Not audited via MCP (would require per-product metafield query) |
| Collection SEO titles/descriptions | UNKNOWN — DATA REQUIRED | Not audited |
| Blog SEO | UNKNOWN — DATA REQUIRED | Article titles appear keyword-relevant but meta descriptions not audited |
| JSON-LD structured data | PARTIAL — Product schema done; FAQPage skipped | Per STATE.md (R5 complete) |
| Google Search Console | UNKNOWN — DATA REQUIRED | No GSC data in repo |
| Google Analytics 4 | UNKNOWN — DATA REQUIRED | No GA4 config file in repo |
| Sitemap | Shopify auto-generates | Assumed present at /sitemap.xml |
| robots.txt | Shopify default | Not customized (assumed) |

**SEO assessment:** Technical SEO foundations in place (structured data, Shopify native sitemap). Content SEO and analytics measurement status unknown — requires GSC + GA4 access.

---

## 9. ANALYTICS & TRACKING

| System | Status | Evidence |
|---|---|---|
| Shopify Analytics | ACTIVE | Sessions/revenue data confirmed via MCP |
| Google Analytics 4 | UNKNOWN — DATA REQUIRED | No tracking confirmed; no .env/config reference in repo |
| Google Search Console | UNKNOWN — DATA REQUIRED | No verification confirmed |
| Meta Pixel | UNKNOWN — DATA REQUIRED | Not verified |
| Google Ads | NOT ACTIVE | No paid traffic (0 conversions, organic-only sessions) |
| Meta Ads | NOT ACTIVE | No paid traffic |
| Pinterest Ads | NOT ACTIVE | No paid traffic |
| Klaviyo / Email | UNKNOWN — DATA REQUIRED | Plan mentions Klaviyo; not confirmed live |
| UTM tracking | UNKNOWN — DATA REQUIRED | No UTM data in repo |

**Analytics assessment:** Shopify native analytics confirmed. All third-party tracking (GA4, Meta Pixel, GSC) is unverified. No paid acquisition active.

---

## 10. SOCIAL PRESENCE

| Channel | Status | Evidence |
|---|---|---|
| Instagram | UNKNOWN — DATA REQUIRED | Not verified |
| Pinterest | UNKNOWN — DATA REQUIRED | Not verified |
| TikTok | UNKNOWN — DATA REQUIRED | Not verified |
| YouTube | UNKNOWN — DATA REQUIRED | Not verified |
| Facebook | UNKNOWN — DATA REQUIRED | Not verified |

**Social assessment:** Business plan identifies Instagram/Pinterest/TikTok/YouTube as target channels. Current social presence and follower counts are unknown — requires manual audit of each platform.

---

## 11. TRAFFIC PERFORMANCE SUMMARY

| Metric | Value | Notes |
|---|---|---|
| Total sessions (all time) | 1,118 | Shopify Analytics |
| Sessions Aug 2026 | 898 | 5× jump vs July — organic gaining |
| Unique visitors Aug | 832 | |
| Conversion rate (all time) | **0%** | No orders ever |
| Revenue (all time) | **€0** | Store has never transacted |
| Avg Order Value | — | No orders to measure |
| Top traffic source | UNKNOWN — DATA REQUIRED | Session referrer API unavailable; needs GA4 |

**Traffic assessment:** Store is building organic presence. 898 sessions in August suggests the site is indexed and being found. Critical gap: no GA4 to understand WHERE traffic comes from or which pages drive it.

### Conversion Funnel Detail (August 2026)

| Funnel Stage | Count | Rate vs Sessions |
|---|---|---|
| Sessions | 898 | 100% |
| Sessions with cart addition | 4 | 0.45% |
| Sessions reaching checkout | 1 | 0.11% |
| Sessions completing checkout | 0 | 0% |

### Device Split (last 90 days)

| Device | Sessions | Share |
|---|---|---|
| Desktop | 1,048 | 93.9% |
| Mobile | 65 | 5.8% |
| Other | 3 | 0.3% |

**Device note:** 94% desktop is expected for high-ticket €6K–€15K products — buyers research on desktop. Mobile de-prioritised correctly.

### Geography (last 90 days) — ⚠ CRITICAL MISMATCH

| Country | Sessions | Share |
|---|---|---|
| **United States** | **991** | **88.8%** |
| Denmark | 63 | 5.6% |
| Latvia | 13 | 1.2% |
| France | 8 | 0.7% |
| Germany | 8 | 0.7% |
| Luxembourg | 6 | 0.5% |
| Czechia | 5 | 0.4% |
| Others | 22 | 2.0% |

**⚠ CRITICAL FINDING: 89% of traffic originates from the United States.** The store is configured for Denmark / EU (EUR pricing, DK tax, EU shipping). US visitors cannot purchase — the store either redirects them with unsuitable tax/shipping, or they bounce on delivery scope. This explains the near-zero add-to-cart rate (0.45%).

**Root cause hypotheses:**
1. Blog articles ("Choosing an Outdoor Barrel Sauna", "Cold Plunge") are ranking in US Google — unintended US organic traffic
2. Early social/referral traffic from US sources
3. Possible bot traffic from US IPs
4. SEO meta is not geo-targeted; no hreflang configured

**Action required:** Confirm actual EU target markets. Evaluate whether to geographically restrict paid acquisition. Assess if blog content should target EU-specific search intent. Consider hreflang implementation for EU markets.

---

## 12. CONVERSION READINESS

| Factor | Status | Severity |
|---|---|---|
| 4 barrel saunas active + priced | ✓ READY | — |
| 4 heaters active + priced | ✓ READY | — |
| Trust pages (shipping/returns/warranty) | ✓ READY | — |
| Contact + How It Works pages | ✓ READY | — |
| Partners page (Auroom) | ✓ READY | — |
| Zero reviews / social proof | ❌ MISSING | HIGH |
| Financing / BNPL not confirmed | ⚠ UNKNOWN | HIGH (for €6K–€15K+ purchases) |
| FAQ page missing | ❌ MISSING | MEDIUM |
| Consultation/inquiry flow | ❌ MISSING | MEDIUM |
| GA4 tracking unverified | ⚠ UNKNOWN | HIGH (can't measure conversion) |
| Live chat | UNKNOWN — DATA REQUIRED | MEDIUM |
| Phone number visible on pages | UNKNOWN — DATA REQUIRED | MEDIUM |
| Payment methods available | UNKNOWN — DATA REQUIRED | MEDIUM |

**Conversion readiness: PARTIAL.** The store can technically accept orders on active products. But zero social proof, unconfirmed financing, and unverified analytics mean first orders will be hard to diagnose and replicate.

---

## 13. CATALOGUE COMPLETENESS vs BUSINESS PLAN

| Category | Business Plan Target | Live Today | Gap |
|---|---|---|---|
| Barrel Saunas | Core category | ✓ 4 products ACTIVE | None |
| Sauna Heaters | Add-on | ✓ 4 products ACTIVE | None |
| Cold Plunge | Core category | ❌ 0 active products | High |
| Hot Tubs / Outdoor Baths | Core category | ❌ 0 active products (VelAqua shower is draft) | High |
| Outdoor Kitchens | Core category | ❌ 0 products at all | High |
| Fire Features | Core category | ❌ 0 active products (EcoSmart prospective) | High |
| Outdoor Furniture | Core category | ❌ 0 active products | High |
| Pergolas | Category | ❌ 0 active products | High |
| Bundles | Strategy | ❌ 0 active bundles | Medium |

**Catalogue gap:** 7 of 9 planned categories have zero active/purchasable products. The store is currently a single-category retailer (barrel saunas + heater add-ons).

---

## 14. PHASE 1 EXIT CRITERIA STATUS

Per Growth OS: *"VeldoraHaven is ready to receive systematic qualified traffic."*

| Criterion | Status |
|---|---|
| Core product architecture live | ✓ YES — 4 barrel saunas + heaters |
| Pricing verified | PARTIAL — 66/72 configs; 6 blocked |
| Imagery complete | PARTIAL — heater images partial; barrel saunas ✓ |
| SEO metadata verified | UNKNOWN |
| Measurement infrastructure confirmed | ❌ NO — GA4/GSC unverified |
| Trust pages live | ✓ YES — 8 pages published |
| Supplier expansion in progress | PARTIAL — Röshults files local, not in Shopify |
| Trade program built | ❌ NO — /trade page does not exist |
| Review system collecting | ❌ NO — 0 reviews |

**Phase 1 exit criteria: NOT MET.**  
Primary blockers: measurement unverified, trade program absent, zero social proof.

---

## 15. PRIORITY ACTIONS (for G0.4 queue)

Ranked by dependency and growth impact:

| Rank | Action | Category | Effort | Autonomous? |
|---|---|---|---|---|
| 1 | Verify GA4 / GSC tracking is live | Analytics | Low | ⚠ Needs user access |
| 2 | Audit product SEO meta (titles/descriptions on 9 active products) | SEO | Medium | ✓ Yes |
| 3 | Publish 3 draft blog articles (Terra/Arti, Aurea, Barrel Guide) | Content | Low | ✓ Yes (with approval) |
| 4 | Build /trade B2B page | B2B | Medium | ✓ Yes |
| 5 | Activate Klaviyo email capture | Email/CRM | Low | ⚠ Needs user platform access |
| 6 | Build /faq page | Trust/CRO | Medium | ✓ Yes |
| 7 | Write Auroom Seo metadata for all 4 barrel sauna products | SEO | Medium | ✓ Yes |
| 8 | Activate Judge.me and publish review request to past contacts | Reviews | Low | ⚠ Needs user dashboard |
| 9 | Confirm Röshults supplier status + prepare first product | Supplier | Low | ⚠ Needs user |
| 10 | Unblock 6 Group C pricing configs (Halo 120/Nora 210/Sola 250 Pre) | Pricing | Low | ⚠ Needs Auroom data |

---

## 16. KNOWN UNKNOWNS

The following cannot be verified without user access to external platforms:

- GA4 property ID and whether tracking fires on veldorahaven.com
- Google Search Console verification and index coverage
- Meta Pixel ID and verification
- Klaviyo account and list size
- Judge.me review count (assumed zero from JUDGEME-EMBED-001 notes)
- Instagram / Pinterest / TikTok handle and follower counts
- Financing provider (Affirm/Klarna) — whether configured in Shopify checkout
- Payment methods available at checkout
- Live chat provider (if any)
- Röshults partnership status (confirmed vs prospective)

---

*G0.2 complete. Next: G0.3 — KPI BASELINE (`growth/KPI-SCOREBOARD.md`).*
