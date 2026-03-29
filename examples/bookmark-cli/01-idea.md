# Idea Intake

## Metadata

| Field | Value |
|---|---|
| **Project** | Bookmark CLI |
| **Date** | 2026-03-29 |
| **Author** | Andre |
| **Stage** | 1 — Idea Capture |

---

## The Idea

I want a simple command-line tool that lets me save, tag, search, and list bookmarks. Instead of using browser bookmarks (which are messy and scattered), I want a single CLI tool that works from any terminal, stores bookmarks in a local JSON file, and lets me find what I need quickly.

---

## Motivation

My browser bookmarks are a mess. I have hundreds of links across multiple browsers and devices. I can never find what I need. I want a single, searchable, tag-based system I can access from the terminal where I already spend most of my time.

---

## Who Is This For?

Me — a developer who works primarily in the terminal and wants quick access to saved links without context-switching to a browser.

---

## What Does Success Look Like?

I can:
- Save a URL with a title and tags from the command line
- Search my bookmarks by tag or keyword
- List all bookmarks or filter by tag
- Delete bookmarks I no longer need
- Have all data persist between sessions in a local file

---

## What Exists Already?

Nothing structured. I currently use a random mix of browser bookmarks, notes in text files, and bookmarks in Slack messages. None of these are searchable or organized.

---

## Known Constraints

- Must work on Windows (my primary OS)
- Should be a standalone Node.js CLI (no external services)
- Data stored locally — no cloud sync needed for v1
- Should be fast — I don't want to wait for a CLI tool

---

## Out of Scope

- Browser extension or GUI
- Cloud sync or multi-device support
- Import from browser bookmarks (future consideration)
- Sharing bookmarks with others

---

## Initial Rough Thinking

Could be a simple Node.js script using Commander.js for CLI parsing and a JSON file for storage. Keep it minimal.

---

## Open Questions

- Should bookmarks have a "category" or just tags?
- Should the tool open bookmarks in the browser, or just display the URL?
- What format should the JSON storage use?
