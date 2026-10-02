# CLAUDE.md

This folder is a clinical research project: a trial protocol, a statistical analysis plan, the analysis, and the manuscript. This file says how to work in it. Read it at the start of every session.

## Who you are working with

The user is a clinician or clinical researcher. They may be using Claude Code, and a terminal, for the first time.

- **Answer in the language they write in.** Documents are written in the language set in `plan.md` (English by default), whatever language the conversation is in.
- **Plain words.** Do not use terms like git, bash, commit, diff or repository without a one-line explanation. Say what you are about to do, and what you did, in a sentence each.
- **Say where things are.** When you create or change a file, give its path.
- **One step at a time.** Do not run ahead through several sections or stages. Finish one, show it, and wait.
- **End with the next step.** Close every answer that finishes a task with one suggested next step, written as something they can type (e.g. `draft the next protocol section`).
- **Ask rather than guess.** When a fact about their study is missing, ask. Group questions into one numbered batch they can answer by number.
- **They are the expert on the clinical content.** You are the expert on structure and on checking. Do not overrule their clinical judgement. Do point out when something does not follow.

If the user seems lost or asks what to do, use the `start` skill. The participant cheat sheet is `snydeark.md` (Danish).

## Read first

Before drafting or changing anything, read:

1. `plan.md`: the stage, what the study must show and must not show, the decisions already made, and any amendments.
2. `todo.md`: open tasks and who owns them.
3. `style.md`: before writing any prose.

If `plan.md` is still the empty template, stop and use the `start` skill.

## Stages

The stage in `plan.md` decides what you work on:

| Stage | Draft with | Folders open for drafting | Locked folders |
| :--- | :--- | :--- | :--- |
| protocol | `draft-protocol` | `protocol/` | |
| sap | `draft-sap` | `sap/`, `analysis/` | `protocol/` |
| running | (data collection) | `analysis/` | `protocol/`, `sap/` |
| manuscript | `draft-manuscript` | `manuscript/`, `analysis/` | `protocol/`, `sap/` |

- **A locked document is not changed.** The lock is recorded in `plan.md` and enforced by a deny rule in `.claude/settings.json`. If the user wants to change a locked document, it is an amendment: log it in the Amendments table in `plan.md` (date, what, why, whether outcome data by group had been seen) before anything is changed, and tell them how to lift the lock.
- **Do not move to the next stage on your own.** Stages change when the user says a document is final.
- **The SAP is locked before outcome data by group are seen.** If that has already happened, say so plainly. It must be reported.

## Hard rules

- **No patient data.** Never read, copy, print or summarize anything that looks like identifiable patient data (names, CPR numbers, dates of birth, addresses, free-text case descriptions, recordings). If you find any in this folder, stop and tell the user.
- **`data/` is read-only.** Never write to, overwrite or "clean" files in `data/`. Recode on read, in the analysis script. The source keeps what was recorded.
- **Never invent facts about the study.** No number, site, name, dose, time point or procedure that the user or the folder has not given you. Where one is missing, write `XX TO FILL: <what is needed> XX` and add a `[Y]` item to `todo.md`.
- **Every result in the manuscript comes from `analysis/output/`.** Do not type a result into the manuscript that no output file contains. If a number is needed and does not exist, add the analysis step instead.
- **Never invent a reference.** A reference you suggest goes on the "References to verify" list in `todo.md`. It does not go into `references.bib` or the manuscript until the user has checked it.
- **Decisions in `plan.md` are settled.** Do not reopen them unless the user asks. If you think one is wrong, say so and point to it. Do not quietly work around it.
- **Scope changes are written down before they are made.** If a request changes what the paper shows, add it to the scope log in `plan.md` first.

## Drafting a section

The protocol, the SAP and the manuscript work the same way: one file per section in `protocol/`, `sap/` or `manuscript/`, numbered in reading order. The `draft-` skills decide what goes in a section. This is how any section is written and revised.

### New section

1. Write the section to `<folder>/<section>.md`.
2. Copy it straight away with `cp`, not by rewriting it:
   ```bash
   cp protocol/04_participants.md protocol/llm_originals/04_participants_original_llm.md
   ```
3. The copy is the untouched first draft. It exists so the user's edits can be compared with it.

### Revision

1. The user edits the section file directly. Questions and instructions for you are inline, marked `XX ... XX`.
2. To see what changed: `diff <folder>/llm_originals/<section>_original_llm.md <folder>/<section>.md`
3. Read both the comparison and the full edited file. The comparison shows the user's edits. The XX comments show what they want from you.
4. Treat the user's edits as preferences. Do not undo them. Where they reveal a general rule, suggest adding it to `style.md`.
5. Resolve each XX comment and remove it. If you cannot resolve one, leave it and say why.

### Writing guidance

- `style.md`: how every sentence is written.
- `writing/protocol_sap_patterns.md`: the thinking errors to check a protocol or SAP section for.
- `writing/completeness_checklist.md`: whether a protocol or SAP is complete, before it is locked.

## Analysis

- Write analysis code in R, unless the user asks for another language.
- Scripts go in `analysis/`. Follow the conventions in `analysis/README.md` (numbered run order, fixed seed, output to `analysis/output/`).
- Run the code after writing it. Report what it printed, including warnings.
- Replaced scripts move to `analysis/superseded/`. Do not delete them.

## References

Every reference passes two checks, in this order:

1. **CrossRef (you).** Run the `crossref-check` skill on every reference you suggest, and on every entry in `references.bib`. It confirms the reference exists and that author, title, year and journal match. A reference without a match is flagged **NO MATCH** on the list in `todo.md` for human review. Never replace it with the nearest search result.
2. **Reading (the user).** A person opens the source and confirms it says what the sentence claims. They record it as `% CHECKED <date> <initials>: <what the source actually says>` above the entry. Never write a `CHECKED` line yourself.

- A CrossRef match proves the paper exists. It does not prove the paper supports the sentence.
- `references.bib` holds only references that have passed both checks. An entry without both a `% CROSSREF` and a `% CHECKED` line is not ready for the manuscript. Flag it.
- Before adding a citation, check whether `references.bib` already has it.

## Checking agents

Two agents in `.claude/agents/` check work independently:

- `code-check` reruns the analysis and compares its output with what the manuscript reports.
- `claim-check` reads a section sentence by sentence and asks whether each claim traces to a result or a checked reference.

Use them after any change to the analysis or to a results or discussion section. `claim-check` also checks the manuscript against the locked SAP: every analysis reported is pre-specified or labelled post hoc. Report their findings to the user as they are. Do not fix a finding and then report it as absent.

## Second opinions

When the user wants a review, critique or fact-check from outside, use the `second-opinion` skill. The prompt goes in `advisors/` and contains the work itself, not our interpretation of it. No patient data goes in a prompt. Answers are saved verbatim next to the prompt and never edited.

## Statistical help

When the user wants help from a statistician, use the `statistician-brief` skill. The brief describes the user's plan as it stands. Problems you notice go to the user in the conversation, not into the brief.

## Feedback

Meeting notes and reviewer comments go in `feedback/` as received. Do not edit them. When asked, turn them into concrete items in `todo.md`, each pointing back to its source file.

## End of session

Before stopping, update `todo.md`: tick what was finished, add what is left, and note anything the user needs to decide. Tell the user they can pick up next time by typing `start`.
