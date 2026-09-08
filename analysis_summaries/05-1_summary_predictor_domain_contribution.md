# Stage 5.1: Predictor-Domain Contribution

**Notebook:** `notebooks/05-1_stage_5_predictor_domain_contribution.ipynb`

## Purpose

Examine how outer-validation performance changes when predefined predictor domains are omitted from the full 69-predictor specification or added separately to a common 23-predictor baseline.

MLR, RF, XGBoost and supplementary BRF use the same five outer folds as Stage 5. Within each model and outer fold, the Stage 5-selected hyperparameters and imbalance setting are held fixed.

The held-out test sample is not used.

## Analysis design

Two complementary analyses are used.

### Leave-one-domain-out omission

Each of the 10 represented domains is omitted separately from the full predictor set.

**LODO loss = full-model performance − domain-omitted performance**

A positive value indicates lower performance after the domain is removed.

### Common-baseline separate addition

The common baseline contains 23 predictors from:

- demographic background
- family socioeconomic background
- SEN, disability and health
- school and local context

Each of six remaining domains is added separately to the same baseline.

**Addition gain = augmented performance − common-baseline performance**

A positive value indicates higher performance after the domain is added.

These comparisons are conditional on the model settings and predictor context. They are not causal effects or fixed model-independent rankings of domain importance.

## Full-model reproduction

Before the domain analyses, the Stage 5 full-model outer predictions were reproduced for all 20 model × outer-fold combinations. This verifies that the Stage 5.1 fitting procedure matches the Stage 5 model specification before predictor sets are changed.

## Leave-one-domain-out results

Educational aspirations and post-16 plans produced the largest mean macro-F1 loss for RF and XGBoost and the clearest pattern across models.

| Model | Mean macro-F1 loss |
|---|---:|
| MLR | 0.0073 |
| RF | 0.0210 |
| XGBoost | 0.0224 |
| BRF | 0.0160 |

The loss was positive in all five outer folds for RF and XGBoost.

For the tree-based models, family socioeconomic background and experiences and behaviours also produced positive mean losses when omitted. Several other domains showed smaller or fold-dependent changes.

## Common-baseline separate-addition results

Educational aspirations and post-16 plans produced the largest mean macro-F1 gain for every model.

| Model | Mean macro-F1 gain |
|---|---:|
| MLR | 0.0482 |
| RF | 0.0562 |
| XGBoost | 0.0541 |
| BRF | 0.0630 |

The gain was positive in all five outer folds for every model.

Other addition results:

| Added domain | MLR | RF | XGBoost | BRF |
|---|---:|---:|---:|---:|
| School experiences and engagement | 0.0189 | 0.0261 | 0.0261 | 0.0260 |
| Psychosocial characteristics | 0.0148 | 0.0166 | 0.0166 | 0.0180 |
| Experiences and behaviours | 0.0087 | 0.0060 | 0.0095 | 0.0090 |
| Parental attitudes, support and engagement | 0.0277 | 0.0398 | 0.0355 | 0.0384 |
| Post-16 social influences and guidance | 0.0328 | 0.0344 | 0.0313 | 0.0356 |

Parental attitudes, support and engagement and post-16 social influences and guidance produced positive mean gains across all four models.

## Interpretation

LODO and separate addition answer different questions.

- LODO assesses what changes when one domain is removed while the remaining domains stay available.
- Separate addition assesses what changes when one domain is added to the same restricted baseline.

A small or negative LODO value does not show that a domain is uninformative or harmful. Information may overlap across domains. Domain sizes also differ, so the estimates are not normalised per predictor.

Fold counts are descriptive checks of consistency, not significance tests.
