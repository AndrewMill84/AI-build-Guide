# 🤖 AI Build Process — Quick Reference

## 🎯 Purpose

This process helps me build software with AI in a structured, repeatable way.

It is designed so I always know:

- ✅ what stage I am in
- ➡️ what I need to do next
- 🧩 what information I need to provide
- 🧾 what artifact should be created
- 🟢 when the AI is ready to take over
- 🔍 what needs to be reviewed and recorded afterward

The goal is to avoid vague starts, messy implementation, and lost context.

---

## 🗺️ The Process at a Glance

**Idea → Clarify → Specify → Plan → Task → Build → Review → Record → Continue**

At each stage, I have a specific responsibility.
The AI uses the output of that stage to complete the next part of the work.

> 📄 Full stage definitions: [`workflow/`](workflow/00-overview.md)
> 📄 Agent rules: [`AGENTS.md`](AGENTS.md)
> 📄 Templates: [`templates/`](templates/)

---

## 🚀 Before Starting Any Project

1. **Create a project folder** (e.g., `projects/my-project/`)
2. **Copy [`project-starter/STATUS.md`](project-starter/STATUS.md)** into the project folder
3. **Fill in the project name, date, and objective**
4. **Start at Stage 1**

### STATUS.md is the control panel

`STATUS.md` is the **single source of truth** for where the project stands. It is structured as a control panel with these fields:

| Field | What It Tells You |
|---|---|
| **Project** | The project name |
| **Current Stage** | Which of the 9 stages you're in |
| **Stage Status** | `not-started` / `in-progress` / `blocked` / `complete` |
| **Objective** | What this stage is trying to achieve |
| **Current Action Required** | The specific thing that must happen right now |
| **Who Acts Next** | `human` / `agent` / `both` |
| **Artifact Due Next** | Which file should be produced next |
| **Required Input From Human** | ⭐ What I still need to provide before the agent can proceed |
| **Relevant Files** | Files to read for context on the current action |
| **Open Questions** | Unresolved questions that may affect progress |
| **Blockers** | What's preventing progress |
| **Last Completed Step** | What was just finished |
| **Next Step After Current** | What happens after the current action is done |

The **Required Input From Human** field is especially important — it tells me exactly what I still owe the process before the AI can move forward.

**Update STATUS.md at every stage transition and whenever the situation changes.**

---

## 1) 💡 Idea Capture

> 📄 Template: [`templates/idea-intake.md`](templates/idea-intake.md) → produces `01-idea.md`
> 📖 Full guide: [`workflow/01-idea-capture.md`](workflow/01-idea-capture.md)

### My job

Define what I want to build at a high level.

### I should provide

- 🧠 the core idea — what I want to build, in plain language
- 🎯 the problem being solved — why this matters
- 👤 who it is for — even if it's just me
- 🏁 what success looks like — how I'll know it works
- 🧱 known constraints — time, technology, integrations
- 🚫 what is out of scope — what this should NOT do
- ❓ open questions — what I already know I'm unsure about

### Output

`01-idea.md` — a clear idea statement using the template.

### Ready to move on when

- The idea is understandable by someone with no prior context
- Motivation and success criteria are stated (even if rough)
- Known constraints and scope boundaries are documented
- ✅ STATUS.md updated → Stage 2

---

## 2) 🧭 Clarify

> 📄 Template: [`templates/clarification.md`](templates/clarification.md) → produces `02-clarification.md`
> 📖 Full guide: [`workflow/02-clarification.md`](workflow/02-clarification.md)

### My job

Fill in missing details, answer key questions, and resolve ambiguity.

### I should provide

- 📦 what is in scope — and what's explicitly out
- 🧠 assumptions I'm making — stated explicitly so the AI doesn't guess differently
- ⚠️ edge cases I already know about
- 🔗 dependencies — what this relies on (systems, APIs, data, other projects)
- 🎯 the MVP — the absolute minimum worth building
- 🛡️ risks and failure modes — what could go wrong
- 📊 priority ranking — if I can't have everything, what matters most
- 🧪 expected behavior for key scenarios
- 🛠️ technical preferences or constraints
- 📝 terminology — define any ambiguous terms

### The AI's role

The AI should **ask clarifying questions** — I answer them, and the answers get compiled into the artifact.

### Output

`02-clarification.md` — clarified requirements with ambiguities resolved, assumptions stated, and MVP defined.

### Ready to move on when

- All key questions are answered or marked as "unknown — acceptable risk"
- The MVP scope is defined
- Dependencies and assumptions are written down
- ✅ STATUS.md updated → Stage 3

---

## 3) 🧾 Specify

> 📄 Template: [`templates/spec.md`](templates/spec.md) → produces `03-spec.md`
> 📖 Full guide: [`workflow/03-specification.md`](workflow/03-specification.md)

### My job

Review and approve the specification — this is the contract for what gets built.

### I should review and confirm

- 📋 functional requirements — what the system must do
- 📐 non-functional requirements — performance, security, usability
- 📦 scope — what's in and what's out
- ✅ acceptance criteria — how each requirement is verified
- 🚶 user stories / use cases — how people will actually use it
- 📊 data requirements — what data is needed, where it comes from
- 🔌 integration points — how this connects to other systems
- 📌 constraints — technical, business, or regulatory
- 🚫 negative requirements — what the system should NOT do

### Output

`03-spec.md` — a precise specification that defines what "done" means.

### Ready to move on when

- The spec is detailed enough that the AI can design a technical approach from it
- Each key requirement has acceptance criteria
- **I have explicitly approved the spec**
- ✅ STATUS.md updated → Stage 4

---

## 4) 🧱 Plan

> 📄 Template: [`templates/implementation-plan.md`](templates/implementation-plan.md) → produces `04-plan.md`
> 📖 Full guide: [`workflow/04-technical-plan.md`](workflow/04-technical-plan.md)

### My job

Review and approve the technical implementation plan before any coding starts.

### I should check

- 🏛️ architecture — does the design make sense?
- 🗂️ file/folder structure — is it clean and logical?
- 🧩 components/modules — are responsibilities clear?
- 🧰 technology choices — do I agree with the stack?
- 🔗 dependencies — are they reasonable?
- 🧭 implementation order — does the sequence make sense?
- 🧪 testing/validation approach — how will it be verified?
- ⚡ risks and mitigations — are they identified?

### Before planning, the AI should

- Check [`memory/patterns.md`](memory/patterns.md) for existing patterns to reuse
- Check [`memory/decisions.md`](memory/decisions.md) for past decisions that apply
- Record any new design decisions in `memory/decisions.md`

### Output

`04-plan.md` — a technical plan with architecture, file structure, dependencies, risks, and implementation order.

### Ready to move on when

- There is a clear and sensible way to build the solution
- Key technical decisions are documented (in `04-plan.md` and `memory/decisions.md`)
- **I have explicitly approved the plan**
- ✅ STATUS.md updated → Stage 5

---

## 5) 🧩 Task Breakdown

> 📄 Template: [`templates/task.md`](templates/task.md) → produces `05-tasks.md`
> 📖 Full guide: [`workflow/05-task-breakdown.md`](workflow/05-task-breakdown.md)

### My job

Make sure the work is broken into small, reviewable, ordered chunks.

### I should look for

- 🐘 tasks that are too large — can each one be done in a single session?
- ❓ tasks that are unclear — would the AI know exactly what to do?
- 🔗 missing dependencies — is the order correct?
- 🧪 missing acceptance criteria — how is each task verified?
- 📁 unidentified files — does each task list affected files?

### Each task should include

- Description, affected files, dependencies, acceptance criteria, and size estimate

### Output

`05-tasks.md` — an ordered list of tasks ready for implementation.

### Ready to move on when

- All work from the plan is captured as tasks
- Each task is small enough to complete and review independently
- ✅ STATUS.md updated → Stage 6

---

## 6) 🛠️ Build

> 📄 Template: [`templates/implementation-log-entry.md`](templates/implementation-log-entry.md) → produces `06-implementation-log.md`
> 📖 Full guide: [`workflow/06-implementation.md`](workflow/06-implementation.md)

### My job

Give the AI **one task at a time** and review the output before moving to the next.

### I should expect the AI to

- 🗣️ restate the task before starting
- 📁 identify the files it will touch
- ✍️ implement the change following the plan
- 🧪 validate the change (tests, build, manual check)
- 🧾 log the session in `06-implementation-log.md`
- 📊 update the task status in `05-tasks.md`
- 📝 record any decisions made in `memory/decisions.md`

### My rules during build

- **One task at a time** — don't let the AI do everything at once
- **Follow the plan** — if it needs to deviate, update the plan first
- **Don't skip validation** — even for "simple" changes

### Output

Working implementation for each task + an implementation log entry for each session.

### Ready to move on when

- All tasks in `05-tasks.md` are marked `done`
- Each task has a log entry
- All changes are validated
- ✅ STATUS.md updated → Stage 7

---

## 7) 🔍 Review

> 📄 Template: [`templates/review-checklist.md`](templates/review-checklist.md) → produces `07-review.md`
> 📖 Full guide: [`workflow/07-review.md`](workflow/07-review.md)

### My job

Verify that the overall implementation meets the spec, not just individual tasks.

### I should review

- 📋 does it match the spec? — walk through each requirement
- 📐 does it match the plan? — were there deviations?
- ✅ are acceptance criteria met?
- 🧪 do tests pass? does the build succeed?
- 🕳️ is anything missing or incorrect?
- ⚠️ are edge cases handled (from the clarification stage)?
- 📖 is documentation up to date?

### If issues are found

Create fix tasks in `05-tasks.md` → go back to Stage 6 → fix → return to review.

### Output

`07-review.md` — completed review checklist with **PASS** or **FAIL** result.

### Ready to move on when

- All checks pass (or issues are logged and fixed)
- ✅ STATUS.md updated → Stage 8

---

## 8) 🗃️ Record

> 📄 Template: [`templates/post-task-report.md`](templates/post-task-report.md) → produces `08-report.md`
> 📖 Full guide: [`workflow/08-documentation.md`](workflow/08-documentation.md)

### My job

Capture what was built so it is easy to continue later and so memory accumulates across projects.

### I should make sure these are recorded

- 🧾 what was built — summary of deliverables
- ✅ which requirements were met
- 🧠 decisions made — are they all in [`memory/decisions.md`](memory/decisions.md)?
- 🔁 what worked well — process, tools, approaches to repeat
- ⚠️ what didn't work well — things to avoid next time
- 🧰 reusable patterns — add to [`memory/patterns.md`](memory/patterns.md)
- 🕳️ known limitations — what it doesn't do yet
- 🧷 follow-up actions — what's next

### Memory updates (critical!)

| Update | File |
|---|---|
| Ensure all decisions are logged | [`memory/decisions.md`](memory/decisions.md) |
| Add reusable patterns/lessons | [`memory/patterns.md`](memory/patterns.md) |
| Add/update the project entry | [`memory/project-index.md`](memory/project-index.md) |

### Output

`08-report.md` — a completion summary + updated project memory.

### Ready to move on when

- Someone returning later can understand what happened without rediscovery
- Memory files are up to date
- ✅ STATUS.md updated → Stage 9

---

## 9) 🔁 Continue / Handoff

> 📄 Template: [`templates/session-handoff.md`](templates/session-handoff.md) → produces `09-handoff.md`
> 📖 Full guide: [`workflow/09-handoff.md`](workflow/09-handoff.md)

### My job

Leave the project in a state where the next session can start quickly — whether that's me, a different agent, or future-me who's forgotten everything.

### I should make sure these are captured

- 📍 current status — one-paragraph summary
- ✅ what was accomplished
- ➡️ what remains — specific remaining items
- 🧱 blockers or known issues
- ❓ open questions
- 📄 key files to read first — for whoever picks this up
- 🛠️ setup/run instructions — how to get it running
- 🧭 recommended next steps — in priority order

### Output

`09-handoff.md` — a handoff note that makes the next action obvious.

### Ready to move on when

- The next action is obvious to anyone reading the handoff
- STATUS.md is updated to `complete` (or reflects the handoff state)

---

## 🧠 What I Should Always Be Asking Myself

At any stage, I should be able to answer:

| Question | How to Answer |
|---|---|
| 🧭 What stage am I in? | Check `STATUS.md` |
| 🧑‍💼 What is my job right now? | Read the stage section above |
| 🧩 What information is still missing from me? | Check the "I should provide" list for my current stage |
| 🧾 What artifact needs to be created next? | Check the template reference for my current stage |
| 🟢 Is the AI ready to act yet? | Check the "Ready to move on" criteria for my current stage |
| 🔍 What do I need to review after the AI finishes? | Read the next stage's review expectations |
| 🗃️ What needs to be recorded before I stop? | Always: update STATUS.md. At Stage 8+: update memory |

If those answers are clear, the process is working.

---

## 🧑‍💼 My Role in This Process

My role is not just to ask the AI to build things.

My role is to:

- 🧠 shape the idea
- 🧭 clarify the requirements
- ✅ approve the spec and the plan (gates)
- 🔍 review the outputs
- 🧾 capture important decisions
- 🏃 keep the project moving stage by stage
- 📝 keep STATUS.md current

The AI helps execute the work, but **I guide the process and own the approval gates**.

### The two approval gates

| Gate | When | Why |
|---|---|---|
| **Spec approval** | End of Stage 3 | Don't build the wrong thing |
| **Plan approval** | End of Stage 4 | Don't build it the wrong way |

Nothing should be coded until both gates are passed.

---

## 📏 Simple Rules

1. **Do not jump to implementation until the current stage is clear enough.**
2. **Always update STATUS.md when moving between stages.**
3. **One task at a time during build.**
4. **Check memory before making new decisions.**

Good results come from:

- 📥 better inputs
- 🧩 smaller tasks
- 🎯 clear review
- 🗃️ strong record keeping

---

## 🧷 One-Line Summary

> This process helps me move from idea to delivery with AI by making my next action clear at every stage and by creating the right artifacts along the way.