# Stage 2: Predictor Construction

**Notebook:** `notebooks/02-0_stage_2_predictor_construction.ipynb`

## Purpose

Construct the pre-transition predictor matrix and document predictor provenance, coding, timing and domain assignment before modelling.

The age-18 outcome is not used to select predictors. The Stage 1 file contributes the participant identifier roster only.

## Predictor specification

The final matrix contains 69 predictors. Eleven conceptual domains were reviewed and ten contain retained predictors.

| Predictor domain | Predictors |
|---|---:|
| Demographic background | 5 |
| Family socioeconomic background | 7 |
| Prior attainment | 0 |
| SEN, disability and health | 8 |
| Educational aspirations and post-16 plans | 2 |
| School experiences and engagement | 9 |
| Psychosocial characteristics | 2 |
| Experiences and behaviours | 7 |
| Parental attitudes, support and engagement | 16 |
| Post-16 social influences and guidance | 10 |
| School and local context | 3 |
| **Total** | **69** |

No suitable direct prior-attainment measure was retained.

## Predictor-matrix results

| Measure | Result |
|---|---:|
| Participant rows | 9,767 |
| Predictors | 69 |
| Duplicated predictor names | 0 |
| All-missing predictors | 0 |
| Constant predictors | 0 |
| Infinite numeric values | 0 |
| Participants with all 69 predictors | 5,203 |
| Participants with at least 65 predictors | 8,866 |
| Participants with at least one predictor | 9,767 |
| Participants with no predictors | 0 |

A distinct group of 243 participants had only one to four observed predictors. All 243 lacked a Wave 1 source record. Among the 9,524 participants with a Wave 1 source record, observed predictor counts ranged from 29 to 69, with a median of 69.

Across the full Stage 2 matrix, the highest missing percentages were 11.72% for `parental_autonomy_support_score_pretransition` and 10.20% for `household_income_band`. Missing predictor values were retained without imputation.

## Interpretation

The Stage 2 construction produced a 69-predictor pre-transition matrix spanning 10 represented predictor domains. No suitable direct prior-attainment measure was retained, so the prior-attainment domain remained unrepresented rather than being replaced with a poorly timed or non-equivalent proxy.

The coverage review also identified 243 participants without a Wave 1 source record, for whom most earlier-wave predictors were structurally unavailable. These records were retained at this stage; modelling-sample eligibility was determined separately in Stage 3. Item-level missing predictor values were also retained for later preprocessing rather than imputed during predictor construction.
