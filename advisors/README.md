# Advisors

Second opinions from readers who have not seen our reasoning: another model, or a Claude subagent with a fresh context. See `.claude/skills/second-opinion/`.

Each round is two or more files: the prompt, and one answer per reader, named with who answered.

```
sample_size_review.txt             the prompt
sample_size_review_copilot.txt     the answer from Copilot Chat
sample_size_review_subagent.txt    the answer from a Claude subagent
```

Rounds that build on each other go in a subfolder, numbered.

**To get an answer from another model:** open the prompt file, copy all of it into a model your institution allows (with training switched off), and save the reply here as `<prompt name>_<model>.txt`. Then ask Claude to read and compare the answers.

**Nothing in a prompt may contain patient data.** Read the prompt before you paste it. You are the one sending it.

Answers are never edited. They are the record. Findings you accept go into `todo.md`, pointing back to the file here.
