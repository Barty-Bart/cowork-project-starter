# examples/

Captured output examples. Emails, reports, research notes, posts, anything Claude produces that the user approves a final version of. The captured examples become the reference style for future outputs of the same type.

This folder grows over time. It starts empty. Each subfolder represents a category of output the user produces in this project.

## Why this exists

The cleanest way to teach Claude how the user wants something written or formatted is to show it examples. Describing style in words is a losing battle. Pasting three approved emails works in one shot.

Every project produces specific kinds of work. A sales project might produce outreach emails, recap emails, and quarterly reports. A trip-planning project might produce itineraries and packing lists. A solo creative project might produce posts, articles, and scripts. Each of those gets a subfolder here once it shows up in real work.

## How the capture loop works

The capture loop is the thing that makes this folder valuable over time.

1. User asks Claude to draft an output. Claude drafts.
2. User pushes back on parts of the draft.
3. Claude updates the draft based on the pushback.
4. Loop continues until the user is happy with the final version.
5. **At the end**, Claude offers to save the final version into `examples/` under the matching subfolder, along with a short summary of the pushback that shaped it.

If the subfolder for that output type doesn't exist yet, Claude proposes creating it. Naming convention: kebab-case, descriptive. `outreach-emails/`, `weekly-reports/`, `research-notes/`, `posts/`.

Each subfolder ends up with:
- The final approved outputs themselves (numbered or dated)
- A `SOP.md` distilling the patterns that emerge once enough examples exist (typically after 3-5 examples)

## When to use examples vs when to ask

When the user asks for an output that has a matching `examples/` subfolder, Claude reads the most recent 2-3 examples in that subfolder before drafting. It uses them as the reference style.

When the user asks for an output that does NOT have a matching subfolder, Claude does not invent a style from thin air. It asks one short question: "I don't have any [output type] examples for this project yet. Do you want to do a quick template-setting pass, or just draft it and iterate?" Either path is fine. The point is to flag the absence so the user knows what's happening.

## Subfolder anatomy (once it grows)

```
examples/outreach-emails/
├── SOP.md                          (the distilled rules, written after a few examples exist)
├── 2026-05-24_acme-corp.md         (final approved version)
├── 2026-05-24_acme-corp_notes.md   (pushback that shaped it; optional)
├── 2026-05-30_widget-co.md
└── 2026-06-05_pied-piper.md
```

The `SOP.md` is written by Claude after enough examples exist for patterns to emerge. The user reviews it. Once approved, future drafts follow the SOP plus the most recent examples.

## Working rules for this folder

1. **Never overwrite an example.** Each final version gets its own file with a date in the filename.
2. **Don't capture half-baked outputs.** Only the final, user-approved version goes here. Drafts and intermediate versions stay in the chat history.
3. **Write the SOP after 3-5 examples, not before.** Patterns are easier to see once there's something to look at.
4. **Update the SOP when patterns shift.** If the user pushes back on something that contradicts the SOP, update the SOP and note the change.
5. **Archive obsolete examples.** When a style changes substantially (new voice, new brand direction), move old examples to `Archive/examples_[subfolder]_[date]/` so they don't pollute the reference set.

## What this folder is not for

- Not for context. Context (people, vendors, constraints) goes in `context/`.
- Not for SOPs that aren't tied to a specific output type. Those go inline in `instructions.md` as working rules, or in `skills/` if they're invokable.
- Not for active work. Active work goes in `active-work/`.
