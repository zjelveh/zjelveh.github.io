# INST 414 — Lab 4 Notes

## Performance metrics, thresholds, and Naive Bayes (as probabilities)

These notes are meant to be read alongside **Lab 4** (the notebook). Most students will complete the pre-lab sections at home, then use the Lab Tasks in class. The goal is to help you build intuition for:

- how a model’s predicted probabilities become **predicted labels** using a **threshold**,
- why performance metrics are just **conditional probabilities**,
- why **base rates** matter a lot for interpreting predictions,
- and what Naive Bayes is doing when it multiplies probabilities together.

---

## 1) Predicted probabilities vs predicted labels

In the dataset, `prediction` is a number between 0 and 1. You can think of it as:

> “the model’s estimated probability that `y = 1`”

But to make a yes/no decision, we need a rule to turn that probability into a label:

- Choose a threshold `t`
- Predict:
  - $\\hat{y} = 1$ if `prediction ≥ t`
  - $\\hat{y} = 0$ if `prediction < t`

Changing `t` changes what counts as “high risk”, which changes the errors you make.

---

## 2) The confusion matrix is a joint distribution

Once you have `y` (the true outcome) and $\\hat{y}$ (the predicted label), every case falls into one of four cells:

- **TP**: $y = 1$ and $\\hat{y} = 1$
- **FP**: $y = 0$ and $\\hat{y} = 1$
- **TN**: $y = 0$ and $\\hat{y} = 0$
- **FN**: $y = 1$ and $\\hat{y} = 0$

In Pandas, a quick way to compute the table of counts is:

```py
df[['y', 'yhat01']].value_counts()
```

If you use `normalize=True`, you get probabilities (shares) instead of counts:

```py
df[['y', 'yhat01']].value_counts(normalize=True)
```

That output is estimating the **joint distribution** $P ( y , \\hat{y} )$.

---

## 3) TPR and PPV are conditional probabilities

Two key metrics in this lab are:

### True Positive Rate (TPR) / Recall

> Among the people who truly have $y = 1$, what share did we predict as $\\hat{y} = 1$?

$TPR = P ( \\hat{y} = 1 \\mid y = 1 )$

### Positive Predictive Value (PPV) / Precision

> Among the people we predicted as $\\hat{y} = 1$, what share truly have $y = 1$?

$PPV = P ( y = 1 \\mid \\hat{y} = 1 )$

**Denominators matter:**
- TPR’s denominator is “all actual positives” ($y = 1$).
- PPV’s denominator is “all predicted positives” ($\\hat{y} = 1$).

---

## 4) Why base rates matter (even with a “good” model)

The **base rate** is the overall rate of the outcome:

$P ( y = 1 )$

When $P ( y = 1 )$ is low (the outcome is rare), it becomes easy to generate lots of **false positives** if you set a low threshold.

That tends to:
- increase **TPR** (you catch more true positives),
- but decrease **PPV** (a larger fraction of your predicted positives are false positives).

This is why “high recall” and “high precision” can trade off with each other.

---

## 5) Rank-based thresholds (top K)

Another way to “set a threshold” is to choose a fixed number of people to flag.

Example idea:
- Sort by `prediction` from highest to lowest.
- Take the top K rows.
- Treat those as $\\hat{y} = 1$.

Then “PPV among the top K” is:

> $P ( y = 1 \\mid \\text{rank} \\le K )$

This is useful when you have capacity limits (for example, only enough resources to intervene on K people).

---

## 6) Naive Bayes: what the multiplication is assuming

In the Naive Bayes section, you compute two scores (one for $y = 1$ and one for $y = 0$) and pick whichever is bigger.

The key assumption is **conditional independence** of the features given the class:

> Given $y$, the features don’t give extra information about each other.

That’s why Naive Bayes multiplies terms like:

$P ( X_1 = 1 \\mid y ) \\times P ( X_2 = 1 \\mid y )$

Even if that assumption is not exactly true, Naive Bayes can still be a useful baseline classifier because it is simple and fast.

