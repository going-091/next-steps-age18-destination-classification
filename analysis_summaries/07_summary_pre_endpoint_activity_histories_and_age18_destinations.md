# Stage 7: Pre-Endpoint Activity Histories and Age-18 Destinations

**Notebook:** `notebooks/07_stage_7_pre_endpoint_activity_histories_and_age18_destinations.ipynb`

## Purpose

Provide supplementary longitudinal context for the four-class age-18 destination analysis using monthly activity histories before the May 2009 endpoint.

The analysis describes:

- duration, transition frequency and continuity before the age-18 destination;
- variation in preceding activity histories within each destination; and
- differences in preceding histories between correctly and incorrectly classified held-out cases.

The activity histories are not predictors and are not used to change the fitted models.

## Analysis samples

| Sample | Participants |
|---|---:|
| Age-18 outcome sample | 9,767 |
| Complete 32-month pre-endpoint sequence sample | 9,724 |
| Modelling sample | 9,524 |
| Sequence-modelling overlap | 9,481 |
| Held-out test sample | 1,905 |
| Sequence-linked held-out test sample | 1,893 |

The sequence window covers September 2006 to April 2009. May 2009 is excluded because it defines the age-18 endpoint.

## Sequence-cluster sensitivity

The six-cluster solution from the sequence analysis was retained. Stage 7 examined sensitivity to participant resampling across 30 repetitions.

Adjusted Rand index across the repetitions:

- mean: 0.875
- median: 0.876
- SD: 0.098
- minimum: 0.548
- maximum: 0.997

Cluster-specific mean Jaccard similarity ranged from 0.533 to 0.941. The lower values occurred for employment-related clusters, indicating greater sensitivity for those cluster assignments than for the predominantly education cluster.

This diagnostic assesses sensitivity to participant resampling and is separate from the repeated-initialisation stability assessment used when constructing the six-cluster solution.

## Pre-endpoint histories and age-18 destinations

The six sequence clusters were strongly associated with the May 2009 destination:

- χ²(15, N = 9,724) = 11,654.10
- p < .001
- bias-corrected Cramér’s V = 0.632

Correspondence was not one-to-one.

### Education

Education showed the clearest continuity with its preceding history:

- 96.17% were in the predominantly education cluster.

### Employment

Employment included several distinct preceding patterns:

- 49.91% later transition to employment;
- 22.47% earlier transition to employment;
- 16.35% predominantly employed.

### Apprenticeship or training

Apprenticeship or training combined both work-based and education-dominated histories:

- 50.48% predominantly apprenticeship/training;
- 27.15% predominantly education.

### Unemployment or inactivity (NEET)

NEET contained varied preceding histories:

- 41.06% predominantly education;
- 27.45% predominantly NEET;
- the remaining cases were distributed across employment- and apprenticeship-related histories.

These distributions show that the same point-in-time age-18 destination can follow different preceding transitions and activity histories.

## Preceding histories and classification status

Stage 6 held-out predictions were linked to complete activity histories for 1,893 of the 1,905 test participants.

Within each observed destination, correctly and incorrectly classified cases were compared using:

- months spent in the eventual destination state;
- transition count;
- number of distinct activity states; and
- terminal spell duration.

The clearest differences were observed for Apprenticeship or training and NEET.

### Apprenticeship or training

Depending on the model, correctly classified cases had spent an average of **7.74–11.53 more months** in apprenticeship/training before the endpoint than incorrectly classified cases.

### NEET

Correctly classified cases had spent an average of **6.80–7.88 more months** in NEET before the endpoint than incorrectly classified cases.

The corresponding differences were smaller for Education and Employment:

- Education: 1.64–2.50 months;
- Employment: 0.93–2.63 months.

The results therefore show an association between classification status and preceding duration or continuity within the same observed destination. They do not show that the activity histories caused classification errors.

## Interpretation boundaries

Stage 7 is supplementary and descriptive.

- The 32-month histories are not model predictors.
- The sequence clusters are not alternative modelling targets.
- The analysis does not estimate causal effects of transitions or activity histories.
- Differences between correctly and incorrectly classified cases do not provide a basis for changing the models after held-out evaluation.
- The analysis describes longitudinal heterogeneity behind the fixed May 2009 destination categories.

## Interpretation

Differences between correctly and incorrectly classified cases show how preceding histories varied within the same age-18 destination.

The analysis provides longitudinal context for the fixed May 2009 destination categories.