---
name: sales-discovery-prep
description: "Research a prospect and generate a discovery call script. Trigger when the user says 'prep for discovery', 'first call with', or 'sales call prep'."
---

Produces a pre-call brief with company context, open-ended discovery questions, talking points, objection prep, and desired outcomes. Research-first, template-second.

## Process

### Step 1: Load Context

Read these files before proceeding:

- `sidekick/context/team-directory.md` - check if this prospect is already known
- `sidekick/memory/competitors/` - identify any competing products the prospect might use (if it exists)
- `sidekick/memory/deals/` - check for any existing deal context on this prospect (if it exists)

### Step 2: Clarify the Meeting

If the user hasn't specified, ask:

- Who is the prospect? (company name, contact name and role)
- What do you know about why they're talking to you?
- What is your desired outcome from this call?

Skip questions if the user's message already answers them.

### Step 3: Research the Prospect

If web search is available, look up:

- Company size, industry, recent news, and known pain points
- The contact's role, tenure, and LinkedIn signals
- Any known competitors or alternative solutions they use

Flag when information is unavailable or unverified.

### Step 4: Build the Brief

Produce the discovery prep output in the format below.

### Step 5: Save Output

Write to `sidekick/outputs/discovery-prep-[company]-[DATE].md`.

## Output Format

```markdown
# Discovery Prep: [Company] — [DATE]

**Contact:** [Name, Title] | **Meeting type:** [Video / Phone / In-person]

## Company Context

[3-5 sentences: what they do, size, market position, recent signals]

## Why They're Talking to Us

[What you know or can infer about their trigger for this conversation]

## Discovery Questions

| Question                                    | Purpose                       |
| ------------------------------------------- | ----------------------------- |
| [Open-ended question about their situation] | [What you're trying to learn] |
| [Question about impact of current problem]  | [Quantify the pain]           |
| [Question about decision-making process]    | [Map the buying committee]    |
| [Question about timeline and urgency]       | [Qualify velocity]            |
| [Question about success criteria]           | [Set up the close]            |

## Talking Points

- [Key differentiator relevant to this prospect's context]
- [Relevant proof point or customer story]

## Objection Prep

| Likely Objection | Suggested Response |
| ---------------- | ------------------ |
| [objection]      | [response]         |

## Desired Outcomes

1. [Primary: what a successful call looks like]
2. [Secondary: minimum viable outcome]

## Competitive Flags

- [Any known or likely competing alternatives this prospect uses]
```

## After This Skill

- **sales-deal-tracker** — log this prospect as a deal after the call → Read `skill-packs/sales-revenue/skills/sales-deal-tracker.md`
- **meeting-processor** — process the discovery call notes → Read `skills/meeting-processor/SKILL.md`

## Rules

- Research the prospect company if web search is available. Flag when data is estimated or missing.
- Flag any competing products the prospect is known to use.
- Discovery questions must be open-ended. Binary questions are not discovery.
- Never fabricate customer quotes, case study results, or proof points.
