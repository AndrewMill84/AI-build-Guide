# New Project Checklist

A quick-start checklist for creating a new project with the AI Build OS. For detailed explanations, see [project-starter/README.md](README.md).

---

## Setup

- [ ] **Create the project folder**
  ```
  mkdir projects/my-project-name
  ```

- [ ] **Copy STATUS.md into the project folder**
  ```
  cp project-starter/STATUS.md projects/my-project-name/STATUS.md
  ```

- [ ] **Fill in STATUS.md**
  - Set **Project** name
  - Set **Started** date
  - Set **Last Updated** date
  - Set **Objective** for Stage 1

---

## Stage 1 — Idea Capture

- [ ] **Copy the idea template**
  ```
  cp templates/idea-intake.md projects/my-project-name/01-idea.md
  ```

- [ ] **Fill in the idea** — describe what you want to build, why it matters, who it's for, and what success looks like

- [ ] **Update STATUS.md** after completing the idea:
  - Stage Status → `complete`
  - Check off `01-idea.md` in Completed Artifacts
  - Current Stage → `2 — Clarification`
  - Who Acts Next → `agent` (to ask clarifying questions)
  - Artifact Due Next → `02-clarification.md`
  - Add a row to Stage History

---

## Ready to Go

- [ ] **Point the agent to the system** — share `AGENTS.md` and `STATUS.md` so the agent knows how to operate
- [ ] **Let the agent drive** — starting from Stage 2, the agent asks clarifying questions and produces artifacts
- [ ] **Your job is to review, answer questions, and approve at gates** (Stage 3: Spec ⛳, Stage 4: Plan ⛳)

---

## Quick Reminders

| Question | Answer |
|---|---|
| Where do projects live? | `projects/` folder (or any location — the folder IS the project) |
| What file do I read first? | `STATUS.md` in the project folder |
| What does the agent read first? | `AGENTS.md` (system rules) then `STATUS.md` (project state) |
| When do I need to approve something? | After Stage 3 (spec) and Stage 4 (plan) ⛳ |
| When is a stage done? | See [workflow/definition-of-done.md](../workflow/definition-of-done.md) |
| What if I'm not sure what to do? | Check [QUICKREF.md](../QUICKREF.md) for your current stage |
