# decisions/ — Architecture Decision Records (L4, durable)

**Responsibility:** durable, dated decisions and their rationale. One file per decision:
`NNNN-short-title.md`. Never rewrite history — supersede with a new record and link back.

## Record template

```markdown
# ADR-0001: <title>
Date: YYYY-MM-DD · Status: accepted | superseded by ADR-XXXX
## Context
## Decision
## Consequences
```

## Log

- **ADR-0001** (2026-08-22, accepted): Hybrid model strategy — Opus for
  strategy/design/architecture/critic; Sonnet for implementation/audit; orchestrator may
  escalate to Opus when reasoning demands. Rationale: quality per token. See
  [`../architecture/MASTER-ARCHITECTURE.md`](../architecture/MASTER-ARCHITECTURE.md) §10.
- **ADR-0002** (2026-08-22, accepted): AI agent system kept **separate** from the
  Shopify theme repository until the theme location is user-confirmed. See
  [`../shopify/README.md`](../shopify/README.md).
- **ADR-0003** (2026-08-22, accepted): Theme confirmed = `adamant1337/VeldoraHaven1`
  (Horizon 3.5.1). Work in a **clean clone at `C:\VeldoraHaven\theme\`**; never edit the
  OneDrive copy or the nested `epiccard` repo. `main` is production-linked via the
  Shopify↔GitHub integration → no pushes to `main` without explicit approval. See
  [`../shopify/SHOPIFY-THEME-INTEGRATION.md`](../shopify/SHOPIFY-THEME-INTEGRATION.md).
- **ADR-0004** (2026-08-22, accepted): `collection-experience` stays on **Sonnet**;
  orchestrator may escalate to Opus for deep reasoning / major UX architecture / complex
  conversion strategy.
- **ADR-0005** (2026-08-22, accepted): **Typography** — Cormorant Garamond is the
  authoritative display/heading font; Inter is body/UI. Josefin Sans is not deleted
  blindly; it is replaced at the theme `type_heading_font` setting (see
  [`../design-system/DESIGN-SYSTEM.md`](../design-system/DESIGN-SYSTEM.md) typography audit).
- **ADR-0006** (2026-08-22, accepted): **Git strategy** — `main` = production. All work
  on task branches `feature/<t>` | `fix/<t>` | `performance/<t>`. Flow: TASK → BRANCH →
  IMPLEMENT → TEST → FINAL CRITIC → REPORT → USER APPROVAL → MERGE. Never force-push,
  never destructive reset, never modify production without explicit approval.
- **ADR-0007** (2026-08-22, accepted): **Source of truth = the LIVE published theme
  `205129482582` + Shopify `spec.*` product metafields.** GitHub `adamant1337/VeldoraHaven1`
  and the local clone (`15eba70`, Aug 2) are a stale snapshot — development moved to
  admin-duplicated themes (v25→v28). Reconcile by pulling **live → local**; never push the
  stale local → live. GitHub is treated as historical until reconnected. See
  [`../shopify/LIVE-LOCAL-RECONCILIATION.md`](../shopify/LIVE-LOCAL-RECONCILIATION.md).
- **ADR-0009** (2026-08-22, accepted): **CAVEMAN MODE** — official token-efficiency
  operating layer. Full record: [`ADR-0009-caveman-token-optimization.md`](ADR-0009-caveman-token-optimization.md);
  policy: [`../.claude/skills/caveman/SKILL.md`](../.claude/skills/caveman/SKILL.md).
- **ADR-0008** (2026-08-22, accepted): **v28 (`205283819862`) is the working draft** —
  edit locally, `shopify theme push -e v28`, and `shopify theme publish -e v28` only on
  explicit approval. Live (`205129482582`) is reference; never push/publish over it from
  local. CLI store `iqeb6u-5h.myshopify.com`; envs in `theme/shopify.theme.toml`; workflow
  in [`../shopify/THEME-DEV-WORKFLOW.md`](../shopify/THEME-DEV-WORKFLOW.md).
- **ADR-0010** (2026-08-23, accepted): **Primary-session delegation criteria** — verified
  by live test that AGENTS.md's model policy governs subagents only (the primary session's
  model is user-set via `/model`, not agent-governed); the orchestrator/specialist layer is
  opt-in each turn, not auto-triggered. Default to direct execution for single-domain work;
  delegate via `Skill(veldorahaven-shopify-os)` → `Agent(orchestrator)` only for genuinely
  multi-domain or Opus-tier-strategy tasks. Full record:
  [`ADR-0010-primary-session-delegation.md`](ADR-0010-primary-session-delegation.md).
