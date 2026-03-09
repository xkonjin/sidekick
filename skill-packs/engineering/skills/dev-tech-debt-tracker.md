---
name: tech-debt-tracker
description: "Audit and prioritize technical debt. Trigger when the user says 'tech debt', 'debt audit', 'what should we refactor', 'technical debt review', or 'what's the state of our codebase'."
---

# Tech Debt Tracker

Surfaces, categorizes, and scores technical debt items so teams can make informed prioritization decisions instead of letting debt pile up invisibly.

## Process

### Step 1: Load Context

Read:

- `sidekick/context/current-priorities.md` - Align debt priority with current goals
- `sidekick/context/working-preferences.md` - Output format (if it exists)

### Step 2: Gather Debt Items

Ask what to audit if not provided:

- Are there known debt items to log, or should we identify them from code/docs?
- Any specific systems, services, or areas to focus on?
- What's the team size and rough velocity? (Context for prioritization)

If the user provides code, a list of issues, or a conversation about the codebase, extract debt items from that input.

### Step 3: Categorize Each Item

For every debt item, assign a category:

| Category          | Examples                                                               |
| ----------------- | ---------------------------------------------------------------------- |
| **Architecture**  | Monolith coupling, wrong abstraction boundaries, service proliferation |
| **Code quality**  | Duplicated logic, God classes, missing abstractions                    |
| **Testing**       | No tests, brittle tests, missing integration coverage                  |
| **Dependencies**  | Outdated packages, deprecated APIs, abandoned libraries                |
| **Documentation** | Missing runbooks, stale docs, undocumented public APIs                 |
| **Observability** | Missing metrics, no alerting, poor log structure                       |
| **Security**      | Unpatched CVEs, hardcoded secrets, missing auth checks                 |
| **Performance**   | Known slow queries, unindexed tables, memory leaks                     |

### Step 4: Score Each Item

Score on two dimensions (1-5 scale):

- **Impact:** How much does fixing this improve reliability, velocity, or safety?
- **Effort:** How long would a fix take? (1 = days, 5 = months)

Priority = Impact / Effort. High impact, low effort = fix first.

### Step 5: Output the Register

```markdown
## Tech Debt Register — [Date]

### High Priority (fix within quarter)

| Item        | Category   | Impact | Effort | Priority    | Owner         | Notes     |
| ----------- | ---------- | ------ | ------ | ----------- | ------------- | --------- |
| [Debt item] | [Category] | [1-5]  | [1-5]  | [I/E ratio] | [Name or TBD] | [Context] |

### Medium Priority (schedule this half)

| Item | Category | Impact | Effort | Priority | Owner | Notes |
| ---- | -------- | ------ | ------ | -------- | ----- | ----- |

### Low Priority / Backlog

| Item | Category | Impact | Effort | Priority | Owner | Notes |
| ---- | -------- | ------ | ------ | -------- | ----- | ----- |

### Won't Fix (accepted debt)

| Item   | Reason                            |
| ------ | --------------------------------- |
| [Item] | [Why this is acceptable to carry] |
```

Save to `sidekick/outputs/tech-debt-[DATE].md`.

## Rules

- Score honestly. Effort is often underestimated — bias toward higher effort estimates.
- "Won't Fix" is a valid category. Acknowledged debt is better than invisible debt.
- Tie priorities to current goals from `sidekick/context/current-priorities.md`
- An unowned item is unlikely to get fixed. Push for owners on high priority items.
- Revisit quarterly at minimum. Debt that ages becomes more expensive to pay down.
