# ADR-0009: Caveman token-optimization system

Date: 2026-08-22 · Status: accepted

> Filename note: requested as "ADR-0007" but renumbered to **0009** — ADR-0007
> (source of truth) and ADR-0008 (v28 working draft) already exist. Duplicate ADR
> numbers are the kind of conflicting knowledge Caveman forbids, so the next free
> number is used.

## Context

The VeldoraHaven AI OS is a 16-agent, multi-document system. Without an explicit
efficiency policy, agents tend to over-read (whole files/repos), re-derive known facts,
over-recruit agents, over-use Opus, run broad searches, and duplicate Markdown — all of
which burn tokens and context without improving quality.

## Decision

Adopt **CAVEMAN MODE** as the official token-efficiency operating layer, defined
authoritatively in [`../.claude/skills/caveman/SKILL.md`](../.claude/skills/caveman/SKILL.md).
`veldorahaven-shopify-os` governs *what/who*; Caveman governs *how efficiently*. Key
commitments:

- **Context minimization** — smallest useful context via the L0→L5 budget; `search →
  locate → read small range`, never read-everything.
- **File-read minimization** — three gates (need-to-read / do-it-myself / SoT-exists);
  never blind-read repos, dirs, or all-of-a-type.
- **Cache strategy** — cache only expensive+reused+stable+multi-agent knowledge; TTL
  classes STATIC / SEMI-STABLE / DYNAMIC / EPHEMERAL; targeted, dependency-driven
  invalidation; never trust stale cache when correctness matters.
- **Agent minimization** — Orchestrator picks the minimum sufficient set; no parallel
  duplicate analysis; read prior results instead of re-deriving.
- **Model escalation** — default Sonnet; Opus only for ambiguity / conflicting systems /
  major UX / high-risk / complex debugging / strategic reasoning.
- **Handoff compression** — `TASK/GOAL/RELEVANT FILES/CURRENT STATE/ACTION/CONSTRAINTS/
  OUTPUT`; references not file bodies; concise output (`DONE/FILES/RESULT/ISSUES`).
- **Priority on conflict** — Correctness > Safety > Existing architecture > Task
  completion > Token efficiency > Elegance. Never trade correctness for tokens.

## Consequences

- Lower token/context use per task with quality preserved (correctness is priority #1).
- Integrated by reference (no duplication) in `AGENTS.md`,
  `architecture/MASTER-ARCHITECTURE.md` §6, and
  `.claude/agents/veldorahaven-orchestrator.md` (token governance).
- Orchestrator gains a token-governance duty and tracks compact efficiency metrics.
