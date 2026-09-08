# Stage 5: Nested Model Development and Comparison

**Notebook:** `notebooks/05-0_stage_5_model_development.ipynb`

## Purpose

Develop and compare multinomial logistic regression (MLR), random forest (RF), XGBoost and supplementary Balanced Random Forest (BRF) using the fixed Stage 4 training sample and nested cross-validation design.

The held-out test sample is not used in this stage.

## Development design

- Training participants: 7,619
- Predictors: 69
- Outer folds: 5
- Inner folds within each outer-training sample: 4
- Primary model-selection criterion: macro F1
- Core models: MLR, RF and XGBoost
- Supplementary model: BRF

Preprocessing is fitted within each training fold. Numeric and ordinal predictors use median imputation; binary and nominal predictors use most-frequent imputation and one-hot encoding. Numeric and ordinal predictors are standardised for MLR only.

MLR, RF and XGBoost compare unweighted and balanced fitting. BRF uses internal balanced sampling.

## Outer-fold development performance

Headline development performance is the mean and standard deviation of metrics calculated separately within the five outer-validation folds.

| Model | Macro F1 mean | Macro F1 SD | Balanced accuracy mean |
|---|---:|---:|---:|
| Majority-class dummy | 0.1710 | 0.0001 | 0.2500 |
| MLR | 0.3943 | 0.0100 | 0.4346 |
| RF | 0.4517 | 0.0230 | 0.4484 |
| XGBoost | 0.4425 | 0.0148 | 0.4381 |
| BRF | 0.4454 | 0.0202 | 0.4538 |

RF achieved the highest mean outer-fold macro F1. BRF had the highest mean balanced accuracy.

## Weighting-mode comparison

| Model | Weighting mode | Macro F1 mean | Macro F1 SD |
|---|---|---:|---:|
| MLR | None | 0.3902 | 0.0057 |
| MLR | Balanced | 0.3943 | 0.0100 |
| RF | None | 0.3757 | 0.0116 |
| RF | Balanced | 0.4517 | 0.0230 |
| XGBoost | None | 0.3870 | 0.0144 |
| XGBoost | Balanced | 0.4425 | 0.0148 |
| BRF | Internal balanced sampling | 0.4454 | 0.0202 |

Balanced fitting improved mean macro F1 for MLR, RF and XGBoost, with the largest changes for RF and XGBoost.

## Class-specific performance

Mean F1 across the five outer-validation folds:

| Model | Education | Employment | Apprenticeship or training | Unemployment or inactivity (NEET) |
|---|---:|---:|---:|---:|
| MLR | 0.7029 | 0.3513 | 0.2141 | 0.3088 |
| RF | 0.7358 | 0.4547 | 0.2703 | 0.3458 |
| XGBoost | 0.7219 | 0.4770 | 0.2482 | 0.3228 |
| BRF | 0.7262 | 0.4381 | 0.2675 | 0.3496 |

Performance differed substantially across outcome classes. Education had the highest F1 for every fitted model, while Apprenticeship or training had the lowest.

## Development-output checks

The completed Stage 5 results contain one outer-validation prediction per training participant for each fitted model. The final audit checks model coverage, outer-fold coverage, candidate-search coverage, class coverage and separation from the held-out test sample.

## Interpretation

During model development, RF had the highest mean macro F1, although RF, XGBoost and BRF produced fairly similar results. Performance differed much more clearly by destination: Education was classified most successfully, while Apprenticeship or training remained the most difficult class.

Balanced fitting improved macro F1 particularly for RF and XGBoost. These results describe performance during model development; the final model comparison is based on the held-out test set in Stage 6.