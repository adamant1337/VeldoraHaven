# VeldoraHaven — Growth Priority Queue (G0.4)

**Created:** 2026-08-31  
**Source:** G0.2 + G0.3 findings  
**Ordering logic:** (1) Dependency unlock value → (2) Autonomous vs user-blocked → (3) Revenue impact  
**Review cadence:** Updated at each phase gate and when blockers resolve  

---

## HOW TO READ THIS QUEUE

**Autonomous** = can be executed in this session without user access to external platforms.  
**User-blocked** = requires user login, supplier contact, or external platform action.  
**Dependency unlock** = completing this task unblocks multiple downstream tasks.

Tasks are sequenced so autonomous work is always available to run. User-blocked tasks are grouped at the bottom and can be actioned in parallel by the user while autonomous work continues.

---

## SECTION A — AUTONOMOUS (execute now, no external access needed)

### #1 — SEO Meta Audit + Optimisation: 9 Active Products

**Engine:** C — Organic Search  
**KPIs unlocked:** C5, C6  
**Effort:** Medium (1 session)  
**Dependency unlock:** HIGH — without verified meta, organic search is unoptimised; blocks C2/C3 targets  
**Revenue impact:** HIGH — correct EU-intent meta titles reduce US bounce, attract EU buyers

**Task:** Query Shopify MCP for SEO title and meta description on all 9 active products (4 barrel saunas + 4 heaters + 1 service). For any missing or generic meta: write EU-market-targeted meta title (≤60 chars) and description (≤155 chars) with primary keyword + location qualifier (e.g. "outdoor barrel sauna Denmark"). Update via Shopify MCP.

**Output:** SEO meta confirmed live on all 9 products. Log findings in `growth/seo/SEO-META-AUDIT.md`.

---

### #2 — Publish 3 Draft Blog Articles

**Engine:** C — Organic Search  
**KPIs unlocked:** C7, C9  
**Effort:** Low (1 session — approval required before publish)  
**Dependency unlock:** MEDIUM — 3 ready-to-publish drafts; immediate EU organic content signal  
**Revenue impact:** MEDIUM — each article is a long-tail EU keyword entry point

**Task:** Review 3 draft articles (Terra vs Arti, Aurea LED, Luma vs Cedar). Confirm each links internally to at least one PDP. Add EU geo-relevant language where absent. Confirm with user, then publish via Shopify MCP.

**Constraint:** Confirm with user before publishing. Do not fabricate review quotes or product claims not in existing copy.

**Output:** 3 articles published. Journal count: 6. Log in `GROWTH-STATE.md`.

---

### #3 — Build /pages/faq

**Engine:** B — Conversion & Trust  
**KPIs unlocked:** B6  
**Effort:** Medium (1 session)  
**Dependency unlock:** MEDIUM — resolves a known trust gap for high-ticket buyers  
**Revenue impact:** HIGH — FAQ is the #1 objection-handler for €6K–€15K purchases; reduces pre-sale email load

**Task:** Write and publish a comprehensive FAQ page covering: delivery timelines, assembly process (DIY vs pre-assembled), warranty/aftercare, payment methods, VAT/tax, returns, sauna sizing, installation requirements, and consultation/contact path. Publish at `/pages/faq`. Add to store navigation.

**Output:** `/pages/faq` published. B6 KPI: 9/11 trust pages live.

---

### #4 — Build /trade Page + TRADE-PROGRAM.md

**Engine:** E — B2B / Trade  
**KPIs unlocked:** E1, E2  
**Effort:** Medium (1 session)  
**Dependency unlock:** HIGH — without a public trade page there is no B2B engine. Outreach cannot start until the landing page exists.  
**Revenue impact:** HIGH — trade/B2B accounts for 20–30% of high-ticket outdoor living revenue in EU markets

**Task:**  
1. Write `growth/outreach/TRADE-PROGRAM.md` defining the program: trade discount tier, eligibility criteria (landscapers, architects, garden design studios, luxury property developers), application process, Auroom-specific benefits (dropship, lead times, no inventory).  
2. Build `/pages/trade` on Shopify: headline, who qualifies, benefits, application form or contact link. Publish.

**Constraint:** Do not promise specific discount % until Peter confirms the margin structure permits it. Use "preferential trade pricing" until confirmed.

**Output:** `/pages/trade` live. `TRADE-PROGRAM.md` written. E1 + E2 KPIs met.

---

### #5 — Define Content Pillars + CONTENT-BACKLOG.md

**Engine:** D — Social Content  
**KPIs unlocked:** D6  
**Effort:** Low-Medium (1 session)  
**Dependency unlock:** MEDIUM — without defined pillars, content creation is ad hoc; defines the engine  
**Revenue impact:** MEDIUM (long-term organic + social)

**Task:** Write `growth/content/CONTENT-BACKLOG.md`. Define 4–5 content pillars (e.g. product education, lifestyle/aspirational, installation/process, buyer journey, Scandinavian design aesthetic). Populate 20+ content ideas across Instagram, Pinterest, blog, and TikTok. Tag each idea by pillar, channel, and estimated effort.

**Output:** `growth/content/CONTENT-BACKLOG.md` created. D6 KPI met.

---

### #6 — Internal Link Audit: Blog → PDPs

**Engine:** C — Organic Search  
**KPIs unlocked:** C9  
**Effort:** Low (single pass)  
**Dependency unlock:** LOW-MEDIUM — links from blog articles to PDPs pass PageRank and drive discovery  
**Revenue impact:** MEDIUM — each article→PDP link is a direct buyer entry point

**Task:** Read all 3 published blog articles. Confirm each contains ≥2 in-text links to relevant product pages (barrel sauna PDPs, collection pages). Add missing links via Shopify MCP article update. Flag if articles need EU context added.

**Output:** 3 articles each with ≥2 internal links to PDPs confirmed. Note in `SEO-META-AUDIT.md`.

---

### #7 — Define UTM Convention + ANALYTICS-PLAN.md

**Engine:** F — Paid Acquisition / All engines  
**KPIs unlocked:** F10, G9  
**Effort:** Low (documentation task)  
**Dependency unlock:** HIGH — without a UTM convention, all paid and social traffic is unattributable. Must be defined before any paid campaign or social post goes live.  
**Revenue impact:** Indirect — enables measurement of all other revenue work

**Task:** Write `growth/ANALYTICS-PLAN.md` defining:
- UTM parameter convention for all channels (Google Ads, Meta, Pinterest, Email, Social organic)
- GA4 event naming convention (purchase, add_to_cart, begin_checkout, consult_click)
- Conversion goal definitions
- Reporting cadence + ownership

**Output:** `growth/ANALYTICS-PLAN.md` created. Share with user for review before any paid spend.

---

### #8 — Draft Klaviyo Email Flows (ready to deploy)

**Engine:** G — Email / CRM  
**KPIs unlocked:** G5, G6  
**Effort:** Medium (1 session)  
**Dependency unlock:** LOW (user must first confirm Klaviyo is live — see #17)  
**Revenue impact:** HIGH once live — abandoned cart recovery is highest-ROI email for high-ticket

**Task:** Write copy for 3 core Klaviyo flows, ready for import:
1. Welcome sequence (2 emails): brand story → why VeldoraHaven → product education → first CTA
2. Abandoned cart flow (3 emails): cart reminder → social proof / trust → urgency/scarcity-free follow-up → consultation offer
3. Post-purchase sequence (2 emails): delivery confirmation → care guide → review request (Judge.me)

Store drafts in `growth/email/KLAVIYO-FLOWS.md`. User imports to Klaviyo when account confirmed.

**Output:** `growth/email/KLAVIYO-FLOWS.md` with 7 email drafts. G5/G6 ready to activate.

---

### #9 — Hreflang Evaluation + Decision Memo

**Engine:** C — Organic Search  
**KPIs unlocked:** C10  
**Effort:** Low (research + memo)  
**Dependency unlock:** LOW-MEDIUM — resolves the EU geo-signal gap  
**Revenue impact:** MEDIUM long-term — correct geo-targeting reduces US bounce in search

**Task:** Evaluate whether hreflang implementation is warranted given current state (single EU market primary — Denmark; secondary DE/FR/NL). Research Shopify hreflang support. Write a 1-page decision memo in `growth/seo/HREFLANG-DECISION.md` with a clear recommendation (implement / defer / not needed) and rationale. If implement: provide the exact Liquid snippet and implementation path.

**Output:** `growth/seo/HREFLANG-DECISION.md` with implementable recommendation.

---

### #10 — Fix Empty Collections (Outdoor Kitchens, Infrared Saunas)

**Engine:** B — Conversion / A — Product  
**KPIs unlocked:** B6 (trust), A6 (catalogue)  
**Effort:** Low  
**Dependency unlock:** LOW — but empty collections actively harm trust and SEO  
**Revenue impact:** LOW immediate / MEDIUM SEO

**Task:** Two collections (outdoor-kitchens, infrared-saunas) are in navigation with zero products — visitors who click land on empty pages. Options: (a) hide from nav until products are added, (b) replace with "coming soon" messaging with email capture. Recommend option (a) for Outdoor Kitchens (no confirmed supplier yet) and (b) for Infrared Saunas (defined category, plausible near-term add). Implement via Shopify MCP.

**Output:** Empty collections removed from nav or replaced with appropriate placeholder. Confirmed via Shopify.

---

### #11 — Google Shopping Campaign Structure Brief

**Engine:** F — Paid Acquisition  
**KPIs unlocked:** F1, F9  
**Effort:** Medium (1 session)  
**Dependency unlock:** MEDIUM — user cannot set up campaigns efficiently without a structure brief  
**Revenue impact:** HIGH (paid is the primary acquisition engine in Phase 2)

**Task:** Write `growth/paid/GOOGLE-SHOPPING-BRIEF.md` with:
- Campaign structure: 1 Performance Max + 1 Standard Shopping (brand terms)
- Geo: Denmark + Germany + France + Netherlands (EU-only, exclude US)
- Budget allocation: €2,000/mo test split
- Product feed requirements (Shopify Google & YouTube app — confirm if installed)
- Conversion goal setup (purchase event from GA4)
- Negative keyword seed list (US-specific terms, DIY-cheap, etc.)
- Target ROAS starting point: 3x (establish baseline before optimising)

**Constraint:** This is a brief for the user to execute in Google Ads. Do not set up ad accounts directly.

**Output:** `growth/paid/GOOGLE-SHOPPING-BRIEF.md` ready for user execution.

---

### #12 — Trade Prospect Research → TRADE-PROSPECTS.csv

**Engine:** E — B2B / Trade  
**KPIs unlocked:** E3  
**Effort:** Medium (research task)  
**Dependency unlock:** LOW (depends on #4 /trade page being live first)  
**Revenue impact:** MEDIUM — seeding the B2B pipeline before outreach begins

**Task:** Research and compile 15+ trade prospects in Denmark, Germany, and the Netherlands: luxury landscaping firms, garden design studios, outdoor living contractors, property developers with outdoor focus. For each: company name, country, category, website, estimated size, LinkedIn/Instagram. Store in `growth/outreach/TRADE-PROSPECTS.csv`. Do not guess contact emails. Do not represent as confirmed partners.

**Constraint:** Outreach requires user approval before any message is sent (per protocol).

**Output:** `growth/outreach/TRADE-PROSPECTS.csv` with 15+ rows, no fabricated contacts.

---

### #13 — SEO Descriptions for 5 Active Collections

**Engine:** C — Organic Search  
**KPIs unlocked:** C5, C6 (collection level)  
**Effort:** Low-Medium  
**Dependency unlock:** LOW-MEDIUM — collection descriptions are indexable content and a ranking signal  
**Revenue impact:** MEDIUM — collection pages rank for category-level terms ("outdoor barrel sauna Denmark")

**Task:** Write EU-targeted SEO descriptions (150–250 words) for 5 active collections: Barrel Saunas, Saunas, Sauna Accessories, Cold Plunge (even if products are draft — description can note "coming soon"), Fire Features (same). Update via Shopify MCP.

**Output:** 5 collection descriptions live. Logged in `SEO-META-AUDIT.md`.

---

### #14 — Build /pages/consultation (Inquiry Path)

**Engine:** B — Conversion & Trust  
**KPIs unlocked:** B6, B8  
**Effort:** Medium  
**Dependency unlock:** MEDIUM — high-ticket buyers frequently want a consultation before €8K–€15K spend  
**Revenue impact:** HIGH — a consultation path converts hesitant buyers who won't add-to-cart cold

**Task:** Build a `/pages/consultation` page: headline ("Speak with a Sauna Specialist"), what to expect, 3 ways to connect (Calendly embed OR contact form, email, WhatsApp if available). Link from PDP CTAs and navigation. Coordinate with existing contact page — don't duplicate, cross-reference.

**Constraint:** Use actual contact method Peter uses — do not invent a Calendly link. If no booking tool exists, build a form that goes to info@veldorahaven.com.

**Output:** `/pages/consultation` published. B8 confirmed.

---

### #15 — Paid Social Creative Brief (Meta / Pinterest)

**Engine:** F — Paid Acquisition / D — Social  
**KPIs unlocked:** F2, F3  
**Effort:** Low-Medium  
**Dependency unlock:** LOW (depends on Meta Pixel verified — see #16)  
**Revenue impact:** MEDIUM — enables Phase 2 Meta/Pinterest campaigns

**Task:** Write `growth/paid/META-PINTEREST-BRIEF.md`:
- Target audience profiles (DK/DE/NL homeowners, 35–60, household income top 30%)
- Ad format recommendations (Carousel for product range, Video for lifestyle, Static for retargeting)
- Creative brief: 3 hero concepts for Meta, 3 pin concepts for Pinterest
- Landing page recommendations per ad type
- Budget allocation: €500–€1,500/mo test split between Meta + Pinterest

**Output:** `growth/paid/META-PINTEREST-BRIEF.md` ready for creative production.

---

## SECTION B — USER-BLOCKED (requires user action; run in parallel with Section A)

These tasks cannot be completed autonomously. They are listed in priority order. The user should work through these alongside the autonomous queue.

---

### #16 — Verify GA4 Tracking is Live ⚠ USER ACTION

**Engine:** F / All  
**KPIs unlocked:** F10, C1–C4 (via GA4 data)  
**Priority:** CRITICAL — without GA4, all acquisition is unmeasurable  
**User action:** Log into GA4 → select veldorahaven.com property → check Realtime view while browsing the store → confirm purchase + add_to_cart events fire. Share property ID with Growth OS session.

**Blocker if unresolved:** Cannot launch any paid acquisition in Phase 2. Cannot measure SEO performance beyond Shopify's native analytics.

---

### #17 — Verify Google Search Console + Submit Sitemap ⚠ USER ACTION

**Engine:** C  
**KPIs unlocked:** C1–C4  
**Priority:** HIGH — GSC is the only way to see EU-specific search impressions and positions  
**User action:** Log into GSC → confirm veldorahaven.com is a verified property → check Coverage report for indexed pages → submit `https://www.veldorahaven.com/sitemap.xml` → share any crawl errors with Growth OS.

---

### #18 — Activate Klaviyo + Confirm Email Capture ⚠ USER ACTION

**Engine:** G  
**KPIs unlocked:** G2, G3  
**Priority:** HIGH — email capture should be live before paid traffic starts  
**User action:** Log into Shopify Admin → Apps → confirm Klaviyo is installed → check Klaviyo dashboard for list size and active flows → confirm whether email popup/footer capture is live on store. Report back.

**When confirmed:** Growth OS will deploy Klaviyo flow drafts from #8.

---

### #19 — Configure Judge.me Dashboard ⚠ USER ACTION

**Engine:** B  
**KPIs unlocked:** B5  
**Priority:** HIGH — zero social proof is the biggest CRO blocker for €6K–€15K products  
**User action:** Log into Judge.me → connect to Veldora Haven store → enable automatic review request emails after delivery → configure review widget display on PDPs → send a manual review request to any existing contacts who have handled Auroom products.

**Target:** 1–3 reviews before Phase 2 paid acquisition launches.

---

### #20 — Confirm Röshults + Unblock Group C Pricing ⚠ USER ACTION

**Engine:** A — Product/Supplier  
**KPIs unlocked:** A3, A4  
**Priority:** MEDIUM (Phase 1 exit criterion)  
**User action (two separate actions):**
1. **Röshults:** Confirm whether partnership discussions have progressed. If confirmed: return with agreement details so Growth OS can begin Shopify product entry. If stalled: remove from P1 scope.
2. **Group C pricing:** Contact Silga or Auroom to request assembly cost for Halo 120, Nora 210, Sola 250 Pre-assembled models. Once received, Growth OS will calculate prices and push to Shopify to close the 66→72 config gap.

---

## QUEUE SUMMARY

| # | Task | Engine | Autonomous? | Priority |
|---|---|---|---|---|
| 1 | SEO meta audit + optimise 9 products | C | ✓ Yes | HIGH |
| 2 | Publish 3 draft blog articles | C | ✓ Yes (approval) | HIGH |
| 3 | Build /pages/faq | B | ✓ Yes | HIGH |
| 4 | Build /trade + TRADE-PROGRAM.md | E | ✓ Yes | HIGH |
| 5 | CONTENT-BACKLOG.md + content pillars | D | ✓ Yes | MEDIUM |
| 6 | Internal link audit: blog → PDPs | C | ✓ Yes | MEDIUM |
| 7 | UTM convention + ANALYTICS-PLAN.md | F/All | ✓ Yes | HIGH |
| 8 | Klaviyo flow drafts (3 flows, 7 emails) | G | ✓ Yes | HIGH |
| 9 | Hreflang evaluation + memo | C | ✓ Yes | MEDIUM |
| 10 | Fix empty collections (nav) | B/A | ✓ Yes | LOW-MED |
| 11 | Google Shopping campaign brief | F | ✓ Yes | HIGH |
| 12 | Trade prospect research → CSV | E | ✓ Yes | MEDIUM |
| 13 | SEO descriptions for 5 collections | C | ✓ Yes | MEDIUM |
| 14 | Build /pages/consultation | B | ✓ Yes | HIGH |
| 15 | Meta/Pinterest creative brief | F/D | ✓ Yes | MEDIUM |
| 16 | Verify GA4 | F/All | ⚠ USER | CRITICAL |
| 17 | Verify GSC + submit sitemap | C | ⚠ USER | HIGH |
| 18 | Activate Klaviyo + email capture | G | ⚠ USER | HIGH |
| 19 | Configure Judge.me dashboard | B | ⚠ USER | HIGH |
| 20 | Confirm Röshults + Group C pricing | A | ⚠ USER | MEDIUM |

**Autonomous tasks: 15 — all executable in current phase**  
**User-blocked tasks: 5 — can be actioned in parallel by Peter**

---

## PHASE 1 EXIT CRITERIA COVERAGE

| Exit Criterion | Queue Tasks That Resolve It |
|---|---|
| SEO metadata verified | #1, #13 |
| Trust pages live (11/11) | #3, #14 |
| Measurement confirmed | #7 (UTM), #16 (GA4 — user), #17 (GSC — user) |
| Trade program built | #4 |
| Product pricing complete | #20 (user) |
| Review system collecting | #19 (user) |
| Organic content infrastructure | #2, #5, #6, #9 |
| Paid acquisition ready to launch | #11, #15 |
| Email infrastructure ready | #8, #18 (user) |

**Completing #1–#15 + user actions #16–#20 = Phase 1 exit criteria met = Phase 2 (paid launch) unlocked.**

---

*G0.4 complete. Next: execute queue starting at #1, or say which task to run.*
