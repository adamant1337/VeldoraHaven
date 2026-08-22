# VeldoraHaven — Live State

_Last updated: 2026-08-22 (R1 verified — no change)_

## Active tasks

```yaml
- task_id: AI-ARCH-001
  title: Establish agent system + source-of-truth scaffolding
  status: complete
- task_id: THEME-INT-001
  title: Confirm + clone theme, read-only integration audit, extract real tokens
  status: complete
  notes: theme at C:\VeldoraHaven\theme (HEAD 15eba70, main)
- task_id: AUDIT-001
  title: Master store audit (live + local), baseline scores, roadmap
  status: complete
  baseline_score: 70/100
- task_id: R0
  title: Reconcile local <-> live + set up dev workflow
  status: complete (CLI pull pending user auth)
  branch: fix/reconcile-local-live
  finding: source of truth = LIVE 205129482582 + spec.* metafields; local/GitHub stale (Aug 2)
  decision: v28 (205283819862) = working draft; live (205129482582) = reference
  captured: real design tokens + custom-source knowledge via Admin API
  outputs: shopify/LIVE-LOCAL-RECONCILIATION.md, shopify/THEME-DEV-WORKFLOW.md, theme/shopify.theme.toml
  pull: COMPLETE 2026-08-22 — v28 verified (byte-match) + committed as baseline on fix/reconcile-local-live
  next_action: R0 complete.
- task_id: R1
  title: Establish authoritative VeldoraHaven heading typography (v28)
  status: complete — NO CHANGE REQUIRED (already satisfied)
  finding: authoritative typography = custom-CSS layer (veldora-custom.css) — Cormorant Garamond
    headings (Google-hosted @import, wght 200-600) + Inter body/UI, forced via !important; renders
    consistently across homepage/collection/PDP/cart/nav/headings/buttons/editorial.
  conflict: theme settings default to anonymous_pro/work_sans (settings_data.json has no font keys)
    but this is fully masked by the CSS layer — latent debt, mirror of R10 color debt. No Josefin
    remains (old conflict was stale local state, confirmed gone in v28).
  decision: did NOT set type_heading_font via font_picker — Shopify-library Cormorant lacks the
    200/300 ultralight brand weights and would double-load fonts atop the required Google @import.
  change: none. no branch, no commit, no empty commit. main untouched. Shopify production untouched.
```

## Theme snapshot

```yaml
root: C:\VeldoraHaven\theme
remote: https://github.com/adamant1337/VeldoraHaven1.git
branch: main
head: 15eba70
base_theme: Shopify Horizon 3.5.1
```

## File-ownership locks

_None active._

```yaml
# template
# - file: ; owner: ; task_id: ; locked: true
```

## Blockers / cautions

- `main` is **production-linked** via the Shopify↔GitHub integration — no pushes to
  `main` without explicit user approval.
- Shopify CLI present but **not authenticated**; store not identified. Read-only until
  the user logs in. See [`../shopify/SHOPIFY-THEME-INTEGRATION.md`](../shopify/SHOPIFY-THEME-INTEGRATION.md).
- **Local theme ≠ live site** (live homepage/PDP richer; likely published-theme-ahead
  and/or metafield-driven). Reconcile (roadmap R0) before any implementation.
