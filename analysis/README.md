# Analysis

Scripts behind every number in the manuscript. Output goes to `output/`, and the manuscript cites numbers only from there.

## Conventions

- **Numbered by run order.** `01_clean.R`, `02_descriptives.R`, `03_primary.R`, ... Run them in order. Each script reads only from `../data/` or from `output/`.
- **Checks are prefixed `chk_`.** Supporting checks that no table or figure in the manuscript cites.
- **Fixed seed.** Any script that uses random numbers sets the seed below at the top.
- **Output is written, not printed.** Every number the manuscript uses is saved to a file in `output/` (CSV for tables, PNG or PDF for figures).
- **Replaced scripts** move to `superseded/`. They are not deleted.
- **Never write to `../data/`.**

## Requirements

R, unless the project decides otherwise. Install it from [cran.r-project.org](https://cran.r-project.org).

<!-- Version and packages, e.g. R 4.5.0, tidyverse 2.0.0. -->

## Seed

<!-- e.g. 20261001 -->

## Run order

| Script | Produces | Used in |
| :--- | :--- | :--- |
| | | |

## Conventions worth knowing

<!-- Anything that would trip up someone rerunning this: how missing values are coded, which cases are excluded and why. -->
