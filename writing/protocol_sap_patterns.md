# Thinking errors in protocols and analysis plans

The recurring errors in drafts of trial protocols and statistical analysis plans (SAPs). Read it before showing a section to a co-author, and when a passage reads well but something is off.

These are errors in the plan, not in the prose. Prose is in `../style.md`. The examples are illustrations, not from a real trial.

---

## 1. Pre-specification leak

A choice that depends on the data, stated without the rule that decides it. Two analysts would follow the plan and do different things.

**Symptom:** "as appropriate", "if the data allow", "depending on the distribution", "a suitable test". A branch ("A if X, otherwise B") where X is not defined.

**Where:** choice of test, missing data, transformations, when to run a subgroup analysis.

**Guideline:** Gamble et al. 2017 (an analysis plan exists to remove the analyst's choices); ICH E9(R1).

**Before:**
> Speech scores are compared between groups with a t-test if approximately normal, or a Mann-Whitney test if skewed.

"Approximately normal" is not a rule.

**After:**
> We compare speech scores between groups with linear regression adjusted for baseline score.

Choose one method and commit. Or state the decision rule exactly: which statistic, which cut-off, checked how.

**Principle:** Give the rule, not the intention. If a decision waits for the data, write the decision rule down now.

---

## 2. Incomplete estimand

The outcome is named but not fully defined. An estimand has five attributes, and a draft that gives two of them looks complete when it is not.

**Symptom:** an outcome with no time point, no assessor, or no statement of what happens to a participant who leaves the intended path. "Improved hearing outcomes" with nothing about when, measured how, or on what scale.

**Where:** primary and secondary outcomes, the population, anywhere a participant can deviate (stops using the device, switches arm, has a second operation).

**Guideline:** ICH E9(R1). The five attributes are population, treatment, endpoint (the variable), intercurrent events, and the population-level summary.

**What a complete one does:** names each intercurrent event (for example, "child receives a second implant before 12 months"), chooses a strategy for it (treatment policy, hypothetical, while on treatment, composite, principal stratum), and gives the reason. An intercurrent event is not missing data.

**Principle:** Before calling an outcome defined, check all five: population, treatment, endpoint, intercurrent events, summary. Name the summary measure (a difference in means, a risk ratio, a hazard ratio), not only the endpoint.

---

## 3. Self-praise and empty precision

An adjective that grades our own work, or a phrase that sounds precise and says nothing.

**Symptom:** "rigorous", "robust", "unbiased", "gold standard", "comprehensive", "standard methods", "appropriate techniques".

**Before:**
> Using blinded audiologists as outcome assessors ensures a rigorous, unbiased evaluation.

**After:**
> Audiologists who do not know the child's group assess the primary outcome. Blinding to group reduces assessment bias.

**Principle:** Say what the design does and let the reader judge it. If a reviewer could write the same adjective about the paper, it does not belong in the paper.

---

## 4. Objective and outcome drift apart

The objective describes one endpoint and the primary outcome defines another. They look aligned and are not.

**Symptom:** the objective talks about a proportion and the outcome is a mean, or the reverse. "Increase the proportion of children with age-appropriate language" against "difference in mean language score".

**Where:** objectives against outcomes; the trial registration against the protocol.

**Principle:** The objective, the primary outcome, the sample size calculation and the registration describe the same estimand in the same words. Read them one after another and check.

---

## 5. Documents disagree

The protocol, the SAP, the sample size calculation and the registration drift apart. A number or a definition changes in one and not the others.

**Symptom:** the follow-up is 12 months in one document and 18 in another. A covariate is defined differently in the SAP and the protocol. The sample size in the protocol is not the one the calculation gives.

**Where:** anything that appears in more than one document. Highest risk just after a revision.

**Guideline:** SPIRIT 2025 (the protocol and the registration must agree).

**Principle:** After changing a shared quantity, search every document for the old value and for the concept, not only the file you edited. Keep one definition and refer to it.

---

## 6. Wrong unit of analysis

A statement made at the wrong level of the data. The unit that is randomized, the unit the outcome is measured on, and the unit the model treats as independent are not always the same.

**Symptom:** ears analysed as independent when children were randomized. Repeated visits analysed as separate observations. A sample size in ears when the trial randomizes children. A covariate that does not vary between the units being compared.

**Guideline:** SPIRIT 2025 and CONSORT 2025 (state the unit of randomization and the analysis population).

**Principle:** State the unit of randomization and the unit of analysis explicitly. If a person contributes more than one measurement, say how the analysis handles it.

---

## 7. Population, estimand and method in one sentence

Who is analysed, which effect is estimated, and which model is used are three decisions. A sentence that merges them hides two.

**Symptom:** "We analyse the ITT population with mixed models to estimate the effect."

**Principle:** Three sentences. First the population (who). Then the estimand (which effect, on which scale). Then the method (which model, which software). Each can then be checked on its own.

---

## 8. Undefined working term

A loaded term used as if everyone reads it the same way.

**Symptom:** "responder", "improved", "adherent", "full-time use", "successful fitting" used before a definition.

**Guideline:** SPIRIT 2025 (define outcomes precisely enough to replicate); Gamble et al. 2017.

**Principle:** Define the term where it first matters, in one operational sentence. "Full-time use: datalogging shows at least 10 hours of device use per day, averaged over the 4 weeks before the visit."

---

Add your own. When a revision catches a new kind of error, add it with a before and after.
