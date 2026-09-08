# Stage 8-1: XGBoost Raw SHAP Interpretation

**Notebook:** `notebooks/08-1_stage_8_xgboost_raw_shap_interpretation.ipynb`

## Purpose

Provide supplementary interpretation of the fixed XGBoost model using TreeSHAP on the raw multiclass-output scale.

The analysis uses the fixed training/test split, 69 pre-transition predictors and frozen Stage 6 XGBoost specification. SHAP values for transformed features are grouped back to the 69 original predictors before destination-specific ranking.

## Analysis structure

- Training participants: 7,619
- Held-out test participants: 1,905
- Original predictors: 69
- Transformed XGBoost features: 118
- Training-background participants: 500

The fixed XGBoost model reproduced the saved Stage 6 held-out predictions and probabilities before interpretation.

## Raw TreeSHAP

TreeSHAP was calculated for all 1,905 held-out participants across 118 transformed features and four destination outputs.

The full SHAP array had shape:

`(1,905, 118, 4)`

Signed SHAP values for transformed features belonging to the same original predictor were then summed.

The grouped SHAP array had shape:

`(1,905, 69, 4)`

Mean absolute grouped raw SHAP values were calculated separately for each destination.

## Destination-specific XGBoost attribution

### Education

| Rank | Predictor | Mean absolute raw SHAP |
|---:|---|---:|
| 1 | `higher_education_application_likelihood` | 0.328887 |
| 2 | `parental_higher_education_expectation_pretransition` | 0.147042 |
| 3 | `expected_post16_route` | 0.107984 |
| 4 | `parental_training_apprenticeship_discussion_profile_pretransition` | 0.073545 |
| 5 | `ethnicity` | 0.073045 |
| 6 | `homework_evenings_pretransition` | 0.072065 |

### Employment

| Rank | Predictor | Mean absolute raw SHAP |
|---:|---|---:|
| 1 | `alcohol_use_frequency_pretransition` | 0.092694 |
| 2 | `government_office_region_pretransition` | 0.084511 |
| 3 | `ethnicity` | 0.080173 |
| 4 | `higher_education_application_likelihood` | 0.076317 |
| 5 | `non_english_home_language` | 0.064015 |
| 6 | `sex` | 0.057393 |

### Apprenticeship or training

| Rank | Predictor | Mean absolute raw SHAP |
|---:|---|---:|
| 1 | `parental_higher_education_expectation_pretransition` | 0.213574 |
| 2 | `highest_parental_qualification_code` | 0.194370 |
| 3 | `ethnicity` | 0.156569 |
| 4 | `academic_self_concept_score` | 0.153036 |
| 5 | `school_attitude_score` | 0.123752 |
| 6 | `sex` | 0.117067 |

### Unemployment or inactivity (NEET)

| Rank | Predictor | Mean absolute raw SHAP |
|---:|---|---:|
| 1 | `working_parent_or_guardian_count` | 0.111195 |
| 2 | `school_attitude_score` | 0.094514 |
| 3 | `highest_parental_qualification_code` | 0.069992 |
| 4 | `birth_month_position` | 0.052962 |
| 5 | `parents_evening_attendance_pretransition` | 0.051753 |
| 6 | `young_person_general_health` | 0.051178 |

The leading predictor set differed across the four destination outputs.

## Validation checks

The final audit confirmed that:

- XGBoost reproduced the Stage 6 predicted classes and probabilities;
- the raw TreeSHAP technical and full-sample checks passed;
- grouped SHAP values had the expected `(1,905, 69, 4)` shape; and
- each destination had six leading predictors.

All final audit checks passed.