# VeldoraHaven — Agent Registry

**Authoritative source of truth for: which agents exist, what each owns, and which
model each runs on.** For *how* they coordinate (routing, handoffs, cache, context,
governance), see [`architecture/MASTER-ARCHITECTURE.md`](architecture/MASTER-ARCHITECTURE.md).
For *when/how to activate* the system, see the
[`veldorahaven-shopify-os`](.claude/skills/veldorahaven-shopify-os/SKILL.md) skill.

Agents are **project-scoped** in `.claude/agents/` (not user scope). Invoke via the
Agent tool by name, or let `veldorahaven-orchestrator` select them.

**All agents operate under CAVEMAN MODE** — the token-efficiency policy in
[`.claude/skills/caveman/SKILL.md`](.claude/skills/caveman/SKILL.md) (ADR-0009): read less,
reuse more, minimum agent set, smallest sufficient context, cheapest capable model,
targeted searches, compact handoffs, no duplicate knowledge.

## Model strategy (hybrid)

Opus for high-reasoning strategy / design / architecture / final judgement. Sonnet for
well-specified implementation and audit roles (default, to minimize tokens). The
**orchestrator may escalate a Sonnet task to Opus** when the task genuinely needs
Opus-level reasoning (ambiguous requirements, novel architecture, cross-cutting
trade-offs, subtle correctness/brand risk). See MASTER-ARCHITECTURE §Model Selection.

## Roster

| # | Agent | Model | Domain it owns | Primary owned paths |
| - | --- | --- | --- | --- |
| 0 | `veldorahaven-orchestrator` | **Opus** | Coordination, task graphs, agent selection, dependency ordering, handoffs, escalation | `state/`, `decisions/` |
| 1 | `veldorahaven-brand-director` | **Opus** | Brand identity, art direction, premium positioning, consistency | `brand/` |
| 2 | `veldorahaven-luxury-ux-cro` | **Opus** | Journey, conversion, trust, high-ticket psychology, consultation flows | — (advisory) |
| 3 | `veldorahaven-visual-designer` | **Opus** | Typography, color, spacing, grid, layout, motion, photo treatment | `design-system/` |
| 4 | `veldorahaven-shopify-architect` | **Opus** | Theme architecture, JSON templates, sections/blocks/snippets, metafields, settings | `architecture/` (theme), `shopify/` structure |
| 5 | `veldorahaven-product-experience` | **Opus** | PDP storytelling per category; required specs/metafields | `products/`, `shopify/` PDP templates |
| 6 | `veldorahaven-homepage-director` | **Opus** | Homepage narrative & section order | `shopify/` homepage template |
| 7 | `veldorahaven-final-critic` | **Opus** | Final quality gate across all dimensions | — (read-only reviewer) |
| 8 | `veldorahaven-liquid-engineer` | Sonnet | Liquid, objects, filters, loops, dynamic/product/collection/cart logic | `shopify/` Liquid |
| 9 | `veldorahaven-component-builder` | Sonnet | Reusable, configurable, responsive, theme-editor components | `shopify/` sections/snippets |
| 10 | `veldorahaven-mobile-specialist` | Sonnet | Mobile layouts, touch, nav, sticky CTAs, responsive behavior | — (advisory / cross-cutting) |
| 11 | `veldorahaven-performance-engineer` | Sonnet | Core Web Vitals, images, JS/CSS, Liquid perf, third-party, requests | — (cross-cutting) |
| 12 | `veldorahaven-accessibility-specialist` | Sonnet | Semantics, keyboard, focus, contrast, ARIA, labels, SR, modals | — (cross-cutting) |
| 13 | `veldorahaven-seo-specialist` | Sonnet | Metadata, titles, descriptions, headings, structured data, links, alt text | `shopify/` templates (SEO fields) |
| 14 | `veldorahaven-cart-aov-specialist` | Sonnet | Cart drawer/page, upsells, cross-sells, bundles, recommendations, AOV | `shopify/` cart |
| 15 | `veldorahaven-collection-experience` | Sonnet | Collection architecture, grids, cards, filters, sorting, discovery | `shopify/` collection templates |

**Advisory** agents produce recommendations/specs rather than owning a directory;
their output is consumed by engineers and captured in `state/` or `decisions/`.

## File-ownership rule (summary)

Before editing a file, check it isn't locked by another active task. Coordinate;
never silently overwrite. Locking mechanics and the active-lock table live in
[`state/`](state/) — see MASTER-ARCHITECTURE §File Ownership.
