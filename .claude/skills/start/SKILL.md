---
name: start
description: Start or resume work in this project. Use when the user types "start", is new to the project, asks what to do next, asks where they are, or asks how the folder works. In a new project it interviews the user and fills in plan.md; in a project already under way it reports the stage and the next step.
---

# Start

The user is a clinician, possibly opening Claude Code for the first time. Be welcoming and concrete. Answer in the language they write in.

## First: new project or not?

Read `plan.md` and `todo.md`.

- If `plan.md` still has the empty template (no question filled in), this is a **new project**. Go to "New project".
- Otherwise, go to "Project under way".

## New project

1. **Explain the folder in five or six sentences.** What Claude reads every time (`CLAUDE.md`, `style.md`, `plan.md`, `todo.md`), where the protocol, the analysis plan and the manuscript will go, and that nothing personal about patients ever goes in this folder. Point to `snydeark.md` for the commands and how to write in the files. No jargon.

2. **Interview them to fill in `plan.md`.** Ask two or three questions at a time, in plain language, and wait for the answers. Cover:
   - The research question: who (population), what (intervention or exposure), compared with what, and which outcome.
   - The design they have in mind (randomized trial, cohort, ...), and whether a protocol already exists somewhere.
   - What the study must show, and what they must not claim.
   - Co-authors and roles, so `todo.md` can tag tasks with their initials.
   - Target journal, if known, and the language the documents should be written in (English by default).

   If they do not know something yet, that is fine. It becomes an item in `todo.md`, not a guess in `plan.md`.

3. **Write their answers into `plan.md`** in their words, tidied but not embellished. Show them the result and ask for corrections.

4. **Set the stage.** Usually `protocol`. If they already have a locked protocol, ask which stage they are at and record the locked versions.

5. **Update `todo.md`:** add the owner tags for the co-authors and the open questions from the interview.

6. **End with the next step.** For a new trial: "Type `draft the next protocol section` when you are ready." Say they can stop at any time and pick up later by typing `start` again.

## Project under way

Report in a few lines:

- The stage, and the locked documents with their versions.
- What was done last (the most recent ticks in `todo.md`, the most recently changed section files).
- What is blocking (`[!]` items) and who owns it.
- Open `XX` comments in the section files, if any (search for `XX`).
- **One suggested next step,** as a command they can type.

Do not start working on it until they say so.
