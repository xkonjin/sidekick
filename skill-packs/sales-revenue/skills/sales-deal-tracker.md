---
name: sales-deal-tracker
description: "Maintain a living pipeline record for a deal. Trigger when the user says 'deal status', 'pipeline review', 'where are my deals', or names a specific company in a sales context."
---

Produces a deal card capturing stage, contacts, next steps, blockers, and probability. Keeps `sidekick/memory/pipeline.md` current.

## Process

### Step 1: Load Context

Read these files before proceeding:

- `sidekick/context/team-directory.md` - identify internal owners and relationship context
- `sidekick/context/current-priorities.md` - confirm which deals are tied to active priorities
- `sidekick/memory/deals/` - check if a record for this company already exists (if it exists)
- `sidekick/memory/pipeline.md` - load the current pipeline view (if it exists)

### Step 2: Clarify Deal Details

If the user hasn't specified, ask:

- What company is this deal with?
- What stage is it in? (Prospecting / Discovery / Proposal / Negotiation / Closed Won / Closed Lost)
- What is the next action and who owns it?
- What is the expected close date?
- Any blockers or risks?

Skip questions if the user's message already answers them.

### Step 3: Write the Deal Card

Produce the deal card in the output format below.

### Step 4: Save and Update Pipeline

- Save the deal card to `sidekick/memory/deals/[company].md`
- Update the relevant row in `sidekick/memory/pipeline.md` (create the file if it doesn't exist)
- Note the date of this update in both files

## Output Format

```markdown
# Deal: [Company Name]

**Last updated:** [DATE] | **Owner:** [Name from team-directory] | **Stage:** [Stage]

## Deal Snapshot

| Field       | Detail          |
| ----------- | --------------- |
| Company     | [Company name]  |
| Stage       | [Stage]         |
| Close date  | [Expected date] |
| Deal value  | [Amount or TBD] |
| Probability | [%]             |

## Contacts

| Name   | Role    | Relationship        |
| ------ | ------- | ------------------- |
| [name] | [title] | [warm/neutral/cold] |

## Next Steps

| Action   | Owner  | Due    |
| -------- | ------ | ------ |
| [action] | [name] | [date] |

## Blockers

- [Blocker and what's needed to clear it]

## Stage History

| Stage   | Date entered | Notes                |
| ------- | ------------ | -------------------- |
| [stage] | [date]       | [what moved it here] |
```

## After This Skill

- **sales-discovery-prep** — prep for an upcoming call with this prospect → Read `skill-packs/sales-revenue/skills/sales-discovery-prep.md`
- **meeting-prep** — prep for a meeting with a contact on this deal → Read `skill-packs/automation/skills/auto-meeting-prep.md`
- **email-drafter** — draft a follow-up to a contact on this deal → Read `skill-packs/automation/skills/auto-email-drafter.md`

## Rules

- Never assume deal stage without explicit confirmation from the user.
- Track every stage change with the date it happened.
- If a deal has no next action logged, flag it as a risk before saving.
- Never fabricate contact names, titles, or relationship warmth.
