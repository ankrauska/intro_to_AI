# Project template for clinical research with Claude Code

Workshop material for *AI i klinisk forskning* (Auden Nordberg Krauska, October 2026). The slides are in `slides/` (Danish).

This folder is an empty research project. It holds the structure I use for my own papers: the data, the analysis, the manuscript, and a few documents that tell the model how to work. Claude Code reads those documents every time it works in the folder. A chat forgets. A project folder remembers.

## Getting started

1. Download the folder: **Code → Download ZIP** on GitHub, or `git clone` it.
2. Install Claude Code: see [docs.claude.com/claude-code](https://docs.claude.com/en/docs/claude-code/overview). It comes with a Claude Pro subscription.
3. Open a terminal in the folder and type `claude`.
4. Start by asking it to read `CLAUDE.md` and explain the project back to you.

You write in plain language, in Danish if you like. The model writes the code.

## The one hard rule

**No identifiable patient data in this folder, and no patient data in a personal Claude account.** Keep the data where it is allowed to be. Put only anonymized data in `data/`, or put nothing there but a note saying where the data lives. The analysis code can run locally next to the data, so only results reach this folder. `.gitignore` keeps everything in `data/` out of git except its README.

## What is in the folder

| Path | What it is | Load-bearing? |
| :--- | :--- | :--- |
| `CLAUDE.md` | How the model works in this folder. It reads this first. | Yes |
| `style.md` | How the manuscript may be written: banned words, reporting rules, voice. | Yes |
| `plan.md` | What the paper must show and must not show. Scope changes and decisions, dated. | Yes |
| `todo.md` | Open tasks with owners, including references still to be checked. | Yes |
| `references.bib` | Bibliography. Each entry carries a comment saying who checked it and what the source says. | Yes |
| `data/` | Anonymized data, or only a path to it. Read-only. | Yes |
| `analysis/` | Scripts, and their output in `analysis/output/`. | Yes |
| `manuscript/` | The paper, one file per section. First drafts are kept in `manuscript/llm_originals/`. | Yes |
| `feedback/` | Co-author meeting notes and reviewer comments, as received. | No, source material |
| `.claude/agents/` | Two checking agents: one reruns the code, one checks each claim. | Yes |
| `.claude/skills/` | Skills: `crossref-check` looks up every reference in CrossRef. | Yes |
| `slides/` | The talk. | No |

The four files `CLAUDE.md`, `style.md`, `plan.md` and `todo.md` are the infrastructure. Fill them in before you ask the model to write anything.

## Working with it

- **Before writing:** fill in `plan.md` (what the paper shows) and add your own rules to `style.md`.
- **Writing a section:** ask for a draft of one section. The model copies the draft to `manuscript/llm_originals/` so you can later see what you changed.
- **Commenting:** edit the section file directly. Put questions for the model inline as `XX your comment XX`, then ask it to address the XX comments.
- **Checking:** ask for `code-check` to rerun the analysis and compare the numbers, and for `claim-check` to go through a section sentence by sentence. The agents find mismatches. They do not decide what is true. You do.
- **References:** a suggested reference is a task, not a source. Claude first looks it up in CrossRef (the DOI registry) with the `crossref-check` skill. If nothing matches, it is flagged **NO MATCH** in `todo.md` for you to find by hand. Either way it stays on the list until you have opened it and added a `CHECKED` comment to `references.bib`. A CrossRef match shows the paper exists, not that it says what your sentence claims.
- **Co-authors:** drop meeting notes into `feedback/` and ask the model to turn them into items in `todo.md`.
