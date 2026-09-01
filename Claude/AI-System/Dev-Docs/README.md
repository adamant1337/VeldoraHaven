# cache/ — Ephemeral Caches (L1)

**Responsibility:** very short-lived, regenerable artifacts — current-task scratch,
computed lookups, transient analysis. TTL: seconds–minutes. Safe to delete anytime.

Rules: nothing authoritative lives here; never treat cache as source of truth. Use
**targeted** invalidation (only dependent entries), never global. See
MASTER-ARCHITECTURE §7 and the Caveman cache policy (`.claude/skills/caveman/SKILL.md`).

## Active reference caches (read these first; ADR-0009)

| Cache | Digest of | SoT | TTL |
| --- | --- | --- | --- |
| [`theme-structure.md`](theme-structure.md) | theme id/version/paths, vh-* sections, file map, risk areas | `shopify/SHOPIFY-THEME-INTEGRATION.md`, `LIVE-LOCAL-RECONCILIATION.md` | 30d |
| [`design-tokens.md`](design-tokens.md) | `--vh-*` colors, type, component tokens, scheme debt | `design-system/DESIGN-SYSTEM.md`, `brand/BRAND.md` | 30d |
| [`pdp-data-map.md`](pdp-data-map.md) | `spec.*` metafields → `vh-product-spec` → PDP | `theme/sections/vh-product-spec.liquid` + metafields | 14d |

Each cache header carries `source_of_truth`, `ttl`, `last_verified`, `invalidate_when`.
