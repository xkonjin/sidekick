---
name: pm-release-notes
description: "Write user-facing release notes from commits, PRs, or tickets."
---

Transforms technical change lists into clear, user-facing release notes. Calibrated to your communication style and audience - not a changelog for engineers.

## Context Loading

1. Read `sidekick/context/communication-style.md` - release notes should sound like the company, not a robot
2. Read `sidekick/context/current-priorities.md` - connect releases to what matters right now
3. Read `sidekick/context/about-me.md` - know the product name and audience

Ask before generating:

- What is the input? (paste commits, PR titles, ticket titles, or describe changes)
- Who is the audience? (end users, developers, internal team, customers)
- What channel will this go to? (in-app, email, Slack, changelog page)
- Is there a version number or release name?

## Process

1. **Parse the input** - group changes by type: new features, improvements, bug fixes, deprecations
2. **Translate to user value** - what does each change mean for the user, not what the engineer did
3. **Cut the noise** - internal refactors, dependency bumps, test fixes don't belong in user-facing notes
4. **Write the notes** - clear, direct, user-first language
5. **Match the channel** - in-app needs to be shorter; email can have more context; changelog can be comprehensive

## Output Format

```markdown
# Release Notes - [Version / Date]

## What's new

[Lead with the biggest user-facing improvement. 1-2 sentences max.]

### New features

- **[Feature name]:** [What it does and why it's useful. One sentence.]

### Improvements

- [What changed and how it makes the experience better]

### Bug fixes

- [What was broken, now fixed. User-centric framing.]

---

_[Optional: link to changelog, support docs, or next steps]_
```

**Short form (in-app / notification):**

```
[Version] is here. [One sentence on the biggest change.] [Optional CTA.]
```

## Rules

- Never use technical jargon in user-facing notes (no "refactored", "migrated", "deprecated API")
- Lead with value, not features. "You can now X" beats "We added X"
- Bug fixes should be phrased as improvements ("Fixed an issue where..." not "Patched null pointer exception")
- Match tone to the user's communication style profile - some brands are casual, some are formal
- If the change list contains nothing user-facing, say so rather than fabricating impact
- Save to `sidekick/outputs/release-notes-[VERSION]-[DATE].md` after user approval
