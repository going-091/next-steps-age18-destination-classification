# Stage 8-2: RF–XGBoost Probability-SHAP Comparison

**Notebook:** `notebooks/08-2_stage_8_rf_xgboost_probability_shap_comparison.ipynb`

## Purpose

Compare RF and XGBoost attribution patterns using the same model-agnostic SHAP procedure on predicted probabilities.

Both models are evaluated with the same held-out cases, transformed predictors and 100-participant training background.

## Analysis structure

- Training participants: 7,619
- Held-out test participants: 1,905
- Predictors: 69
- Shared training-background participants: 100
- Transformed features: 118
- Probability outputs: 4

Both fixed models reproduced the saved Stage 6 held-out predictions and probabilities before interpretation.

## Probability-scale SHAP

Permutation SHAP was applied to each model's predicted probabilities using the same training background.

The SHAP arrays had shape:

- RF: `(1,905, 118, 4)`
- XGBoost: `(1,905, 118, 4)`

Signed SHAP values for transformed features belonging to the same predictor were summed to the 69 original predictors.

The grouped arrays had shape:

- RF: `(1,905, 69, 4)`
- XGBoost: `(1,905, 69, 4)`

Predictor rankings were calculated separately for each destination and model.

## Destination-specific top-six predictors

### Education

| Rank | RF | RF mean |SHAP| | XGBoost | XGBoost mean |SHAP| |
|---:|---|---:|---|---:|
| 1 | `higher_education_application_likelihood` | 0.053069 | `higher_education_application_likelihood` | 0.070461 |
| 2 | `parental_higher_education_expectation_pretransition` | 0.032884 | `parental_higher_education_expectation_pretransition` | 0.037279 |
| 3 | `ethnicity` | 0.023008 | `ethnicity` | 0.024126 |
| 4 | `expected_post16_route` | 0.018385 | `alcohol_use_frequency_pretransition` | 0.022132 |
| 5 | `alcohol_use_frequency_pretransition` | 0.015407 | `homework_evenings_pretransition` | 0.020979 |
| 6 | `academic_self_concept_score` | 0.014899 | `expected_post16_route` | 0.019499 |

Five of the six leading predictors were shared between RF and XGBoost.

### Employment

| Rank | RF | RF mean |SHAP| | XGBoost | XGBoost mean |SHAP| |
|---:|---|---:|---|---:|
| 1 | `higher_education_application_likelihood` | 0.025070 | `higher_education_application_likelihood` | 0.041646 |
| 2 | `ethnicity` | 0.020138 | `alcohol_use_frequency_pretransition` | 0.025561 |
| 3 | `parental_higher_education_expectation_pretransition` | 0.015362 | `government_office_region_pretransition` | 0.021326 |
| 4 | `alcohol_use_frequency_pretransition` | 0.013900 | `ethnicity` | 0.020536 |
| 5 | `expected_post16_route` | 0.007805 | `sex` | 0.016191 |
| 6 | `highest_parental_qualification_code` | 0.005663 | `parental_higher_education_expectation_pretransition` | 0.016065 |

Four of the six leading predictors were shared.

### Apprenticeship or training

| Rank | RF | RF mean |SHAP| | XGBoost | XGBoost mean |SHAP| |
|---:|---|---:|---|---:|
| 1 | `higher_education_application_likelihood` | 0.017596 | `parental_higher_education_expectation_pretransition` | 0.019025 |
| 2 | `parental_higher_education_expectation_pretransition` | 0.014187 | `highest_parental_qualification_code` | 0.018816 |
| 3 | `expected_post16_route` | 0.011722 | `academic_self_concept_score` | 0.014596 |
| 4 | `parental_training_apprenticeship_discussion_profile_pretransition` | 0.010413 | `higher_education_application_likelihood` | 0.014195 |
| 5 | `ethnicity` | 0.008437 | `sex` | 0.013906 |
| 6 | `apprenticeship_guidance_profile_pretransition` | 0.007973 | `ethnicity` | 0.013465 |

Three of the six leading predictors were shared.

### Unemployment or inactivity (NEET)

| Rank | RF | RF mean |SHAP| | XGBoost | XGBoost mean |SHAP| |
|---:|---|---:|---|---:|
| 1 | `higher_education_application_likelihood` | 0.012594 | `working_parent_or_guardian_count` | 0.020716 |
| 2 | `school_attitude_score` | 0.011682 | `school_attitude_score` | 0.019798 |
| 3 | `working_parent_or_guardian_count` | 0.008505 | `higher_education_application_likelihood` | 0.016400 |
| 4 | `homework_evenings_pretransition` | 0.007456 | `highest_parental_qualification_code` | 0.014363 |
| 5 | `highest_parental_qualification_code` | 0.006663 | `government_office_region_pretransition` | 0.012265 |
| 6 | `ethnicity` | 0.006268 | `ethnicity` | 0.011073 |

Five of the six leading predictors were shared.

## RF–XGBoost rank agreement

Agreement across all 69 predictor rankings was summarised using Spearman's rho and overlap among the six highest-ranked predictors.

| Destination | Spearman rho | Shared top six |
|---|---:|---:|
| Education | 0.875667 | 5 |
| Employment | 0.892656 | 4 |
| Apprenticeship or training | 0.831385 | 3 |
| Unemployment or inactivity (NEET) | 0.865619 | 5 |

Rank agreement was highest for Employment and lowest for Apprenticeship or training. Top-six overlap ranged from three to five predictors.

## Validation checks

The final audit confirmed that:

- RF and XGBoost reproduced the Stage 6 outputs;
- the same 100-participant training background was used for both models;
- probability-scale SHAP checks passed for both models;
- both models were aggregated to 69 predictors; and
- all four destination outputs were compared.

All final checks passed.