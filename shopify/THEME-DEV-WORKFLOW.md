# VeldoraHaven — Theme Development Workflow (Shopify CLI)

Authoritative workflow for pulling, editing, previewing, pushing, and publishing the
VeldoraHaven theme. Source of truth + theme IDs:
[`LIVE-LOCAL-RECONCILIATION.md`](LIVE-LOCAL-RECONCILIATION.md). Git rules: ADR-0006.

## Themes & roles

| Env | Theme | ID | Role | Use |
| --- | --- | --- | --- | --- |
| `v28` | VeldoraHaven — v28 Vendor + Footer | `205283819862` | UNPUBLISHED | **Working draft — edit/push here, publish when approved** |
| `live` | Copy of VeldoraHaven — v27… | `205129482582` | MAIN (LIVE) | Current published — reference only, never push/publish over from local |

Store (CLI): `iqeb6u-5h.myshopify.com` · Storefront: `www.veldorahaven.com`. CLI
environments are pre-configured in [`../theme/shopify.theme.toml`](../theme/shopify.theme.toml).

## One-time: authenticate (interactive terminal — Claude cannot do this)

```bash
cd C:\VeldoraHaven\theme
shopify auth login --store iqeb6u-5h.myshopify.com
shopify theme list          # confirm auth + the theme IDs above are visible
```

## Step 1 — Pull the working draft (v28) into the local repo

```bash
cd C:\VeldoraHaven\theme
git checkout fix/reconcile-local-live      # already created
shopify theme pull -e v28                  # overwrites local files with the real v28
git add -A && git commit -m "Baseline: pull live v28 theme (205283819862)"
```
This replaces the stale Aug-2 clone with the real v28 source (all 460 files, binaries
included). Git then tracks v28 as the true baseline.

## Step 2 — Pull the current live theme for reference (separate folder)

```bash
cd C:\VeldoraHaven\theme
shopify theme pull -e live --path ../theme-live-ref
```
Keeps a read-only reference of what customers see today, without disturbing v28.

## Step 3 — Develop v28 (local preview with hot reload)

```bash
shopify theme dev -e v28
```
Opens a local preview against the store's data. Safe — does not affect live.

## Step 4 — Push changes to the v28 draft (never to live)

```bash
shopify theme push -e v28
```
Updates the unpublished v28 theme so you can review it in the Shopify preview. Do **not**
run `shopify theme push -e live` and never `--live` from local.

## Step 5 — Publish (only on explicit approval)

When v28 is approved (final-critic + your sign-off), publish it:
```bash
shopify theme publish -e v28      # promotes v28 to MAIN/live
```
Publishing is the ONLY step that changes the customer-facing store. It requires explicit
user approval every time (ADR-0006). After publishing, v28 becomes live; create the next
draft (duplicate) for further work.

## Guardrails

- **Never** `theme push -e live`, `--live`, or `theme publish` without explicit approval.
- Work on a git branch; logically scoped commits; never force-push / destructive reset.
- After pulling v28, **re-extract design tokens** into
  [`../design-system/DESIGN-SYSTEM.md`](../design-system/DESIGN-SYSTEM.md) (already
  pre-filled from the API capture) and verify against the pulled files.
- Binary assets (images, fonts) come only via the CLI pull — the API capture covered
  text source only.

## Note on GitHub

GitHub (`adamant1337/VeldoraHaven1`) is stale/historical. Decide later whether to
re-point it at v28 (push the pulled baseline) or retire it in favour of CLI-based deploys.
Do not rely on the old GitHub↔Shopify auto-sync — it is not connected to the live lineage.
