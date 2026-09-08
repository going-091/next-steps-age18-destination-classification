# Stage 1 EDA: Age-18 Activity Outcome

**Notebook:** `notebooks/01-2_stage_1_outcome_construction_eda.ipynb`

## Purpose

Describe the distribution and class balance of the valid Stage 1 May 2009 activity outcome.

## Sample checks

| Measure | Result |
|---|---:|
| Valid Stage 1 outcome sample | 9,767 |
| Unique NSID values | 9,767 |
| Duplicate NSID values | 0 |
| Missing outcome values | 0 |
| Outcome classes | 4 |

The outcome coding and category counts matched the Stage 1 construction files.

## Class distribution

| Age-18 activity status | Participants | Percentage |
|---|---:|---:|
| Education | 5,132 | 52.54% |
| Employment | 2,831 | 28.99% |
| Apprenticeship or training | 524 | 5.37% |
| Unemployment or inactivity (NEET) | 1,280 | 13.11% |

Class-balance indicators:

- largest class: Education, 5,132
- smallest class: Apprenticeship or training, 524
- largest-to-smallest ratio: 9.79:1
- majority-class accuracy in the valid Stage 1 outcome sample: 52.54%

## Interpretation

The age-18 outcome was moderately imbalanced, with Education accounting for just over half of participants and Apprenticeship or training representing the smallest group. The approximately 9.8:1 difference between the largest and smallest classes indicates that overall accuracy alone would give disproportionate weight to the majority class.

This class structure informed the later use of class-balanced evaluation measures, particularly macro F1 and class-specific precision, recall and F1, alongside overall accuracy.
