---
name: statistician-brief
description: Write a short reference sheet for a statistician who is going to help with the study. Use when the user wants statistical help, is preparing for a meeting with a statistician, or asks for a "statistician brief", "stats sheet" or "analysis summary". Covers the hypothesis, the variables and how they are measured, the question for the statistician, the planned models and tests, and the secondary analyses.
---

# Statistician brief

A statistician can help quickly if they get the study in the form they think in: what is being compared, on what scale, in whom, and what exactly the question is. This skill writes that sheet.

The reader is a statistician, not a clinician. They know models and tests. They do not know what a speech-in-noise score is, whether higher is better, or why a child might be measured twice. Explain the clinical side. Do not explain the statistics.

## Where the content comes from

Read these first, and take everything you can from them:

- `plan.md`: the question, what the paper must show, decisions.
- `data/README.md`: the variables, their coding and missing values.
- `analysis/README.md` and the scripts in `analysis/`: what is planned or already run.
- `analysis/output/`: descriptive results, if they exist.
- A protocol or analysis plan, if the user points to one.

Then list what is still missing and ask the user for it **in one batch**, not one question at a time. Typical gaps: the direction of a scale, the range, how the outcome is distributed, whether people were measured more than once, the exact question for the statistician.

**Never fill a gap with a plausible guess.** If a fact is not in the project and the user does not know, write `unknown` in the sheet. An honest `unknown` tells the statistician what to ask. An invented "approximately normal" sends them the wrong way.

**What the data looks like comes from the data.** Distribution, range and missingness are only stated if they come from `analysis/output/`, a published source for the instrument, or the user. If the data is available and nothing describes it yet, offer to write a descriptive script (`analysis/chk_descriptives.R` or similar) whose output is aggregated only. Mark anything taken from the instrument's documentation rather than our data as such ("manual: 0 to 95").

**No patient data in the brief.** Aggregated numbers only. No rows, no example patients.

## Do not do the statistician's job

The planned models and tests are **the user's plan, as it stands**, including if you think it is wrong. Do not replace it with what you would do, and do not add methods to it. A statistician needs to see what the clinician intends in order to help with it.

If you notice a problem (a t-test on a bounded score, repeated measures analysed as independent, a secondary analysis with no stated purpose), tell the user in the conversation, not in the brief. They decide whether to fix the plan first or ask the statistician about it. If they want it asked, it goes in section 3 as their question.

## The sheet

Write it to `advisors/statistician_brief_<YYYY-MM-DD>.md`. Keep it to one or two pages. Use the template below, in this order. Do not add sections.

```markdown
# Statistician brief: <short study title>

<Date> · <Clinician name, role, contact> · Status: <planning / data collected / analysis underway>

**Design:** <e.g. retrospective cohort from clinic records; two-arm RCT; cross-sectional survey>
**Unit of analysis:** <e.g. child; ear; visit>. <Say if there is more than one per person: both ears, repeated visits, siblings, clinics.>
**Sample size:** <N, or planned N and how it was chosen>

## 1. Research hypothesis

<One to three sentences, in plain language. Then the hypothesis as a comparison: which groups or which association, on which outcome, in which direction.>

## 2. Variables

| Variable | Role | What it measures | Scale and range | Direction | Distribution / known properties | Missing |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| <name as in the data> | Primary outcome / secondary outcome / exposure / covariate / grouping | <clinical meaning, one line, no jargon> | <e.g. integer 0 to 95; continuous, dB HL; yes/no; 4 ordered categories> | <higher = better / worse> | <e.g. ceiling effect above 90 in our data (analysis/output/descriptives.csv); manual reports approx. normal in norm sample; unknown> | <n or %, and why, if known> |

<Below the table, only if relevant: when and how often each outcome is measured; a clinically meaningful difference, with its source; anything about how the measurement is taken that could matter (different testers, different equipment, changed version of a test).>

## 3. The question for the statistician

<The clinician's question, in their words, as specific as possible. If there are several, number them and put the most important first. Say what kind of help is wanted: a check of the plan, a choice between methods, a sample size, help interpreting a result, or someone to run the analysis.>

## 4. Planned models and tests

<Numbered. For each: the outcome, what it is compared across or adjusted for, the model or test, and the software, as the clinician currently plans it. Mark anything not yet decided as "undecided".>

## 5. Secondary outcomes and other planned analyses

<Numbered. Secondary outcomes, subgroup analyses, sensitivity analyses, and any analyses planned for a different paper from the same data. For each, one line on why it is planned.>
```

## After writing

1. Show the user the sheet and the list of fields that say `unknown`. Ask whether any can be filled before it is sent.
2. Tell them separately about any problems you noticed in the plan (see above).
3. Remind them to read it through before sending: they are responsible for what it says about their study.
4. When the statistician answers or the meeting has happened, the notes go in `feedback/`, and agreed changes go into `plan.md` under Decisions.
