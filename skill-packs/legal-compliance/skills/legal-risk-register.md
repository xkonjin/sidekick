---
name: risk-register
description: "Build or update a living risk register with probability/impact matrix, owners, and mitigation status. Trigger when the user says 'risk register', 'what are our risks', 'risk assessment', or 'risk matrix'."
---

# Risk Register

Maintains a living log of organizational, operational, and project risks. Assigns probability, impact, owners, and mitigation status. Produces a prioritized matrix for review at milestones.

## Process

### Step 1: Load Context

Read:

- `sidekick/memory/decisions.md` - Check for risks flagged in past decisions
- `sidekick/memory/projects/*.md` - Understand active projects and their dependencies
- `sidekick/context/current-priorities.md` - Anchor risk severity to what matters now
- `sidekick/memory/risk-register.md` - Load existing register if it exists; update rather than replace

### Step 2: Scope the Session

Ask if not specified:

- Is this a new risk register or an update to an existing one?
- What is the scope? (specific project, product area, whole organization)
- Are there specific risk categories to focus on? (technical, regulatory, financial, team, market)

### Step 3: Identify and Score Risks

For each risk, capture:

- **Description** — specific failure scenario, not a vague category
- **Category** — Technical / Regulatory / Financial / Team / Market / Operational / External
- **Probability** — H (likely within 6 months) / M (possible) / L (unlikely but plausible)
- **Impact** — H (blocks a top priority or causes significant harm) / M (material disruption) / L (manageable setback)
- **Priority** — derived: HH = Critical, HM/MH = High, MM = Medium, everything else = Low
- **Owner** — one person accountable for monitoring this risk
- **Mitigation** — what is actively being done to reduce probability or impact
- **Status** — Open / Mitigated / Accepted / Closed

### Step 4: Write and Save the Register

Write to `sidekick/memory/risk-register.md`. If the file already exists, update in place — do not overwrite entries without checking their current status first.

```markdown
# Risk Register

**Last updated:** [date] | **Scope:** [project / organization]

## Priority Matrix

| Priority | Criteria                       | Count |
| -------- | ------------------------------ | ----- |
| Critical | High probability + High impact | [n]   |
| High     | High + Medium or Medium + High | [n]   |
| Medium   | Medium + Medium                | [n]   |
| Low      | All other combinations         | [n]   |

## Risk Log

| ID   | Risk                        | Category   | Prob  | Impact | Priority              | Owner  | Mitigation          | Status |
| ---- | --------------------------- | ---------- | ----- | ------ | --------------------- | ------ | ------------------- | ------ |
| R001 | [Specific risk description] | [Category] | H/M/L | H/M/L  | Critical/High/Med/Low | [name] | [What's being done] | Open   |

## Critical Risks — Detail

### R[ID]: [Risk Name]

- **Scenario:** [What happens if this risk materializes]
- **Early warning signal:** [What you'd see before it becomes a crisis]
- **Mitigation:** [Steps to reduce probability or impact]
- **Contingency:** [Response plan if it materializes anyway]
- **Owner:** [name] | **Review date:** [when to reassess]

## Change Log

| Date   | Change                      |
| ------ | --------------------------- |
| [date] | [What was added or updated] |
```

## After This Skill

- **pre-mortem** — run a forward-looking failure analysis on a specific project using this register as input → Read `skill-packs/product-management/skills/pm-pre-mortem.md`
- **decision-log** — log a decision to accept, mitigate, or close a risk → Read `skills/decision-log/SKILL.md`

## Rules

- Every risk needs one named owner. "Team" or "leadership" is not an owner.
- Probability and impact are scored independently. Do not conflate them.
- Critical risks must have a mitigation AND a contingency. A mitigation without a contingency is incomplete.
- When updating an existing register, append to the Change Log — never silently overwrite.
- "Accepted" status means a deliberate decision was made to live with the risk. Require confirmation before setting this.
