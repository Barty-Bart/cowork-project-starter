# active-work/

The default home for sub-projects. Each subfolder here is one chunk of multi-step work that has its own working memory.

## When something lands here

When the user asks for a piece of work that has multiple steps, multiple sessions, and its own moving parts, the `new-chunk-of-work` skill creates a subfolder here. Examples:

- A sales-team project might spin up `active-work/hire-account-executive/`
- A house-buying project might spin up `active-work/renovate-kitchen/`
- A CEO project might spin up `active-work/q3-product-launch/`

The parent project's context (the stuff in `context/`, the rules in `instructions.md`, the spirit in `SOUL.md`) still applies. The sub-project just gets its own scratchpad so the parent doesn't drown in detail.

## Anatomy of a sub-project folder

```
active-work/hire-account-executive/
├── instructions.md       (mini operating manual scoped to this sub-project)
├── tracker.xlsx          (Problem statement / Evaluations / Output / Plan / Done sheets)
├── Resources/            (created as needed; reference material for this sub-project only)
└── Archive/              (per-subproject archive)
```

The mini `instructions.md` inherits the universal working rules from the parent `instructions.md` (just by reference: "rules from `../../instructions.md` apply unless overridden below").

## Naming convention

Kebab-case. Verb-led where possible.
- `hire-account-executive/`
- `renovate-kitchen/`
- `launch-skills-blueprint-video/`
- `migrate-from-quickbooks/`

Skip generic names. `new-thing/`, `project-1/`, `untitled/` are dead on arrival.

## Lifecycle

1. **Created.** `new-chunk-of-work` skill creates the folder and the mini files. A row appears in `../tracker.xlsx` "In progress" sheet with the subfolder name filled in. A line appears in `../instructions.md` "Mini-projects" section.

2. **Active.** Sessions can be scoped to this subfolder. The agent reads `active-work/[subfolder]/instructions.md` when working on it, not the parent.

3. **Paused.** If work pauses, the agent updates the status to "paused" in the parent `tracker.xlsx` row and the parent's `instructions.md` mini-projects line. The folder stays where it is.

4. **Done.** When the sub-project completes:
   - The agent writes a one-line summary into the parent project's "Project history" in `../instructions.md`.
   - The entire subfolder moves to `../Archive/active-work_[subfolder]_completed_YYYY-MM-DD/`.
   - The parent file map is updated.
   - Any patterns that should generalise to the parent get proposed as new working rules in the parent `instructions.md`.

5. **Promoted.** If a sub-project keeps expanding past the parent project's domain, the agent recommends promoting it to its own top-level Cowork project. The user decides. Default to promotion when in doubt.

## Working rules for this folder

1. **One sub-project per folder.** Don't bundle.
2. **A sub-project has its own `instructions.md` and `tracker.xlsx`.** No exceptions. If you skip the structure, the working memory leaks back into the parent.
3. **Sub-projects never modify parent files directly.** They propose changes to the parent's `instructions.md` working rules at the end of their lifecycle.
4. **The parent's context (`context/`) is read-only from inside a sub-project.** The sub-project can reference it but shouldn't add entities to it. Add entities at the parent level only.

## What this folder is not for

- Not for one-off tasks. One-off tasks happen inline in a session.
- Not for examples of outputs. Output examples go in `../examples/`.
- Not for context. Context goes in `../context/`.
- Not for permanent infrastructure. Permanent infrastructure stays at the project root.
