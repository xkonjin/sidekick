---
name: research-reading-digest
description: "Distill an article, report, or long-form content into thesis, key findings, implications, and actions — contextualized to what matters to you. Trigger when the user says 'summarize this article', 'key takeaways', 'digest this', or 'what should I take from this'."
---

# Reading Digest

Extracts what actually matters from long-form content. Distinguishes the author's claims from the evidence. Flags bias and gaps.

## Process

### Step 1: Load Context

Read these files before starting:

- `sidekick/context/current-priorities.md` - contextualize findings against what's relevant right now

### Step 2: Receive Content

If content is provided in the message, proceed. If not, ask:

- What article, report, or document should I digest?

Skip this question if the content or URL is already in the user's message.

### Step 3: Assess the Source

Before summarizing:

- What type of source is this? (vendor report, academic paper, news article, opinion piece)
- Does the author or publisher have an obvious angle or commercial interest?
- When was it published? Is it dated?

Flag source bias prominently if it exists.

### Step 4: Write the Digest

```markdown
# Reading Digest: [Title or Topic]

**Source:** [Author / Publication] | **Published:** [Date] | **Digested:** [DATE]
**Source type:** [Vendor report / Academic / News / Opinion / Other]
**Bias flag:** [None detected / [Specific bias or conflict of interest]]

## Thesis

[One sentence: what is the author's central argument or finding?]

## Key Findings

| Finding     | Evidence provided | Author's claim vs. data |
| ----------- | ----------------- | ----------------------- |
| [Finding 1] | [Yes / No / Weak] | [Claim / Supported]     |
| [Finding 2] | [Yes / No / Weak] | [Claim / Supported]     |
| [Finding 3] | [Yes / No / Weak] | [Claim / Supported]     |

## What It Doesn't Address

- [Gap 1 — important topic the article avoids or omits]
- [Gap 2]

## Relevant to You

[Why this matters given current priorities. Be specific — "interesting" is not enough.]

## Action Items

- [Specific action 1, if any]
- [Specific action 2, if any]

## Notable Quotes

> "[Quote 1 — verbatim, with page or section reference if available]"

> "[Quote 2]"
```

### Step 5: Save

Save to `sidekick/outputs/digest-[topic]-[DATE].md`.

## After This Skill

| Condition                                      | Suggestion                                                                             |
| ---------------------------------------------- | -------------------------------------------------------------------------------------- |
| Findings worth preserving for future reference | **knowledge-base** → `skill-packs/research-learning/skills/research-knowledge-base.md` |
| Content triggers a decision                    | **decision-log** → `skills/decision-log/SKILL.md`                                      |
| Content feeds into a larger research question  | **research-brief** → `skill-packs/research-learning/skills/research-brief.md`          |

## Rules

- Distinguish the author's claims from evidence — label each finding as "Claim" or "Supported"
- Flag when the source has obvious bias or a commercial interest in the conclusion
- Note what the article does NOT address — gaps are as telling as what's included
- Never fabricate quotes or findings; if you can't confirm a detail, say so
- If the content is behind a paywall and wasn't provided, say so rather than summarizing from partial information
