# Stage 1: Age-18 Activity Outcome Construction

**Notebook:** `notebooks/01-0_stage_1_outcome_construction.ipynb`

## Purpose

Construct the four-category May 2009 age-18 activity outcome from the Next Steps monthly activity file.

## Source and outcome definition

The selected source was `lsype_main_activity_w4-7_nov2011_suppressed.dta`. The endpoint variable was `W7FinAct53_B11`, labelled `DV: Main Activity May 2009 - Bulletin 11 (Main Activity at 18)`.

The four retained source categories were recoded as:

| Source code | Source label | Analytical label |
|---:|---|---|
| 1 | Education | Education |
| 4 | Employed | Employment |
| 5 | Apprenticeship/training | Apprenticeship or training |
| 6 | Unemployed/Inactive (NEET) | Unemployment or inactivity (NEET) |

Source code `-94` was labelled `Insufficient information` and was excluded from the outcome dataset.

## Results

| Measure | Result |
|---|---:|
| Source participants | 11,811 |
| Insufficient information | 2,044 (17.31%) |
| Missing endpoint values | 0 |
| Valid Stage 1 outcome sample | 9,767 (82.69%) |
| Duplicate NSID values in outcome dataset | 0 |
| Missing values in outcome dataset | 0 |

Outcome distribution:

| Age-18 activity status | Participants | Percentage |
|---|---:|---:|
| Education | 5,132 | 52.54% |
| Employment | 2,831 | 28.99% |
| Apprenticeship or training | 524 | 5.37% |
| Unemployment or inactivity (NEET) | 1,280 | 13.11% |

## Validation

The source file contained one record per participant. Source codes and labels were checked for one-to-one correspondence. The 2,044 excluded records corresponded exactly to the records labelled `Insufficient information`; no participant with one of the four retained activity categories was excluded.

Saved files were reloaded and compared with the in-memory objects.

## Interpretation

The outcome-construction stage produced a complete four-category age-18 activity outcome for 9,767 participants. All records with one of the four defined activity statuses were retained, while exclusions were limited to records coded as having insufficient information.

This fixed outcome definition is used consistently in the subsequent descriptive and modelling stages. Differences in class size are examined separately in the Stage 1 outcome EDA.

## Data access and disclosure

The Next Steps data used in this project are safeguarded data. Participant-level source data, derived datasets, identifiers and individual-level analytical outputs are retained locally and are not redistributed through this repository. The repository contains code, documentation and disclosure-safe aggregate outputs only.