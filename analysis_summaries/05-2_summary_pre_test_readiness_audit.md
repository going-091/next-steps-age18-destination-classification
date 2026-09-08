# Stage 5.2: Pre-test Readiness Audit

**Notebook:** `notebooks/05-2_stage_5_pre_test_readiness_audit.ipynb`

## Purpose

Check that the Stage 5 development procedure is complete and internally consistent before the held-out test evaluation in Stage 6.

The audit uses the training sample, fixed Stage 4 split and fold specifications, and saved Stage 5 development outputs. Test-set outcomes and predictors are not used for model evaluation or selection; test identifiers are used only to verify separation from the training sample.

## Required checks

The audit verifies:

- the fixed training sample of 7,619 participants;
- unique and non-overlapping training and test identifiers;
- registration and availability of all 69 predictors;
- the four fixed outcome classes;
- the five outer folds and four inner folds;
- the four model families specified in Stage 4;
- macro F1 as the model-selection metric;
- successful completion of the Stage 5 final audit;
- one outer-validation prediction per training participant for each model and the majority-class benchmark;
- separation of Stage 5 predictions from the held-out test sample;
- completion of the prespecified candidate search;
- complete inner-fold macro-F1 results;
- a complete model × outer-fold selection register;
- reproduction of the saved outer-fold selections from the inner-CV macro-F1 results; and
- convergence of the selected MLR fits without hard fitting diagnostics.

All required readiness checks passed.

## Search-completion checks

The saved Stage 5 search contains:

- 189 registered hyperparameter configurations;
- 9 MLR candidates;
- 60 RF candidates;
- 60 XGBoost candidates;
- 60 BRF candidates; and
- 1,590 inner-search candidate summaries across the five outer folds and the specified fitting modes.

The saved outer-fold selections were reproduced from the inner-CV macro-F1 results.

## Review diagnostics

Review diagnostics are kept separate from required checks and do not determine model changes.

### Near-best candidate scores

Eighteen model × outer-fold × fitting-mode searches contained more than one candidate within 0.005 macro F1 of the best inner-CV score. This indicates limited score separation within parts of the searched candidate space rather than a fitting failure.

### MLR fitting

The five selected fold-specific MLR specifications were refitted on their corresponding outer-training samples. No convergence warning, iteration-limit failure or non-finite coefficient was identified.

### Categorical-level sparsity

Across the outer-training samples:

- 2 categorical level-fold rows had fewer than 20 observed cases;
- 7 categorical level-fold rows had a zero count in at least one destination class.

These are descriptive sparsity checks. They do not by themselves justify recoding categories or changing the fitted models.

## Readiness decision

The required integrity, search-completion, selection-reproduction and MLR-fitting checks passed. The review diagnostics did not constitute readiness failures.

Stage 5 development was therefore ready to proceed to the held-out test evaluation in Stage 6.