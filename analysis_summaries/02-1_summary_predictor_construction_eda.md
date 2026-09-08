# Stage 2 EDA: Predictor Matrix

**Notebook:** `notebooks/02-1_stage_2_predictor_construction_eda.ipynb`

## Purpose

Check the structure, missingness, value distributions and predictor overlap of the 69-predictor Stage 2 matrix without loading the age-18 outcome.

## Structural checks

| Measure | Result |
|---|---:|
| Participant rows | 9,767 |
| Predictors | 69 |
| Conceptual domains reviewed | 11 |
| Domains represented in the predictor matrix | 10 |
| Missing NSID values | 0 |
| Duplicate NSID values | 0 |
| Entirely missing predictors | 0 |
| Constant predictors | 0 |
| Exact duplicate predictor pairs | 0 |
| Infinite numeric values | 0 |
| Outcome columns loaded | 0 |

The CSV import produced 65 predictors with numeric dtype and four with string dtype. These imported dtypes are not treated as the substantive measurement roles used later in preprocessing.

## Missingness and coverage

Across all 9,767 Stage 2 records:

- 5,203 participants had all 69 predictors observed.
- 8,866 had at least 65 predictors observed.
- 243 had five or fewer predictors observed.

The 243 low-coverage records all lacked a Wave 1 source record. Among the 9,524 participants with a Wave 1 source record, the number of missing predictors had:

| Statistic | Missing predictors |
|---|---:|
| Mean | 1.2203 |
| Median | 0 |
| 75th percentile | 1 |
| Maximum | 40 |

There were 143 participants with a Wave 1 source record and ten or more missing predictors. These are item-level missingness patterns rather than the broad structural absence seen in the 243 records without Wave 1 support.

## Value and overlap checks

- Numeric predictors containing infinite values: 0
- Numeric predictors containing negative values: 1 (`birth_month_position`, minimum −11)
- Numeric predictor pairs assessed with Spearman correlation: 2,080
- Pairs with |Spearman correlation| ≥ 0.80: 0
- Low-cardinality predictor pairs assessed with bias-corrected Cramér's V: 2,145
- Pairs with corrected Cramér's V ≥ 0.80: 0

The strongest observed Spearman correlation was 0.640 between `household_income_band` and `working_parent_or_guardian_count`. The strongest corrected Cramér's V was 0.717 between `ethnicity` and `non_english_home_language`. These screens were descriptive and did not automatically remove predictors.

## Result

The structural EDA checks passed. Missingness, value-range and association checks did not identify an all-missing, constant, duplicate or infinite-valued predictor requiring removal at this stage.

## Interpretation

The structural EDA checks did not identify an all-missing, constant, duplicate or infinite-valued predictor requiring removal at this stage. No pair of predictors exceeded the prespecified high-association screening threshold, so the descriptive overlap checks did not provide a basis for removing predictors.

Missingness was concentrated in a distinct group of 243 participants without a Wave 1 source record, while the remaining participants generally had substantially greater predictor coverage. These findings were carried forward to the modelling-sample construction stage rather than being resolved through deletion or imputation during EDA.
