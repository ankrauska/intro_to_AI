---
name: crossref-check
description: Check references against CrossRef, the DOI registry for scholarly publications. Use whenever a reference is suggested, added to references.bib, or cited in the manuscript, and when asked to check the bibliography. Confirms the reference exists and that its details match; anything without a match goes on the todo.md list for human review.
---

# CrossRef check

A model can produce a reference that looks right and does not exist, or that exists with a different author, year or journal. This check confirms that each reference matches a real record in CrossRef. It does **not** confirm that the source says what the manuscript claims. Only a person who has read the source can do that.

## When to run it

- Every time you suggest a reference, before it goes on the list in `todo.md`.
- Before an entry is added to `references.bib`.
- When asked to check the bibliography: run it on every entry in `references.bib`.

## How to look up a reference

CrossRef's public API needs no key. Use `curl` and read the JSON.

**With a DOI**, look it up directly:

```bash
curl -s "https://api.crossref.org/works/10.2307/2529310"
```

A 404 means CrossRef has no record of that DOI. A wrong or invented DOI is a **no match**, even if the paper turns out to exist under another DOI. Report both.

**Without a DOI**, search with the citation as written (authors, year, title, journal):

```bash
curl -s -G "https://api.crossref.org/works" --data-urlencode "query.bibliographic=Landis Koch 1977 The measurement of observer agreement for categorical data Biometrics" --data-urlencode "rows=5" --data-urlencode "select=DOI,title,author,issued,container-title,volume,page,type"
```

Keep each lookup on one line, starting exactly as above. The project's settings let these two forms run without asking the user each time.

Keep to one request at a time. Do not loop over many references in parallel.

## What counts as a match

The search always returns something, even for a reference that does not exist. **Never accept a result because it came first or has a high score.** Compare the fields:

| Field | Must agree |
| :--- | :--- |
| First author's surname | Yes |
| Year | Yes. One year off is acceptable only for online-first versus print, and you say so. |
| Title | Yes, apart from capitalization and punctuation. |
| Journal | Yes, allowing for abbreviations. |

- **Match:** all four agree. Record the DOI.
- **Partial match:** a real record exists, but one field differs (wrong year, wrong journal, a different first author). Treat it as no match and say which field differs. This is the common failure: a real paper, cited wrongly.
- **No match:** nothing in the results agrees on author, title and year.

Some legitimate sources are not in CrossRef: many books, guidelines, reports, theses, websites and some older or regional journals. They are still a **no match** here. Say that the source type may explain it, and leave the judgment to a person.

## What to record

**In `todo.md`**, under "References to verify", one row per reference, with the CrossRef column filled in:

- `match (10.xxxx/xxxx)`
- `**NO MATCH**: <one line: nothing found / DOI does not resolve / year differs: CrossRef says 2019 / not a journal article>`

A row with **NO MATCH** needs a person to find the source by hand before anything else happens to it. Never fix a no match yourself by swapping in the closest result.

**In `references.bib`**, only for entries that are already there, add or update the CrossRef line above the entry:

```
% CROSSREF 2026-10-02: match, doi 10.2307/2529310
% CHECKED <date> <initials>: <design, n, and what the source actually says>
@article{landis1977, ...}
```

The `CROSSREF` line is yours. The `CHECKED` line is the person's. Never write a `CHECKED` line.

## Report

End with a short summary: how many references were checked, how many matched, and a list of each partial match or no match with its reason.
