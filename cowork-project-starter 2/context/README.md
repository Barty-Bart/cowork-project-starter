# context/

The data store for everything Claude needs to know about your world that isn't already in `instructions.md` or `tracker.xlsx`.

The shape of `context/` depends on the project. A sales team manager's context is different from a person planning a trip is different from a CEO running a company. The bootstrap picks one of the archetype templates below during onboarding, adapts it to the specific project, and removes the others.

After bootstrap, the agent reads from `context/` on demand. When you mention a name, a vendor, a region, a metric, the agent checks here first. If the file exists, the agent uses it. If it doesn't, the agent asks for context and writes a new file.

## Working rules for this folder

1. **One file per entity.** A person, a vendor, a region, a constraint, a key metric. Each gets its own file. Don't pile entities into a single file.
2. **Short and skimmable.** Each context file is 1-2 paragraphs plus a few bullet points. Long-form notes belong in `examples/` or in subfolders of `active-work/`.
3. **Update on contradiction.** If the user says something that contradicts a context file, ask which version is current. Don't silently overwrite.
4. **Archive when no longer relevant.** When a person leaves the team, a vendor is dropped, a region is closed, move the file to `Archive/context_[name]/`. Don't delete.

## Naming convention

Use kebab-case filenames matching the entity. Examples:
- `jane-smith.md`
- `acme-corp.md`
- `region-emea.md`
- `metric-mrr.md`
- `constraint-budget.md`

## Archetype templates

The bootstrap picks one of the templates below as the starting shape for `context/`, adapts it, then removes the others. These are starting points, not rules. If your project doesn't fit any of them, the bootstrap will propose a new shape.

---

### Template 1. Team manager / department lead

For someone responsible for a team, a function, or a domain inside a business.

Default files:
- `team-overview.md`. what the team does, its mission, current size and shape
- `metrics.md`. the numbers this team is measured on
- `people/`. one file per team member (direct reports, peers, manager). Example: `people/jane-smith.md`
- `stakeholders.md`. people outside the team this work depends on or impacts
- `tools.md`. the systems and software the team runs on
- `recurring-rhythms.md`. daily, weekly, monthly cycles (standups, reviews, reports)
- `known-issues.md`. current problems, blockers, things being worked through
- `successes.md`. wins worth referencing in future work
- `roles-responsibilities.md`. who owns what

---

### Template 2. CEO / founder / department head running a business

For someone running an entire business or a major division.

Default files:
- `business-overview.md`. what the company does, who it serves, business model
- `metrics.md`. top-line numbers (revenue, growth, key ratios)
- `team.md`. org chart and key people
- `customers.md`. types of customers; specific named customers get files in `customers/`
- `vendors.md`. same pattern for vendors
- `competitors.md`. short profiles, refresh quarterly
- `strategic-priorities.md`. current 90-day and annual priorities
- `known-issues.md`
- `successes.md`
- `roles-responsibilities.md`. only YOUR roles. The team org chart lives in `team.md`.

---

### Template 3. Short-lived project with named stages (buy a house, plan a trip, ship a launch)

For a project with a defined end state and a sequence of stages.

Default files:
- `variables.md`. the inputs that drive every decision (budget, timeline, locations, preferences)
- `stages.md`. the named stages of the project, with current stage marked
- `stakeholders.md`. anyone else involved (partner, agent, advisor)
- `options.md`. the alternatives being considered, with notes
- `constraints.md`. what's ruled out and why
- `decisions.md`. running log of decisions made and why
- `risks.md`. what could go wrong, what we're doing about it

---

### Template 4. Personal life domain (health, finances, learning, relationships)

For ongoing life domains that don't have a finish line but do have an optimum running condition.

Default files:
- `current-state.md`. where things stand right now, baseline metrics if any
- `goals.md`. the running goals in this domain (short-term and long-term)
- `routines.md`. the habits and routines that move the needle
- `metrics.md`. what's tracked, how often
- `known-issues.md`. current frustrations, blockers, things being worked on
- `successes.md`. wins worth referencing
- `constraints.md`. time, money, energy budgets

---

### Template 5. Solo project / creative work (writing a book, building a product, making a channel)

For solo creative or product work.

Default files:
- `project-overview.md`. what's being made, for whom, why
- `audience.md`. who this is for
- `voice-and-style.md`. voice rules, style preferences (link to brand-voice skill if applicable)
- `body-of-work.md`. what's been produced so far, with one-line descriptions
- `pipeline.md`. what's in flight, what's queued
- `constraints.md`. time, scope, format
- `inspirations.md`. references, models, things to study
- `known-issues.md`
- `successes.md`
