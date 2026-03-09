---
name: sales-objection-bank
description: "Maintain and query a living library of sales objections and responses. Trigger when the user says 'objection handling', 'how do I respond to', or 'common pushback'."
---

Produces evidence-backed responses to specific objections and maintains a living library at `sidekick/memory/objection-bank.md`. Responses improve over time based on user feedback.

## Process

### Step 1: Load Context

Read these files before proceeding:

- `sidekick/memory/objection-bank.md` - load the existing library (if it exists)
- `sidekick/memory/competitors/` - load competitive context relevant to objections (if it exists)
- `sidekick/memory/deals/` - look for objections encountered in recent deals (if it exists)

### Step 2: Clarify the Request

If the user hasn't specified, ask:

- What specific objection do you need to handle, or do you want to browse the full library?
- Any context on who raised it? (role, company size, stage in the deal)

Skip questions if the user's message already answers them.

### Step 3: Generate or Retrieve the Response

For a specific objection: produce a structured response with the objection, recommended reply, and supporting proof points.

For a library browse: display all objections grouped by category.

### Step 4: Update the Library

Add new objections and responses to `sidekick/memory/objection-bank.md`. If the user flags that a response worked or didn't work, annotate the entry.

## Output Format

```markdown
## Objection: [Exact objection phrasing]

**Category:** [Price / Timing / Competition / Trust / Fit]
**Frequency:** [How often this comes up, if known]

### Recommended Response

[1-3 sentence response. Direct, not defensive. Reframes or validates before countering.]

### Proof Points

- [Specific evidence: customer result, metric, case study]
- [Second proof point if available]

### What Works / What Doesn't

- Works: [observed effective approaches]
- Avoid: [approaches that backfire]
```

## After This Skill

- **sales-discovery-prep** — incorporate objection prep into next discovery call → Read `skill-packs/sales-revenue/skills/sales-discovery-prep.md`
- **sales-win-loss-analysis** — review a recent loss to surface new objection patterns → Read `skill-packs/sales-revenue/skills/sales-win-loss-analysis.md`

## Rules

- Track which responses worked based on user feedback. Update entries when new evidence arrives.
- Never fabricate customer quotes, case study results, or proof points.
- Objection responses must acknowledge the concern before countering. Dismissiveness loses deals.
- If the objection is legitimate (e.g., a real product gap), say so rather than coaching the user to deflect.
