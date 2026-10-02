# Completeness checklist: protocol and statistical analysis plan

Run it before sending the protocol or SAP to a co-author, an ethics committee, a registry or a journal. Three files, three questions:

- `../style.md`: does the sentence read well?
- `protocol_sap_patterns.md`: is the thinking right?
- **this file:** is everything there? Is the document an operating manual another team could follow, not an outline?

## How to use it

Go through it item by item, per document. Each item is **present and specific**, or a **gap**. The test behind every item: *could another research team carry this out without asking us a single question?* An item that does not apply is done only if the document says so, with the reason. A blank is a gap.

## A. Guideline coverage

- [ ] The protocol covers every SPIRIT 2025 item, working from the official checklist (see `protocol/README.md`). Items that do not apply say so, with a reason.
- [ ] The SAP covers every applicable item in Gamble et al. 2017.
- [ ] The reporting guideline for the final paper is named (CONSORT 2025 for a randomized trial).
- [ ] The registration matches the protocol: title, objective, groups, primary outcome, sample size.

## B. The estimand (for each outcome)

- [ ] All five ICH E9(R1) attributes are there: population, treatment, endpoint, intercurrent events, population-level summary.
- [ ] The primary outcome is fully defined: what is measured, on what scale, when, by whom, and how disagreements are resolved.
- [ ] Each intercurrent event is named and has a strategy. It is not treated as missing data by default.

## C. Tables, figures and code (SAP)

- [ ] An empty Table 1 (baseline by group), with a footnote fixing the population and the summary measures.
- [ ] An empty outcomes table, with a footnote naming the model or test for every row.
- [ ] Figures described: layout, axes, units.
- [ ] The primary model written out, with the covariates listed.
- [ ] Software and version named, and where the analysis code will be.

## D. Operational detail

- [ ] Every procedure has a **who**, a **where** and a **how**.
- [ ] Randomization: how the sequence is generated, how allocation is concealed, who enrolls, who assigns.
- [ ] Blinding: who is blinded, how, what could unblind them, and what prevents it.
- [ ] Data: how it is collected, where it is stored, who has access, how it is pseudonymized or anonymized.
- [ ] No "as appropriate", "standard methods", "where relevant" or "if necessary" without a rule after it.

## E. Appendices

- [ ] The intervention described well enough to repeat it (TIDieR, if relevant).
- [ ] Data dictionary: variable name, type, allowed values, source, how it is derived.
- [ ] Schedule of visits and assessments.
- [ ] Participant information and consent form.

## F. Missing data and edge cases (SAP)

- [ ] The assumption about why data are missing is stated, with a reason, even if the plan is complete-case analysis.
- [ ] Named edge cases with a fallback: a visit that does not happen, an assessor who leaves, a device that fails.
- [ ] The analysis population is defined, and exclusions and their reasons are tabulated by group.

## G. Consistency between documents

- [ ] One definition per quantity. Outcome scale, sample size, effect size, follow-up and covariates are identical in the protocol, the SAP, the sample size calculation and the registration.
- [ ] The objective, the primary outcome, the sample size target and the registration describe **the same estimand in the same words**.
- [ ] After changing a shared quantity, every document was searched for the old value **and** for the concept.

## H. Front matter and governance

- [ ] Title, version and date, roles, sponsor, funding, registration number.
- [ ] Version history: what changed and why.
- [ ] Ethics approval, consent, confidentiality, data access, and plans for publication.

## References

These are the guidelines named above, checked against CrossRef on 2026-10-02. They are not in `references.bib`, because they are not cited in the manuscript unless you add them there.

- Chan A-W, et al. SPIRIT 2025 statement: updated guideline for protocols of randomised trials. *BMJ* 2025;389:e081477. doi:10.1136/bmj-2024-081477
- Gamble C, et al. Guidelines for the content of statistical analysis plans in clinical trials. *JAMA* 2017;318(23):2337–2343. doi:10.1001/jama.2017.18556
- ICH E9(R1). Addendum on estimands and sensitivity analysis in clinical trials. 2019.
- Hopewell S, et al. CONSORT 2025 statement: updated guideline for reporting randomised trials. *BMJ* 2025;389:e081123. doi:10.1136/bmj-2024-081123
