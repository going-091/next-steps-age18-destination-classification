# Stage 6: Final Held-Out Test Evaluation

**Notebook:** `notebooks/06_stage_6_final_held_out_test_evaluation.ipynb`

## Purpose

Select one final specification for each model using the fixed training sample, refit the selected specifications on all 7,619 training participants, and evaluate them once on the 1,905-participant held-out test sample.

Macro F1 was used for final model selection. Test-set predictors and outcomes were not used for preprocessing, weighting or model selection.

## Final model selection

The final specifications were selected from the registered Stage 5 candidate sets using fixed five-fold cross-validation on the full training sample.

| Model | Selected fitting mode | Candidate | CV macro F1 mean | SD |
|---|---|---:|---:|---:|
| MLR | Balanced | 1 | 0.3948 | 0.0101 |
| RF | Balanced | 16 | 0.4502 | 0.0189 |
| XGBoost | Balanced | 9 | 0.4425 | 0.0148 |
| BRF | Internal balanced sampling | 13 | 0.4528 | 0.0212 |

These cross-validation scores were used for final specification selection and are not treated as independent held-out performance estimates.

All four final models were fitted successfully with no recorded fitting warnings.

## Held-out test performance

| Model | Macro F1 | Balanced accuracy | MCC | Accuracy | Weighted F1 |
|---|---:|---:|---:|---:|---:|
| Majority-class reference | 0.1711 | 0.2500 | 0.0000 | 0.5202 | 0.3560 |
| MLR | 0.3905 | 0.4317 | 0.2588 | 0.5024 | 0.5196 |
| RF | 0.4378 | 0.4284 | 0.3294 | 0.5948 | 0.5838 |
| XGBoost | 0.4157 | 0.4141 | 0.2909 | 0.5549 | 0.5576 |
| BRF | 0.4309 | 0.4385 | 0.2964 | 0.5559 | 0.5589 |

RF achieved the highest held-out macro F1 among the core models. BRF achieved the highest balanced accuracy.

## Class-specific performance

Class-specific F1 scores were:

| Destination | MLR | RF | XGBoost | BRF |
|---|---:|---:|---:|---:|
| Education | 0.7044 | 0.7471 | 0.7198 | 0.7252 |
| Employment | 0.3477 | 0.4814 | 0.4642 | 0.4217 |
| Apprenticeship or training | 0.2085 | 0.1951 | 0.2105 | 0.2348 |
| Unemployment or inactivity (NEET) | 0.3012 | 0.3274 | 0.2685 | 0.3419 |

Education had the highest F1 for every model, while Apprenticeship or training had the lowest.

The precision–recall pattern differed across the smaller classes. For Apprenticeship or training, MLR recall was 0.4231 with precision 0.1384; RF recall was 0.1538 with precision 0.2667; XGBoost recall was 0.1923 with precision 0.2326; and BRF recall was 0.2596 with precision 0.2143.

## Bootstrap uncertainty

Uncertainty was estimated using 5,000 stratified paired bootstrap resamples of the saved held-out predictions. The observed destination counts were preserved within each resample, and the same resampled participants were used for each model comparison.

Macro-F1 bootstrap intervals were:

| Model | Point estimate | 95% CI |
|---|---:|---:|
| MLR | 0.3905 | 0.3687–0.4123 |
| RF | 0.4378 | 0.4104–0.4663 |
| XGBoost | 0.4157 | 0.3891–0.4433 |
| BRF | 0.4309 | 0.4053–0.4566 |

Paired model differences on the primary metric were:

| Comparison | Macro F1 difference | 95% CI |
|---|---:|---:|
| RF − MLR | +0.0473 | 0.0218–0.0721 |
| XGBoost − MLR | +0.0253 | 0.0023–0.0480 |
| RF − XGBoost | +0.0220 | 0.0021–0.0426 |
| BRF − RF | −0.0068 | −0.0261–0.0128 |

For balanced accuracy, the corresponding paired intervals for RF − MLR, XGBoost − MLR, RF − XGBoost and BRF − RF all included zero.

## Validation checks

The final audit confirmed that:

- all four final model specifications were present;
- all four final fits completed;
- each evaluation model produced 1,905 held-out predictions for 1,905 unique participants;
- predicted probability rows summed to one;
- all four destination classes were evaluated for each model;
- each model had 5,000 stratified bootstrap repetitions; and
- all required Stage 6 output files were present.

All nine final audit checks passed.

