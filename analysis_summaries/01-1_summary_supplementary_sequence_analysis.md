# Stage 1 Supplementary Analysis: Pre-Endpoint Activity Sequences

**Notebook:** `notebooks/01-1_stage_1_supplementary_sequence_analysis.ipynb`

## Purpose

Summarise monthly activity histories before the May 2009 endpoint and examine how the resulting sequence clusters relate to age-18 activity status.

The sequence window covers September 2006 to April 2009. May 2009 is excluded from the 32-month histories used for clustering.

## Sequence construction

Complete 32-month histories were available for 9,724 participants. These histories contained 2,090 unique activity sequences. Hamming distance was used to compare monthly states, and weighted k-medoids was fitted to the unique histories using participant frequencies as weights.

Cluster selection was based on fit, silhouette and repeated multi-start stability rather than the May 2009 endpoint.

## Selected six-cluster solution

| Sequence cluster | Participants | Percentage |
|---|---:|---:|
| Predominantly education | 5,774 | 59.38% |
| Later transition to employment | 1,604 | 16.50% |
| Earlier transition to employment | 900 | 9.26% |
| Predominantly employed | 606 | 6.23% |
| Predominantly NEET | 459 | 4.72% |
| Predominantly apprenticeship/training | 381 | 3.92% |

Selection diagnostics:

| Diagnostic | Result |
|---|---:|
| Reduction in weighted objective from k = 5 to k = 6 | 12.42% |
| Weighted silhouette | 0.571 |
| Mean pairwise ARI across repeated multi-start fits | 0.893 |
| Minimum pairwise ARI | 0.852 |
| Minimum cluster mean Jaccard | 0.799 |
| Median cluster mean Jaccard | 0.943 |

The repeated multi-start assessment used five batches of ten initialisations for the five- to seven-cluster comparison.

## Relationship with age-18 activity status

The sequence-analysis sample contained 9,724 participants with both a valid age-18 outcome and a complete 32-month history.

The association between the six sequence clusters and the four age-18 activity statuses was:

- χ²(15) = 11,654.10
- p < .001
- bias-corrected Cramér's V = 0.632
- minimum expected cell count = 20.49

## Interpretation

The six sequence clusters show that participants reached the same age-18 destination through different preceding activity histories. Education showed the clearest continuity with a predominantly educational history, whereas Employment, Apprenticeship or training, and NEET were associated with more heterogeneous pathways.

These patterns provide descriptive longitudinal context for the age-18 outcome categories. They do not represent predictive trajectories and were not used as predictors in the classification models.

This association is descriptive. It is not a predictive-performance measure and was not used to select the cluster solution.


