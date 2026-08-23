# ADR-0010: Primary-session delegation criteria
Date: 2026-08-23 · Status: accepted

## Context

A model-routing audit (2026-08-23) verified the actual Claude Code mechanism behind
AGENTS.md's roster and MASTER-ARCHITECTURE §10's model policy, rather than assuming the
documented flow ran automatically. Findings, confirmed by live test (two `Agent` calls,
one to a Sonnet-frontmatter specialist, one to the Opus-frontmatter orchestrator, with the
primary session itself on Sonnet at the time):

- The **primary/top-level session's model is user-controlled only**, via the `/model`
  slash command. No agent, skill, or orchestrator logic can change it. AGENTS.md's model
  policy governs **subagents only** — it has no jurisdiction over the session actually
  talking to the user.
- A subagent's `model:` frontmatter **is honored** by the `Agent` tool, confirmed by
  isolation test (orchestrator subagent self-reported Opus while the parent session was
  Sonnet).
- Nothing auto-invokes `Skill(veldorahaven-shopify-os)` or
  `Agent(veldorahaven-orchestrator)` on a VeldoraHaven-shaped user message. Both are
  opt-in, decided each turn by whichever assistant is currently running, informed by
  Caveman's own instruction: *"Before calling an agent: 'Can I do this myself?' Yes → do
  it yourself."*
- Across a full multi-task session (R0–R4), the primary session never invoked the
  orchestrator or any specialist and completed every task directly — correctly, per
  Caveman, since each task was single-domain and well-scoped. Each diagnostic subagent
  call in the audit cost 11k–17k tokens just to spin up and report back, confirming that
  routing everything through the orchestrator layer by default would be a net token loss,
  not a saving.

## Decision

Formalize the decision the primary session must make each turn, as the layer that sits
**above** the hierarchy in MASTER-ARCHITECTURE §1 (that diagram starts at the orchestrator;
this ADR defines what decides whether the diagram is entered at all):

```
PRIMARY SESSION (model set by user via /model — NOT agent-governed)
 ↓ judgment call each turn:
   "Is this VeldoraHaven work I can do directly (Caveman: 'can I do this myself?'),
    or does it need the multi-agent org (multi-domain, needs Opus-tier strategy
    I shouldn't do solo, or the user explicitly wants the orchestrated flow)?"
 ↓ if delegating:
 Skill(veldorahaven-shopify-os)  ← the documented entry point, actually invoked
 ↓
 Agent(veldorahaven-orchestrator, model: opus per frontmatter)
 ↓
 orchestrator calls Agent(specialist, model: per specialist's own frontmatter)
 ↓
 optional Agent(veldorahaven-final-critic, model: opus)
```

Default: direct execution by the primary session for single-domain, well-scoped work.
Delegate (enter the diagram via the skill, not by skipping straight to a named agent) when
the task is genuinely multi-domain, needs an Opus-tier strategic call the primary session
shouldn't make solo, or the user explicitly asks for the orchestrated/agency flow.

Do not build a router, hook, or auto-trigger for this — none exists in Claude Code, and
inventing one would violate the "only supported mechanisms" rule. The judgment call stays
a judgment call.

## Consequences

- `AGENTS.md` and `MASTER-ARCHITECTURE.md` §1 must not imply the hierarchy is entered
  automatically; both now point here.
- Sessions doing small, well-scoped VeldoraHaven work correctly skip the orchestrator —
  that is not a bug to fix.
- The token-cost figures above (11k–17k per diagnostic subagent round-trip) are the
  reference point for judging whether a given task's delegation overhead is worth it.
