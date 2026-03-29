# Patterns, Failures & Lessons Learned

A dual-track knowledge base of **what works** and **what doesn't**. Check this before designing new solutions or repeating old mistakes.

For the entry template, see [`templates/patterns-and-lessons.md`](../templates/patterns-and-lessons.md).

This file tracks two kinds of knowledge:

| Track | What It Captures | Why It Matters |
|---|---|---|
| ✅ **Good Patterns** | Reusable approaches that worked well | So you don't reinvent what already works |
| ❌ **Failure Patterns** | Repeated mistakes, bad prompts, rework triggers | So you don't repeat the same failures |

---

# ✅ Good Patterns

<!-- Append new good patterns below this line. Use the template for each entry. -->

## Pattern: STATUS.md as the Next-Action Oracle

| Field | Value |
|---|---|
| **Date** | 2026-03-29 |
| **Discovered In** | AI Build OS (meta) |
| **Category** | Process |

### Context

Needed a way for both humans and AI agents to quickly understand project state and know what to do next, without reading all project artifacts.

### The Pattern

Place a `STATUS.md` file at the root of each project. It contains a structured table with: current stage, status, current action required, who acts next, artifact due, and blockers. Also includes a checklist of completed artifacts.

Any agent or human reads this one file to know exactly where the project is and what needs attention.

### When to Use It

- Every project that uses the AI Build OS
- Any context where multiple sessions or agents might work on the same project
- When you want to make the next action self-evident

### When NOT to Use It

- Trivial one-shot tasks that don't need tracking
- Tasks fully completed within a single session

### Example

```markdown
| Field | Value |
|---|---|
| **Current Stage** | `4 — Technical Plan` |
| **Status** | `in-progress` |
| **Current Action** | Agent drafts 04-plan.md from approved spec |
| **Who Acts Next** | `agent` |
| **Artifact Due** | `04-plan.md` |
| **Blockers** | None |
```

### Anti-Pattern to Avoid

Using chat history as the source of truth for project state. Chat is ephemeral and context-limited — structured files persist.

---

# ❌ Failure Patterns

<!-- Append failure patterns below this line. Use the template for each entry. -->

## Failure: Jumping to implementation without a clear spec

| Field | Value |
|---|---|
| **Date** | 2026-03-29 |
| **Discovered In** | AI Build OS (meta — observed in prior projects) |
| **Category** | Process |
| **Type** | Repeated mistake |

### What Happened

Started coding based on a vague idea without writing a spec or getting clarification. The implementation went in the wrong direction and had to be significantly reworked.

### Root Cause

Skipping Stages 2–4 (Clarification, Specification, Technical Plan) because the task "seemed simple enough."

### Impact

- Wasted implementation time
- Had to redo work from scratch
- Lost confidence in the output

### How to Prevent It

- Follow the staged process even for tasks that seem simple
- At minimum, write a brief spec with acceptance criteria before coding
- Ask: "Could someone else build this correctly from what I've written?" — if no, you're not ready to build

### Warning Signs

- "This is straightforward, let's just build it"
- No written acceptance criteria before implementation starts
- Agent starts coding immediately without restating the task

---
