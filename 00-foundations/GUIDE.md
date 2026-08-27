# Foundations

The vocabulary every other topic assumes. Read once now, come back whenever a term is fuzzy.

## The core idea

A model is a function with tunable numbers (parameters). **Training** = showing it examples and nudging the parameters so its outputs get closer to the right answers. That's it. Everything else is detail about *what function*, *what nudge*, and *how you know it worked*.

## Keywords decoded

- **Features / labels** — inputs (columns, pixels, words) / the answer you want predicted.
- **Supervised learning** — you have labels (churn: yes/no). **Unsupervised** — you don't; you look for structure (clustering customers). Supervised is ~90% of paid client work.
- **Classification vs regression** — predict a category (churn yes/no) vs a number (revenue next month).
- **Train / validation / test split** — data you learn from / data you tune decisions on / data you touch **once** at the end to get the honest score. Mixing these up is the #1 beginner sin.
- **Loss function** — a single number measuring "how wrong is the model right now." Training = minimizing it.
- **Overfitting** — the model memorized the training data instead of learning the pattern. Symptom: great training score, bad test score. **Underfitting** — model too simple to capture the pattern; bad everywhere.
- **Hyperparameters** — settings you choose *before* training (tree depth, learning rate), unlike parameters, which training learns.
- **Baseline** — the dumbest possible predictor (always guess the majority class; predict yesterday's value). Every model must beat a baseline or it's worthless. Always build the baseline first.

## Metrics (know these cold)

- **Accuracy** — % correct. Misleading when classes are imbalanced (95% of customers don't churn → "predict no churn always" scores 95%).
- **Precision** — of the ones I flagged, how many were right? **Recall** — of the true positives out there, how many did I catch? There's always a tradeoff; which matters depends on the business cost of each error type.
- **F1** — harmonic mean of precision and recall, one number when you need balance.
- **ROC-AUC** — how well the model ranks positives above negatives, across all thresholds. Good default for binary classification.
- **For regression**: MAE (average error in real units — clients understand this), RMSE (punishes big misses harder).

## What to master

1. Explain the train/val/test split and *why* touching test data during development invalidates your score.
2. Pick the right metric from a business description of the problem.
3. Reflexively build a baseline before any model.

## Advisor lens

Clients will show you "95% accuracy" claims. Your first two questions, always: *accuracy against what baseline?* and *measured on data the model never saw?* Those two questions alone are worth your fee.
