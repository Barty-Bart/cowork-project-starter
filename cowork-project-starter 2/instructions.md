# instructions.md

This file is the entry point for every session in this Cowork project. Read it top to bottom before doing anything else.

The order of operations on every session boot:

1. **Read this file (`instructions.md`).**
2. **If `BOOTSTRAP.md` exists in the project root, run it.** That file is the onboarding for session 1. It runs once, then removes itself.
3. **Read `SOUL.md`.** Short. Holds the project's purpose and the rules of the room.
4. **Read `tracker.xlsx`.** Current Backlog, In progress, Resolved, and Master backlog.
5. **Read the last 10 lines of `activity_log.xlsx`.** Get oriented to what recent sessions actually did.
6. **Skim `overflow.xlsx`.** Edge cases and "for later" items captured but not yet acted on.

Only then start engaging with the user's request.

---

## Project purpose

> [BOOTSTRAP FILLS IN: one paragraph from the Phase 1 context summary. What this project is for, why it matters, who it affects.]

## Archetype

> [BOOTSTRAP FILLS IN: "Short-lived" or "Continuous". Set during Phase 0 Card 3.]

### If short-lived

> [BOOTSTRAP FILLS IN]
>
> - End state: what "done" looks like
> - Deadline: real or vague
> - Stages: extrapolated from Phase 1
> - Kill conditions: what would make us abandon this project

### If continuous

> [BOOTSTRAP FILLS IN]
>
> - Optimum running condition: what "running well" looks like
> - Recurring rhythms: weekly, monthly, quarterly cycles
> - Leading indicators: signs things are going well early
> - Lagging indicators: signs things went well (or didn't) after the fact
> - Failure mode to avoid

The unused archetype section above gets deleted by the bootstrap.

## Preferences

> [BOOTSTRAP FILLS IN from Phase 1 preferences questions]
>
> - Communication style:
> - Push-back style:
> - Confirmation rules:
> - Bluntness scale:

## Working rules

These rules apply to every session. They are not optional.

### Reading

1. **Read `instructions.md` first.** Every session. No exceptions.
2. **Then read `SOUL.md`, `tracker.xlsx` (all four sheets), the last 10 lines of `activity_log.xlsx`, and skim `overflow.xlsx`.** This is the minimum context.
3. **Read files on demand.** When the user mentions something, check the file map below. If a relevant file exists, read it before responding.

### Writing files

4. **Ask before creating files.** Plan the file, tell the user what you're about to create and where, get a yes, then create. No silent file creation.
5. **Ask before deleting or rewriting.** Anything that destroys or substantially overwrites an existing file requires explicit confirmation. Default behaviour is "archive, don't delete."
6. **Archive, don't delete.** Nothing ever leaves this project. When a file is no longer useful, move it to `Archive/`. The weekly review will surface it later and ask if it's safe to drop permanently.

### Tracker hygiene

7. **Log every piece of work.** When a session completes a piece of work, append one line to `activity_log.xlsx`. Date, session, action (one short sentence), duration if known, tags. One line. No prose.
8. **Capture overflow as it happens.** When the user says something like "good point, but for later" or "interesting, we should explore that another time" or otherwise surfaces a thought that isn't being acted on right now, append it to `overflow.xlsx` automatically. Don't ask, just capture. Then keep going with the current work.
9. **Move tasks across the tracker sheets in real time.** When a task starts, move it from Backlog to In progress. When it's done, move it to Resolved. Don't batch.
10. **Update the file map.** Every time a folder or significant file is created, moved, or archived, update the "File map" section of this document.

### Surfacing new entities

11. **Surface new entities.** When the user mentions a new person, vendor, region, organisation, or recurring concept that doesn't have a file yet, pause and ask for a short voice note or a few sentences of context. Offer to create a reference file under the right slot in `context/`. Don't create the file without yes.

### Bigger pieces of work

12. **Detect chunks of work.** If a request is itself a multi-step piece of work (build an AI agent, run a hiring round, renovate a kitchen, plan a launch), do not try to handle it inline. Read `skills/new-chunk-of-work/SKILL.md` and follow its instructions. That skill creates a subfolder inside `active-work/` with its own mini-`instructions.md` and `tracker.xlsx`.

### Examples and outputs

13. **Use existing examples before inventing.** When asked to draft an output (email, report, research note), check `examples/` for the matching subfolder first. If examples exist, follow their style. If none exist, ask the user how they want this format established.
14. **Capture corrections as examples.** When the user pushes back on a draft and a final version is agreed, save the final version (and the corrections that led to it) into the matching `examples/` subfolder. Future sessions will use it as the reference.

### Connectors and Claude tasks

15. **Connectors are recommended, never silent.** If you spot an opportunity to wire up a new tool, tell the user the connector name and what value it adds. Wait for yes before connecting.
16. **Track autonomous work in `claude_tasks.xlsx`.** Whenever a new scheduled task or autonomous workflow is set up, add a row to the Active sheet of `claude_tasks.xlsx` (Task name, summary, frequency). The actual instructions for the task live inside the scheduled task itself, not here. This file is the index.

### Process improvement

17. **Propose new working rules.** When a session reveals a lesson that should outlive the session ("never send emails on Fridays," "always run X check before Y"), propose adding it to this "Working rules" section. Don't add it silently.
18. **One question at a time.** When asking the user for context, ask one thing and wait. Don't dump three questions in one message. The exception is the optional choice-card affordance for branching decisions.
19. **Confirm contradictions.** If the user says something that contradicts an earlier saved answer or a file in the project, flag it. Don't silently overwrite. Ask which version is current.
20. **Refuse scope creep.** This project has one purpose (defined above and in `SOUL.md`). If the user starts dumping work from a different domain, pause and ask if it belongs in a different project.

### Dashboard

21. **Keep `dashboard.html` current.** When tracker state changes, when stages advance, when overflow items pile up, update `dashboard.html` so the visual snapshot reflects reality. The dashboard reads its data from the project files, so updating it usually means edits in those files; if the user wants a refresh, regenerate it from `tracker.xlsx` and `overflow.xlsx`.

## File map

> [BOOTSTRAP FILLS IN AND MAINTAINS]
>
> Format:
> ```
> /                              project root
> ├── instructions.md            this file
> ├── SOUL.md                    project spirit
> ├── tracker.xlsx               task board (4 sheets)
> ├── overflow.xlsx              captured asides and "for later" items
> ├── activity_log.xlsx          one line per piece of completed work
> ├── claude_tasks.xlsx          index of autonomous work Claude runs (Active / Planned)
> ├── dashboard.html             live visual snapshot
> ├── FOLDER_LAYOUT.md           folder rules reference
> ├── Archive/                   archived files (BOOTSTRAP.md sits here after session 1)
> ├── context/                   project context (people, vendors, variables, whatever the archetype needs)
> ├── examples/                  captured output examples (emails, reports, research formats)
> ├── active-work/               sub-projects with their own working memory
> └── skills/                    skill files read on demand (new-chunk-of-work, etc.)
> ```
>
> Update this map every time a folder or significant file is created, removed, archived, or renamed.

## Connectors

> [BOOTSTRAP FILLS IN]
>
> Active:
> - [tool name]: [what it gives this project]
>
> Deferred:
> - [tool name]: [reason and when to revisit]

## Mini-projects (active subfolders inside `active-work/`)

> [BOOTSTRAP AND FUTURE SESSIONS MAINTAIN]
>
> When a mini-project is spun up, add a one-line entry here:
> - `active-work/[subfolder]/`. [one-sentence purpose]. Status: [active/paused/done/archived].

## Secondary projects to spin up later

> [BOOTSTRAP FILLS IN IF DISCOVERY SURFACED THEM]
>
> Candidate projects identified during Phase 0.5 Discovery that the user did not pick for this Cowork project. They belong in their own separate Cowork projects.
>
> Format:
> - **[project name]**. [one-line description]. Suggested archetype: [short-lived / continuous].

## Open questions

> [BOOTSTRAP AND FUTURE SESSIONS MAINTAIN]
>
> Anything we deliberately said "open" to during onboarding or in subsequent sessions. Don't pretend it's resolved.

## Project history

> [FUTURE SESSIONS MAINTAIN]
>
> Major milestones, decisions, and pivots. Not the daily log (that's `activity_log.xlsx`). This is the highlight reel.
>
> Append entries dated `YYYY-MM-DD`. Most recent on top.
