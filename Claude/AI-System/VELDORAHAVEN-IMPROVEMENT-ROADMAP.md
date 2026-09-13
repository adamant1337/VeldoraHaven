# VeldoraHaven — Improvement Roadmap (CURRENT → BETTER)

**Read-only audit — no theme files modified. `main` not touched.** Date: 2026-08-22.
Philosophy: **elevate the existing VeldoraHaven, do not rebuild it.** Baseline of what
exists: [`VELDORAHAVEN-CURRENT-STATE.md`](VELDORAHAVEN-CURRENT-STATE.md). Tokens:
[`../design-system/DESIGN-SYSTEM.md`](../design-system/DESIGN-SYSTEM.md). Theme facts:
[`../shopify/SHOPIFY-THEME-INTEGRATION.md`](../shopify/SHOPIFY-THEME-INTEGRATION.md).

> Sources: **live** https://www.veldorahaven.com/ (customer baseline) + **local**
> `C:\VeldoraHaven\theme\` (implementation). They are **not identical** — see R0.
> No implementation begins until the user approves this roadmap.

---

## 1. Headline

The live VeldoraHaven is **already a strong, premium, high-ticket store** — excellent PDP
transparency, editorial copy, a clear 4-step process, and trust-forward positioning. The
work is **refinement and elevation**, not reconstruction. The biggest immediate issue is
**governance**: the local theme does not match the live site, so we must reconcile before
touching anything.

## 2. KEEP / IMPROVE / REPLACE — major components

| Component | Verdict | Rationale |
| --- | --- | --- |
| Brand identity (forest/gold/cream, serif, editorial voice) | **KEEP** | Coherent and genuinely premium |
| Editorial copy & category taglines | **KEEP** | High quality; a real asset |
| Homepage structure (hero → category → USP → process → journal → about) | **KEEP + IMPROVE** | Strong shell; add social proof, polish hierarchy |
| PDP content architecture (specs / included / options / delivery, metafield-driven) | **KEEP** | Best asset in the store — protect it |
| "The Veldora Haven Process" + USP/trust row | **KEEP** | Excellent high-ticket reassurance |
| Collections (price filter + sort + cards) | **IMPROVE** | Solid; add premium heroes + curation |
| Navigation (desktop drawer-only) | **IMPROVE** | Evaluate discoverability; do not replace outright |
| Typography implementation (Josefin vs Cormorant + `!important`) | **IMPROVE** | Fix at theme level — the decision, not a rebuild |
| Hero asset weight + font `@import` | **IMPROVE** | Perf/LCP |
| Contrast (footer/vendor/nav) | **IMPROVE** | WCAG AA |
| Structured data (JSON-LD) | **IMPROVE (add)** | Absent in theme meta-tags |
| Customer reviews / social proof | **ADD** | Not observed live — genuine gap |
| Cart AOV/upsell | **IMPROVE** | Headroom without harming conversion |
| Shopify architecture (Horizon + isolated custom layer) | **KEEP** | Clean, maintainable |
| **REPLACE** | **none justified** | No component is fundamentally broken |

## 3. Baseline scores (0–100, re-based on the LIVE site, critical)

| Area | Score | Note (Δ vs local-only view) |
| --- | :--: | --- |
| Brand | 78 | Live copy/positioning strong; font debt remains |
| Visual Design | 72 | Editorial & restrained; polish + font/contrast fixes (visual pass pending) |
| UX | 74 | Clear journey, how-it-works; drawer-nav discoverability to test |
| CRO | 66 | Strong trust/process; **no reviews**, no assisted-selling path |
| Homepage | 76 | Excellent structure; add social proof |
| Collections | 70 | Filter/sort/cards solid; premium curation headroom |
| Product Pages | 80 | Comprehensive, transparent — the standout (add reviews) |
| Cart | 62 | Functional; AOV/upsell headroom (live not deeply verified) |
| Mobile | 72 | Horizon responsive + drawer nav; visual pass pending |
| Performance | 60 | 3 MB hero asset + `@import` fonts; live optimization unverified |
| Accessibility | 64 | Skip-link/focus good; footer/vendor contrast fails |
| SEO | 70 | Strong titles/meta + rich content; no theme JSON-LD |
| Shopify Architecture | 68 | Clean Horizon + metafields; **local≠live** discrepancy is a risk |
| **BASELINE OVERALL** | **70** | Strong foundation; elevation, not rebuild |

## 4. Problems (evidence-based)

- **P0-gov** Local theme ≠ live site (homepage + PDP richer live; likely published-theme-
  ahead and/or metafield/section-config). Editing stale files risks regressions or
  overwriting live editor work.
- **P-A** Typography conflict — Josefin (`type_heading_font` → `--font-heading--family`)
  vs Cormorant `!important` on `h1–h6` → inconsistent headings live.
- **P-B** 3.1 MB `LakeSaunaHeroPicture.png` in assets → LCP risk (confirm live usage).
- **P-C** Render-blocking Cormorant `@import` at top of `veldora-custom.css`.
- **P-D** No customer reviews / social proof observed (homepage + PDP).
- **P-E** Contrast fails: footer links `rgba(247,247,245,0.45)` & copyright `0.2` on
  `#152E25`; vendor `#7A9E87` on cream; nav `0.7` borderline.
- **P-F** No JSON-LD (Product/Breadcrumb/Organization/FAQ) in theme `meta-tags`.
- **P-G** `!important` saturation → brittle vs Horizon updates.
- **P-H** Cart AOV/upsell + trust reinforcement minimal.
- **P-I** Desktop navigation hidden behind a single drawer — discoverability to evaluate.
- **P-J** Dead asset `standard-events.d.ts` (32 KB) shipped.

## 5. Opportunities

- **O-1** Reconcile local↔live → safe, confident development baseline.
- **O-2** Fix typography at theme level → consistency + perf + less CSS debt.
- **O-3** Add reviews/social proof (homepage + PDP) → trust + CRO on high-ticket.
- **O-4** Optimize hero + fonts → LCP.
- **O-5** Add structured data → rich results.
- **O-6** Elevate visual hierarchy/spacing/photography (premium polish pass).
- **O-7** Collection premium heroes + curation.
- **O-8** Cart AOV: accessory/care/install upsells + delivery/guarantee trust.
- **O-9** Assisted-selling path (consultation / "help me choose") beyond email.
- **O-10** Accessibility contrast pass.

## 6. Prioritized roadmap (priority = Impact × Effort × Risk)

Impact ▲high/►med/▽low · Complexity S/M/L · Risk Low/Med/High. Flow for every task:
`BRANCH → IMPLEMENT → TEST → FINAL CRITIC → REPORT → USER APPROVAL → MERGE` (ADR-0006).

### P0 — Critical

| ID | Verdict · Fix | Why it matters | Impact | Cplx | Risk | Agent | Deps | Branch |
| --- | --- | --- | :--: | :--: | :--: | --- | --- | --- |
| **R0** | governance · **Reconcile local theme ↔ live/published theme** (confirm published version vs GitHub `main`, map metafield-driven content). Read-only + CLI pull; needs Shopify auth (user). | Prevents building on stale files or overwriting live editor work | ▲ | M | Low | shopify-architect + orchestrator | Shopify auth | `fix/reconcile-local-live` |
| **R1** | IMPROVE · **Typography** — set `type_heading_font` = Cormorant at theme level; retire redundant `!important` heading rules | Fixes most visible brand inconsistency; unblocks all type work | ▲ | S–M | Med | shopify-architect + liquid-engineer | R0 | `fix/typography-heading-font` |
| **R2** | IMPROVE · **Hero + fonts perf** — compress/convert hero to responsive WebP; move Cormorant off `@import` | LCP on the most-viewed page | ▲ | S | Low | performance-engineer | R0, R1 | `performance/hero-and-fonts` |

### P1 — High impact

| ID | Verdict · Fix | Why it matters | Impact | Cplx | Risk | Agent | Deps | Branch |
| --- | --- | --- | :--: | :--: | :--: | --- | --- | --- |
| R3 | ADD · **Reviews / social proof** (PDP + homepage) | Biggest remaining CRO/trust lever for high-ticket | ▲ | M | Med | ux-cro + component-builder + product-experience | R0 | `feature/reviews-social-proof` |
| R4 | IMPROVE · **Premium polish pass** (hierarchy, spacing, photography treatment) | Elevates perceived value across pages | ► | M | Low | visual-designer + brand-director | R1 | `feature/premium-polish` |
| R5 | IMPROVE(add) · **JSON-LD** (Product/Breadcrumb/Organization/FAQ) | Rich results | ► | M | Low | seo-specialist + liquid-engineer | R0 | `feature/structured-data` |
| R6 | IMPROVE · **Contrast to WCAG AA** (footer/vendor/nav) | Compliance + legibility | ► | S | Low | accessibility-specialist + liquid-engineer | none | `fix/contrast-aa` |

### P2 — Medium

| ID | Verdict · Fix | Why it matters | Impact | Cplx | Risk | Agent | Deps | Branch |
| --- | --- | --- | :--: | :--: | :--: | --- | --- | --- |
| R7 | IMPROVE · **Cart AOV** (accessory/care/install upsells + trust) | AOV without hurting conversion | ► | M | Med | cart-aov-specialist + liquid-engineer | R0 | `feature/cart-aov` |
| R8 | IMPROVE · **Navigation discoverability** (evaluate desktop drawer vs revealed nav) | Category discovery | ► | M | Med | ux-cro + component-builder | R0 | `feature/nav-discoverability` |
| R9 | IMPROVE · **Collections premium heroes + curation** | Discovery + brand feel | ► | M | Low | collection-experience + visual-designer | R0 | `feature/collection-premium` |
| R10 | IMPROVE · **Reduce `!important` debt** (migrate to Horizon settings) | Maintainability | ► | L | Med | shopify-architect + liquid-engineer | R1 | `fix/reduce-important-debt` |

### P3 — Nice to have

| ID | Verdict · Fix | Why it matters | Impact | Cplx | Risk | Agent | Deps | Branch |
| --- | --- | --- | :--: | :--: | :--: | --- | --- | --- |
| R11 | ADD · **Assisted-selling / consultation path** | Higher-touch conversion | ► | M | Med | ux-cro + component-builder | R3 | `feature/consultation-path` |
| R12 | cleanup · **Remove dead `standard-events.d.ts`** | Hygiene | ▽ | S | Low | performance-engineer | R0 | `performance/asset-cleanup` |
| R13 | polish · **Mobile fixed-px review** | Polish | ▽ | S | Low | mobile-specialist | R1 | `fix/mobile-typography-polish` |

## 7. Recommended first task

**R0 — `fix/reconcile-local-live`** (P0, no redesign).

- **Why first:** every other task assumes the local files reflect the live store. They do
  not. Reconciling is a prerequisite that protects the live site and makes all later work
  safe. It is investigation + a controlled pull, not a redesign.
- **Scope:** with the user's Shopify auth, confirm the published theme version vs GitHub
  `main`; identify whether the live homepage/PDP richness comes from a newer commit or from
  metafields/section config; document metafield definitions the PDP depends on; update
  `SHOPIFY-THEME-INTEGRATION.md` and `CURRENT-STATE.md` accordingly.
- **Then:** R1 (typography) is the first *visible* improvement.
- **Guardrails:** read-only until auth; no push to `main`; no live-theme modification.

> Awaiting user approval of this roadmap before any implementation begins.
