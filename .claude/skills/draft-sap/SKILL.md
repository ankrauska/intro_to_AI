---
name: draft-sap
description: Draft the statistical analysis plan (SAP), section by section, from the locked protocol, following Gamble et al. 2017 and the ICH E9(R1) estimand framework. Use when the user asks to draft, continue, check or finish the SAP or analysis plan, or to write the analysis code before data are in. Also covers locking the SAP.
---

# Draft the statistical analysis plan

The SAP turns the protocol's analysis section into rules another analyst could follow and get the same result. It is locked before anyone sees outcome data by group. Every choice in it is one the analyst no longer gets to make later.

Read before starting: `plan.md`, the locked protocol in `protocol/`, `style.md`, `writing/protocol_sap_patterns.md`, and sections B, C and F of `writing/completeness_checklist.md`.

**Work with a statistician.** Clinicians should not lock a SAP alone. Suggest `statistician-brief` early, and again before locking.

## Before starting

- If the protocol is not locked (see `plan.md`), say so. The user may still go ahead, but anything taken from the protocol may change.
- If outcome data by group have been seen, say so plainly. A SAP written after that is not pre-specified, and the paper must say so.

## 1. The checklist (first time only)

The SAP follows Gamble C, et al. *JAMA* 2017;318(23):2337–2343. Ask the user for the checklist from that paper (it is in the article and its supplement) and save it in `sap/sources/`. Build `sap/sap_checklist.md` from it: item, section file, status.

If it is not available, build the checklist from sections B, C and F of `writing/completeness_checklist.md` plus the protocol's statistical methods, and say in the checklist file that this is what it is based on. **Never reconstruct the Gamble items from memory.**

## 2. Estimands first

Before drafting any section, write `sap/01_estimands.md`: one table per outcome (primary first) with the five ICH E9(R1) attributes:

| Attribute | |
| :--- | :--- |
| Population | |
| Treatment (what is compared) | |
| Endpoint (variable, time point) | |
| Intercurrent events and strategy for each | |
| Population-level summary (e.g. difference in means) | |

Take every value from the locked protocol and give the protocol section. Where the protocol is silent or vague, that is a question for the user, not a gap to fill. Show the table to the user and get it confirmed before going on. Everything else in the SAP follows from it.

## 3. Drafting a section

As in `draft-protocol`: pick the section, list what it needs, find what is known, ask for the rest in one batch, draft only from what you know (`XX TO FILL: ... XX` for the rest), follow the section workflow in `CLAUDE.md`, check against `writing/protocol_sap_patterns.md` (pre-specification leaks above all), update the checklist, report and suggest the next step.

Rules specific to the SAP:

- **One method per analysis.** No "t-test or Mann-Whitney depending on the distribution". If there is a decision rule, it is written out with its threshold.
- **Population, estimand and method in separate sentences.**
- **Software and version named.**
- **Empty tables.** Draft the shells for Table 1 (baseline by group) and the outcomes table in the SAP itself, with footnotes naming the population and the method for each row.
- **Missing data:** the assumed mechanism and the reason, even for complete-case analysis.
- **Every analysis has a label:** primary, secondary, sensitivity, or exploratory.

## 4. Analysis code before the data

Writing the code now, on simulated data, catches problems while the SAP can still change.

- Write a simulation script (`analysis/00_simulate.R` or similar) that produces a fake dataset with the variables and coding in the data dictionary. Save the fake data in `analysis/simulated/`, never in `data/`.
- Write the analysis scripts to run on it, following `analysis/README.md`.
- If the real data are in `data/` but outcomes are blinded, the scripts may read baseline data only. Do not run anything that compares outcomes by group before the SAP is locked.

## Locking

When the user says the SAP is final:

1. Go through the SAP checklist and sections B, C and F of `writing/completeness_checklist.md`. Report gaps. No `XX` left in `sap/`.
2. Check that every estimand, outcome definition and sample size agrees with the locked protocol. List any difference: each is either a correction to the SAP or an amendment to the protocol.
3. Ask the user to confirm that **no outcome data by group have been seen**, and record the answer in `plan.md`.
4. Record the version, date and who locked it in `plan.md`.
5. Add `"Edit(/sap/**)"` to the `deny` list in `.claude/settings.json` (this also blocks writing new files there).
6. Set the stage to `running`.
