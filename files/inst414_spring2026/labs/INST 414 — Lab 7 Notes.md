# INST 414 — Lab 7 Notes

## Cross-validation + model selection (and an example with decision trees)

These notes are meant to be read alongside **Lab 7** (the notebook). The goal of this lab is to learn the basic workflow for estimating out-of-sample performance and tuning model settings using **cross-validation**.

In Lab 7, you will:

- Split data into **train** and **holdout** sets.
- Use **K-fold cross-validation** on the training set.
- Use `GridSearchCV` to pick the best hyperparameter value(s).
- Evaluate the chosen model on holdout data.
- (Optional) Run **nested cross-validation** to get an out-of-sample prediction for every row.

This lab is also a bridge to Week 8–9: once you know cross-validation, you can apply the same tools to **logistic regression**, **decision trees**, **random forests**, and **gradient boosting**.

---

## What you should be able to do after reading this

- Explain the difference between a **holdout set** and a **validation fold**.
- Explain why cross-validation is used for **model selection** (choosing hyperparameters).
- Use `GridSearchCV` (estimator, parameter grid, CV folds, scoring).
- Interpret `best_params_` and `best_score_`.
- Generate predicted probabilities on a test set with `predict_proba`.
- Explain what nested cross-validation is doing (at a high level).

---

## 1) Why we split into train vs holdout

If you evaluate a model on the same data you trained on, you will usually get an overly optimistic performance estimate.

So we split the data:

- **Train**: used to fit models and tune settings
- **Holdout**: used once at the end to estimate out-of-sample performance

Think of the holdout set as your “final exam” for the model.

---

## 2) K-fold cross-validation: what it is

Within the **training** data, we split into $$K$$ folds:

- Hold out 1 fold as a **validation set**
- Train on the other $$K-1$$ folds
- Repeat so each fold is used as validation once

This produces $$K$$ validation scores, which we average.

**Key idea:** Cross-validation is about estimating how a model will do on new data *without* using the holdout set repeatedly.

---

## 3) Model selection with `GridSearchCV`

In this class, we’ll use cross-validation mainly for **model selection**:

> choose hyperparameters by picking the setting with the best average validation performance.

`GridSearchCV` takes:

- `estimator`: the model class (logistic regression, decision tree, etc.)
- `param_grid`: which hyperparameters to try
- `cv`: number of folds (e.g., 5)
- `scoring`: what you’re trying to maximize/minimize (e.g., accuracy, AUC)

After `.fit(...)`, you can inspect:

- `grid.best_params_`
- `grid.best_score_`

---

## 4) Logistic regression reminder: `C` vs “lambda”

The slides talk about trying many values of $$\\lambda$$ (regularization strength).

In `sklearn.LogisticRegression`, the main regularization knob is `C`:

- smaller `C` → **stronger** regularization
- larger `C` → **weaker** regularization

So scanning a grid of `C` values is similar to scanning different $$\\lambda$$ values (just with the inverse direction).

---

## 5) Decision tree example (GridSearchCV)

This is the same workflow as the logistic regression example in the lab, but using a **decision tree** instead.

Assume you already have:

- `X_train`, `X_test` (features)
- `y_train`, `y_test` (labels)

### A simple decision-tree grid search

```py
from sklearn.model_selection import GridSearchCV
from sklearn.tree import DecisionTreeClassifier

tree = DecisionTreeClassifier(random_state=0)

param_grid = {
    "max_depth": [2, 3, 4, 6, 10],
    "min_samples_leaf": [1, 5, 20],
}

grid = GridSearchCV(
    estimator=tree,
    param_grid=param_grid,
    cv=5,
    scoring="accuracy",
)

grid.fit(X_train, y_train)

grid.best_params_
```

### Predict on the holdout set

```py
yhat = grid.predict(X_test)
yprob = grid.predict_proba(X_test)[:, 1]
```

**How to interpret this:** the CV procedure is choosing how complex the tree is allowed to be (depth / leaf size). Deeper trees can fit training data very closely, but can also overfit, which is why we tune these settings.

---

## 6) Nested cross-validation (what it’s for)

When you do a single train/holdout split, your final evaluation depends on that particular split.

Nested CV tries to reduce that randomness by:

- repeatedly treating different parts of the data as “outer holdout” folds
- doing a full inner-loop CV (`GridSearchCV`) inside each outer fold

The result is that every row gets an **out-of-sample** prediction at least once.

**Why we like it:** more stable performance estimates (uses more of the dataset for evaluation).  
**Why it’s expensive:** you are doing cross-validation inside cross-validation.

---

## Common pitfalls

- Using the holdout set to tune hyperparameters (leaks information).
- Forgetting that in logistic regression, smaller `C` means stronger regularization.
- Mixing up `predict(...)` (labels) vs `predict_proba(...)` (probabilities).
- Using a scoring metric that doesn’t match your goal (e.g., optimizing accuracy when you care about ranking risk).

