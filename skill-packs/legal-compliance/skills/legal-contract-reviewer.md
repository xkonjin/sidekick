---
name: contract-reviewer
description: "First-pass contract review: key terms, unusual clauses, missing protections, and questions for legal. Trigger when the user says 'review this contract', 'contract red flags', 'terms to watch', or 'NDA review'."
---

# Contract Reviewer

First-pass review of a contract or agreement. Surfaces key terms, unusual clauses, missing standard protections, and questions to raise with legal counsel. Not a substitute for legal advice.

## Process

### Step 1: Load Context

Read:

- `sidekick/context/team-directory.md` - Identify the counterparty and any internal legal contacts

### Step 2: Identify the Contract

If not already provided, ask:

- What type of contract is this? (NDA, vendor agreement, employment, service contract, partnership)
- Who are the parties?
- What is the contract term and value?
- Is there an existing relationship with this counterparty?
- Paste or attach the contract text.

### Step 3: Review the Contract

Work through the contract systematically. For each section, identify:

**Key Terms to Extract:**

- Parties, effective date, term, renewal, and termination conditions
- Payment terms, amounts, and invoicing requirements
- Deliverables, SLAs, and performance obligations
- Liability cap and indemnification scope
- Intellectual property ownership and licensing
- Confidentiality obligations and carve-outs
- Governing law and dispute resolution

**Red Flags to Check:**

- Unilateral amendment rights (one party can change terms without consent)
- Automatic renewal without notice requirement
- Broad IP assignment (assigns work product beyond the scope of engagement)
- Uncapped liability or indemnification
- Exclusivity clauses that limit future options
- Non-compete or non-solicitation scope
- Data handling clauses inconsistent with privacy obligations

**Missing Standard Protections:**

- No limitation of liability clause
- No force majeure clause
- No dispute escalation path before litigation
- No data breach notification obligation
- No termination for convenience right

### Step 4: Output the Review

Save to `sidekick/outputs/contract-review-[name]-[DATE].md`.

```markdown
# Contract Review: [Contract Name / Counterparty]

**Date:** [date] | **Reviewed by:** Sidekick (first pass only)
**Contract type:** [NDA / vendor / service / employment / other]
**Parties:** [Party A] and [Party B]
**Term:** [start] to [end] | **Value:** [if applicable]

## Key Terms Summary

| Term           | Detail                      |
| -------------- | --------------------------- |
| Effective date | [date]                      |
| Term / Renewal | [duration + auto-renew Y/N] |
| Termination    | [conditions]                |
| Payment        | [amounts + schedule]        |
| Liability cap  | [amount or "uncapped"]      |
| IP ownership   | [who owns what]             |
| Governing law  | [jurisdiction]              |

## Red Flags

| Clause        | Location    | Concern                     | Severity     |
| ------------- | ----------- | --------------------------- | ------------ |
| [Clause name] | [Section X] | [Why it's unusual or risky] | High/Med/Low |

## Missing Protections

- [Protection that is absent and should be requested]
- [Protection that is absent and should be requested]

## Questions for Legal

- [Specific question requiring legal interpretation]
- [Specific question requiring legal interpretation]

## Recommended Next Steps

- [Action: negotiate, accept, reject, or escalate which clause]
```

## After This Skill

- **email-drafter** — draft a response or negotiation email to the counterparty → Read `skill-packs/automation/skills/auto-email-drafter.md`
- **decision-log** — log the decision to sign, reject, or escalate → Read `skills/decision-log/SKILL.md`

## Rules

- **This is not legal advice.** This is a first-pass review to prepare for legal review, not replace it. Always flag this explicitly in the output.
- Never give a "safe to sign" verdict. Surface issues and questions; decisions belong to the user and their legal counsel.
- If the contract text is not provided, do not proceed — ask for it.
- If a clause is missing from the contract entirely, note its absence. Absence is as important as presence.
- Severity ratings (High/Med/Low) reflect how commonly these clauses cause disputes, not legal conclusions.
