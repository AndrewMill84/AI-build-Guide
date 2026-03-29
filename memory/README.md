# Project Memory

Project memory is a lightweight knowledge base that persists across sessions, projects, and agents. It helps answer:

- **What has already been built?** → `project-index.md`
- **What decisions have been made?** → `decisions.md`
- **What reusable patterns exist?** → `patterns.md`
- **What is currently in progress?** → `project-index.md` (status column)
- **What still needs to be done?** → Each project's `STATUS.md`

---

## Files

| File | Purpose | Update Frequency |
|---|---|---|
| [decisions.md](decisions.md) | Log of all significant decisions across projects | When a decision is made (any stage) |
| [patterns.md](patterns.md) | Reusable patterns, failure patterns, and lessons learned | When a pattern is discovered (usually Stage 8) |
| [project-index.md](project-index.md) | Master index of all projects with status | When a project starts or completes |

---

## How to Use

### Before Starting New Work
1. **Check `decisions.md`** — See if relevant decisions have already been made
2. **Check `patterns.md`** — See if reusable patterns exist that apply
3. **Check `project-index.md`** — See what's been built before and what's in progress

### During a Project
1. **Add decisions** to `decisions.md` using `templates/decision-log-entry.md`
2. **Add good patterns** to `patterns.md` using `templates/patterns-and-lessons.md`
3. **Add failure patterns** to `patterns.md` when something goes wrong — use the failure pattern format in the same template

### After Completing a Project
1. **Update `project-index.md`** with the project summary and status
2. **Ensure all decisions** from the project are in `decisions.md`
3. **Add any new patterns** (good and bad) to `patterns.md`

---

## For AI Agents

When entering a project:
- **Always check memory first** before making design decisions
- **Search `decisions.md`** for decisions affecting your area of work
- **Search `patterns.md`** for existing solutions before creating new approaches

When completing work:
- **Record decisions** that others might need to know about
- **Record good patterns** that could be reused in future projects
- **Record failure patterns** — mistakes, bad prompts, rework triggers, and anti-patterns so they are not repeated
- **Update `project-index.md`** if the project's status has changed

---

## What Gets Recorded

Memory captures **both positive and negative knowledge**:

| Track | What to Record | Heading in `patterns.md` |
|---|---|---|
| ✅ **Good patterns** | Approaches, architectures, tool configurations, prompt strategies that worked well | `## Pattern: [name]` |
| ❌ **Failure patterns** | Repeated mistakes, bad prompts, rework triggers, failure modes, anti-patterns | `## Failure: [name]` |

Both use the template in `templates/patterns-and-lessons.md`. Failure patterns include root cause, impact, prevention steps, and warning signs.

> Negative lessons are often more valuable than positive ones — they prevent the same mistake from happening twice.

---

## Design Principles

- **Append-only** — Don't modify past entries; add new ones
- **Searchable** — Use clear titles and consistent formatting
- **Cross-referenced** — Link back to the project that produced each entry
- **Lightweight** — Keep entries concise; full details live in project artifacts
- **Dual-track** — Always capture both what worked and what didn't
