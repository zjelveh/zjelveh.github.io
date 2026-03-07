# INST 414 — Lab 6 Notes

## Regression + evaluation: OLS vs logistic regression

These notes are meant to be read alongside **Lab 6** (the notebook). The goal of this lab is to connect regression models to the probability and performance-metrics ideas we’ve been using all semester.

In Lab 6, you will:

- Create an outcome: whether someone is rearrested within **1 year**.
- Fit an **OLS (linear probability)** model and a **logistic regression** model.
- Turn predicted probabilities into predicted labels using a **threshold** (we use the **base rate**).
- Compute **TPR (recall)** and **PPV (precision)**.
- Compare models and see how logistic regression’s `C` parameter changes performance.
- (Extension) Look at average predictions by **sex** and **race**.

---

## What you should be able to do after reading this

- Create an outcome using a time window (“rearrest within 1 year”).
- Explain why we use a train/test split and what **stratify** means.
- Fit OLS and logistic regression in `sklearn`.
- Explain what `predict` vs `predict_proba` returns.
- Compute TPR and PPV from a DataFrame and explain the denominators.
- Explain what the logistic regression parameter `C` does (regularization strength).
- Compute average predicted risk by group (e.g., by sex or race).

---

## 0) Before anything else: predicted probabilities vs predicted labels

Regression models can give you a **predicted probability** (or something you treat like a probability):

> “estimated chance that `y = 1`”

But to make a yes/no decision you need a **threshold** `t`:

- predict $\hat{y}=1$ if `prediction ≥ t`
- predict $\hat{y}=0$ if `prediction < t`

In this lab, we often use the **base rate** as a threshold:

$$t = P(y=1).$$

This is a simple, transparent rule for turning probabilities into labels.

---

## 1) Creating the outcome with a time window (rearrest within 1 year)

The dataset has:

- `universe`: one row per “current arrest” we care about
- `arrest_events`: event-level rows (many rows per person)

To create “rearrest within 1 year”, the key idea is:

1) Merge `universe` with `arrest_events` on `person_id` so you can compare dates.
2) Keep only events that happen **after** the universe arrest date.
3) Keep only events within **1 year** of the universe arrest date.
4) Create an outcome indicator in `universe` using `isin(...)`.

**Why do we filter to *after* the universe date?**  
To avoid “leakage”: you should not use future information when defining a feature, and for the outcome we want strictly *subsequent* arrests.

---

## 2) OLS as a “linear probability model”

In Lab 6, OLS predicts:

$$\\widehat{y} = \\beta_0 + \\beta_1 x_1 + \\beta_2 x_2 + \\cdots$$

When `y` is 0/1, people sometimes interpret $\\widehat{y}$ as a probability estimate.

**Important limitation:** OLS can produce predictions below 0 or above 1. That doesn’t break the code, but it’s one reason we often prefer logistic regression for probabilities.

In `sklearn`, OLS is:

- `LinearRegression().fit(X, y)`
- predictions from `model.predict(X)` (one number per row)

---

## 3) Logistic regression produces probabilities in (0, 1)

Logistic regression models:

$$P(y=1\\mid x) = \\sigma(\\beta_0 + \\beta^T x)$$

where $\\sigma(\\cdot)$ is the logistic (S-shaped) function.

In `sklearn`:

- Fit with `LogisticRegression(...).fit(X, y)`
- Get probabilities with `predict_proba(X)[:, 1]`

That `[:, 1]` is the model’s probability for class `y=1`.

---

## 4) Train/test split (why we do it)

If you evaluate performance on the same data you trained on, you can get an overly optimistic view of performance.

So we split into:

- **train**: fit the model
- **test**: evaluate performance on new data

In this lab you’ll often see:

- `train_test_split(..., stratify=y)`

**Stratify** means we force train and test to have similar base rates of the outcome, so comparisons are fair and stable.

---

## 5) TPR and PPV are conditional probabilities

Once you have `y` (truth) and `yhat` (predicted label), the metrics are:

### TPR / Recall

> Among the true positives ($y=1$), what share did we predict as positive?

$$TPR = P(\\hat{y}=1\\mid y=1) = \\frac{TP}{TP+FN}$$

### PPV / Precision

> Among the predicted positives ($\\hat{y}=1$), what share are truly positive?

$$PPV = P(y=1\\mid \\hat{y}=1) = \\frac{TP}{TP+FP}$$

**What to watch for:** the denominators are different. That’s why TPR and PPV can move in different directions when you change the threshold.

---

## 6) Logistic regression regularization and the meaning of `C`

In `sklearn.LogisticRegression`, `C` controls **regularization strength**:

- larger `C` → weaker regularization (model fits the training data more closely)
- smaller `C` → stronger regularization (model is more constrained)

In the lab task, you compare `C=0.1` to `C=10`.

**Why can `C` affect performance?**  
Because it changes how much the model is allowed to use the features to separate `y=1` from `y=0`. With too much flexibility you can overfit; with too much constraint you can underfit.

---

## 7) Group averages of predictions (sex / race)

Later in the lab, you compute average predicted probabilities by group, like:

$$E[\\widehat{P}(y=1)\\mid sex] \\quad \\text{and} \\quad E[\\widehat{P}(y=1)\\mid race].$$

In Pandas this is usually a `groupby(...).mean()` on a prediction column.

Interpretation:

> “On average, which group is the model assigning higher predicted risk to?”

This is not (by itself) a proof of bias or unfairness, but it is a useful diagnostic to see how predictions vary across groups.

---

## Common pitfalls

- Using the **test** base rate as the threshold instead of the **train** base rate.
- Forgetting `predict_proba(... )[:, 1]` for logistic regression.
- Mixing up the denominator for TPR vs PPV.
- Forgetting to convert booleans to 0/1 (it’s fine either way, but 0/1 often makes means and formulas clearer).
- Accidentally counting events on or before the universe date when defining a “rearrest” outcome.

