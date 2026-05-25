# cowork-project-starter

A second-brain starter for Claude Cowork projects. Drop it into a new project, run the bootstrap, and you get a task tracker, an activity log, an instructions file, a live dashboard, and a self-improving weekly review loop.

## How to use it

1. **Download this repo as a ZIP** — click the green **Code** button above and pick **Download ZIP**.
2. **Unzip it** somewhere on your computer.
3. **Open Cowork** → **Projects** → **New Project** → **Use an existing folder**, then pick the unzipped folder.
4. **Open a new chat in the project** and ask the agent to *read the files and run `BOOTSTRAP.md`*.

The agent will walk you through onboarding (about 15–30 minutes on the express path, longer if you choose the deep path with voice notes). At the end of session one, `BOOTSTRAP.md` archives itself and the project is ready to use.

## What's inside

| File / folder | Purpose |
|---|---|
| `BOOTSTRAP.md` | One-time onboarding prompt. Archives itself after session 1. |
| `SOUL.md` | The spirit of the project. Short on purpose. Read first every session. |
| `instructions.md` | The operating manual. Every session reads this first. |
| `FOLDER_LAYOUT.md` | What each file and folder is for, and the rules around them. |
| `tracker.xlsx` | Task board — Backlog / In progress / Resolved / Master backlog. |
| `overflow.xlsx` | "For later" items captured automatically as they come up. |
| `activity_log.xlsx` | One line per piece of completed work. |
| `claude_tasks.xlsx` | Index of autonomous tasks Claude runs in this project. |
| `dashboard.html` | Live visual snapshot of the project. |
| `context/` | Project data store — people, vendors, constraints, whatever the project needs. |
| `examples/` | Captured output examples (emails, reports, posts) that teach Claude your style. |
| `active-work/` | Sub-projects, each with their own working memory. |
| `skills/` | Skill files read on demand by sessions. |

## Philosophy

- One project, one piece of work. Cross-domain leakage breaks the second-brain effect.
- Context first, work second. The right context up front saves a hundred small misunderstandings later.
- Nothing gets deleted. Things move to `Archive/`.
- Every piece of work logs to `activity_log.xlsx`. The log is how the system learns.
- When you push back, the rules update. Pushback is signal, not friction.

See `SOUL.md` and `instructions.md` for the full picture.
