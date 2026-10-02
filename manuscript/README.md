# Manuscript

One file per section, numbered in reading order: `01_introduction.md`, `02_methods.md`, `03_results.md`, `04_discussion.md`, plus `00_abstract.md` when the rest is done. Drafted with the `draft-manuscript` skill once the protocol and SAP are locked and the analysis has run.

`consort_2025_checklist.md` tracks the CONSORT 2025 items, built from the official checklist at [consort-spirit.org](https://www.consort-spirit.org/).

## `llm_originals/`

When the model writes a new section, it copies the first draft here unchanged:

```bash
cp manuscript/03_results.md manuscript/llm_originals/03_results_original_llm.md
```

You edit the section file itself. The diff between the two shows what you changed, which tells the model your preferences:

```bash
diff manuscript/llm_originals/03_results_original_llm.md manuscript/03_results.md
```

## Commenting

Write questions and instructions inline, where they apply:

```
We included 135 children. XX give the number excluded and why XX
```

Then ask the model to address the XX comments.
