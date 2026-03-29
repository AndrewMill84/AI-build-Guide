# Clarification

## Metadata

| Field | Value |
|---|---|
| **Project** | Bookmark CLI |
| **Date** | 2026-03-29 |
| **Author** | Agent (with Andre's input) |
| **Stage** | 2 — Clarification |
| **Idea Source** | `01-idea.md` |

---

## Ambiguity Review

| # | Ambiguity | Resolution |
|---|---|---|
| 1 | Categories vs. tags? | **Tags only.** Flat tagging is simpler and more flexible than categories. A bookmark can have multiple tags. |
| 2 | Should the tool open URLs in a browser? | **Yes.** Add an `open` command that launches the default browser. But listing/searching just displays the URL. |
| 3 | What JSON format for storage? | See decision in `decisions.md`. Array of bookmark objects with id, url, title, tags, and created timestamp. |
| 4 | What happens with duplicate URLs? | Warn the user but allow duplicates. They may want the same URL with different tags. |

---

## Assumptions

| # | Assumption | Validated? | Notes |
|---|---|---|---|
| 1 | Node.js is already installed | Yes | Andre uses Node.js daily |
| 2 | Windows is the primary platform | Yes | Confirmed by Andre |
| 3 | No concurrent access to the JSON file | Yes | Single user, single machine |
| 4 | URLs don't need validation | Partially | Basic format check is enough — no need to verify the URL is reachable |

---

## Edge Cases

| # | Edge Case | How Should It Be Handled? |
|---|---|---|
| 1 | JSON file doesn't exist yet | Create it automatically on first `add` |
| 2 | JSON file is corrupted | Show a clear error message; suggest backing up and resetting |
| 3 | Very long URL or title | Accept it — no artificial length limits |
| 4 | Search with no results | Display "No bookmarks found" message |
| 5 | Delete by ID that doesn't exist | Show "Bookmark not found" error |

---

## Dependencies

| # | Dependency | Type | Risk Level |
|---|---|---|---|
| 1 | Node.js (>=18) | External | Low |
| 2 | Commander.js | External (npm) | Low |
| 3 | Local filesystem | Internal | Low |

---

## MVP Definition

### Must Have (MVP)
- `add` command: save a bookmark with URL, title, and tags
- `list` command: show all bookmarks
- `search` command: find bookmarks by keyword (searches title and tags)
- `delete` command: remove a bookmark by ID
- `open` command: open a bookmark URL in the default browser
- Local JSON file persistence

### Should Have (v1.1)
- `export` command (CSV or markdown)
- `edit` command (modify title or tags)
- Color-coded terminal output

### Could Have (Future)
- Import from browser bookmarks
- Fuzzy search
- Cloud sync

---

## Risks & Failure Modes

| # | Risk | Likelihood | Impact | Mitigation |
|---|---|---|---|---|
| 1 | JSON file gets corrupted by interrupted write | Low | Medium | Write to temp file then rename (atomic write) |
| 2 | User loses data if JSON file is deleted | Low | High | Document where the file lives; suggest backups |

---

## Priority Ranking

| Priority | Feature / Requirement |
|---|---|
| 1 (highest) | `add` — ability to save bookmarks |
| 2 | `list` — ability to see all bookmarks |
| 3 | `search` — ability to find specific bookmarks |
| 4 | `delete` — ability to remove bookmarks |
| 5 | `open` — ability to open in browser |

---

## Terminology

| Term | Definition |
|---|---|
| Bookmark | A saved URL with a title and zero or more tags |
| Tag | A single-word or hyphenated label attached to a bookmark |
| ID | An auto-generated numeric identifier for each bookmark |

---

## Clarification Q&A

| # | Question | Answer |
|---|---|---|
| 1 | Should tags be case-sensitive? | No — normalize to lowercase |
| 2 | Where should the JSON file be stored? | In the user's home directory: `~/.bookmarks.json` |
| 3 | Should `list` support filtering by tag? | Yes — `list --tag dev` should show only bookmarks with that tag |
| 4 | What output format for `list`? | Table format with columns: ID, Title, URL, Tags |

---

## Remaining Unknowns

| # | Unknown | Why It's Acceptable | When It Might Need Resolving |
|---|---|---|---|
| 1 | Performance with thousands of bookmarks | Unlikely to hit this scale initially | If/when the file grows large, consider indexing |
