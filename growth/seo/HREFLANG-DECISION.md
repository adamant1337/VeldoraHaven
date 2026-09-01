# VeldoraHaven — Hreflang Evaluation & Decision Memo

**Created:** 2026-08-31  
**KPI unlocked:** C10  
**Phase:** 1 — Commercial Foundation

---

## QUESTION

Should VeldoraHaven implement hreflang tags to improve EU geo-targeting in search?

---

## CONTEXT

- **Primary market:** Denmark (DK) — pricing in EUR, EU-targeted copy
- **Secondary markets:** Germany (DE), Netherlands (NL), France (FR) — aspirational
- **Current problem:** 89% of sessions are US-origin — wrong market
- **Language:** Store is single-language (English) — no localised versions exist
- **Shopify plan:** Horizon theme — standard Shopify OS 2.0

---

## HOW HREFLANG WORKS

Hreflang tells Google which version of a page to serve to users in specific countries or language contexts. It resolves two problems:

1. **Multiple language versions of the same URL** — e.g. `/en/` vs `/da/` vs `/de/`
2. **Country-specific targeting** — e.g. `en-DK` vs `en-US` for the same English-language page

It does **not** resolve the root cause of US traffic domination. If US traffic comes from US-based keywords in blog posts or unqualified backlinks, hreflang does not fix that — EU-targeted content and link signals do.

---

## SHOPIFY HREFLANG SUPPORT

Shopify automatically generates hreflang tags when:
- **Shopify Markets** is used with multiple market configurations (e.g. a Denmark market, a Germany market), OR
- **Shopify Translate & Adapt** app adds language variants

Without Markets or Translate & Adapt, Shopify does not inject hreflang tags.

A manual Liquid implementation is possible but fragile — it requires hardcoding market/language combinations in `theme.liquid` and maintaining them as the store grows.

---

## ANALYSIS

### Option A: Implement hreflang via manual Liquid snippet

**Pros:** Forces geo-signal into `<head>`  
**Cons:** Fragile; hard to maintain; does not fix US traffic root cause (wrong content); requires defining country variants that don't actually exist as separate pages; Google may ignore if content is identical

**Verdict:** Not recommended. High maintenance cost for uncertain SEO benefit.

### Option B: Implement via Shopify Markets configuration

**Pros:** Native Shopify implementation; auto-maintained; correct Google recognition; enables future currency localisation (DKK for Denmark, EUR for DE/NL/FR)  
**Cons:** Requires Markets setup — defining separate market configs per country; minor ongoing admin overhead

**Verdict:** Right approach if/when VeldoraHaven expands to local currency pricing. Not yet a priority at Phase 1 — single currency (EUR) store with no localised content.

### Option C: Defer — focus on EU content signals first

**Rationale:** The 89% US traffic problem is a **content geo-signal problem**, not a hreflang problem. US visitors arrive because content uses generic terms ("barrel sauna", "outdoor sauna") that rank for US queries. The fix is EU geo-qualified content: "outdoor barrel sauna Denmark", "barrel sauna Netherlands delivery", "buy barrel sauna Germany" — in titles, meta, headers, body copy.

Hreflang provides incremental geo-signal after content geo-qualification. It is not a shortcut past the content work.

---

## RECOMMENDATION

**DEFER hreflang. Execute EU content geo-qualification first.**

Priority order:
1. ✅ EU-targeted meta titles + descriptions (done — queue #1)
2. EU-qualified blog content with location terms (queue #2 ongoing)
3. EU-qualified collection descriptions (queue #13)
4. **Then evaluate Shopify Markets** when at least 2 EU markets are active with meaningful traffic

**Revisit hreflang decision:** When store has ≥500 EU organic sessions/month and is ready to split Denmark vs DE/NL/FR markets in Google Search Console.

---

## IF HREFLANG IS LATER IMPLEMENTED

Use Shopify Markets (not manual Liquid). Setup path:
1. Shopify Admin → Settings → Markets → Add market (Denmark, Germany, Netherlands)
2. Configure currency per market if localising pricing
3. Shopify auto-injects correct `<link rel="alternate" hreflang="...">` tags in `<head>`
4. Verify in GSC → International Targeting report

---

*Memo complete. C10 KPI: hreflang evaluated + decision recorded. Revisit at Phase 2 entry.*
