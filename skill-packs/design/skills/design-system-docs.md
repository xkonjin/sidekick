---
name: design-system-docs
description: "Document components for a design system or component library. Trigger when the user says 'document components', 'design system', 'component library', 'document this component', or 'add this to the system'."
---

# Design System Documentation

You are producing design system documentation for a component or set of components. Output must be precise enough for both designers and engineers to work from without back-and-forth.

## Context Loading

Before documenting, read:

- `sidekick/context/about-me.md` — understand the product and tech stack
- `sidekick/context/current-priorities.md` — understand what's shipping soon
- `sidekick/context/communication-style.md` — match formatting to preferences

## What to Gather First

Ask if not already provided:

- Component name and category (atoms, molecules, organisms, or equivalent)
- All variants that exist (not hypothetical future ones)
- The primary use case — when does this component appear?
- Any existing usage rules the team has already established

## Documentation Structure

For each component:

### Component: [Name]

**Category:** [atom / molecule / organism / page]
**Status:** [stable / beta / deprecated]

**Description**
One sentence. What it is and when to use it.

**Props / API**

| Prop     | Type    | Default | Required | Description               |
| -------- | ------- | ------- | -------- | ------------------------- |
| variant  | string  | primary | no       | Visual style of component |
| disabled | boolean | false   | no       | Prevents interaction      |

**Variants**

| Variant   | Use Case                        |
| --------- | ------------------------------- |
| primary   | Main CTA, one per page          |
| secondary | Supporting actions              |
| ghost     | Low-emphasis, often in toolbars |

**States**
Default, Hover, Focus, Active, Disabled, Loading (if applicable)

**Do / Don't**

| Do                                               | Don't                                |
| ------------------------------------------------ | ------------------------------------ |
| Use primary for the single most important action | Use multiple primaries on one screen |
| Pair with a secondary for two-action flows       | Use ghost for critical actions       |

**Spacing & Layout**
Minimum touch target, padding, margin requirements.

**Accessibility**
ARIA role, keyboard behavior, required attributes.

## Rules

- Document only what exists, not aspirational variants
- Props table must reflect the real implementation, not the ideal
- Do/Don't examples must be concrete and specific, not generic
- If a component has no defined states, flag it as a gap
