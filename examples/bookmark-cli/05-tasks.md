# Task Breakdown

## Metadata

| Field | Value |
|---|---|
| **Project** | Bookmark CLI |
| **Date** | 2026-03-29 |
| **Source** | `04-plan.md` |

---

### Task 1: Project Setup

| Field | Value |
|---|---|
| **Status** | `done` |
| **Size** | Small |
| **Depends On** | None |
| **Assigned To** | Agent |

**Description**: Initialize the Node.js project with package.json, install dependencies (commander, cli-table3, open), create the folder structure, and set up the bin entry point.

**Files Affected**:

| File | Action |
|---|---|
| `package.json` | Create |
| `bin/bm.js` | Create (stub) |
| `src/commands/` | Create directory |
| `src/storage.js` | Create (stub) |
| `src/display.js` | Create (stub) |

**Acceptance Criteria**:
- [x] `npm install` runs without errors
- [x] Folder structure matches the plan
- [x] `node bin/bm.js --version` outputs a version number

---

### Task 2: Storage Module

| Field | Value |
|---|---|
| **Status** | `done` |
| **Size** | Medium |
| **Depends On** | Task 1 |
| **Assigned To** | Agent |

**Description**: Implement the storage module with functions: `loadBookmarks()`, `saveBookmarks(data)`, `addBookmark(bookmark)`, `deleteBookmark(id)`, `findBookmarks(query)`, `getBookmark(id)`. Use atomic writes (write to temp file, then rename).

**Files Affected**:

| File | Action |
|---|---|
| `src/storage.js` | Implement |
| `test/storage.test.js` | Create |

**Acceptance Criteria**:
- [x] Can add a bookmark and read it back
- [x] Can delete a bookmark by ID
- [x] Can search bookmarks by keyword
- [x] Auto-creates JSON file if it doesn't exist
- [x] Uses atomic write pattern
- [x] Unit tests pass

---

### Task 3: Display Module

| Field | Value |
|---|---|
| **Status** | `done` |
| **Size** | Small |
| **Depends On** | Task 1 |
| **Assigned To** | Agent |

**Description**: Implement the display module with a `formatTable(bookmarks)` function that formats bookmark data as a terminal table using cli-table3.

**Files Affected**:

| File | Action |
|---|---|
| `src/display.js` | Implement |

**Acceptance Criteria**:
- [x] Outputs a readable table with columns: ID, Title, URL, Tags
- [x] Handles empty bookmark list with a "No bookmarks" message
- [x] Tags are displayed as comma-separated values

---

### Task 4: Command Handlers

| Field | Value |
|---|---|
| **Status** | `done` |
| **Size** | Large |
| **Depends On** | Task 2, Task 3 |
| **Assigned To** | Agent |

**Description**: Implement all five command handlers: add, list, search, delete, open. Each handler uses the storage and display modules.

**Files Affected**:

| File | Action |
|---|---|
| `src/commands/add.js` | Create |
| `src/commands/list.js` | Create |
| `src/commands/search.js` | Create |
| `src/commands/delete.js` | Create |
| `src/commands/open.js` | Create |

**Acceptance Criteria**:
- [x] `add` saves a bookmark with URL, title, and tags; confirms with message
- [x] `list` displays all bookmarks; supports `--tag` filter
- [x] `search` finds bookmarks matching a keyword in title or tags
- [x] `delete` removes a bookmark by ID; confirms deletion
- [x] `open` launches the bookmark URL in the default browser
- [x] All commands show helpful error messages for invalid input

---

### Task 5: CLI Entry Point & Integration

| Field | Value |
|---|---|
| **Status** | `done` |
| **Size** | Medium |
| **Depends On** | Task 4 |
| **Assigned To** | Agent |

**Description**: Wire up all commands in the Commander.js entry point. Test end-to-end from the command line.

**Files Affected**:

| File | Action |
|---|---|
| `bin/bm.js` | Implement |
| `test/commands.test.js` | Create |

**Acceptance Criteria**:
- [x] `bm add <url> --title "Title" --tags tag1,tag2` works
- [x] `bm list` works
- [x] `bm list --tag dev` works
- [x] `bm search "query"` works
- [x] `bm delete <id>` works
- [x] `bm open <id>` works
- [x] `bm --help` shows all commands
- [x] Integration tests pass
