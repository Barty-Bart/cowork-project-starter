# Folder Layout

What each file and folder is for, plus the rules around keeping, growing, and archiving them.

## Root files

| File | Lifespan | Purpose |
|---|---|---|
| `instructions.md` | Permanent | The entry point. Read first on every session. |
| `SOUL.md` | Permanent | The spirit of the project. Short. Read second. |
| `FOLDER_LAYOUT.md` | Permanent | This file. Folder rules reference. |
| `BOOTSTRAP.md` | Session 1 only | Onboarding prompt. Moved to `Archive/` at end of session 1. |
| `tracker.xlsx` | Permanent, grows | Task board. Sheets: Backlog / In progress / Resolved / Master backlog. |
| `overflow.xlsx` | Permanent, grows | Captured asides and "for later" items. The weekly review processes this. |
| `activity_log.xlsx` | Permanent, grows | One line per piece of completed work. Every session writes here. |
| `claude_tasks.xlsx` | Permanent, grows | Index of autonomous work Claude runs. Active / Planned sheets. |
| `dashboard.html` | Permanent | Live visual snapshot of the project. Regenerated when tracker state changes. |

## Root folders

| Folder | Purpose |
|---|---|
| `context/` | Project data store. Adapted to one of five archetypes during onboarding. People, vendors, regions, variables, constraints. |
| `examples/` | Captured output examples. Emails, reports, research notes. Grows as user pushback shapes finals. |
| `active-work/` | Sub-projects. Each mini-project gets its own subfolder with its own mini-`instructions.md` and `tracker.xlsx`. |
| `skills/` | Skill files read on demand by sessions. After session 1, only `new-chunk-of-work/` typically remains. |
| `Archive/` | Nothing is deleted. Things move here. Including `BOOTSTRAP.md`, archived skill files, and anything else superseded. |

## context/ shape

`context/` starts with a `README.md` containing five archetype templates. The bootstrap picks one and removes the others. The shape after bootstrap depends on the archetype:

- **Team manager:** `team-overview.md`, `metrics.md`, `people/`, `stakeholders.md`, `tools.md`, `recurring-rhythms.md`, `known-issues.md`, `successes.md`, `roles-responsibilities.md`
- **CEO / founder:** `business-overview.md`, `metrics.md`, `team.md`, `customers/`, `vendors/`, `competitors.md`, `strategic-priorities.md`, `known-issues.md`, `successes.md`, `roles-responsibilities.md`
- **Short-lived staged project:** `variables.md`, `stages.md`, `stakeholders.md`, `options.md`, `constraints.md`, `decisions.md`, `risks.md`
- **Personal life domain:** `current-state.md`, `goals.md`, `routines.md`, `metrics.md`, `known-issues.md`, `successes.md`, `constraints.md`
- **Solo creative:** `project-overview.md`, `audience.md`, `voice-and-style.md`, `body-of-work.md`, `pipeline.md`, `constraints.md`, `inspirations.md`, `known-issues.md`, `successes.md`

See `context/README.md` for the full templates.

## examples/ shape

`examples/` starts with just a `README.md`. Subfolders appear as the user produces real outputs and Claude captures finals. Common subfolders:

- `examples/outreach-emails/`
- `examples/weekly-reports/`
- `examples/research-notes/`
- `examples/posts/`

Each subfolder ends up with the captured finals plus an `SOP.md` distilling the patterns once 3-5 examples exist. See `examples/README.md` for the capture loop.

## active-work/ shape

`active-work/` starts empty. Subfolders appear when the `new-chunk-of-work` skill is invoked. Each subfolder has its own `instructions.md` and `tracker.xlsx`. See `active-work/README.md` for the lifecycle.

## skills/ shape

`skills/` ships with two files:

- `skills/new-chunk-of-work/SKILL.md`. **permanent.** Read on demand when a request is a multi-step chunk of work.
- `skills/weekly-review/SKILL.md`. **temporary.** Consumed by the bootstrap during Phase 5: the body of this file gets pasted into the scheduled task that runs the weekly review. After that, the file moves to `Archive/`.

If the user defers the weekly review during bootstrap, the file stays for later activation.

## Archive/ rules

Nothing leaves this project. Things move to `Archive/`.

- `BOOTSTRAP.md` lands here after session 1
- `skills/weekly-review/` lands here after the scheduled task is created
- Old context files land here when entities are no longer relevant
- Superseded examples land here when style shifts
- Completed sub-project folders land here as `Archive/active-work_[subfolder]_completed_YYYY-MM-DD/`

Every Sunday afternoon, the weekly review scans `Archive/` and asks if anything 30+ days old is safe to drop permanently. Until the user says yes, it stays.

## When the file map changes, `instructions.md` changes

Every time a folder or significant file is created, moved, or archived, the agent updates the "File map" section of `instructions.md`. Future sessions only know what exists by reading that map. A drifted map means a future session asking "what's in `context/`?" with no answer.

This is the single most-broken rule in long-running Cowork projects. Treat it as non-negotiable.

## The Excel-vs-Markdown choice

Five files at the root are Excel: `tracker.xlsx`, `overflow.xlsx`, `activity_log.xlsx`, `claude_tasks.xlsx`, plus per-subproject trackers in `active-work/`. Everything else is markdown.

Excel is used where structured data and sheet-based grouping matter (tasks across states, overflow items, log rows, autonomous task index). Markdown is used everywhere else because the agent reads on demand, narrative belongs in prose, and overhead is lower.

The agent does not load all Excel sheets into context at session boot. It reads the sheets relevant to the current request. The minimum-on-boot is the last 10 lines of `activity_log.xlsx` and the current state of `tracker.xlsx`.
