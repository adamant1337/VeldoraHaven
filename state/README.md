# state/ — Live Working State (L2 cache)

**Responsibility:** current, volatile system state — active tasks, agent state, file
locks, and recent results. TTL: minutes–hours. Compact and prune often. Durable choices
graduate to [`../decisions/`](../decisions/); finished work goes to
[`../archive/`](../archive/). See MASTER-ARCHITECTURE §7–8, §12.

- `STATE.md` — the single live state file (active tasks + file-ownership locks).
- Keep entries compact (references, not file dumps). Delete stale entries.
