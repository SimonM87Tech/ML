# Mission 01 — Customer Churn Prediction

**End model:** a classifier that, given a telecom customer's account data, outputs the probability they'll cancel — plus the *reasons* driving churn, framed for a business audience.

**Why this mission first:** churn prediction is the archetypal paid ML engagement — every subscription business wants it, the data is tabular, and it exercises the complete classical-ML workflow you'll reuse on real clients. It also has a built-in imbalanced-classes lesson (most customers don't churn) that breaks naive approaches in an instructive way.

## Dataset

Telco Customer Churn — 7,043 customers, 20 features (contract type, tenure, services, charges), label `Churn` yes/no. ~26% churn rate.

```bash
mkdir -p ../../datacenter/telco-churn/raw
curl -o ../../datacenter/telco-churn/raw/telco-churn.csv \
  https://raw.githubusercontent.com/IBM/telco-customer-churn-on-icp4d/master/data/Telco-Customer-Churn.csv
```

## Success criteria

- Beat two baselines you'll build honestly: majority-class, and "predict churn if contract is month-to-month."
- ROC-AUC ≥ 0.84 on a test set touched exactly once.
- A `WRITEUP.md` a non-technical telco manager could act on: top churn drivers + which customers to target with retention offers.

## Rules

Work per the protocol in `../README.md` (instructor mode, predict-before-run, stage gates). Create `LEARNINGS.md` in this folder at stage 1.

## Stages

### Stage 1 — Look at the data
**Build:** download script ran; a notebook/script exploring distributions, missing values, class balance, and feature-vs-churn relationships. Fix the known dirty column (`TotalCharges` has blank strings).
**Learn:** features/labels, class imbalance, data leakage — `00-foundations/GUIDE.md`.
**Checkpoint:** What's the churn rate, and why does that number already tell you accuracy will be a misleading metric? Name one feature that would be leakage if it existed in this data.

### Stage 2 — Baselines and metric choice
**Build:** train/test split; majority-class baseline; single-rule baseline (month-to-month → churn). Score both with accuracy, precision, recall, ROC-AUC.
**Learn:** the metrics block of `00-foundations/GUIDE.md`.
**Checkpoint:** The telco loses ~$1,000 per churned customer; a retention offer costs $50. Which error is more expensive — false positive or false negative — and which metric should we therefore favor? Predict before computing: what accuracy does the majority baseline get?

### Stage 3 — First real model
**Build:** preprocessing pipeline (one-hot encoding, scaling) + logistic regression, in an sklearn `Pipeline`. Compare to baselines.
**Learn:** one-hot encoding, logistic regression, pipelines — `01-classical-ml/GUIDE.md`.
**Checkpoint:** Why must preprocessing be fit on training data only? Explain what a logistic regression coefficient for `Contract_Month-to-month` means.

### Stage 4 — The workhorse
**Build:** gradient boosting (XGBoost) with 5-fold cross-validation; handle class imbalance (`scale_pos_weight` or class weights); compare all models so far in one table.
**Learn:** gradient boosting, cross-validation, class weights — `01-classical-ml/GUIDE.md`.
**Checkpoint:** In one paragraph: how does boosting differ from a random forest? Predict before running: will XGBoost beat logistic regression here, and by roughly how much? (The honest answer on this dataset is a lesson in itself.)

### Stage 5 — Squeeze and interpret
**Build:** 2–3 engineered features (e.g., charges-per-tenure); light hyperparameter tuning; feature importance + SHAP plot; pick the final model and run the test set **once**.
**Learn:** feature engineering, SHAP — `01-classical-ml/GUIDE.md`.
**Checkpoint:** Which three features drive churn most, and do they survive a common-sense check? Why is the test score only now allowed to be computed?

### Stage 6 — Client deliverable
**Build:** `WRITEUP.md` — problem, approach, honest numbers vs baselines, top drivers, recommended action (which segment to target, expected value of the campaign using the $1,000/$50 figures).
**Learn:** `07-advisory/GUIDE.md` — the whole thing.
**Checkpoint:** Read your writeup aloud. Would a CFO understand every sentence? Deliver the two-sentence version.
