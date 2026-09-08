# Stage 3: Modelling Dataset Construction

**Notebook:** `notebooks/03_stage_3_modelling_dataset_construction.ipynb`

## Purpose

Combine the age-18 activity outcome with the 69-predictor matrix by `NSID` and define the final modelling sample from predictor-source availability.

No imputation, encoding, resampling or model fitting is performed in this stage.

## Merge checks

| Measure | Result |
|---|---:|
| Outcome records | 9,767 |
| Predictor records | 9,767 |
| Common NSID values | 9,767 |
| Outcome-only NSID values | 0 |
| Predictor-only NSID values | 0 |
| Predictors | 69 |
| Outcome values preserved after merge | True |
| Predictor values preserved after merge | True |

After removal of the merge indicator, the matched dataset contained 9,767 rows and 72 columns: `NSID`, two outcome columns and 69 predictors.

## Modelling-sample definition

The sample-support file identified 243 participants without a Wave 1 source record. For this group, only one to four of the 69 predictors were observed, and 65 predictors were missing for every participant.

Eligibility was therefore defined from the Wave 1 source-record indicator rather than from complete-case status or model performance.

| Sample step | Participants |
|---|---:|
| Matched outcome and predictor sample | 9,767 |
| Excluded without a Wave 1 source record | 243 |
| Final modelling sample | 9,524 |

Among retained participants, 29 to 69 predictors were observed. Item-level missing predictor values were retained for later preprocessing.

## Final outcome composition

| Age-18 activity status | Participants | Percentage |
|---|---:|---:|
| Education | 4,952 | 51.99% |
| Employment | 2,801 | 29.41% |
| Apprenticeship or training | 520 | 5.46% |
| Unemployment or inactivity (NEET) | 1,251 | 13.14% |
| **Total** | **9,524** | **100.00%** |

All four activity-status categories remain in the final modelling sample.

## Interpretation

Stage 3 defined the modelling sample from source-record availability rather than complete-case status or model performance. The 243 participants without a Wave 1 source record were excluded because most predictors were structurally unavailable for this group, leaving 9,524 participants for modelling.

Item-level missing predictor values among retained participants were preserved for later preprocessing. The resulting modelling sample retained all four age-18 destination classes and formed the fixed sample used for subsequent data partitioning and model development.