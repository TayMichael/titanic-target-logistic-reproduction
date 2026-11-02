# Titanic Target-Encoded Logistic Regression Reproduction

Reproducible, explained notebook for the NTU DSAI Titanic Kaggle class competition submission that achieved a **public ROC-AUC of 0.78218**.

## What this repo reproduces

The model is Logistic Regression using engineered Titanic passenger features plus smoothed, leave-one-out target encoding for surname and ticket groups.

The notebook recreates the feature engineering, target encoding, model fitting, Kaggle probability CSV, repeated cross-validation result, and comparison against the exact submitted reference file.

## Run in VS Code

```bash
git clone https://github.com/TayMichael/titanic-target-logistic-reproduction.git
cd titanic-target-logistic-reproduction
python -m venv .venv
```

Activate the virtual environment, then install dependencies:

```bash
pip install -r requirements.txt
```

Open:

`Titanic_Target_Logistic_Reproduction.ipynb`

Select the `.venv` Python kernel and click **Run All**.

## Data

The repo does not duplicate the standard Titanic source CSVs. On first execution the notebook automatically downloads the exact byte-identical `train.csv`, `test.csv`, and `gender_submission.csv` from a public GitHub mirror and verifies their SHA-256 hashes before modelling. If any input differs, the notebook stops.

## Key files

- `Titanic_Target_Logistic_Reproduction.ipynb` — complete explained reproduction
- `reference/final_target_logistic_candidate.csv` — exact submitted reference predictions
- `requirements.txt` — Python dependencies
- `VERIFICATION.md` — reproduction evidence

The generated submission is written to:

`output/final_target_logistic_candidate.csv`

## Original modelling results

- Repeated 5-fold × 3 ROC-AUC mean: **0.882810**
- Repeated CV standard deviation: **0.026435**
- Kaggle public ROC-AUC: **0.78218**

## Validation caveat

Later diagnostics showed that ordinary stratified cross-validation was optimistic because related passengers could cross folds. Group-aware validation was therefore used as a robustness check. The notebook preserves the actual submitted modelling route and explains this limitation rather than hiding it.
