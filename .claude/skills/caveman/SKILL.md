---
name: caveman
description: Token-minimal operating system for VeldoraHaven agents. Reduces context consumption, repeated reads, redundant reasoning, unnecessary tool calls, and duplicated information while preserving quality.
---

# CAVEMAN MODE

**Do more work · with less context · using fewer tokens · without reducing quality.**

Authoritative token-efficiency policy for the VeldoraHaven AI OS. Applies to every agent.
This file does not restate the architecture — it references it:
roster → [`AGENTS.md`](../../../AGENTS.md); system design →
[`architecture/MASTER-ARCHITECTURE.md`](../../../architecture/MASTER-ARCHITECTURE.md);
live state → [`state/STATE.md`](../../../state/STATE.md); caches → [`cache/`](../../../cache/);
decisions → [`decisions/`](../../../decisions/) (ADR-0009).

## Core rule

READ LESS · REMEMBER MORE · REUSE MORE · WRITE ONLY WHAT MATTERS · ASK ONLY WHEN BLOCKED ·
DO NOT REPEAT CONTEXT · DO NOT RE-ANALYZE KNOWN INFORMATION.

Three gates before acting:
- **Before reading a file:** "Do I need this to finish the task?" No → don't read it.
- **Before calling an agent:** "Can I do this myself?" Yes → do it yourself.
- **Before creating a doc:** "Does a source of truth exist?" Yes → update/reference it.

## Context budget (load the least that suffices)

`L0 task → L1 agent instructions → L2 source-of-truth → L3 cache → L4 implementation
files → L5 history`. Never load L3–L5 when L0–L2 suffice. Never load the whole repo for a
local task. Pattern: **search → locate → read small range**, never read-everything.

## File-reading rules

Never blind-read entire repos/dirs/all-*.md/all-agents/all-liquid/all-assets. Instead:
identify task → identify likely files → search for the exact spot → read only that range →
implement → verify only affected areas. (Fixing a button ≠ reading every snippet;
optimizing one hero ≠ reading every asset.)

## Handoff protocol (compact, never a context dump)

```
TASK: · GOAL: · RELEVANT FILES: · CURRENT STATE: · ACTION REQUIRED: · CONSTRAINTS: · OUTPUT:
```
Extends the structured handoff in MASTER-ARCHITECTURE §4. Pass references (paths/line
ranges/IDs), never file bodies.

## Cache (see MASTER-ARCHITECTURE §7 for the L1–L4 model; TTLs authoritative here)

Cache only knowledge that is **expensive to discover + frequently reused + stable +
multi-agent**. Candidates: [`cache/theme-structure.md`](../../../cache/), `design-tokens.md`,
`shopify-architecture.md`, `pdp-data-map.md`, `agent-context.md`. Never cache trivial or
constantly-changing info without a TTL.

**TTL classes:** STATIC (brand, design tokens, architecture) 30–90d / until source changes ·
SEMI-STABLE (theme structure, component map, Shopify architecture) 7–30d · DYNAMIC (task
state, git branch, Shopify/live state) minutes–hours · EPHEMERAL (reasoning, searches) task
lifetime.

**Invalidation is targeted, dependency-driven:** `DESIGN-SYSTEM.md → cache/design-tokens.md
→ visual agents`; theme-arch change → theme-structure cache; product-data change → PDP/
product caches. Never invalidate unrelated caches. Never trust stale cache when correctness
matters.

## Agent economy

Stay in role (boundaries: MASTER-ARCHITECTURE §1–3 + `AGENTS.md`). Never let multiple agents
independently solve or inspect the same thing — the Orchestrator picks the **minimum
sufficient set**. If a trustworthy prior result exists, **read it, don't re-derive it**;
re-analyze only when the source changed, cache expired, the result is incomplete/contradicted,
or the task needs more depth.

## Tool & search discipline

Before any tool call: "Can I answer this from what I already have?" Yes → skip it. Search
**targeted and once** ("where is the product-card heading font defined?"), not broad ("find
everything Shopify"); reuse results; no overlapping searches unless the first was
insufficient. Don't re-check the same state.

## Communication

Concise. No repeating the task/architecture/brand/prior findings, no narrating obvious
actions, no summarizing unchanged files. Prefer:
```
DONE: · FILES: · RESULT: · ISSUES:
```

## Documentation

No duplicate `.md` (no `x-analysis / x-audit / x-review / x-final`). One authoritative file
per topic in the existing tree (`architecture/ brand/ design-system/ products/ shopify/
state/ cache/ decisions/`). Update or reference — never fork knowledge.

## Git efficiency

`git status` / `git diff --stat` first; inspect full diffs only for relevant files. Focused
commits. Don't re-inspect unchanged files or dump huge diffs into context.

## Implementation & change discipline

Smallest correct change. No unrelated refactors/redesigns/rewrites; don't replace working
architecture without evidence. Follow **KEEP → IMPROVE → REPLACE**
([`architecture/VELDORAHAVEN-IMPROVEMENT-ROADMAP.md`](../../../architecture/VELDORAHAVEN-IMPROVEMENT-ROADMAP.md)).

## Error handling

No blind retries. Identify failure → read the error → determine likely cause → one targeted
fix → retry → if still blocked, report. Never burn tokens repeating a failed operation.

## Orchestrator: token governance

Before delegating, estimate complexity / agents / files / context / tool calls and choose the
**smallest sufficient team** (simple CSS change = Component Builder + verify, not all 15).
Track compactly: agents invoked · files read/modified · tool calls · cache hits/misses ·
reads & agent-calls avoided · escalations. Compact summaries only — no per-action logs.

## Model policy (see AGENTS.md / MASTER-ARCHITECTURE §10)

Default to the cheapest capable model (**Sonnet** for straightforward, localized, clear-
architecture work). **Escalate to Opus** only for ambiguity, conflicting systems, major UX
decisions, high-risk changes, complex debugging, or strategic reasoning. Never Opus just
because it's available.

## Decision tree

```
TASK → know enough? ─yes→ EXECUTE
                    └no→ get ONLY the smallest missing info → EXECUTE → VERIFY
                         → cache if reusable → STOP
```

## Stop condition

Stop when the requested task is done, verification passes, and state is updated if needed.
Don't keep exploring or auto-optimize unrelated files. Then report.

## Priority when rules conflict

1 Correctness · 2 Safety · 3 Existing architecture · 4 Task completion · 5 Token efficiency ·
6 Elegance. **Never sacrifice correctness to save tokens.**

## Anti-patterns (never)

Reread the whole repo/all agents · repeat architecture/brand · duplicate SoT · call agents
unnecessarily · Opus without cause · broad search for a narrow task · duplicate `.md` · dump
huge diffs · retry failures blindly · analyze unrelated components · work past completion.

## Activation

Applies to all VeldoraHaven work by default (it is the OS's efficiency layer). The
`veldorahaven-shopify-os` skill governs *what/who*; Caveman governs *how efficiently*.
