# Lecture 9 Practice Problems (Random Forest + Gradient Boosting + AUC)

> **How to use this:** Try these before the quiz. If you get stuck, write down what part is confusing:
> (1) what the metric/model is asking, (2) what quantity you should compute/compare, or (3) arithmetic.

> **Notation reminders:**
> - $$P ( A , B )$$ means the joint probability $$P ( A \cap B )$$.
> - $$P ( A \mid B )$$ means “the probability of $$A$$ given $$B$$.”
> - In this set, “positive” means $$y = 1$$ and “negative” means $$y = 0$$.

---

## A. AUC

### A1. Compute AUC by hand from positive-negative pairs

Suppose a model assigns the following scores:

| Observation | True $$y$$ | Score |
|---|---:|---:|
| 1 | 1 | 0.90 |
| 2 | 1 | 0.70 |
| 3 | 1 | 0.40 |
| 4 | 0 | 0.80 |
| 5 | 0 | 0.60 |
| 6 | 0 | 0.20 |

1. List all positive-negative pairs.
2. For each pair, mark whether the positive case gets the higher score.
3. Compute the AUC.
4. Interpret your answer in one sentence using the **probability definition** of AUC.

---

### A2. Ranking versus calibration

Two models are evaluated on the same 6 observations.

#### Model A

| Observation | True $$y$$ | Predicted probability |
|---|---:|---:|
| 1 | 1 | 0.95 |
| 2 | 1 | 0.85 |
| 3 | 0 | 0.75 |
| 4 | 1 | 0.25 |
| 5 | 0 | 0.15 |
| 6 | 0 | 0.05 |

#### Model B

| Observation | True $$y$$ | Predicted probability |
|---|---:|---:|
| 1 | 1 | 0.65 |
| 2 | 0 | 0.60 |
| 3 | 1 | 0.55 |
| 4 | 0 | 0.45 |
| 5 | 1 | 0.40 |
| 6 | 0 | 0.35 |

1. Which model has the higher AUC? Show enough work to justify your answer.
2. For each model, compare:
   - the average predicted probability among the top 3 observations
   - the actual positive rate among the top 3 observations
   - the average predicted probability among the bottom 3 observations
   - the actual positive rate among the bottom 3 observations
3. Which model looks better calibrated?
4. Briefly explain why AUC and calibration are different questions.

---

## B. Random Forest versus Gradient Boosting

### B1. True/False

Mark each statement as **True** or **False**.

1. In random forest, the trees are built independently and then averaged.
2. In gradient boosting, each new tree is built after the previous ones and tries to improve the current model.
3. Random forest is best understood as “many trees making small corrections one after another.”
4. Both random forest and gradient boosting can capture interactions automatically.
5. If a model has a higher AUC, it must also be better calibrated.
6. AUC is a ranking metric rather than a calibration metric.

---

### B2. Compare the two ensemble methods

Fill in the blanks using the phrases below. You can use each phrase once.

- **averaging many trees**
- **sequentially correcting mistakes**
- **reducing variance**
- **improving fit step by step**

1. Random forest is mainly about ____________________.
2. Random forest is often explained as ____________________.
3. Gradient boosting is mainly about ____________________.
4. Gradient boosting is often explained as ____________________.

---

## C. Interactions

### C1. Which models can capture this automatically?

Suppose the effect of `age` on risk depends strongly on whether someone was previously `ROR'ed`. In other words, the relationship between `age` and the outcome looks different for different values of `ROR`.

For each model below, say whether it can capture that interaction **automatically** or only if the interaction is added manually.

1. Logistic regression with only main effects for `age` and `ROR`
2. Logistic regression with an `age × ROR` interaction term added by hand
3. Random forest
4. Gradient boosting

---

### C2. Short interpretation

In one or two sentences: why are tree-based models often appealing when we think interactions may matter?

---

# Answers

## A. AUC

### A1.
There are $$3 \times 3 = 9$$ positive-negative pairs.

- Positive score 0.90 beats all three negatives: 3 wins
- Positive score 0.70 beats 0.60 and 0.20, but loses to 0.80: 2 wins
- Positive score 0.40 beats only 0.20: 1 win

So the total number of wins is $$3 + 2 + 1 = 6$$.

Therefore,

$$
\text{AUC} = \frac{6}{9} = \frac{2}{3} \approx 0.667.
$$

Interpretation: if we randomly choose one positive case and one negative case, the model gives the positive case the higher score about 66.7% of the time.

---

### A2.
#### 1. Which model has the higher AUC?

**Model A**

Positives have scores $$0.95, 0.85, 0.25$$.  
Negatives have scores $$0.75, 0.15, 0.05$$.

- 0.95 beats all 3 negatives
- 0.85 beats all 3 negatives
- 0.25 beats 0.15 and 0.05, but loses to 0.75

So Model A has $$3 + 3 + 2 = 8$$ wins out of 9 pairs:

$$
\text{AUC}_A = \frac{8}{9} \approx 0.889.
$$

**Model B**

Positives have scores $$0.65, 0.55, 0.40$$.  
Negatives have scores $$0.60, 0.45, 0.35$$.

- 0.65 beats all 3 negatives
- 0.55 beats 0.45 and 0.35, but loses to 0.60
- 0.40 beats only 0.35

So Model B has $$3 + 2 + 1 = 6$$ wins out of 9 pairs:

$$
\text{AUC}_B = \frac{6}{9} \approx 0.667.
$$

So **Model A has the higher AUC**.

#### 2. Top 3 versus bottom 3

**Model A**

- Top 3 predicted probabilities: $$0.95, 0.85, 0.75$$
- Average predicted probability in top 3:
  $$
  \frac{0.95 + 0.85 + 0.75}{3} = 0.85
  $$
- Actual positive rate in top 3: $$2/3 \approx 0.667$$

- Bottom 3 predicted probabilities: $$0.25, 0.15, 0.05$$
- Average predicted probability in bottom 3:
  $$
  \frac{0.25 + 0.15 + 0.05}{3} = 0.15
  $$
- Actual positive rate in bottom 3: $$1/3 \approx 0.333$$

**Model B**

- Top 3 predicted probabilities: $$0.65, 0.60, 0.55$$
- Average predicted probability in top 3:
  $$
  \frac{0.65 + 0.60 + 0.55}{3} = 0.60
  $$
- Actual positive rate in top 3: $$2/3 \approx 0.667$$

- Bottom 3 predicted probabilities: $$0.45, 0.40, 0.35$$
- Average predicted probability in bottom 3:
  $$
  \frac{0.45 + 0.40 + 0.35}{3} = 0.40
  $$
- Actual positive rate in bottom 3: $$1/3 \approx 0.333$$

#### 3. Which model looks better calibrated?

**Model B** looks better calibrated, because its average predicted probabilities are closer to the actual rates in both the top and bottom groups.

#### 4. Why are AUC and calibration different questions?

AUC asks whether positives tend to get higher scores than negatives, while calibration asks whether predicted probabilities match observed rates. A model can rank observations well but still give probabilities that are systematically too high or too low.

---

## B. Random Forest versus Gradient Boosting

### B1.
1. True
2. True
3. False
4. True
5. False
6. True

---

### B2.
1. Random forest is mainly about **reducing variance**.
2. Random forest is often explained as **averaging many trees**.
3. Gradient boosting is mainly about **improving fit step by step**.
4. Gradient boosting is often explained as **sequentially correcting mistakes**.

---

## C. Interactions

### C1.
1. Logistic regression with only main effects: **manual only** (it does not capture the interaction automatically)
2. Logistic regression with an `age × ROR` term added: **yes, but only because the interaction was added manually**
3. Random forest: **automatic**
4. Gradient boosting: **automatic**

---

### C2.
Tree-based models are appealing because they can capture interactions without requiring us to specify them ahead of time. Different splits can create different relationships in different parts of the feature space, which lets the model adapt to subgroup-specific patterns.
