# VeldoraHaven — Phase 2: Paid Acquisition Launch Plan

**Phase:** 2 — Traffic & Revenue (October 2026)  
**Trigger:** All Phase 1 exit criteria met (#16–#20 user actions resolved)  
**Goal:** First paying customers in EU markets via systematic paid acquisition  

---

## PHASE 2 ENTRY CRITERIA

All 5 must be confirmed before Phase 2 spending begins:

| # | Criterion | Status | Unblocked by |
|---|---|---|---|
| 1 | GA4 tracking verified (purchase + add_to_cart events fire) | ⚠ USER ACTION | #16 |
| 2 | Google Search Console verified + sitemap indexed | ⚠ USER ACTION | #17 |
| 3 | Klaviyo live + email capture active | ⚠ USER ACTION | #18 |
| 4 | Judge.me configured + review request active | ⚠ USER ACTION | #19 |
| 5 | All 72 product pricing configs live (or Röshults adds new SKUs) | ⚠ USER ACTION | #20 |

**Do not launch paid spend until GA4 is confirmed (#16).** All spend is unmeasurable without it.

---

## PHASE 2 OBJECTIVES

| Objective | Target | Timeframe |
|---|---|---|
| First paying customer | ≥1 order | October 2026 |
| Monthly revenue | €5,000+ | End of October |
| EU organic sessions | 200+/mo | End of October |
| Email list size | 50+ subscribers | End of October |
| Google Shopping impressions (EU) | 10,000+/mo | 4 weeks post-launch |
| Product reviews | ≥3 | End of October |

---

## ENGINE A — PAID ACQUISITION (Priority #1)

### Google Shopping

**Brief:** `growth/paid/GOOGLE-SHOPPING-BRIEF.md`

**Launch sequence:**
1. Install Shopify Google & YouTube app (if not already installed)
2. Connect product feed to Google Merchant Center
3. Create Performance Max campaign — geo: DK + DE + NL + FR only
4. Budget: €1,500/mo to start (scale on ROAS data)
5. Conversion goal: purchase event from GA4
6. Negative keywords: exclude US terms, DIY-cheap terms (see brief)
7. Review after 2 weeks — adjust bids, pause low-performers

**Expected timeline:** Live within 5 days of Phase 2 entry

### Meta (Instagram / Facebook)

**Brief:** `growth/paid/META-PINTEREST-BRIEF.md`

**Launch sequence:**
1. Verify Meta Pixel fires on veldorahaven.com (check Events Manager)
2. Create 1 awareness campaign — top-of-funnel lifestyle creative
3. Create 1 retargeting campaign — website visitors (30-day window)
4. Budget: €500/mo split 70/30 awareness/retargeting
5. Audiences: DK/DE/NL, 35–60, interests: outdoor living, sauna, Scandinavian design
6. Review after 2 weeks — test carousel vs. static

**Expected timeline:** Live within 7 days of Phase 2 entry (after Meta Pixel confirmed)

### Pinterest

Lower priority. Launch after Google Shopping is stable. €200/mo test.

---

## ENGINE B — CONVERSION & TRUST

### Klaviyo Flows

**Drafts:** `growth/email/KLAVIYO-FLOWS.md`

**Activation sequence:**
1. User confirms Klaviyo is installed and list capture is live (#18)
2. Import 3 flows from KLAVIYO-FLOWS.md:
   - Welcome sequence (2 emails)
   - Abandoned cart (3 emails)
   - Post-purchase (2 emails)
3. Test each flow with a test subscriber before activating
4. Set abandoned cart trigger: 1hr after cart abandoned

**Expected timeline:** 1 day after #18 confirmed

### Reviews (Judge.me)

Goal: 3 reviews before Meta campaign launches (social proof essential for high-ticket ads).

- Request reviews from any contacts who have seen/used Auroom products
- Configure Judge.me widget to show on all 4 barrel sauna PDPs
- Set automatic post-purchase review request: 21 days after order (allows delivery + use)

---

## ENGINE C — ORGANIC SEARCH

Phase 2 SEO is content acceleration. Infrastructure is already live (meta, descriptions, FAQ, consultation).

**Month 1 content target:** 2 new blog articles from `growth/content/CONTENT-BACKLOG.md`

Priority picks (highest commercial intent + EU geo-signal):
1. "Outdoor barrel sauna buyers guide Denmark 2026" — targets C2/C5 KPIs
2. "DIY vs pre-assembled sauna: what buyers in Germany need to know" — targets DE market

**GSC monitoring:** Once #17 confirmed, check weekly:
- Impressions for EU-language queries
- Pages with impressions but no clicks (CTR optimisation)
- Coverage errors

---

## ENGINE D — SOCIAL CONTENT

**Phase 2 content cadence (minimum viable):**
- Instagram: 3 posts/week (product, lifestyle, educational)
- Pinterest: 5 pins/week (repurpose IG content + blog imagery)
- TikTok: 1 video/2 weeks (installation process, sauna lifestyle)

Content pulled from `growth/content/CONTENT-BACKLOG.md` — 26 ideas banked.

---

## ENGINE E — B2B / TRADE

**Phase 2 outreach start:** Week 2 of October (after /trade page confirmed live + 1 review minimum)

**Target:** Contact 5 prospects from `growth/outreach/TRADE-PROSPECTS.csv`

**Sequence:**
1. LinkedIn connection + message (personalised per firm)
2. Wait 1 week → follow up with trade program details
3. If response: book call, send TRADE-PROGRAM.md

**Constraint:** Outreach requires user approval before sending (per protocol). Prepare message templates; user reviews and sends.

---

## ENGINE F — MEASUREMENT

**Week 1 Phase 2 actions (after GA4 + GSC confirmed):**
1. Update `growth/KPI-SCOREBOARD.md` with first real data
2. Set up GA4 audience segments: EU visitors, product viewers, cart abandoners
3. Link GA4 → Google Ads for conversion import
4. Set UTM tracking on all paid campaigns (per `growth/ANALYTICS-PLAN.md`)

**Weekly review cadence:** Every Monday — update KPI scoreboard, flag any KPI off-track.

---

## RÖSHULTS INTEGRATION (when partnership confirmed)

If Röshults products arrive ~week of 2026-09-07:

1. Create Outdoor Kitchens collection products in Shopify (entry via Shopify MCP)
2. Write EU-targeted SEO meta for each product
3. Update Outdoor Kitchens collection description (it currently says "coming soon")
4. Add Outdoor Kitchens back to main navigation
5. Write 1 blog article: "Outdoor Kitchen Design Guide: Röshults in Denmark" (after at least 1 product is live)

**Constraint:** Do not publish any Röshults content until user confirms partnership is formally active.

---

## BUDGET FRAMEWORK (Phase 2, Month 1)

| Channel | Budget | Notes |
|---|---|---|
| Google Shopping (Performance Max) | €1,500 | Primary acquisition |
| Meta (awareness + retargeting) | €500 | Secondary acquisition |
| Pinterest | €200 | Test only |
| **Total paid** | **€2,200/mo** | Scale on ROAS data |

**ROAS target (Month 1):** 2x (break-even at ~€4,400 revenue from €2,200 spend)  
**ROAS target (Month 2+):** 3x+ as optimisation compounds

---

## PHASE 2 EXIT → PHASE 3 (Scale)

Phase 3 triggers when ALL of:
- Monthly revenue ≥ €10,000
- ROAS ≥ 3x on Google Shopping
- ≥5 verified product reviews
- B2B pipeline: ≥2 active conversations

Expected: December 2026 / January 2027

---

*Created: 2026-08-31 — Phase 1 complete, awaiting user action on #16–#20 to enter Phase 2.*
