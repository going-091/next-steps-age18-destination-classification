# Stage 4: Modelling Design and Data Partitioning

**Notebook:** `notebooks/04_stage_4_modelling_design_and_data_partitioning.ipynb`

## Purpose

Define the modelling design before model fitting, including the held-out test partition, nested cross-validation folds, preprocessing roles, model-search specifications, evaluation measures and predictor-domain contribution analyses.

No model is fitted in this stage.

## Modelling sample

The Stage 3 final modelling dataset contains 9,524 participants and 69 predictors.

Outcome composition:

| Age-18 activity status | Participants |
|---|---:|
| Education | 4,952 |
| Employment | 2,801 |
| Apprenticeship or training | 520 |
| Unemployment or inactivity (NEET) | 1,251 |

All four outcome categories are represented.

## Predictor preprocessing roles

The 69 predictors are assigned to one preprocessing route each.

| Measurement role | Predictors |
|---|---:|
| Numeric | 11 |
| Ordinal | 27 |
| Binary | 21 |
| Nominal | 10 |
| **Total** | **69** |

Preprocessing rules:

- Numeric and ordinal predictors: median imputation.
- Binary and nominal predictors: most-frequent imputation and one-hot encoding.
- Numeric and ordinal predictors are standardised for multinomial logistic regression.
- Tree-based models are not scaled.

Preprocessing parameters are estimated from training data only.

## Held-out test partition

A participant-level stratified 80:20 split is used.

| Sample | Participants |
|---|---:|
| Training | 7,619 |
| Held-out test | 1,905 |

Class distribution:

| Sample | Education | Employment | Apprenticeship or training | Unemployment or inactivity (NEET) |
|---|---:|---:|---:|---:|
| Training | 3,961 | 2,241 | 416 | 1,001 |
| Test | 991 | 560 | 104 | 250 |

The held-out test sample is not used for preprocessing-parameter estimation, hyperparameter selection, imbalance-option selection or predictor-domain contribution analysis.

## Nested cross-validation

Model development uses five outer folds. Four inner folds are constructed separately within each outer-training sample.

- Inner folds select hyperparameters and imbalance handling.
- Outer validation folds estimate development performance.
- Every outer and inner validation fold contains all four outcome classes.

Outer-fold sizes are 1,524, 1,524, 1,524, 1,524 and 1,523 participants.

## Model-search design

The core model families are multinomial logistic regression, random forest and XGBoost. Balanced Random Forest is supplementary.

| Model | Search design |
|---|---|
| Multinomial logistic regression | Exhaustive grid over 9 `C` values |
| Random forest | 60 fixed-seed structural configurations |
| XGBoost | 60 fixed-seed configurations across 12 learning-rate / boosting-round regimes |
| Balanced Random Forest | Same 60 structural configurations as random forest |

Macro F1 is the single hyperparameter-selection criterion.

### Imbalance handling

- Multinomial logistic regression: unweighted and balanced class weighting.
- Random forest: unweighted and balanced class weighting.
- XGBoost: unweighted and balanced sample weighting calculated within the training fit.
- Balanced Random Forest: internal balanced sampling without additional class weighting.

No resampling is applied before data partitioning or cross-validation.

## Evaluation specification

Primary selection measure:

- Macro F1

Supporting overall measures:

- Balanced accuracy
- Matthews correlation coefficient
- Accuracy
- Weighted F1

Class-specific measures:

- Precision
- Recall
- F1
- Support

Diagnostics include confusion-matrix counts, row-normalised confusion matrices, observed and predicted class distributions, and a majority-class dummy baseline.

## Predictor-domain contribution design

Two analyses are specified for the training sample using the same outer folds as model development.

### Leave-one-domain-out omission

Each of the 10 represented predictor domains is omitted in turn from the full 69-predictor specification. Performance is compared on the same outer-validation participants with the selected model specification held fixed within each outer fold.

### Common-baseline separate addition

A common 23-predictor baseline contains:

- demographic background
- family socioeconomic background
- SEN, disability and health
- school and local context

Each of the six remaining represented domains is then added separately to this same baseline.

Macro F1 is the primary performance-change measure; balanced accuracy and class-specific recall and F1 are supporting measures.

## Held-out evaluation rule

For final evaluation, each model family is tuned on the complete training sample using the fixed search design and macro-F1 criterion. The selected configuration is then fitted to the complete training sample and evaluated once on the held-out test sample.

The evaluation design includes 5,000 paired stratified bootstrap resamples of held-out predictions for uncertainty estimates and paired model comparisons.

## Design audit

The Stage 4 audit confirms:

- final modelling sample: 9,524 participants
- 69 predictors represented once
- four outcome classes present
- no overlap between training and test identifiers
- training sample: 7,619 participants
- test sample: 1,905 participants
- five outer folds
- four inner folds within every outer-training sample
- all validation folds contain all four classes
- macro F1 is the single selection metric
- core models are MLR, RF and XGBoost
- Balanced Random Forest is supplementary
- 10 represented domains are specified for domain omission
- one common baseline and six separate domain additions are specified

## Interpretation

Stage 4 established the fixed analytical framework used in all subsequent model development and evaluation. By separating model selection from final testing and defining the evaluation criteria in advance, it provided a consistent basis for comparing the core and supplementary models.