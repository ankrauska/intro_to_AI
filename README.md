# Project template for clinical trials with Claude Code

Workshop material for *AI i klinisk forskning* (Auden Nordberg Krauska, October 2026). The slides are in `slides/` (Danish). The participant cheat sheet is **`snydeark.md`** (Danish).

This folder is an empty research project that takes a trial from idea to paper: the protocol, the statistical analysis plan, the analysis, and the manuscript. A few documents in it tell Claude how to work, and Claude Code reads them every time it works in the folder. A chat forgets. A project folder remembers.

## Getting started

1. Download the folder: **Code → Download ZIP** on GitHub, and unzip it.
2. Install Claude Code: see [docs.claude.com/claude-code](https://docs.claude.com/en/docs/claude-code/overview). It comes with a Claude Pro subscription.
3. Open **Terminal**, type `cd ` (with a space), drag the folder into the window, and press Enter.
4. Type `claude`, then `start`.

`start` explains the folder, interviews you about your study, and fills in `plan.md` with you. Write in plain language, in Danish if you like. Claude writes any code.

## The one hard rule

**No identifiable patient data in this folder, and no patient data in a personal Claude account.** Put only anonymized data in `data/`, or nothing but a note saying where the data lives. The analysis scripts can run next to the data, so only results reach this folder. `.gitignore` keeps everything in `data/` out of git except its README, and `.claude/settings.json` stops Claude from opening data files itself. That is a safety net, not a guarantee. The rule is still yours to keep.

## From idea to paper

| Stage | You type | Claude drafts | Guideline | Then |
| :--- | :--- | :--- | :--- | :--- |
| Protocol | `draft the next protocol section` | `protocol/` | SPIRIT 2025 | `the protocol is final, lock it` |
| Analysis plan | `draft the next SAP section` | `sap/`, analysis code on simulated data | Gamble et al. 2017, ICH E9(R1) | Lock before anyone sees outcome data by group |
| Trial runs | | | | |
| Manuscript | `draft the next manuscript section` | `manuscript/` | CONSORT 2025 | `claim-check`, `code-check`, submission |

Claude works section by section and asks for the facts it needs. It never invents a number, a site or a procedure: a missing fact becomes `XX TO FILL: ... XX` in the text and a task in `todo.md`. Once a document is locked, Claude cannot change it. A change is then an amendment, logged in `plan.md` and reported in the paper.

## What is in the folder

| Path | What it is |
| :--- | :--- |
| `CLAUDE.md` | How Claude works in this folder. It reads this first. |
| `plan.md` | The stage, what the study must show and must not show, decisions, amendments. |
| `todo.md` | Open tasks with owners, including references still to be checked. |
| `style.md` | How every document may be written: banned words, reporting rules, voice. |
| `references.bib` | Bibliography. Each entry is checked against CrossRef and by a person. |
| `protocol/` | The protocol, one file per section, with its SPIRIT checklist. |
| `sap/` | The statistical analysis plan, one file per section. |
| `manuscript/` | The paper, one file per section, with its CONSORT checklist. |
| `writing/` | Common thinking errors in protocols and SAPs, and a completeness checklist. |
| `data/` | Anonymized data, or only a note on where it is. Read-only. |
| `analysis/` | Scripts, and their output in `analysis/output/`. |
| `feedback/` | Co-author meeting notes and reviewer comments, as received. |
| `advisors/` | Second opinions and statistician briefs. |
| `.claude/skills/` | `start`, `draft-protocol`, `draft-sap`, `draft-manuscript`, `crossref-check`, `second-opinion`, `statistician-brief`. Type `/` in Claude Code to see them. |
| `.claude/agents/` | `code-check` reruns the analysis; `claim-check` checks each claim. |
| `.claude/settings.json` | What Claude may do without asking, and what it may not do at all. |
| `slides/` | The talk. |

Folders starting with a dot are hidden in Finder. Press `Cmd + Shift + .` to show them.

## Working with it

- **Editing:** open the section files in a text editor (VS Code, or TextEdit in plain-text mode), not Word. Edit the text directly. Claude keeps its first draft in `llm_originals/` and learns your preferences from what you changed.
- **Commenting:** put questions for Claude inline as `XX your comment XX`, then type `address the XX comments in <file>`.
- **Checking:** `claim-check` goes through a section sentence by sentence; `code-check` reruns the analysis and compares the numbers. They find mismatches. They do not decide what is true. You do.
- **References:** Claude looks every reference up in CrossRef. No match means **NO MATCH** in `todo.md`, for you to find by hand. Either way, you read the source and add a `CHECKED` line to `references.bib`. A CrossRef match shows the paper exists, not that it says what your sentence claims.
- **Second opinions:** Claude writes a prompt to `advisors/` that contains the work but not your reasoning. Paste it into another model your institution allows, or let a fresh Claude subagent answer.
- **Statistical help:** `write a statistician brief` collects your hypothesis, variables, question and planned analyses into one sheet for a statistician.
- **Co-authors:** put meeting notes in `feedback/` and ask Claude to turn them into tasks.
