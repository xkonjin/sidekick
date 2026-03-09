---
name: component-spec
description: "Generate a technical component spec bridging design to implementation. Trigger when the user says 'component spec', 'spec this component', 'write a spec for', 'spec out this UI', or 'document this for engineers'."
---

# Component Spec

You are writing a technical specification that bridges design to implementation. Engineers should be able to build from this without a design walkthrough. Designers should be able to verify implementation against it.

## Context Loading

Before speccing, read:

- `sidekick/context/about-me.md` — understand the tech stack and team structure
- `sidekick/context/current-priorities.md` — understand sprint scope and what's in-flight
- `sidekick/context/communication-style.md` — match output format to preferences

## What to Gather First

Ask if not already provided:

- Component name and what screen/flow it appears in
- All states that must be handled (not just the happy path)
- Any existing similar components to maintain consistency with
- Platform: web, iOS, Android, or multi-platform

## Spec Structure

### Component: [Name]

**Overview**
One sentence. What this component does and where it lives.

**Props**

| Prop     | Type                    | Default | Required | Description           |
| -------- | ----------------------- | ------- | -------- | --------------------- |
| label    | string                  | —       | yes      | Button label text     |
| variant  | primary/secondary/ghost | primary | no       | Visual treatment      |
| onPress  | () => void              | —       | yes      | Callback on tap/click |
| disabled | boolean                 | false   | no       | Prevents interaction  |
| loading  | boolean                 | false   | no       | Shows loading state   |

**States**

| State    | Visual                       | Behavior                        |
| -------- | ---------------------------- | ------------------------------- |
| Default  | [describe appearance]        | Responds to interaction         |
| Hover    | Background lightens 10%      | Cursor: pointer                 |
| Focus    | 2px outline, offset 2px      | Keyboard accessible             |
| Active   | Background darkens 15%       | Pressed appearance              |
| Disabled | 40% opacity, no hover effect | No events fire                  |
| Loading  | Spinner replaces label       | No events fire, maintains width |

**Interactions**

| Trigger     | Action                     | Duration  |
| ----------- | -------------------------- | --------- |
| Click/tap   | Fire onPress callback      | Immediate |
| Enter/Space | Same as click when focused | Immediate |
| Hover enter | Transition to hover state  | 150ms     |

**Responsive Behavior**

| Breakpoint | Behavior                    |
| ---------- | --------------------------- |
| Mobile     | Full width, min-height 44px |
| Tablet     | Auto width, min-width 120px |
| Desktop    | Auto width, min-width 120px |

**Edge Cases**

- Long label text: truncate with ellipsis, never wrap inside button
- Icon-only variant: requires aria-label, no visible text
- Loading state: preserve button width to prevent layout shift

**Accessibility**

- Role: `button`
- Required: keyboard focusable, responds to Enter and Space
- Loading: aria-busy="true" when loading
- Disabled: aria-disabled="true" (not `disabled` attribute if inside a form)

**Do Not**

- List behaviors or states the engineer should never implement

## Rules

- Spec real states, not aspirational ones
- Every edge case must have a defined resolution — no "TBD"
- If the design doesn't specify something, flag it rather than invent a solution
- Responsive table must cover all breakpoints the product actually targets
