# Verification

This notebook was executed end-to-end against the exact Titanic input files used by the competition.

- Input SHA-256 checks: PASS
- Repeated 5-fold × 3 ROC-AUC mean: `0.882810`
- Repeated CV SD: `0.026435`
- Reference submission: `final_target_logistic_candidate.csv`
- Maximum absolute prediction difference after regeneration: `5.118e-13`
- Acceptance criterion: `<= 1e-12`
- Result: **PASS**

The small non-zero difference is floating-point numerical variation; the reproduced probabilities are numerically identical to the submitted reference at the stated tolerance.
