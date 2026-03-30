# INST 414 - Lab 8 Notes

## What this lab is about

This lab introduces two new models:

- random forest
- gradient boosting

Both models are built from decision trees, but they improve on a single tree in different ways.

The main conceptual goal of the lab is to compare models using:

- **AUC**
- **calibration**
- **precision**

These are related, but they are not the same thing.

## Random forest

Random forest builds many decision trees and averages their predictions.

Key idea:

- a single decision tree can be unstable
- random forest reduces that instability by averaging many trees

Random forest also keeps the useful part of trees:

- it can model **interactions automatically**

So if the relationship between two predictors depends on a third variable, random forest can often capture that without you having to manually create interaction terms.

## Gradient boosting

Gradient boosting also uses trees, but in a different way.

Instead of building many trees independently and averaging them, gradient boosting builds trees **sequentially**.

The basic idea is:

1. start with a simple prediction
2. find where the current model is doing poorly
3. fit a small tree to improve those mistakes
4. update the predictions
5. repeat

So while random forest is best understood as averaging many trees, gradient boosting is best understood as making a series of corrections.

Like random forest, gradient boosting can also model **interactions automatically**.

An important difference for this course is that gradient boosting can be trained with **log loss**, so it is directly trying to learn probabilities.

That makes it especially interesting because it can potentially give us both:

- automatic interactions
- probability-focused training

## AUC

In this class, the most useful way to think about AUC is as a **probability**.

**Definition:**

AUC is the probability that the model gives a randomly chosen positive case a higher score than a randomly chosen negative case.

In symbols, if we randomly choose:

- one observation with `y = 1`
- one observation with `y = 0`

then AUC is the probability that:

`score(y=1) > score(y=0)`

Why this matters:

- AUC is a **ranking** metric
- it tells us how well the model orders positive cases above negative cases
- it does **not** directly tell us whether the probabilities are calibrated

Interpretation:

- AUC close to `1` means the model is very good at ranking
- AUC close to `0.5` means the model is about as good as random guessing

## Calibration

Calibration asks a different question.

Instead of asking whether positive cases tend to get higher scores, calibration asks:

- when the model predicts a probability like `0.30`, do about 30% of those cases actually have `y = 1`?

So calibration is about whether predicted probabilities match actual rates.

In this lab, we use a helper function to draw a calibration plot.

The helper uses **quantile-based bins**, which means:

- predictions are split into groups with about the same number of observations
- for each group, we compare:
  - the average predicted probability
  - the actual rate of `y = 1`

If the model is well calibrated, the points should lie close to the 45-degree line.

## Why AUC and calibration can disagree

This is the most important idea in the lab.

A model can have:

- strong AUC but poor calibration

because these metrics measure different things.

For example, a model might do an excellent job ranking high-risk cases above low-risk cases, but still produce probabilities that are systematically too high or too low.

That would mean:

- good ranking
- weak calibration

So when you compare models in this lab, do not assume that the model with the highest AUC will also be the model with the best calibration.

## Precision in this lab

Precision is defined as:

- among the cases predicted positive, what fraction are actually positive?

In symbols:

`Precision = P(y = 1 | yhat = 1)`

In the notebook, you create `yhat` by thresholding predicted probabilities at `0.5`.

Then you compute precision manually by looking only at the rows where `yhat = 1` and taking the mean of the true outcome.

This is useful because it reinforces the distinction between:

- predicted probabilities
- thresholded class predictions
- evaluation metrics

## What to pay attention to

As you work through the lab, focus on these questions:

- Which model has the highest AUC?
- Which model looks best calibrated?
- Are those the same model?
- How is random forest different from gradient boosting?
- What does the comparison suggest about ranking versus calibration?

## Big picture

This lab connects directly to the course narrative:

- logistic regression is probability-focused, but interactions must be added manually
- random forest gives automatic interactions and often strong ranking performance
- gradient boosting gives automatic interactions and can also be trained to learn probabilities

So the broader question in the lab is:

- which model is best for ranking?
- which model is best for probability estimation?

Those are not always the same question, and they do not always have the same answer.
