---
name: cs-account-health
description: "Score and document the health of a customer account. Trigger when the user says 'account health', 'how is [customer] doing', or 'churn risk'."
---

Produces a health card capturing usage signals, relationship warmth, recent interactions, risk factors, and recommended actions. Flags accounts at risk before they become escalations.

## Process

### Step 1: Load Context

Read these files before proceeding:

- `sidekick/context/team-directory.md` - identify the account owner and any internal contacts
- `sidekick/memory/accounts/[customer].md` - load existing account record (if it exists)
- `sidekick/outputs/` - scan for recent meeting notes or QBR docs related to this account (if it exists)

### Step 2: Identify the Account

If the user hasn't specified, ask:

- Which customer account is this for?
- Any specific concern that triggered this review?

Skip questions if the user's message already answers them.

### Step 3: Score Account Health

Assess each dimension based on available data. Flag dimensions where data is missing.

| Dimension           | Signal to assess                                     |
| ------------------- | ---------------------------------------------------- |
| Product usage       | Active / declining / no recent activity              |
| Relationship warmth | Last contact date, response rate, sponsor engagement |
| Commercial status   | Renewal date, expansion potential, past disputes     |
| Support load        | Open tickets, recent escalations                     |
| Strategic fit       | Are they using the product for its intended purpose? |

### Step 4: Save and Update

- Save health card to `sidekick/memory/accounts/[customer].md`
- If health is Red, recommend immediate action before saving

## Output Format

```markdown
# Account Health: [Customer Name]

**Last reviewed:** [DATE] | **Owner:** [Name] | **Overall health:** Green / Yellow / Red

## Health Scorecard

| Dimension     | Status           | Notes                           |
| ------------- | ---------------- | ------------------------------- |
| Product usage | Green/Yellow/Red | [what you observed]             |
| Relationship  | Green/Yellow/Red | [last contact, sponsor status]  |
| Commercial    | Green/Yellow/Red | [renewal date, expansion flags] |
| Support load  | Green/Yellow/Red | [open tickets, recent issues]   |
| Strategic fit | Green/Yellow/Red | [using as intended?]            |

## Risk Factors

- [Specific risk and why it matters]

## Recommended Actions

| Action   | Owner  | By When |
| -------- | ------ | ------- |
| [action] | [name] | [date]  |

## Interaction History

| Date   | Type             | Summary              |
| ------ | ---------------- | -------------------- |
| [date] | [call/email/QBR] | [what was discussed] |
```

## After This Skill

- **cs-qbr-builder** — if renewal or quarterly review is upcoming → Read `skill-packs/customer-success/skills/cs-qbr-builder.md`
- **meeting-prep** — prep for an account check-in call → Read `skill-packs/automation/skills/auto-meeting-prep.md`
- **email-drafter** — draft a re-engagement message for an at-risk account → Read `skill-packs/automation/skills/auto-email-drafter.md`

## Rules

- Flag accounts with no interaction in 30+ days regardless of other scores.
- Distinguish symptoms from root causes. "Usage is declining" is a symptom. Investigate why.
- Never fabricate interaction history or usage data. If data is missing, state it.
- Overall health score must be the worst of any individual dimension, not an average.
