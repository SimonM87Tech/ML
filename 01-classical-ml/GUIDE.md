# Classical ML (tabular data)

Models for data that fits in a table: customers, transactions, sensors, rows and columns. Not glamorous, but this is where most real business value — and most consulting revenue — lives. On tabular data, these methods still routinely **beat deep learning**.

## Keywords decoded

- **Linear / logistic regression** — draw the best straight line through the data (logistic = squashed into a 0–1 probability for classification). Simple, fast, interpretable. Always a strong first model.
- **Decision tree** — a learned flowchart of if/else splits ("tenure < 6 months? → contract month-to-month? → likely churn"). Interpretable but overfits alone.
- **Random forest** — hundreds of trees, each trained on random subsets, votes averaged. Robust, hard to mess up.
- **Gradient boosting (XGBoost / LightGBM)** — trees built *sequentially*, each one correcting the previous ones' mistakes. The reigning champion on tabular data. If a Kaggle tabular competition was won, this probably won it.
- **Ensemble** — any combination of models voting together (forests and boosting are both ensembles).
- **Feature engineering** — creating better input columns from raw ones (e.g., `TotalCharges / tenure` = average monthly spend). On tabular data this moves the needle more than model choice.
- **One-hot encoding** — turning a category column ("Contract: monthly/1yr/2yr") into 0/1 columns, because models eat numbers, not strings.
- **Cross-validation** — instead of one train/val split, rotate through k splits and average the scores. More reliable estimate, standard practice.
- **Feature importance / SHAP** — which columns drove the predictions. This is what you show the client; often more valuable to them than the predictions themselves.
- **Class imbalance** — when one label is rare (fraud, churn). Fixes: class weights, resampling, and choosing metrics that don't lie (see foundations).

## The standard workflow (memorize this shape)

1. Load data → look at it (distributions, missing values, leakage suspects)
2. Baseline
3. Split (before any tuning!)
4. Simple model (logistic regression) → score
5. Strong model (gradient boosting) → score
6. Feature engineering iterations → score
7. Interpret (feature importance) → sanity-check with domain logic
8. Final score on untouched test set, once

- **Data leakage** — a feature that secretly contains the answer (e.g., "account_closed_date" when predicting churn). Great scores, useless model. Hunt for it in step 1 and whenever a score looks too good.

## What to master

scikit-learn's API (`fit` / `predict` / `Pipeline`), pandas fluency, the workflow above until it's muscle memory.

## Advisor lens

When a client says "we need AI," the first diagnostic is: *is this actually a tabular problem?* If yes, the honest pitch is a 2-week gradient-boosting project, not a 6-month deep learning one. Saying that builds the trust that gets you the next contract.
