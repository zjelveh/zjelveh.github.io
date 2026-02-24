# INST 414 — Lab 4 Notes

## Performance metrics, thresholds, conditional independence, and Naive Bayes

These notes are meant to be read alongside **Lab 4** (the notebook). Most students will complete the pre-lab sections at home, then use the Lab Tasks in class. The goal is to help you build intuition for:

- how a model’s predicted probabilities become **predicted labels** using a **threshold**,
- why performance metrics are just **conditional probabilities**,
- why **base rates** matter a lot for interpreting predictions,
- and why Naive Bayes multiplies probabilities (and what assumption makes that reasonable).

---

## What you should be able to do after reading this

- Turn predicted probabilities into predicted labels using a threshold.
- Explain the confusion-matrix cells (TP, FP, TN, FN).
- Compute TPR (recall) and PPV (precision) from data and explain the denominators.
- Explain why changing the threshold can change TPR and PPV in different directions.
- Explain (in words) what **conditional independence** means and why it matters for Naive Bayes.

---

## Before you start: A constraint for this class

In this lab, we will **not** use DataFrame indices on purpose. We’ll keep everything as regular columns and use boolean conditions like `df[condition]` to filter rows.

---

## 1) Predicted probabilities vs predicted labels (thresholding)

In the dataset, `prediction` is a number between 0 and 1. You can think of it as:

> “the model’s estimated probability that `y = 1`”

But to make a yes/no decision, we need a rule to turn that probability into a label:

- Choose a threshold `t`
- Predict:
  - $\\hat{y} = 1$ if `prediction ≥ t`
  - $\\hat{y} = 0$ if `prediction < t`

Changing `t` changes what counts as “high risk”, which changes the errors you make.

---

## 2) Why we store predicted labels as 0/1 (not True/False)

When you apply a threshold in Pandas, you naturally get `True/False`. In this lab, we usually store the predicted label as **0/1** because:

- It’s easy to count cases like `yhat == 1`.
- The mean of a 0/1 column is a probability (a share).
- It keeps formulas and code consistent.

In Pandas, you can go from boolean → 0/1 using `map`:

```py
df["yhat"] = (df["prediction"] >= 0.5).map({True: 1, False: 0})
```

---

## 3) The confusion matrix is a joint distribution

Once you have `y` (the true outcome) and $\\hat{y}$ (the predicted label), every case falls into one of four cells:

- **TP**: $y = 1$ and $\\hat{y} = 1$
- **FP**: $y = 0$ and $\\hat{y} = 1$
- **TN**: $y = 0$ and $\\hat{y} = 0$
- **FN**: $y = 1$ and $\\hat{y} = 0$

In Pandas, you can compute these counts directly with boolean conditions:

```py
TP = ((df["y"] == 1) & (df["yhat"] == 1)).sum()
FP = ((df["y"] == 0) & (df["yhat"] == 1)).sum()
TN = ((df["y"] == 0) & (df["yhat"] == 0)).sum()
FN = ((df["y"] == 1) & (df["yhat"] == 0)).sum()
```

Conceptually, these four counts come from the **joint distribution** $P ( y , \\hat{y} )$.

---

## 4) TPR and PPV are conditional probabilities

Two key metrics in this lab are:

### True Positive Rate (TPR) / Recall

> Among the people who truly have $y = 1$, what share did we predict as $\\hat{y} = 1$?

$TPR = P ( \\hat{y} = 1 \\mid y = 1 )$

In counts:

$TPR = \\frac{TP}{TP + FN}$

### Positive Predictive Value (PPV) / Precision

> Among the people we predicted as $\\hat{y} = 1$, what share truly have $y = 1$?

$PPV = P ( y = 1 \\mid \\hat{y} = 1 )$

In counts:

$PPV = \\frac{TP}{TP + FP}$

**Denominators matter:**
- TPR’s denominator is “all actual positives” ($y = 1$).
- PPV’s denominator is “all predicted positives” ($\\hat{y} = 1$).

---

## 5) Why base rates matter (even with a “good” model)

The **base rate** is the overall rate of the outcome:

$P ( y = 1 )$

When $P ( y = 1 )$ is low (the outcome is rare), it becomes easy to generate lots of **false positives** if you set a low threshold.

That tends to:
- increase **TPR** (you catch more true positives),
- but decrease **PPV** (a larger fraction of your predicted positives are false positives).

This is why “high recall” and “high precision” can trade off with each other.

---

## 6) Conditional independence (why we talk about it before Naive Bayes)

Naive Bayes multiplies conditional probabilities like:

$P ( X_1 = 1 \\mid y ) \\times P ( X_2 = 1 \\mid y )$

That multiplication is only exactly valid when the features are **conditionally independent given** $y$.

One way to write conditional independence is:

$P ( X_1 = 1 , X_2 = 1 \\mid y ) = P ( X_1 = 1 \\mid y ) \\times P ( X_2 = 1 \\mid y )$

In the notebook, you’ll check this idea using a tiny toy dataset (for $y = 0$ and for $y = 1$).

---

## 7) Rank-based thresholds (top K)

Another way to “set a threshold” is to choose a fixed number of people to flag.

Example idea:
- Sort by `prediction` from highest to lowest.
- Take the top K rows.
- Treat those as $\\hat{y} = 1$.

Then “PPV among the top K” is:

> $P ( y = 1 \\mid \\text{rank} \\le K )$

This is useful when you have capacity limits (for example, only enough resources to intervene on K people).

---

## 8) Maryland dataset: what the columns mean (for this lab)

This lab uses a dataset where each row is one person.

- `umd_id`: an ID for each person (not a feature for prediction).
- `outcome_violent_rearrest`: the true outcome (0/1). In the notebook we rename this to `y`.
- `prediction`: the model’s predicted probability that `y = 1`.

We’ll also use a few columns as toy “features” for Naive Bayes:
- `age_at_arrest`: age (in years) at the time of arrest.
- `n_vio_convictions_last_4yrs`: number of violent convictions in the last 4 years.
- `n_vio_convictions_last_180days`: number of violent convictions in the last 180 days.
- `n_vio_arrests_last_4yrs`: number of violent arrests in the last 4 years.
- `n_vio_arrests_last_180days`: number of violent arrests in the last 180 days.

---

## 9) Naive Bayes: what the multiplication is assuming

In the Naive Bayes section, you compute two scores (one for $y = 1$ and one for $y = 0$) and pick whichever is bigger.

The key assumption is **conditional independence** of the features given the class:

> Given $y$, the features don’t give extra information about each other.

That’s why Naive Bayes multiplies terms like:

$P ( X_1 = 1 \\mid y ) \\times P ( X_2 = 1 \\mid y )$

Even if that assumption is not exactly true, Naive Bayes can still be a useful baseline classifier because it is simple and fast.

---

## Common pitfalls

- Mixing up what you are conditioning on (the denominator) for TPR vs PPV.
- Forgetting that lowering a threshold can increase false positives.
- Treating `prediction` as a label (it’s a probability until you threshold it).
