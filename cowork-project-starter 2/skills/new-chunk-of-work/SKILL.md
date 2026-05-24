---
name: new-chunk-of-work
description: Permanent skill. Read this on demand when the user asks for a multi-step piece of work that warrants its own working memory inside the parent project. Trigger phrases include "build an AI agent for X," "renovate the kitchen," "run a hiring round," "ship a launch," "plan a workshop," "set up a new region," or any request that clearly involves multiple sessions, multiple stages, and its own moving parts. Do not trigger for one-off tasks ("analyse this file," "draft this email"). Those stay inline.
status: permanent
---

# Skill: new-chunk-of-work

Use when a request inside a Cowork project is itself a multi-step piece of work. Creates a subfolder inside `active-work/` with its own mini operating manual and its own tracker, so the sub-project has working memory without polluting the parent project's context.

## When to use this skill

Triggers:
- The user names something that has multiple stages and multiple deliverables.
- The request would generate three or more tasks in `tracker.xlsx`.
- The work has its own problem statement, its own evaluation criteria, and its own end output that's distinct from the parent project's end state.

Do not trigger for:
- One-off questions or single-task requests.
- Edits to existing files in the parent project.
- Anything that finishes in a single session.

If unsure, ask the user: "This sounds like its own piece of work. Do you want me to spin up a sub-project folder for it under `active-work/`, or handle it inline?"

## What the skill does

1. Confirms the sub-project scope with the user in one sentence.
2. Proposes a folder name (kebab-case, descriptive, verb-led where possible). Gets confirmation.
3. Creates the subfolder under `active-work/`: `active-work/<subfolder-name>/`.
4. Creates inside it:
   - `instructions.md` (mini operating manual scoped to this sub-project)
   - `tracker.xlsx` (with sheets: Problem statement, Evaluations, Output, Plan, Done)
   - empty `Resources/` and `Archive/` subfolders for the sub-project
5. Updates the parent project files:
   - Adds a row in parent `tracker.xlsx` "In progress" sheet, with the subfolder name in the "Subfolder (if any)" column.
   - Adds the sub-project to the "Mini-projects" section in parent `instructions.md`.
   - Updates the file map in parent `instructions.md`.

## Mini instructions.md template

```markdown
# instructions.md for [sub-project name]

This is a sub-project of [parent project name]. Operating rules from the parent `../../instructions.md` apply here unless explicitly overridden below. The parent's `SOUL.md` and `context/` also apply.

## Problem statement

> [User fills in. One paragraph. What problem this sub-project solves and why it exists.]

## Success criteria

> [User fills in. What "done" looks like for this sub-project specifically. Distinct from the parent project's end state.]

## Constraints

> [User fills in. Budget, deadline, dependencies, things ruled out.]

## Stages

> [Agent extrapolates from the problem statement and success criteria. User confirms or edits.]

## Working rules (sub-project specific)

1. All universal rules from `../../instructions.md` apply.
2. When the sub-project finishes, move this entire folder to the parent project's `../../Archive/active-work_[subfolder]_completed_YYYY-MM-DD/`.
3. If the sub-project surfaces a lesson that should generalise to the parent project, propose adding it to the parent `instructions.md` working rules.
4. The parent's `context/` is read-only from inside this sub-project. Don't add entities there from here; surface them to the user instead.

## File map

> [Maintained as files are created.]

## Open questions

> [Maintained as questions emerge.]
```

## Mini tracker.xlsx sheets

| Sheet | Purpose | Columns |
|---|---|---|
| Problem statement | One row, the problem in detail | Problem, Context, Stakes, Constraints |
| Evaluations | What we'll measure to know it worked | Metric, Target, Current, Method |
| Output | What we're building or producing | Artifact, Format, Owner, Status |
| Plan | Task list | Task, Owner, Status, Due, Notes |
| Done | Completed tasks | Task, Completed on, Notes |

## When the sub-project finishes

1. Confirm with the user the sub-project is done.
2. Write a one-line summary into the parent project's "Project history" section in `../../instructions.md`.
3. Move the row in parent `tracker.xlsx` from In progress to Resolved.
4. Move the entire sub-project folder to `../../Archive/active-work_<subfolder-name>_completed_YYYY-MM-DD/`.
5. Update the parent file map to reflect the move.
6. If patterns from the sub-project apply to the parent, propose them as new working rules in the parent `instructions.md`.

## When to escalate to a separate Cowork project instead

If the sub-project scope keeps expanding past the parent project's domain, stop and tell the user:

> This sub-project has grown past the parent project's domain. I recommend we promote it to its own top-level Cowork project. Cross-domain leakage breaks the second-brain effect.

The user decides. Default to promotion if uncertain.
