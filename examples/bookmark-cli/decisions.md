# Decision Log — Bookmark CLI

Decisions made during the Bookmark CLI example project.

---

## Decision 1: Use flat JSON file for storage

| Field | Value |
|---|---|
| **Date** | 2026-03-29 |
| **Project** | Bookmark CLI |
| **Stage** | 4 — Technical Plan |
| **Decided By** | Agent (approved by Andre) |

### Context

Needed a storage mechanism for bookmarks. Options range from a simple JSON file to a full database.

### Decision

Use a flat JSON file at `~/.bookmarks.json`. The file contains an array of bookmark objects.

### Rationale

Simplest approach for the expected scale (tens to hundreds of bookmarks). JSON files are human-readable, easy to debug, need no additional dependencies, and are portable.

### Alternatives Considered

| Alternative | Why Rejected |
|---|---|
| SQLite | Overkill for the scale; adds a dependency |
| YAML | Less tooling support; no native Node.js parser |
| CSV | Harder to handle complex data (arrays of tags) |

### Consequences

- Storage is simple to implement and debug
- Performance may degrade with thousands of entries (acceptable risk)
- File is human-readable and can be manually edited

### Revisit Conditions

If bookmark count exceeds ~5000 or if multi-user access is needed, switch to SQLite.

---

## Decision 2: Auto-incrementing numeric IDs

| Field | Value |
|---|---|
| **Date** | 2026-03-29 |
| **Project** | Bookmark CLI |
| **Stage** | 4 — Technical Plan |
| **Decided By** | Agent |

### Context

Each bookmark needs a unique identifier for the `delete` and `open` commands.

### Decision

Use auto-incrementing integers. Track the next ID by finding the max ID in the file and adding 1.

### Rationale

Numeric IDs are easy to type in a CLI context. `bm delete 3` is much nicer than `bm delete 7f3a9c2e`.

### Alternatives Considered

| Alternative | Why Rejected |
|---|---|
| UUIDs | Hard to type manually; overkill for local-only tool |
| Slugs from title | Could collide; messy with special characters |

### Consequences

- IDs are simple and predictable
- Deleting a bookmark does not reassign IDs (no renumbering)
- IDs may have gaps after deletions (acceptable)

### Revisit Conditions

If the tool needs to sync across devices or integrate with other systems, switch to UUIDs.

---

## Decision 3: Atomic writes via temp file + rename

| Field | Value |
|---|---|
| **Date** | 2026-03-29 |
| **Project** | Bookmark CLI |
| **Stage** | 6 — Implementation |
| **Decided By** | Agent |

### Context

Writing to a JSON file is not crash-safe by default. If the process is interrupted mid-write, the file could be corrupted.

### Decision

Write to a temporary file (`.bookmarks.json.tmp`) first, then rename it to `.bookmarks.json`. On most filesystems, rename is atomic.

### Rationale

Simple, well-known pattern for crash-safe file writes. No additional dependencies needed.

### Alternatives Considered

| Alternative | Why Rejected |
|---|---|
| Direct fs.writeFile | Risk of corruption if interrupted |
| Write-ahead log | Overkill for this use case |

### Consequences

- Data is safe from corruption during writes
- Slight performance overhead (negligible at this scale)

### Revisit Conditions

None likely — this pattern is solid for all scales of JSON file usage.
