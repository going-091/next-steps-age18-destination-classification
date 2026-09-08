# Stage 8: Individual-Predictor Interpretation

**Notebook:** `notebooks/08-0_stage_8_individual_predictor_interpretation.ipynb`

## Purpose

Interpret the fixed MLR and RF models after final held-out evaluation.

MLR is examined through class-specific coefficients and pairwise class contrasts on the multinomial-logit scale. RF is examined using probability-scale TreeSHAP.

## Analysis structure

- Modelling sample: 9,524
- Training sample: 7,619
- Held-out test sample: 1,905
- Original predictors: 69
- RF transformed features: 118
- Outcome classes: Education, Employment, Apprenticeship or training, and Unemployment or inactivity (NEET)

The fixed MLR and RF specifications were refitted on the training sample. Both models reproduced the saved Stage 6 held-out predictions and probabilities before interpretation.

## MLR interpretation

MLR coefficients were obtained for the transformed predictors across the four destination classes. Pairwise class contrasts were then calculated for each transformed feature.

The MLR interpretation is kept on the multinomial-logit scale:

- coefficient magnitude is not used as a global ranking of predictors;
- coefficient signs are not interpreted as direct changes in predicted probability; and
- pairwise class contrasts are used to examine how the same predictor contributes differently across fitted class scores.

For focused reporting, MLR coefficients and class contrasts were retained for the same original predictors identified in the RF top-six destination-specific sets.

## RF probability TreeSHAP

A reproducible background sample of 500 training participants was used for the RF probability-scale TreeSHAP analysis.

TreeSHAP was calculated for all 1,905 held-out participants across 118 transformed features and four destination outputs:

`(1,905, 118, 4)`

The RF TreeSHAP technical and probability reconstruction checks passed.

## Grouping to original predictors

SHAP values for encoded features belonging to the same original predictor were summed before calculating mean absolute grouped SHAP values.

The resulting grouped array had shape:

`(1,905, 69, 4)`

Predictors were then ranked separately for each destination output.

## Overall RF attribution

Averaging absolute grouped SHAP values across held-out participants and the four destination outputs produced the following leading RF predictors:

| Rank | Predictor | Mean absolute SHAP |
|---:|---|---:|
| 1 | Higher-education application likelihood | 0.027092 |
| 2 | Parental higher-education expectation | 0.015734 |
| 3 | Ethnicity | 0.013823 |
| 4 | Expected post-16 route | 0.010447 |
| 5 | Alcohol-use frequency | 0.009232 |
| 6 | School attitude score | 0.008194 |
| 7 | Homework evenings | 0.007954 |
| 8 | Highest parental qualification | 0.007352 |
| 9 | Academic self-concept score | 0.007023 |
| 10 | Parental training/apprenticeship discussion | 0.005895 |
| 11 | Apprenticeship guidance profile | 0.005511 |
| 12 | Working-parent or guardian count | 0.005086 |

Higher-education application likelihood had the largest mean absolute RF attribution overall.

## Destination-specific RF attribution

Higher-education application likelihood ranked first for all four destination outputs, while the remaining leading predictors differed across classes.

### Education

| Rank | Predictor | Mean absolute SHAP |
|---:|---|---:|
| 1 | Higher-education application likelihood | 0.053326 |
| 2 | Parental higher-education expectation | 0.030716 |
| 3 | Ethnicity | 0.022000 |
| 4 | Expected post-16 route | 0.018409 |
| 5 | Homework evenings | 0.014812 |
| 6 | Alcohol-use frequency | 0.014602 |

### Employment

| Rank | Predictor | Mean absolute SHAP |
|---:|---|---:|
| 1 | Higher-education application likelihood | 0.024028 |
| 2 | Ethnicity | 0.018607 |
| 3 | Parental higher-education expectation | 0.013975 |
| 4 | Alcohol-use frequency | 0.013354 |
| 5 | Expected post-16 route | 0.007876 |
| 6 | Working-parent or guardian count | 0.006339 |

### Apprenticeship or training

| Rank | Predictor | Mean absolute SHAP |
|---:|---|---:|
| 1 | Higher-education application likelihood | 0.016681 |
| 2 | Parental higher-education expectation | 0.013007 |
| 3 | Expected post-16 route | 0.011199 |
| 4 | Parental training/apprenticeship discussion | 0.009238 |
| 5 | Ethnicity | 0.008654 |
| 6 | Apprenticeship guidance profile | 0.007869 |

### Unemployment or inactivity (NEET)

| Rank | Predictor | Mean absolute SHAP |
|---:|---|---:|
| 1 | Higher-education application likelihood | 0.014334 |
| 2 | School attitude score | 0.011681 |
| 3 | Working-parent or guardian count | 0.009481 |
| 4 | Homework evenings | 0.007423 |
| 5 | Highest parental qualification | 0.006731 |
| 6 | Housing tenure | 0.006074 |

Across the four outputs, the top-six sets contained 12 distinct original predictors.

## Predictor domains represented in the top-six sets

The destination-specific top-six predictors came from several predictor domains, including:

- educational aspirations and post-16 plans;
- parental attitudes, support and engagement;
- post-16 social influences and guidance;
- demographic background;
- school experiences and engagement;
- experiences and behaviours; and
- family socioeconomic background.

The pattern differed by destination rather than reducing to one common set of predictors.

## Direction and shape

Mean absolute SHAP values were used for attribution magnitude. Signed grouped SHAP values were examined separately for direction.

For numeric and ordinal predictors, value-versus-SHAP plots were examined for the relevant destination-specific top-six predictors. Categorical predictors were summarised by observed category using the count, mean, median and standard deviation of signed SHAP values.

These analyses describe the fitted RF prediction function.

## Focused MLR–RF interpretation

The six highest-ranked RF predictors for each destination define the focused reporting set. MLR coefficients and pairwise class contrasts were examined for the same original predictors.

RF SHAP values and MLR coefficients are on different scales and are interpreted separately.

## Validation checks

The Stage 8 audit confirmed that:

- MLR and RF reproduced the Stage 6 predictions and probabilities;
- the RF probability TreeSHAP technical check passed;
- the full-sample probability reconstruction check passed;
- all 69 original predictors were represented in the RF feature map;
- grouped RF SHAP contained all four destination outputs; and
- each destination had six detailed RF predictors.

All Stage 8 audit checks passed, and the notebook completed without execution errors.

## Interpretation

MLR coefficients and class contrasts are interpreted on the multinomial-logit scale, while RF SHAP values are interpreted on the predicted-probability scale.