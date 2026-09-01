# VeldoraHaven — Analytics Plan

**Created:** 2026-08-31  
**KPIs unlocked:** F10, G9  
**Phase:** 1 — Commercial Foundation  
**Status:** READY FOR USER REVIEW — implement before any paid spend

---

## 1. UTM CONVENTION

All traffic sources must be tagged before any campaign or social post goes live.

### Structure

```
utm_source={source}&utm_medium={medium}&utm_campaign={campaign}&utm_content={content}
```

`utm_term` is used only for paid search (keyword).

### Source / Medium pairs

| Channel | utm_source | utm_medium | utm_campaign example |
|---|---|---|---|
| Google Shopping | google | cpc | pmax-barrel-saunas-dk |
| Google Brand | google | cpc | brand-veldorahaven |
| Meta (Facebook/Instagram) | meta | paid-social | luma-dk-homeowners-q4 |
| Pinterest Ads | pinterest | paid-social | lifestyle-barrel-sauna-nl |
| Instagram Organic | instagram | social | pillar-wellness |
| Pinterest Organic | pinterest | social | placement-inspiration-board |
| TikTok Organic | tiktok | social | diy-assembly-series |
| Email — Klaviyo | klaviyo | email | welcome-flow |
| Email — Klaviyo | klaviyo | email | abandoned-cart |
| Email — Klaviyo | klaviyo | email | post-purchase |
| Blog internal CTA | blog | internal | luma-guide-pdp-cta |
| Trade outreach | outreach | direct | trade-landscapers-dk |

### Campaign naming convention

```
{product-or-category}-{market}-{audience}-{date}
e.g. luma-dk-homeowners-2026q4
     pmax-barrel-saunas-de-2026q4
     trade-landscapers-dk-sep26
```

### utm_content (ad/creative variant)

Use descriptive slugs: `carousel-lifestyle`, `video-assembly`, `static-trust`, `reel-morning-ritual`

---

## 2. GA4 EVENT NAMING CONVENTION

### Core commerce events (must fire on all paths)

| Event | Trigger | Parameters required |
|---|---|---|
| `page_view` | Every page load | `page_location`, `page_title` |
| `view_item` | PDP load | `item_id`, `item_name`, `price`, `currency` |
| `add_to_cart` | Add to cart click | `item_id`, `item_name`, `value`, `currency` |
| `begin_checkout` | Checkout start | `value`, `currency`, `items` |
| `purchase` | Order confirmation | `transaction_id`, `value`, `currency`, `items` |

### VeldoraHaven custom events

| Event | Trigger | Notes |
|---|---|---|
| `consult_click` | Click on "Book Consultation" / contact CTA | Tag all consultation CTAs |
| `faq_view` | Load `/pages/faq` | Page-level engagement signal |
| `trade_inquiry` | Submit trade inquiry form | B2B pipeline entry |
| `pdp_gallery_engage` | Gallery swipe/click on PDP | High-intent signal |
| `heater_selector_click` | Click heater add-on | AOV expansion signal |

### Conversion goals in GA4

| Goal | Event | Priority |
|---|---|---|
| Purchase | `purchase` | P0 — primary |
| Consultation request | `consult_click` | P1 — high-ticket proxy |
| Trade inquiry | `trade_inquiry` | P1 — B2B proxy |
| Add to cart | `add_to_cart` | P2 — funnel |
| Begin checkout | `begin_checkout` | P2 — funnel |

---

## 3. REPORTING CADENCE

| Report | Frequency | Owner | Source |
|---|---|---|---|
| Weekly growth review | Weekly (Monday) | Peter | GA4 + Shopify + GSC |
| KPI scoreboard update | Weekly | Growth OS | Shopify + GA4 |
| Phase gate report | At phase exit | Growth OS | All engines |

### Weekly review minimum reads (once GA4 live):
1. Sessions — total + by channel + EU vs non-EU split
2. Product page views — which products, bounce rate
3. Add-to-cart rate
4. Checkout starts + purchase completions
5. Top landing pages (organic only)

---

## 4. IMPLEMENTATION CHECKLIST (user actions)

Before any paid campaign launches, confirm all of the following:

- [ ] GA4 property verified (veldorahaven.com) — see #16 in queue
- [ ] GA4 purchase event firing on order confirmation page
- [ ] GA4 add_to_cart event firing
- [ ] Google Search Console verified + sitemap submitted — see #17
- [ ] Meta Pixel installed on store — see #16
- [ ] Shopify Google & YouTube app installed (for Google Shopping feed)
- [ ] UTM parameters tested: build a UTM URL, click it, verify session appears in GA4 Acquisition report tagged correctly

---

## 5. PLATFORM PROPERTY IDS (fill in when verified)

| Platform | Property / Account ID | Status |
|---|---|---|
| GA4 | TBC | Unverified |
| Google Ads | TBC | Not yet created |
| Google Search Console | TBC | Unverified |
| Meta Pixel | TBC | Unverified |
| Pinterest Tag | TBC | Not yet created |
| Klaviyo | TBC | See queue #18 |

---

*Share with user before any paid spend. UTM convention is operational immediately — start tagging all social posts and email CTAs now.*
