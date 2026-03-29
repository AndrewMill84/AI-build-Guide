# Starting a New Project

Follow these steps to create a new project using the AI Build OS.

---

## Step 1: Create the Project Folder

Create a new folder for your project. You can put it anywhere, but a `projects/` folder under `ai-build-os/` works well for keeping things organized.

```
mkdir projects/my-project-name
```

---

## Step 2: Initialize STATUS.md

Copy the STATUS.md template into your project folder:

```
cp project-starter/STATUS.md projects/my-project-name/STATUS.md
```

Open it and fill in:
- The project name
- Set current stage to `1 — Idea Capture`
- Set status to `not-started`
- Set who acts next (likely `human`)

---

## Step 3: Create the Idea Capture

Copy the idea intake template:

```
cp templates/idea-intake.md projects/my-project-name/01-idea.md
```

Fill in the template with your idea. Don't worry about being perfect — the clarification stage will fill gaps.

---

## Step 4: Update STATUS.md

Once `01-idea.md` is complete:
- Check off `01-idea.md` in the completed artifacts list
- Update current stage to `2 — Clarification`
- Update the current action
- Update who acts next

---

## Step 5: Follow the Workflow

From here, follow the stages in order:

1. Read the current stage definition in `workflow/`
2. Use the corresponding template from `templates/`
3. Create the artifact in your project folder
4. Meet the exit criteria
5. Update STATUS.md
6. Move to the next stage

---

## For AI Agents

If an agent is helping you start a project:

1. **Tell the agent about this system** — point them to `README.md` and `AGENTS.md`
2. **Share the idea** — either verbally or by filling in `01-idea.md` yourself
3. **Let the agent drive clarification** — they'll ask good questions
4. **Review and approve key artifacts** — spec (Stage 3) and plan (Stage 4) need your approval

---

## Artifact Naming Convention

Every project uses the same file names. This makes projects predictable, searchable, and agent-friendly.

### Numbered stage artifacts

These files map 1:1 to the workflow stages. The two-digit prefix keeps them in order.

| File | Stage | Template Source |
|---|---|---|
| `01-idea.md` | 1 — Idea Capture | `templates/idea-intake.md` |
| `02-clarification.md` | 2 — Clarification | `templates/clarification.md` |
| `03-spec.md` | 3 — Specification | `templates/spec.md` |
| `04-plan.md` | 4 — Technical Plan | `templates/implementation-plan.md` |
| `05-tasks.md` | 5 — Task Breakdown | `templates/task.md` |
| `06-implementation-log.md` | 6 — Implementation | `templates/implementation-log-entry.md` |
| `07-review.md` | 7 — Review & Validation | `templates/review-checklist.md` |
| `08-report.md` | 8 — Documentation | `templates/post-task-report.md` |
| `09-handoff.md` | 9 — Handoff | `templates/session-handoff.md` |

### Non-numbered project files

These files don't belong to a single stage — they are maintained throughout the project.

| File | Purpose | Template Source |
|---|---|---|
| `STATUS.md` | Project control panel — single source of truth | `project-starter/STATUS.md` |
| `decisions.md` | Project-level decision log (append entries throughout) | `templates/decision-log-entry.md` |

### Rules

1. **Use these exact names.** Don't rename artifacts or add prefixes like the project name. The folder provides the project context.
2. **One file per artifact.** Don't split `05-tasks.md` into multiple files. Keep all tasks in one file.
3. **Append, don't replace.** For `06-implementation-log.md` and `decisions.md`, add new entries at the bottom — don't overwrite previous entries.
4. **The two-digit prefix is the stage number.** It keeps files sorted in workflow order in any file browser.

### Example project folder

```
my-project/
├── STATUS.md
├── 01-idea.md
├── 02-clarification.md
├── 03-spec.md
├── 04-plan.md
├── 05-tasks.md
├── 06-implementation-log.md
├── 07-review.md
├── 08-report.md
├── 09-handoff.md
└── decisions.md
```
