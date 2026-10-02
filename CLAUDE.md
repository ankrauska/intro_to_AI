# CLAUDE.md

This folder is a clinical research project: data, analysis, and a manuscript. This file says how to work in it. Read it at the start of every session.

## Read first

Before writing or changing anything, read:

1. `plan.md`: what the paper must show, what it must not show, and the decisions already made.
2. `todo.md`: open tasks and who owns them.
3. `style.md`: before writing any prose for the manuscript.

If `plan.md` is still the empty template, stop and help the user fill it in before drafting anything.

## Hard rules

- **No patient data.** Never read, copy, print or summarize anything that looks like identifiable patient data (names, CPR numbers, dates of birth, addresses, free-text case descriptions, recordings). If you find any in this folder, stop and tell the user.
- **`data/` is read-only.** Never write to, overwrite or "clean" files in `data/`. Recode on read, in the analysis script. The source keeps what was recorded.
- **Every number in the manuscript comes from `analysis/output/`.** Do not type a number into the manuscript that no output file contains. If a number is needed and does not exist, add the analysis step instead.
- **Never invent a reference.** A reference you suggest goes on the "References to verify" list in `todo.md`. It does not go into `references.bib` or the manuscript until the user has checked it.
- **Decisions in `plan.md` are settled.** Do not reopen them unless the user asks. If you think one is wrong, say so and point to it. Do not quietly work around it.
- **Scope changes are written down before they are made.** If a request changes what the paper shows, add it to the scope log in `plan.md` first.

## Writing the manuscript

The manuscript lives in `manuscript/`, one file per section.

### New section

1. Write the section to `manuscript/<section>.md`.
2. Copy it straight away with `cp`, not by rewriting it:
   ```bash
   cp manuscript/03_results.md manuscript/llm_originals/03_results_original_llm.md
   ```
3. The copy is the untouched first draft. It exists so edits can be diffed against it.

### Revision

1. The user edits the section file directly. Questions and instructions for you are inline, marked `XX ... XX`.
2. To see what changed: `diff manuscript/llm_originals/<section>_original_llm.md manuscript/<section>.md`
3. Read both the diff and the full edited file. The diff shows the user's edits. The XX comments show what they want from you.
4. Treat the user's edits as preferences. Do not undo them. Where they reveal a general rule, suggest adding it to `style.md`.
5. Resolve each XX comment and remove it. If you cannot resolve one, leave it and say why.

## Analysis

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

Use them after any change to the analysis or to a results or discussion section. Report their findings to the user as they are. Do not fix a finding and then report it as absent.

## Second opinions

When the user wants a review, critique or fact-check from outside, use the `second-opinion` skill. The prompt goes in `advisors/` and contains the work itself, not our interpretation of it. No patient data goes in a prompt. Answers are saved verbatim next to the prompt and never edited.

## Statistical help

When the user wants help from a statistician, use the `statistician-brief` skill. The brief describes the user's plan as it stands. Problems you notice go to the user in the conversation, not into the brief.

## Feedback

Meeting notes and reviewer comments go in `feedback/` as received. Do not edit them. When asked, turn them into concrete items in `todo.md`, each pointing back to its source file.

## End of session

Before stopping, update `todo.md`: tick what was finished, add what is left, and note anything the user needs to decide.
