# Decision Log & Assumption Register

Created automatically when a decision is first recorded. Prevents re-litigating settled decisions and catches when assumptions go stale.

---

## Decisions

| #   | Date | Decision | Owner | Rationale | Status |
| --- | ---- | -------- | ----- | --------- | ------ |

## Assumptions Register

| #   | Assumption | Evidence | Confidence | Invalidation Signal | Review Date | Status |
| --- | ---------- | -------- | ---------- | ------------------- | ----------- | ------ |

## Rules

- Never fabricate decisions. If you can't find the source, say so.
- When an assumption is invalidated, flag all linked decisions
- Decisions can be reversed. Mark old as SUPERSEDED, log the new one.
