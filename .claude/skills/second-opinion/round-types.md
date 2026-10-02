# Round types

The type of round decides three things nothing else decides:

- **The fence:** what the reader may take as settled, and which answers are off-limits.
- **Disclosure:** whether we say what we believe, or keep it to ourselves.
- **The question block:** what we actually ask.

Get the type wrong and the round is wasted however good the prose is. The most common way to get it wrong is to write a verification round with a design-review fence, which tells the reader the numbers are correct in a round whose whole purpose was to doubt them.

**Name the type by contrast.** Every prompt says what kind of round it is and what it is not: "This is a verification request, not a design review." Without the contrast the reader defaults to a general design review, which is the safest-sounding answer and usually not the one we need.

---

## design-review: "is this study design sound"

For a protocol, a study design, an outline of a statistical analysis plan, before anything has been run.

- **Naming sentence.** "We have a planned study design and want an independent assessment of it."
- **Fence.** Settled: the research question. Off-limits: a different research question. "Stay on whether this design can answer the question as stated."
- **Disclosure.** State the design, and separately **the reasoning we believe it rests on**, so the reader can attack the reasoning and not just the conclusion. Do not say whether we think it works.
- **Stance.** "Your job is diagnosis, not endorsement. If the design is sound, say so and state what it depends on. If it breaks, say where, and whether the break is fatal or repairable."
- **Question block.** Can the design answer the question at all. Population and selection. Comparison group. Outcome and how it is measured. Confounding and bias. Sample size and precision. Alternatives, ranked.
- **Guards against.** Being told a plan is fine because we sounded confident.

## procedure-critique: "we are about to do this"

For a concrete procedure we will carry out: an analysis plan step by step, a data cleaning procedure, a recruitment or randomization procedure, a coding manual.

- **Naming sentence.** "This is a procedure we intend to carry out. We want to know what goes wrong before we do it, not a general review of the study."
- **Fence.** Settled: the study design. Off-limits: nothing within the procedure.
- **Disclosure.** Full. Give the procedure as a numbered list of the steps we will actually take, including the interpretation at the end, which is usually where the trouble is.
- **Stance.** "If it is sound but the result would be hard to interpret, say that. It is the outcome we least want to discover afterwards."
- **Question block.** Where a step can fail or be done two ways. What a stranger following the steps would do differently from us. Whether the last step is a pre-specified analysis or a search for a result. What else would produce the same result. What to change before starting.
- **Guards against.** Running something that can only be interpreted in the direction we hoped.

## assumption-stress: "do the assumptions survive real patients"

For a limitations section, or before committing to an analysis: what has to be true for the result to mean what we say.

- **Naming sentence.** "This is about whether the study's assumptions hold in practice, not a review of the design as a whole."
- **Fence.** Settled: the design and the analysis. Off-limits: a new design, unless an assumption is fatal without one.
- **Disclosure.** List the assumptions as we understand them and ask what we have missed. Say if we are drafting a limitations section.
- **Stance.** "We would rather you find the holes than a reviewer. Diagnosis, not reassurance."
- **Question block.** For each assumption that may fail: the direction it would bias the estimate, how large the bias could plausibly be, what in the data would show it, and the assumptions ranked by likelihood times damage.
- **Guards against.** A limitations section that lists only the comfortable limitations.

## verification: "we do not trust what we already have"

For numbers, calculations and claims we have already written down: a sample size calculation, the numbers in a results section against its tables, a claim in the abstract against the results.

- **Naming sentence.** "This is a verification request. Check each statement yourself from what is given. Do not assume our statements are correct, and do not quietly correct them."
- **Fence.** Settled: **nothing.** Never write "this is correct" in a round of this type. Off-limits: replacing our calculation with one the reader prefers instead of checking ours.
- **Disclosure.** Full. State every claim to be checked, numbered. A claim that is not shown cannot be checked.
- **Stance.** "If a statement is wrong, say so and show why. If it is right only under a condition we have not stated, name the condition. If it is right, say what it relied on."
- **Question block.** One question per claim, in the order they depend on each other. Then edge cases. Then conditions we have not stated.
- **Guards against.** Carrying an error through three drafts because each draft assumed the last one had been checked.

## source-grounding: "what do the sources actually say"

For what a reporting guideline, a clinical guideline, a regulation or a cited paper actually states, and whether it covers our case.

The order is the point: first the sources, then what they state, then what that means for us. A reader who starts at the third step has answered from its own judgement, and the round is wasted.

- **Naming sentence.** "This is a request about the sources, not a design review. We want the authoritative sources first, then what they actually state, then what that implies for the case below."
- **Fence.** Settled: the description of our situation. Off-limits: answering from your own judgement without naming a source. State it bluntly: **an answer with no source is a wasted answer.**
- **Disclosure.** Full on the situation. Say what we believe the source says and label it as our reading, which may be wrong. Say where the reading came from, including a co-author or an earlier round, so a wrong attribution is caught rather than inherited.
- **Stance.** "Name the sources before you use them. For each, say what it actually states, including its conditions and scope, rather than what it is commonly cited for. Then say whether our case falls inside those conditions. If no source covers our case, say so rather than stretching one. Where you are unsure whether a source says what we need, say that."
- **Question block.** The sources come first. Then what each states and under what conditions. Whether our case is inside them. What none of them covers. What we should write.
- **Guards against.** An opinion arriving with the authority of a guideline. And a citation attached to a claim the cited paper does not make: the right authors, the wrong paper. Every source the answer names goes through `crossref-check`.

## option-generation: "what have we not thought of"

For alternatives: outcome measures, recruitment routes, comparison groups, ways to present a result.

- **Naming sentence.** "This prompt is NOT asking you to evaluate the options below. We want options we have not thought of."
- **Fence.** List what we already have, precisely, and state bluntly: **"A response that proposes any of these, or a cosmetic variant of one, is a wasted response."**
- **Disclosure.** Full on what we have, and on what we control and what we cannot change (the population, the clinic, the budget, the registry data available), because that is what makes new options possible.
- **Stance.** Each option concrete enough to act on and to criticize.
- **Question block.** Not questions. A list of the things we control, one per numbered block, each asking what option it opens.
- **Guards against.** Getting our own three ideas back in new words.

## reader-test: "does it say what we think it says"

For text a particular reader must understand without us: an abstract, a plain-language summary, a patient information sheet, a consent form, a cover letter.

- **Naming sentence.** "This is a reading test, not a review. Read the text below as [the intended reader] would, and tell us what it says."
- **Fence.** Settled: nothing. Off-limits: rewriting the text. That comes later.
- **Disclosure.** **None about the content.** Do not say what the main finding is or what the participant is agreeing to. That is what we are testing. Say only who the intended reader is.
- **Stance.** "Answer only from the text. Where the text does not tell you, say so rather than guessing."
- **Question block.** What is the main point. What is being asked of the reader. What are the risks or limitations, as the reader would understand them. Which words or sentences a reader of this kind would not understand. Compare the answers with what we meant: every difference is a finding.
- **Guards against.** A text that is clear only to the people who wrote it.

---

## Choosing between neighbours

- **Design review or procedure critique?** A plan we have not committed to is a design review. Steps we are about to carry out are a procedure critique.
- **Verification or source grounding?** If we could settle it ourselves with a calculation or by checking our own tables, it is verification. If we have to read something first, it is source grounding. A claim we made *by citing something* is source grounding, because the thing to check is the citation.
- **Design review or assumption stress?** Doubting the plan is a design review. Doubting whether the world behaves as the plan assumes is assumption stress.
- **Reader test or review?** If the question is "is this good", it is a review. If the question is "would they understand it", it is a reader test, and nothing about our intent goes in the prompt.
