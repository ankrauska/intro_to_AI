---
name: draft-manuscript
description: Draft the trial manuscript, section by section, following CONSORT 2025, from the locked protocol and SAP and the analysis output. Use when the user asks to draft, continue, check or finish the paper or any section of it (methods, results, discussion, introduction, abstract).
---

# Draft the manuscript

The paper reports what the protocol and SAP said would be done, what was done, and what was found. Most of the work is already in the folder. The risks are claims the results do not carry, analyses that were not planned presented as if they were, and numbers that do not match the output.

Read before starting: `plan.md` (including Amendments), the locked `protocol/` and `sap/`, `style.md`, `references.bib`.

If the stage in `plan.md` is not `manuscript`, or the protocol or SAP is not locked, say so before going on.

## 1. The CONSORT checklist (first time only)

If `manuscript/consort_2025_checklist.md` does not exist, build it from the official CONSORT 2025 checklist, downloaded from [consort-spirit.org](https://www.consort-spirit.org/), the same way `draft-protocol` builds the SPIRIT checklist. **Never from memory.** If the journal asks for its own checklist or an extension (e.g. for non-pharmacological treatments or pilot trials), ask the user for it.

## 2. Order

Draft in this order unless the user asks otherwise. Each section builds on the ones before it.

1. **Methods.** From the locked protocol and SAP, in the past tense, citing the protocol and the registration. Every amendment in `plan.md` is reported where it applies, with its reason.
2. **Results.** Only from `analysis/output/`. Follow the SAP's table shells. The participant flow numbers come from the output too.
3. **Discussion.** Main finding with its estimate and interval, then limitations, then comparison with other studies, then implications. Each claim traces to a result or a checked reference.
4. **Introduction.** Short: what is known, what is not, what this trial asked.
5. **Abstract and title.** Last, from the finished sections.

For each section, use the section workflow in `CLAUDE.md`, and update the CONSORT checklist.

## Rules for the paper

- **Every number from the output.** Before writing a number, find the file and the value. If it is not there, the analysis step is missing; add it to `todo.md` rather than calculating in your head.
- **Pre-specified or not.** Each analysis reported is labelled as in the SAP: primary, secondary, sensitivity, exploratory. An analysis not in the SAP is called post hoc, with the reason it was done. A planned analysis that is not reported is mentioned, with the reason.
- **The primary outcome comes first,** as defined in the SAP, even if a secondary outcome is more interesting.
- **`style.md` applies in full,** especially the reporting rules and banned words.
- **No new references without `crossref-check`.**

## After each results or discussion section

Run `code-check` (after results) and `claim-check` (after results and discussion). Report their findings to the user as they are.

## Before submission

1. Every CONSORT item is done or `n/a` with a reason. No `XX` left.
2. `claim-check` on the whole manuscript, and `code-check` once more.
3. A `second-opinion` reader test of the abstract.
4. Every reference in `references.bib` has both a `CROSSREF` and a `CHECKED` line.
5. Remind the user of the journal's policy on AI use, and offer to draft the disclosure statement. They check the policy themselves.
