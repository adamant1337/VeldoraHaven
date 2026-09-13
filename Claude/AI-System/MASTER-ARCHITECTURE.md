# VeldoraHaven AI System — Master Architecture

**Authoritative source of truth for how the VeldoraHaven multi-agent system is
designed and operates.** This document owns: agent hierarchy, dependencies, task
routing, handoffs, context management, token optimization, cache, file ownership,
repository & markdown governance, state management, quality gates, model selection,
and parallel/sequential execution.

**It does NOT restate:** the agent roster (see [`AGENTS.md`](../AGENTS.md)), activation
rules (see the [`veldorahaven-shopify-os`](../.claude/skills/veldorahaven-shopify-os/SKILL.md)
skill), brand truth (see [`brand/BRAND.md`](../brand/BRAND.md)), or the design system
(see [`design-system/DESIGN-SYSTEM.md`](../design-system/DESIGN-SYSTEM.md)).

> Scope note: this describes the **AI agent system**, which is deliberately kept
> separate from the Shopify theme repository. The theme is external and its linkage is
> tracked in [`shopify/README.md`](../shopify/README.md).

---

## 1. Agent hierarchy

**Above this hierarchy sits the primary session** (the assistant actually talking to the
user), whose own model is set only by the user via `/model` — not by anything below.
Entering this hierarchy at all is a per-turn judgment call, not automatic: default to
direct execution for single-domain, well-scoped work (Caveman: "can I do this myself?");
delegate — via `Skill(veldorahaven-shopify-os)` then `Agent(veldorahaven-orchestrator)` —
only when the task is genuinely multi-domain, needs an Opus-tier strategic call the primary
session shouldn't make solo, or the user explicitly wants the orchestrated flow. Verified by
live test, not assumed: see [ADR-0010](../decisions/ADR-0010-primary-session-delegation.md).

Three layers coordinated by one orchestrator (roster + models: [`AGENTS.md`](../AGENTS.md)):

```
                    veldorahaven-orchestrator  (Opus)
                                │
        ┌───────────────────────┼───────────────────────┐
   STRATEGY / DESIGN        TECHNICAL              PAGE EXPERIENCE
   brand-director (O)       shopify-architect (O)  product-experience (O)
   luxury-ux-cro (O)        liquid-engineer (S)    homepage-director (O)
   visual-designer (O)      component-builder (S)  collection-experience (S)
                            performance-eng (S)    cart-aov-specialist (S)
   CROSS-CUTTING            accessibility (S)      seo-specialist (S)
   mobile-specialist (S)
                                │
                    veldorahaven-final-critic  (Opus, gate)
```
(O = Opus, S = Sonnet.) The orchestrator selects the **minimum** set per task.

---

## 2. Dependencies

Typical producer → consumer edges:

- brand-director → visual-designer → (component-builder | liquid-engineer)
- luxury-ux-cro → page-experience agents (product/collection/homepage/cart)
- shopify-architect → liquid-engineer, component-builder
- product-experience → (needs specs; may block on missing product data → `products/`)
- all implementation → mobile / performance / accessibility (review) → final-critic

**Rule:** design/architecture decisions precede implementation; cross-cutting reviews
follow implementation; final-critic is always last for significant work.

---

## 3. Task routing

Orchestrator maps request → minimum agent set:

| Request shape | Route |
| --- | --- |
| Visual change to a page | brand-director → visual-designer → page-experience → shopify-architect → final-critic |
| New/updated PDP | product-experience → (architect if new structure) → liquid-engineer/component-builder → a11y/mobile → final-critic |
| Homepage restructure | homepage-director → brand/visual → component-builder → perf/mobile → final-critic |
| Cart/AOV | cart-aov-specialist → ux-cro → liquid-engineer → final-critic |
| Perf regression | performance-engineer → (liquid/component-builder to fix) → final-critic |
| SEO pass | seo-specialist → (liquid-engineer for template edits) → final-critic |
| Pure Liquid bug | liquid-engineer → final-critic |

Do NOT auto-add SEO/a11y/cart/perf/product unless the task requires them.

---

## 4. Handoffs

Compact structured YAML; never require rereading the full conversation:

```yaml
task_id: ; status: in-progress|complete|blocked
completed: ; files_changed: ; tests: ; decisions:
blockers: ; dependencies: ; next_action:
```

Handoffs pass **references** (paths, line ranges, IDs), not file dumps. Completed
handoffs of note are summarized into `state/` (active) or `decisions/` (durable).

---

## 5. Context management

Never hand an agent the whole repo. Progressive loading:

```
L0 current task  →  L1 relevant file names  →  L2 relevant file sections
                 →  L3 dependencies         →  L4 broader repo context
```

Start at the smallest useful level; escalate only when necessary. After milestones,
**compact** context into `state/STATE.md` and discard transient history.

---

## 6. Token optimization → CAVEMAN MODE

First-class constraint. The authoritative token-efficiency policy is **CAVEMAN MODE**:
[`.claude/skills/caveman/SKILL.md`](../.claude/skills/caveman/SKILL.md) (ADR-0009).
Essence: minimize input+output tokens, repeated context, duplicated reasoning, unnecessary
agents, and unnecessary file reads; prefer paths/line-ranges/diffs/IDs/compact summaries
over whole files or prior outputs; fewer, stronger agents beat many weak ones; default to
the cheapest capable model (§10). Follow Caveman for the full rules (context budget,
file-read discipline, cache TTL/invalidation, handoff compression, search/tool minimization,
stop condition). Do not restate them here.

---

## 7. Cache hierarchy, TTL, invalidation

Conceptual cache (materialized as the `state/`, `cache/`, `decisions/`, `archive/`
directories):

| Level | Holds | Store | TTL |
| --- | --- | --- | --- |
| L1 current task | objective, current files, errors, immediate decisions | in-context / `cache/` | seconds–minutes |
| L2 active agent state | agent state, active tasks, recent results | `state/` | minutes–hours |
| L3 stable knowledge | brand, design system, architecture, Shopify rules | `brand/` `design-system/` `architecture/` | days–weeks |
| L4 historical | completed tasks, old decisions, previous implementations | `archive/` `decisions/` | indefinite |

**Volatility → TTL:** git/build/test status = seconds–minutes; agent/task state =
minutes–hours; architecture/design/brand = days–weeks; history = indefinite.

**Invalidation is targeted, never global.** Example chain:
`product-card.liquid → product-card cache → collection UI cache`. Invalidate only
dependent entries; leave unrelated knowledge intact.

---

## 8. File ownership

Before editing a file, confirm no active task locks it. Conceptual lock record (kept in
`state/`):

```yaml
file: sections/main-product.liquid
owner: product-experience
task_id: PDP-042
locked: true
```

Coordinate before simultaneous edits; **never silently overwrite** another agent's
uncommitted work. Release the lock on handoff/completion.

---

## 9. Repository & markdown governance

- Before edits: check state, inspect changes, verify ownership, identify active tasks +
  dependencies, change the minimum necessary.
- **No destructive Git operations without explicit user authorization.**
- Never destroy another agent's uncommitted work.
- Before creating a `.md`: search existing docs; reuse/extend rather than duplicate.
- No `x-v2 / x-new / x-final` duplicates without real versioning. Split large files only
  when genuinely useful. **One authoritative source per topic** (see the map in §12).

---

## 10. Model selection (hybrid)

- **Opus:** orchestrator, brand-director, luxury-ux-cro, visual-designer,
  shopify-architect, product-experience, homepage-director, final-critic.
- **Sonnet (default for implementation/audit):** liquid-engineer, component-builder,
  mobile-specialist, performance-engineer, accessibility-specialist, seo-specialist,
  cart-aov-specialist.
- **Escalation:** the orchestrator may promote a normally-Sonnet task to Opus when it
  genuinely needs Opus-level reasoning (ambiguous requirements, novel architecture,
  cross-cutting trade-offs, subtle correctness/brand risk), stating why in one line.
  It does not escalate routine, well-scoped work. Optimize quality per token.

---

## 11. Parallel vs sequential execution

- **Parallel** — independent analysis: `brand + UX + technical → orchestrator →
  implementation → review`.
- **Sequential** — dependent work: `architecture → implementation → integration test →
  review`. Never parallelize a dependency chain.

---

## 12. State management & source-of-truth map

Each topic has exactly one authoritative file/dir:

| Topic | Authoritative source |
| --- | --- |
| System architecture (this doc) | `architecture/MASTER-ARCHITECTURE.md` |
| Agent roster & models | `AGENTS.md` |
| Activation / operating rules | `.claude/skills/veldorahaven-shopify-os/SKILL.md` |
| Agent behavior (per agent) | `.claude/agents/*.md` |
| Brand | `brand/BRAND.md` |
| Design system | `design-system/DESIGN-SYSTEM.md` |
| Product data & specs | `products/` |
| Shopify theme linkage & notes | `shopify/README.md` |
| Live working state / locks | `state/` |
| Ephemeral caches | `cache/` |
| Durable decisions (ADRs) | `decisions/` |
| History | `archive/` |

**State lifecycle:** active work → `state/STATE.md`; durable choices → `decisions/`;
finished/superseded → `archive/`.

---

## 13. Quality gates

Before significant work is "done": correct implementation; relevant tests pass; no
unintended changes; no duplicate docs; state updated + cache invalidated as needed;
design-system consistent; mobile/performance/accessibility considered; Shopify
architecture maintainable; **final-critic** reviewed → APPROVE / REQUEST CHANGES /
REJECT.
