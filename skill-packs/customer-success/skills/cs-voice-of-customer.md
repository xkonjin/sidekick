---
name: cs-voice-of-customer
description: "Synthesize customer feedback into themed insights. Trigger when the user says 'customer feedback summary' or 'what are customers saying'."
---

Produces themed insights with frequency, severity, representative quotes, and recommended actions. Designed for synthesis, not raw aggregation.

## Process

### Step 1: Load Context

Read these files before proceeding:

- `sidekick/memory/accounts/` - load account records for feedback signals (if it exists)
- `sidekick/outputs/` - scan for recent meeting notes, QBR docs, or escalation records (if it exists)
- `sidekick/context/current-priorities.md` - filter insights by what's relevant to current focus

### Step 2: Clarify the Scope

If the user hasn't specified, ask:

- What timeframe should this cover?
- Any specific topics or product areas to focus on?

Skip questions if the user's message already answers them.

### Step 3: Identify and Group Themes

From all available sources, extract distinct feedback signals. Group into themes by:

- Pain points (friction, frustration, things that don't work)
- Feature requests (things customers wish existed)
- Positive signals (what's working, why they stay)
- Strategic concerns (questions about direction, trust, or fit)

Weight themes by frequency of mention, not volume of words.

### Step 4: Save Output

Write to `sidekick/outputs/voc-report-[DATE].md`.

## Output Format

```markdown
# Voice of Customer Report — [DATE]

**Sources reviewed:** [list of files or meetings used] | **Timeframe:** [range]

## Key Themes

### [Theme Name]

**Frequency:** [High / Medium / Low — how many accounts raised this]
**Severity:** [Critical / Moderate / Low — impact if unaddressed]

**What customers are saying:**

- "[Representative quote or paraphrase]" — [Account, Role if known]

**Pattern:** [What this signals beyond the individual complaint]

**Recommended action:** [Concrete next step — product, process, or communication]

---

## Summary Table

| Theme   | Frequency | Severity | Recommended Action |
| ------- | --------- | -------- | ------------------ |
| [theme] | High      | Critical | [action]           |

## Data Gaps

- [Feedback areas where we have insufficient signal]
```

## After This Skill

- **decision-log** — log any decisions triggered by this synthesis → Read `skills/decision-log/SKILL.md`
- **cs-success-playbook** — update playbooks if patterns suggest a systemic fix → Read `skill-packs/customer-success/skills/cs-success-playbook.md`

## Rules

- Weight themes by frequency of mention across distinct accounts, not by who complained loudest.
- Distinguish pain points from feature requests — they require different responses.
- Never fabricate customer quotes. Paraphrase clearly if the exact wording isn't available.
- Flag data gaps where the signal is insufficient to draw conclusions.
