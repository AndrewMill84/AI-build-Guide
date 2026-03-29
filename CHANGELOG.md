# Changelog — AI Build Operating System

All notable changes to the AI Build OS are documented here. This tracks the evolution of the system itself, not individual projects built using it.

Format: reverse chronological. Most recent changes first.

---

## v1.1 — 2026-03-29 — Improvement Pass

Focused improvement pass to increase operator usability, next-action clarity, and long-term maintainability.

### Added

| Change | File | Rationale |
|---|---|---|
| Definition of Done | `workflow/definition-of-done.md` | Concrete completion criteria were missing — stages, tasks, features, and handoffs now have a clear "done" checklist |
| OS Changelog | `CHANGELOG.md` | System evolution was invisible — now tracked |
| New Project Checklist | `project-starter/new-project-checklist.md` | Fast copy-paste checklist for starting a project without re-reading the full README |
| Projects folder | `projects/README.md` | System/project separation was implied but never explicit — now documented |

### Changed

| Change | File | Rationale |
|---|---|---|
| Added Stage History section | `project-starter/STATUS.md` | The example project had this but the template did not — now consistent |
| Added anti-pattern guidance | `memory/README.md` | Memory README only mentioned positive patterns — now explicitly covers failure patterns too |
| Cleaned up project-env section | `AGENTS.md` | Placeholder brackets made it look like an unfilled template — now reads as clear instructions |
| Added cross-references | `workflow/00-overview.md` | Related files (definition-of-done, roles) were not linked |
| Updated folder structure | `README.md` | Added `projects/`, `CHANGELOG.md`, and `definition-of-done.md` references |

### Unchanged (reviewed and confirmed strong)

- All 9 workflow stage files — already well-defined
- All 11 templates — already consistent and well-formatted
- `QUICKREF.md` — already comprehensive, kept at root for fast access
- `workflow/roles-and-responsibilities.md` — already detailed with stage-by-stage coverage
- `memory/patterns.md` — already has dual-track (good patterns + failure patterns)
- Go-back rules in `AGENTS.md` and `workflow/00-overview.md` — already thorough
- Example project (`examples/bookmark-cli/`) — already complete
- Diagrams — already accurate

---

## v1.0 — 2026-03-29 — Initial Release

### Created

The complete AI Build Operating System with:

- 9-stage workflow lifecycle (Idea → Clarification → Specification → Plan → Tasks → Implementation → Review → Documentation → Handoff)
- 11 fill-in templates for all artifact types
- Agent operating contract (`AGENTS.md`) with Think→Act→Reflect philosophy
- Operator quick reference (`QUICKREF.md`)
- Project memory system (decisions, patterns, project index)
- Roles and responsibilities definition
- STATUS.md control panel concept
- Project starter with naming conventions
- Complete worked example (Bookmark CLI)
- Mermaid diagrams (artifact map, workflow lifecycle)

### Design Decisions

- **Repo-native**: Everything is plain markdown — no external tools required
- **Agent-compatible**: Any AI agent can operate from the file structure alone
- **Stage-based**: Each stage has clear inputs, outputs, and exit criteria
- **Memory-preserving**: Decisions and patterns persist across sessions and projects

---

<!-- Append new versions above this line -->
