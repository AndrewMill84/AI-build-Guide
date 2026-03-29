# Product / Feature Specification

## Metadata

| Field | Value |
|---|---|
| **Project** | Bookmark CLI |
| **Date** | 2026-03-29 |
| **Author** | Agent |
| **Stage** | 3 — Specification |
| **Status** | Approved |

---

## Summary

Bookmark CLI is a command-line tool for saving, tagging, searching, listing, and opening web bookmarks. It stores data in a local JSON file and is designed for developers who prefer terminal-based workflows over browser bookmark managers.

---

## Functional Requirements

| ID | Requirement | Priority | Acceptance Criteria |
|---|---|---|---|
| FR-01 | Add a bookmark with URL, title, and optional tags | Must | `bm add <url> --title "Title" --tags tag1,tag2` creates an entry in the JSON file |
| FR-02 | List all bookmarks in a table format | Must | `bm list` displays all bookmarks with ID, Title, URL, Tags columns |
| FR-03 | Filter bookmarks by tag | Must | `bm list --tag dev` shows only bookmarks with the "dev" tag |
| FR-04 | Search bookmarks by keyword | Must | `bm search <query>` matches against title and tags (case-insensitive) |
| FR-05 | Delete a bookmark by ID | Must | `bm delete <id>` removes the bookmark and confirms deletion |
| FR-06 | Open a bookmark URL in the default browser | Must | `bm open <id>` launches the URL in the system default browser |
| FR-07 | Auto-create storage file on first use | Must | If `~/.bookmarks.json` doesn't exist, create it automatically |
| FR-08 | Auto-generate unique IDs for bookmarks | Must | Each bookmark gets an auto-incremented numeric ID |

---

## Non-Functional Requirements

| ID | Requirement | Category | Target |
|---|---|---|---|
| NF-01 | CLI should respond in under 200ms | Performance | <200ms for any command |
| NF-02 | Data should survive ungraceful exits | Reliability | Use atomic write pattern |
| NF-03 | Error messages should be clear and actionable | Usability | No stack traces for user errors |

---

## User Stories / Use Cases

### Use Case 1: Save a new bookmark

- **Actor**: Developer
- **Goal**: Save a useful URL for later reference
- **Steps**:
  1. User runs `bm add https://example.com --title "Example Site" --tags reference,docs`
  2. System adds the bookmark with an auto-generated ID
  3. System confirms: "Bookmark #1 saved: Example Site"
- **Expected Result**: Bookmark is persisted in the JSON file
- **Error Cases**: If URL is missing, show usage help

### Use Case 2: Find a bookmark

- **Actor**: Developer
- **Goal**: Find a previously saved bookmark about "react hooks"
- **Steps**:
  1. User runs `bm search "react hooks"`
  2. System searches titles and tags for matches
  3. System displays matching bookmarks in table format
- **Expected Result**: Relevant bookmarks are shown
- **Error Cases**: If no matches, display "No bookmarks found matching 'react hooks'"

### Use Case 3: Open a bookmark

- **Actor**: Developer
- **Goal**: Open a saved bookmark in the browser
- **Steps**:
  1. User runs `bm list` to see bookmarks and their IDs
  2. User runs `bm open 3` to open bookmark #3
  3. System launches the URL in the default browser
- **Expected Result**: Browser opens with the bookmark URL
- **Error Cases**: If ID doesn't exist, show "Bookmark #3 not found"

---

## Scope

### In Scope
- Five commands: `add`, `list`, `search`, `delete`, `open`
- Local JSON file storage at `~/.bookmarks.json`
- Tag-based organization with case-insensitive matching
- Table-formatted output
- Duplicate URL warning (not blocked)

### Out of Scope
- Browser extension or GUI
- Cloud sync or multi-device support
- Import/export functionality
- Fuzzy search
- Edit existing bookmarks (future enhancement)

---

## Data Requirements

| Data | Source | Format | Storage |
|---|---|---|---|
| Bookmarks | User input via CLI | JSON objects | `~/.bookmarks.json` |

### Bookmark Object Schema

```json
{
  "id": 1,
  "url": "https://example.com",
  "title": "Example Site",
  "tags": ["reference", "docs"],
  "created": "2026-03-29T10:00:00Z"
}
```

---

## Constraints

| Constraint | Impact | Flexibility |
|---|---|---|
| Must run on Windows | Node.js handles cross-platform; use `open` package for browser | Hard |
| No external services | All data local; no API calls | Hard |
| Node.js CLI | Technology is fixed | Hard |

---

## Approval

| Role | Name | Status | Date |
|---|---|---|---|
| Stakeholder | Andre | Approved | 2026-03-29 |
