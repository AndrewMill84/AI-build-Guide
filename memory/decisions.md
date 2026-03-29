# Decision Log

A chronological record of significant decisions made across all projects. Each entry provides context, rationale, and alternatives considered so that future work doesn't revisit solved problems.

For the entry template, see [`templates/decision-log-entry.md`](../templates/decision-log-entry.md).

---

<!-- Append new decisions below this line. Use the template for each entry. -->

## Decision 1: Adopt the AI Build OS for all future projects

| Field | Value |
|---|---|
| **Date** | 2026-03-29 |
| **Project** | AI Build OS (meta) |
| **Stage** | Setup |
| **Decided By** | Andre |

### Context

Needed a repeatable, agent-compatible process for building software projects with AI coding tools. Previous work was ad-hoc — decisions were lost, work was redone, and agents lacked clear instructions.

### Decision

Create and adopt a repo-native AI Build Operating System with a 9-stage workflow, reusable templates, structured memory, and an agent operating contract.

### Rationale

A durable file-based system is agent-compatible, version-controllable, and works without external tooling. It creates predictable artifacts and preserves memory across sessions.

### Alternatives Considered

| Alternative | Why Rejected |
|---|---|
| External project management tool (Jira, Linear) | Not agent-readable; adds tool dependency |
| Chat-only instructions | Ephemeral; lost between sessions |
| Wiki-based system | External dependency; harder to keep in sync with code |

### Consequences

All future projects should follow this process. Templates and memory will accumulate value over time. The system itself can evolve through use.

### Revisit Conditions

If the process proves too heavyweight for small tasks, consider adding a "lightweight" track. If a team grows beyond 1-2 people, consider whether the markdown-based approach still scales.

---
