# FasterRisk (NeurIPS 2022) — An explainer for INST 414

This is a class-level summary of what **FasterRisk** is doing and why it matters for the kinds of feature engineering + prediction problems we’ve been working on (e.g., “rearrest within 1 year”).

The main theme:

> The models we learn in class (especially logistic regression) are *conceptually simple*, but building **high-quality, usable, interpretable** versions of them can be a genuinely hard machine learning / optimization problem.

---

## 1) What is a “risk score” model?

A **risk score** is an interpretable prediction model that looks like:

1. Convert a person’s information into a small set of **binary features** (0/1 indicators), like:
   - `age_18_to_25`
   - `prior_arrests_last_year_ge_1`
   - `current_charge_felony`
2. Add up **integer points**:
   \[
   \text{SCORE}(x) = \beta_0 + \sum_{j=1}^p \beta_j x_j
   \]
   where each \(\beta_j\) is a small integer (e.g., \(-5\), \(-2\), \(+3\), \(+7\)).
3. Convert the score into a predicted **risk probability** (often via a logistic-shaped mapping):
   \[
   \widehat{P}(y=1\mid x) = \sigma(\alpha\cdot \text{SCORE}(x))
   \]
   where \(\sigma(\cdot)\) is the logistic function, and \(\alpha\) is a learned scaling (“multiplier”).

Why people like these models in high-stakes settings:

- easy to compute (even by hand),
- easy to audit (“what features mattered?”),
- easy to communicate to decision-makers.

---

## 2) How does this relate to what we do in class?

In class, we often use:

- **Feature engineering** from event data (e.g., “# arrests in last year”)
- **Logistic regression** to estimate \(P(y=1\mid x)\)

Risk scores are basically:

> logistic regression, but with extra constraints that make it usable in practice (sparse + integer coefficients).

So FasterRisk connects directly to Week 6–7 topics:

- calibration / probabilities,
- overfitting / regularization,
- bias–variance tradeoff,
- and the idea that “model simplicity” doesn’t mean “problem is easy.”

---

## 3) What is the hard ML problem FasterRisk is addressing?

If we ignore interpretability constraints, training logistic regression is straightforward.

But a *risk score* model imposes constraints like:

- **Use only a few features:** for example, limit the model to ~5 features total (instead of hundreds)
- **Integer coefficients:** points must be small integers

That changes the learning problem into:

> Find the best “few-features + integer-points” model that predicts well.

Two common “simple” approaches are:

1. **Build a logistic regression and round coefficients** to integers.
2. **Hand-design** a points system without data.

The issue: rounding a good continuous model does *not* reliably produce a good integer model.

Why? Because small coefficient changes can flip decisions, change probability mapping, and increase loss a lot—especially when you also require sparsity (dropping features) and small integers.

This is why the background problem is hard: there are **huge numbers of possible feature combinations** and **huge numbers of possible point systems**, and we want to find one that is both simple *and* accurate without trying everything.

---

## 4) What FasterRisk does (big picture)

FasterRisk is designed to quickly produce **a collection** (a “pool”) of **high-quality** risk scores.

At a high level it uses a two-stage strategy:

### Stage A: Find good “few-feature” models (which features to use)

Instead of trying every possible set of features (which is infeasible), FasterRisk uses a smart search strategy to generate a *diverse pool* of good candidate models.

Key idea:

- Many different feature subsets can give nearly the same logistic loss.
- In practice, you may want choices:
  - one model with “age + priors,”
  - another with “current charge + priors,”
  - etc.

So FasterRisk aims to find **many** near-optimal sparse supports, not just one.

### Stage B: Convert each continuous model into an integer “points” model

For each candidate model, FasterRisk then converts it into an integer-coefficient “points” score using a specialized procedure that tries to keep the model both:

- **simple** (small integers, few features), and
- **good at probability prediction** (not just “rounding because it looks nice”).

Intuition for what this stage is trying to do:

- you want integer coefficients that stay close to the continuous solution,
- but you also want the resulting integer model to keep **low logistic loss**,
- so the rounding is done in a careful, loss-aware way (not just “round everything to nearest integer”).

### Output: a ranked pool of models

Instead of giving you a single model, it returns a ranked list of candidate risk scores, so a human can choose a model that balances:

- performance (loss / AUC / accuracy),
- simplicity (how many features),
- and face validity / policy constraints (what features are acceptable).

---

## 5) Why the “pool of models” idea is useful (in practice)

In criminal justice / public policy settings, you often have constraints like:

- “don’t use certain variables,”
- “keep it to 5 features,”
- “avoid redundant features,”
- “prefer features that are easy to verify.”

If you only return one model, you can easily end up with a model that is accurate but unacceptable.

If you return a **diverse pool**, you can choose among multiple near-optimal models that fit the policy context.

---

## 6) Where calibration fits in

In our class language, “calibration” is about whether predicted probabilities match observed frequencies.

FasterRisk focuses on producing a risk score that:

- is a logistic-style probability model (so probabilities are in \((0,1)\)),
- and is trained using a standard ML objective that **rewards good probability estimates**.

An intuitive way to think about that objective:

- Predicting 0.90 when the event is unlikely is “penalized a lot,” because you were very confident and wrong.
- Predicting 0.55 when you’re unsure is penalized less.

This does not automatically guarantee perfect calibration out-of-sample (nothing does), but it is aligned with the goal of producing meaningful probabilities.

The model card-style “SCORE → RISK” table is one way to communicate calibration-like information:

- people with the same score get the same predicted risk,
- and you can check whether that predicted risk matches the empirical rate for that score/bin.

---

## 7) Caveats (important for our course framing)

- **Interpretability is not the same as fairness.** A sparse points system can still reflect biased measurement in the data.
- **Rearrest is not the same as reoffending.** Labels can reflect enforcement patterns.
- Feature engineering choices (time windows, censoring, leakage) can dominate performance and calibration—this is exactly why our labs emphasize careful construction.

---

## Optional glossary (plain-language)

- **“Use only a few features”** (often called “sparse”): the model includes only a small number of predictors.
- **Smart search strategy** (often called “beam search”): instead of trying every option, you keep only a small number of the best candidates as you build models step-by-step.
- **Objective for probability prediction** (often called “logistic loss” or “log loss”): a scoring rule that rewards probabilities that match outcomes, and heavily penalizes confident wrong predictions.
