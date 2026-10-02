---
name: draft-protocol
description: Draft the trial protocol, section by section, following SPIRIT 2025. Use when the user asks to draft, continue, check or finish the protocol, or asks what is still missing from it. Also covers locking the protocol when it is final.
---

# Draft the protocol

The protocol is the plan for the trial. Another team should be able to run the trial from it without asking a question. Drafting it is mostly a matter of getting the facts out of the clinician's head and into the right SPIRIT item, so this skill interviews more than it writes.

Read before starting: `plan.md`, `todo.md`, `style.md`, `writing/protocol_sap_patterns.md`.

If the stage in `plan.md` is not `protocol`, or `plan.md` has no research question yet, stop and say so. Suggest `start`.

## 1. The SPIRIT checklist (first time only)

If `protocol/spirit_2025_checklist.md` does not exist, build it. **Never from memory.** Item numbers and wording must come from the official checklist.

1. Download the editable SPIRIT 2025 checklist from [consort-spirit.org](https://www.consort-spirit.org/). Fetch the home page and find the link to the SPIRIT 2025 checklist (a .docx); the link changes, so do not guess it. Save it in `protocol/sources/`.
2. Extract the text. On a Mac, `textutil -convert txt <file>.docx`. Otherwise use Python's `zipfile` to read `word/document.xml`. If neither works, ask the user to open the file and save it as plain text in the same folder.
3. Write `protocol/spirit_2025_checklist.md`: one row per item, with the item number, a short version of the item, the section file that will cover it, and a status (`open`, `drafted`, `done`, or `n/a: <reason>`).
4. Propose a list of section files, numbered in checklist order (e.g. `01_administrative.md`, `02_introduction.md`, ...), grouped the way the checklist groups the items. Show it to the user before creating anything.

If the download fails, say so and ask the user to download the checklist into `protocol/sources/`. Do not continue without it.

## 2. Drafting a section

When asked to "draft the next protocol section" (or a named one):

1. **Pick the section.** The named one, or the first in order with `open` items.
2. **List what the section needs.** For each SPIRIT item in it, write down the facts required (e.g. for eligibility: inclusion criteria, exclusion criteria, who checks them, where).
3. **Find what is already known** in `plan.md`, earlier sections, and documents the user has put in the folder.
4. **Ask for the rest in one batch**, in plain language, numbered so they can answer by number. Explain briefly why each item matters when it is not obvious ("the ethics committee will ask who can see which child is in which group").
5. **Draft only from what you know.** Where a fact is missing, write `XX TO FILL: <what is needed> XX` in the text and add a `[Y]` item in `todo.md`. Never invent a number, a site, a name, a dose, a time point or a procedure.
6. **Follow the section workflow in `CLAUDE.md`:** write the file, copy it to `llm_originals/`.
7. **Check it against `writing/protocol_sap_patterns.md`.** Fix pre-specification leaks and undefined terms, or flag them if fixing needs a decision from the user.
8. **Update the checklist** statuses for the section's items.
9. **Report:** what was drafted, which items still have gaps, and the next step as a command.

## Things that need someone else

- **Sample size:** do not produce a sample size on your own. Help the user write down the assumptions (the expected effect, its source, variability, power, significance level, dropout). Suggest `statistician-brief` before they meet a statistician. Any calculation is a script in `analysis/`, with its output in `analysis/output/`.
- **References:** every source goes through `crossref-check`, and onto the list in `todo.md`.
- **Ethics, data protection, insurance:** draft the structure, but the content comes from the user and their institution. Do not describe local rules from memory.

## Consistency

Whenever a quantity appears in more than one place (sample size, follow-up, outcome scale, visit schedule), keep one definition and refer to it. After changing one, search every file in `protocol/` for the old value and the concept.

## Before calling it final

When the user says the protocol is nearly done:

1. Go through `writing/completeness_checklist.md`, sections A, B, D, E, G and H, and report each gap.
2. Every SPIRIT item is `done` or `n/a` with a reason.
3. No `XX` left in `protocol/`.
4. Suggest a `second-opinion` design review, and a reader test of the participant information.

## Locking

Only when the user explicitly says the protocol is final:

1. Record the version, date and who locked it in the table in `plan.md`.
2. Add these to the `deny` list in `.claude/settings.json`, so Claude can no longer change the protocol:
   `"Edit(/protocol/**)"` (this also blocks writing new files there)
3. Set the stage in `plan.md` to `sap`.
4. Tell the user what this means: changes from now on are amendments, logged in `plan.md`. To make one, they edit `.claude/settings.json` (or ask you how) and record why.
