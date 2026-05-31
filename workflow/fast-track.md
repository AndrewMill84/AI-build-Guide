# Fast Track Mode

Fast Track is a lightweight 4-stage flow for **small, well-understood tasks** that do not need the full 9-stage lifecycle.

---

## When To Use Fast Track

Use Fast Track when ALL of the following are true:

| Condition | Example |
|---|---|
| The task is **small** — completable in a single session | Add a new field to a model, fix a bug, add a utility function |
| The task is **well-understood** — no significant ambiguity | Requirements are already clear, no open questions |
| The task is **low risk** — a mistake is easily reversed | Not changing auth, billing, or core data models |
| The task is **not a new feature from scratch** | Adding to or improving something that already exists |

**Do NOT use Fast Track when:**

- You are building something from scratch
- The task touches auth, billing, database migrations, or core APIs
- There is significant ambiguity in what needs to be built
- The task will take more than one focused session
- You are unsure of the correct technical approach

---

## The Fast Track Stages

Fast Track uses 4 stages instead of 9:

```
FT1 — Brief  →  FT2 — Spec  →  FT3 — Build  →  FT4 — Check
```

| Stage | Purpose | Full Equivalent | Output |
|---|---|---|---|
| **FT1 — Brief** | State the task clearly | Stage 1 + 2 combined | `ft-brief.md` (or inline in STATUS.md) |
| **FT2 — Spec** | Define what done looks like | Stage 3 | Acceptance criteria (can be inline) |
| **FT3 — Build** | Implement the change | Stage 6 | Working code + implementation note |
| **FT4 — Check** | Verify and log | Stage 7 + 8 combined | Verification result + memory update |

---

## Fast Track Artifacts

Fast Track minimises paperwork. Artifacts are lightweight:

### Option A — Inline (for very small tasks)
Add the brief, criteria, and result directly into `STATUS.md` notes and `05-tasks.md`. No separate files needed.

### Option B — Single file (for slightly larger tasks)
Create one `ft-[task-name].md` file covering all four stages. Use this template:

```markdown
# Fast Track: [Task Name]

## Brief
What are we doing and why? (2–5 sentences)

## Acceptance Criteria
- [ ] Criterion 1
- [ ] Criterion 2
- [ ] Criterion 3

## Files Affected
| File | Action |
|---|---|
| `path/to/file` | Modify |

## Implementation Notes
(Filled in after build — what was done, any deviations)

## Verification Result
- Tests: PASS / FAIL
- Manual check: PASS / FAIL / N/A
- Date: YYYY-MM-DD
```

---

## Fast Track Rules

| Rule | Detail |
|---|---|
| **Write the brief first** | Do not start building without stating what you are building and why |
| **Define done before building** | Acceptance criteria must exist before implementation starts |
| **Verify before closing** | Run tests or a manual check — do not skip |
| **Log the decision if one was made** | If you made a meaningful design choice, add it to `memory/decisions.md` |
| **Update STATUS.md** | Even on Fast Track, update Last Completed Step and Current Action Required |
| **Escalate to full track if scope grows** | If the task turns out to be larger than expected, stop and switch to the full 9-stage process |

---

## Fast Track vs Full Track Decision Guide

```
Is the task small AND well-understood AND low-risk?
        │
        ├── YES → Use Fast Track
        │
        └── NO → Use the full 9-stage lifecycle
                 Start at Stage 1 — Idea Capture
```

---

## Example Fast Track Tasks

✅ **Good Fast Track candidates**:
- Add a `notes` field to the Property model
- Fix a URL routing bug
- Update a template to show a new field
- Add a utility function for date formatting
- Write a test for an existing view

❌ **Not suitable for Fast Track**:
- Implement the full inspection upload and transcription flow
- Add Stripe billing integration
- Redesign the data model
- Build the Property CRUD from scratch

---

## Related Files

| File | Purpose |
|---|---|
| [workflow/00-overview.md](00-overview.md) | Full 9-stage lifecycle |
| [definition-of-done.md](definition-of-done.md) | Completion criteria for all levels |
| [QUICKREF.md](../QUICKREF.md) | Stage-by-stage operator guide |
