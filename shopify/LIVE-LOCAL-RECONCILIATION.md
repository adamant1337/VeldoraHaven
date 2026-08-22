# VeldoraHaven — LIVE ↔ GITHUB ↔ LOCAL Reconciliation

**Authoritative record of the relationship between the live Shopify store, GitHub, the
local theme clone, and Shopify data.** Task R0, 2026-08-22 (read-only; no live changes).

## TL;DR — Source of truth

> **The LIVE published theme `205129482582` + Shopify product metafields (`spec.*`) are
> the source of truth.** The GitHub repo and the local clone (`C:\VeldoraHaven\theme`,
> HEAD `15eba70`, 2026-08-02) are a **stale snapshot** and are NOT authoritative. Do not
> push local → live. Reconcile by pulling live → local (see "Recommended action").

## Store

- **Veldora Haven** · `www.veldorahaven.com` · Shopify plan · EUR · Denmark ·
  `info@veldorahaven.com`.

## Theme lineage (from Shopify Admin API)

| Theme | ID | Role | Updated |
| --- | --- | --- | --- |
| VeldoraHaven — v25 Pre-Application | 204381356374 | UNPUBLISHED | 2026-08-18 |
| VeldoraHaven — v26 Search Styling | 204762743126 | UNPUBLISHED | 2026-08-12 |
| VeldoraHaven — v27 Coming Soon + Journal | 205066731862 | UNPUBLISHED | 2026-08-19 |
| **Copy of VeldoraHaven — v27 Coming Soon + Journal** | **205129482582** | **MAIN (LIVE)** | **2026-08-19** |
| VeldoraHaven — v28 Vendor + Footer | 205283819862 | UNPUBLISHED | 2026-08-21 |

Development is a **chain of admin-duplicated themes** (v25 → v28). The live theme is a
duplicate ("Copy of…v27"). **v28** (2026-08-21) is the newest work-in-progress and is
*ahead of live*.

## Versions

| Source | Identity | Date |
| --- | --- | --- |
| **LIVE (MAIN)** | theme `205129482582`, "Copy of VeldoraHaven — v27" | 2026-08-19 |
| Newest WIP | theme `205283819862`, "v28 Vendor + Footer" (unpublished) | 2026-08-21 |
| GitHub `origin/main` | `adamant1337/VeldoraHaven1` @ `15eba70` | 2026-08-02 |
| Local clone | `C:\VeldoraHaven\theme` @ `15eba70` (= GitHub) | 2026-08-02 |

Local == GitHub exactly (0 ahead/0 behind). Both are ~17 days + 3 theme-versions behind
live.

## GitHub connection

- GitHub↔Shopify integration **was** active on the *original* `VeldoraHaven1` theme
  (evidence: `"Update from Shopify for theme VeldoraHaven1/main"` auto-commits, Jun 2026).
- The **current live theme (`205129482582`) is an admin-duplicated theme and is not being
  synced to GitHub** — its v25→v27 content (Aug) never reached `main` (last commit Aug 2).
- **Conclusion:** GitHub is effectively disconnected from the live lineage. Treat GitHub
  as historical, not current. (Exact connection status is a Shopify-admin UI detail not
  exposed by the API; this is the evidence-based determination.)

## Root cause of LIVE ≠ LOCAL

**Development moved out of the GitHub-synced theme into admin-duplicated themes
(v25→v28) and never flowed back to GitHub.** The live theme therefore contains
substantial work absent from GitHub/local. Not a merge conflict — a **divergent lineage**.

## What differs (live vs local)

**Custom sections — live-only (do not exist in local):**
`vh-brand-story`, `vh-category-cards`, `vh-category-links`, `vh-collection-guide`,
`vh-collection-hero`, `vh-editorial`, `vh-how-it-works`, `vh-journal`,
`vh-product-spec`, `vh-trust-bar` (all `sections/vh-*.liquid`); snippet
`vh-coming-soon.liquid`.

**Custom assets — live-only:** `veldora-footer.css`, `veldora-mobile.css`,
`veldora-reveal.js`. And `veldora-custom.css` is **16.8 KB live vs 5.2 KB local** (3×;
more tokens, scroll-reveal, hero/story CSS vars pointing at CDN images).

**Homepage:** live `index.json` (3.5 KB) is built from the custom `vh-*` sections
(hero → vh-category-cards → vh-trust-bar → vh-how-it-works → vh-journal → vh-brand-story).
Local `index.json` (57 KB) is the **stock Horizon demo homepage** (hero/marquee/
product-list/media-with-content). Entirely different pages.

**Design tokens differ:** live adds `--vh-cream-pure #FAFAF8`, `--vh-stone #2A2A22`
(local `#3D3D35`), `--vh-forest-deep #0f2018` (local `#152E25`), `--vh-cream #F5F0E8`
(local `#F7F7F5`). The tokens documented in `design-system/DESIGN-SYSTEM.md` were
extracted from the **stale local** copy and must be re-extracted from live.

**Local-only (stale) files not on live:** `assets/standard-events.d.ts`,
`templates/page.about.json`, `page.faq.json`, `page.how-it-works.json`,
`page.returns.json`, `page.shipping.json`. (Live handles those pages via the default
`page` template + assigned sections.)

> A precise byte-level, file-by-file 3-way diff is only possible after pulling the live
> theme locally; the above is the verified structural divergence.

## PDP data-source map (verified)

```
spec.* PRODUCT METAFIELDS            (Shopify data)
        └─ product.metafields.spec.{dim_external, dim_internal, capacity, materials,
             power, weight_kg, certification, warranty, lead_time, delivery_method,
             base_req, included, not_included}
                 ↓  read by
        sections/vh-product-spec.liquid   (enabled_on templates: product; empty rows hide)
                 ↓  outputs
        Live PDP: Specification table + Included / Not included + Delivery & installation
```

- **Metaobjects:** none defined.
- **App blocks:** none material found; `blocks/review.liquid` exists (Horizon) but no
  review content/app is wired — reviews are absent live (matches audit).
- **Unrelated leftover data:** `custom.*` product metafields (game/set/rarity/grading,
  Danish labels) belong to a previous **epiccard** trading-card use of this store — dead
  weight, not used by VeldoraHaven. Cleanup candidate (not touched).

## Decision (2026-08-22): working model

- **v28 (`205283819862`) is the working draft** — edit locally, push to v28, publish to
  live only when approved. **Live (`205129482582`) is reference.** Store CLI domain:
  `iqeb6u-5h.myshopify.com`.
- CLI environments configured in [`../theme/shopify.theme.toml`](../theme/shopify.theme.toml);
  full workflow in [`THEME-DEV-WORKFLOW.md`](THEME-DEV-WORKFLOW.md).
- **Pull status: ✅ COMPLETE (2026-08-22).** The user ran `shopify theme pull -e v28`;
  `C:\VeldoraHaven\theme` now holds the real v28 theme (`205283819862`). Verified: pulled
  `veldora-custom.css` is byte-identical to the API capture (18,371 B); all 10 `vh-*`
  sections + `vh-coming-soon` + `veldora-footer.css`/`veldora-mobile.css`/`veldora-reveal.js`
  present; `vh-product-spec.liquid` reads `product.metafields.spec.*`; Horizon 3.5.1; stale
  files (incl. `standard-events.d.ts`, `page.about/faq/how-it-works/returns/shipping.json`)
  removed. Committed as the dev baseline on `fix/reconcile-local-live`.
- **v28 vs live delta** (from its name + CSS): v28 adds the Auroom **vendor mark** and a
  **compressed footer** (`veldora-footer.css`), plus a luxury **mobile nav** redesign
  (`veldora-mobile.css`); v28 `veldora-custom.css` is 18.4 KB vs live 16.8 KB.

## Recommended action (CLI pull — user runs, per THEME-DEV-WORKFLOW.md)

1. **Adopt live theme `205129482582` as the baseline.** Pull it into the local clone:
   `shopify theme pull --theme 205129482582 --path C:\VeldoraHaven\theme` (needs Shopify
   CLI auth — user runs it in an interactive terminal). This is read-only on live.
   *Alternative:* API export file-by-file (heavier), or reconnect GitHub to the live
   theme and let it push, then `git pull`.
2. **Decide whether to also capture `v28` (205283819862)** — it is newer than live and may
   contain intended next changes.
3. **Re-extract design tokens** from the pulled live `veldora-custom.css` /
   `veldora-*.css` into `design-system/DESIGN-SYSTEM.md`.
4. **Re-point git:** after pulling live, commit to a branch and decide the go-forward
   sync model (GitHub reconnect vs CLI-based). Never push the stale local → live.

**Do NOT** run local → live (would destroy ~3 versions of live work). **Do NOT** publish
or modify any theme. No conflicting-edit STOP condition beyond the divergence above.
