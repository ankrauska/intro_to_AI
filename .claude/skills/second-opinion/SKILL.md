---
name: second-opinion
description: Get an independent second opinion on a piece of research work (protocol, analysis plan, results section, limitations, patient information sheet, sample size, a claim about the literature) from a reader who has not seen our reasoning. Use when the user asks for a second opinion, a review, a critique, a fact-check, or wants to run the same question past another model. Covers how to write the prompt so the answer is an independent diagnosis rather than agreement with us.
---

# Second opinion

A second opinion is only worth having if the reader has not been told what to think. Every rule below exists to keep the reviewer's reading of the work uncontaminated by our framing.

Adapted for clinical research from the `ea` skill by Karl Rohe ([github.com/karlrohe/ea](https://github.com/karlrohe/ea)).

## Before anything else: what may leave the folder

The prompt is sent to another model. **No patient data goes in it.** No names, CPR numbers, dates of birth, case descriptions, or row-level data, even anonymized. Aggregated results, analysis code and manuscript text are fine for a model with training switched off or an institutionally approved tool.

If the work to be reviewed contains anything personal, stop and tell the user. Do not "clean it up" and send it.

## Two ways to get the opinion

Write the prompt to a file in `advisors/` first, whichever route is used. Then:

1. **Another model, by hand (preferred).** Tell the user the prompt is ready and where. They paste it into a model their institution allows (e.g. Copilot Chat logged in with an SDU account, or ChatGPT/Gemini with training switched off), and save the reply next to the prompt. A different model has different blind spots, and the user sees exactly what leaves the folder.
2. **A Claude subagent (when no other model is available).** Start a subagent and give it **only the text of the prompt file**, verbatim. Not the conversation, not your summary, not `plan.md`. Tell it to answer from the prompt alone and not to read other files in the project. Save its reply verbatim. It is the same model family as you, so say so when you report it.

The user can do both and compare. Disagreement between two readers is information.

## Files

```
advisors/
  sample_size_review.txt             ← the prompt
  sample_size_review_copilot.txt     ← an answer (suffix = who answered)
  sample_size_review_subagent.txt

  limitations/                       ← several related rounds
    01_assumption_stress.txt
    01_assumption_stress_chatgpt.txt
    02_followup.txt
```

Number files when rounds build on each other. Name them by what they ask; the answers inherit the name. Never edit an answer file. It is the record.

## Prime directive

**Lead with the work and the task. Never with our interpretation of it.**

The moment the prompt says what the work does, which problem we suspect, or what we hope to hear, the reader stops reviewing the work and starts reacting to our description of it.

## Core rules

1. **The work itself goes in the prompt.** Paste the paragraph, the table, the analysis plan, the code. "We have a sample size calculation that might be off" is not a review request.
2. **Context needed to read it: yes. Our intentions: no.** Include what a stranger needs to understand the work: the study type, the population, what the abbreviations mean, which reporting guideline applies. Leave out what we think it shows, why we chose it, and which problem we suspect. Reading context helps the reviewer see. Intent tells them what to see.
3. **Diagnosis before fixes.** Ask what is wrong, how serious it is, and what in the text shows it, before asking how to fix it. "How can I improve this?" gets plausible patches for misdiagnosed problems.
4. **Demand evidence and priority.** The reviewer quotes the sentence or number each finding is about, ranks findings by severity, and says how sure it is. Otherwise you get ten small comments and miss the one that matters.
5. **Invite disagreement.** One line is enough: *"If the most important problem is different from what the authors probably expect, say so."*

## Round types

The type of round decides what is settled, what we disclose, and which questions we ask. They are in `round-types.md`: design review, procedure critique, assumption stress, verification, source grounding, option generation, and reader test. Read it before writing a prompt.

The user names the type. If they have not, name the one you infer back to them and get it confirmed before writing. Naming it back is the check that the question was understood.

## Three modes: keep them apart

- **Independent review.** Fresh eyes. Never paste earlier answers, our own diagnosis, or a co-author's objection. This is the default.
- **Adjudication.** Two answers disagree and we want a tiebreaker. Now paste both, and ask which is better supported by the work itself.
- **Targeted probe.** A narrow check ("Is this the CONSORT item for allocation concealment?"). Use only when the question really is narrow, or as a second round after an independent review.

One prompt, one mode. A prompt that mixes review, fact-check and brainstorm gets a muddled answer.

## Don'ts

- **No yes/no questions.** "Does this look right?" and "Any problems?" invite "yes, it looks good".
- **No checklists of categories.** "Check for bias, confounding, missing data, power..." makes the reader stop at the list. Ask it to find and rank the problems itself.
- **No personas.** "Act as a senior epidemiologist" adds theatre, not signal.
- **No "be balanced" or "say what is good too".** It softens the critique. In a review, bias the reader toward finding important problems.
- **No conversation dumps.** Never paste the chat with Claude into the prompt. The reader will absorb our reasoning and repeat it.
- **No leading with the suspected problem.** "Check whether the dropout assumption is too optimistic" makes the reader hunt that and miss the wrong outcome definition two lines up. A targeted pass is a second prompt.
- **No naming the outcome you want.** Name the standard if it matters ("for submission to a BMJ-family journal", "for an ethics committee"), never the verdict.
- **No treating confidence as truth.** The answer will sound sure and is often wrong on specifics. Use it for objections and hypotheses, not verdicts. Any reference it names goes through `crossref-check` and onto the list in `todo.md` like any other.

## Before and after

**Bad: leads the witness, asks for reassurance.**
> We wrote this sample size justification for our cochlear implant trial. I'm mostly worried the 15% dropout is too optimistic. Does it look OK, and how can we improve it?
> ```<text>```

**Better: the work first, the task stated, room to disagree.**
> Below is the sample size section of a randomized trial protocol in paediatric audiology. Review it independently. Identify the most important problems, quote the sentence or number each one concerns, and rank them by how much they would change the required sample size or the trial's credibility. Do not assume the authors' choices are sound. If nothing serious is wrong, say so.
> ```<text>```

**The reverse explain.** Ask the reader first to say what they think the work is trying to do, and only then to critique it. If they misread the aim, that is unprompted evidence the text is unclear.

## Phrasings to reuse

Pick what fits. Do not string them all together.

- "Review this independently. Do not assume the authors' framing is correct."
- "Identify the most important problems first. Skip minor wording."
- "Quote the sentence or number each finding is about."
- "If the biggest problem is different from the obvious one, say so."
- "Say plainly where you are unsure. Do not present guesses as facts."
- "First say what you think this is trying to do. Then critique it."
- "What is the most dangerous assumption here?"
- "What is missing that a reviewer or ethics committee would expect?"

## After the answer

1. Read the answer in full. Read the prompt again too, to check what the reader was actually asked.
2. Report to the user: the main findings, ranked, each with whether you agree, and why, based on the work, not on the reader's confidence.
3. When two answers exist, set out where they agree and where they differ. Do not average them. The user decides.
4. Turn accepted findings into items in `todo.md`, each pointing to the answer file. A decision that comes out of it goes in `plan.md` under Decisions.

## When not to use it

- The answer is in the project already: in `plan.md`, the data, the analysis output, or a source you can open. Look there first.
- The value would come from back-and-forth. Each round is one prompt and one answer.
- The work is too large to send whole. Narrow it to the part that matters. A focused prompt beats a long one.
