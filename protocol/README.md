# Protocol

The trial protocol, one file per section, numbered in the order of the SPIRIT 2025 checklist. Drafted with the `draft-protocol` skill.

## The checklist

`spirit_2025_checklist.md` tracks every SPIRIT 2025 item: which section covers it, and whether it is done, a gap, or not applicable (with a reason). The `draft-protocol` skill builds it from the official checklist, downloaded from [consort-spirit.org](https://www.consort-spirit.org/). It is never written from memory.

## Drafts and comments

Same workflow as `manuscript/`:

- The first draft of each section is copied unchanged to `llm_originals/`.
- You edit the section file itself. Questions and instructions for Claude go inline as `XX ... XX`.

## Locking

When the protocol is final, it is locked (see `plan.md`, Stage). After that, Claude does not edit files in this folder. Changes are amendments: logged in `plan.md` with the date, what changed, why, and whether any outcome data had been seen.
