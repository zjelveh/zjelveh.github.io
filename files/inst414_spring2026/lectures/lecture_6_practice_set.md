# Lecture 6 Practice Problems (Calibration + Regression)

> **How to use this:** Try these before the quiz. If you get stuck, write down what part is confusing:
> (1) defining variables/events, (2) setting up the right probability expression, or (3) arithmetic.

> **Notation reminders:**
> - Throughout, $$P ( A , B )$$ means the joint probability $$P ( A \cap B )$$.
> - Use “given” to read conditionals: $$P ( A \mid B )$$.

---

## A. Bayes rule vs naive Bayes (counts + conditional independence)

Let $$Y \in \{ 0 , 1 \}$$ be the outcome, and let $$X_1, X_2 \in \{ 0 , 1 \}$$ be two binary predictors.

You observe the following **counts** in a labeled dataset.

### Counts when $$Y = 1$$

| $$X_1$$ | $$X_2$$ | Count |
|---:|---:|---:|
| 0 | 0 | 10 |
| 0 | 1 | 6 |
| 1 | 0 | 14 |
| 1 | 1 | 10 |

### Counts when $$Y = 0$$

| $$X_1$$ | $$X_2$$ | Count |
|---:|---:|---:|
| 0 | 0 | 20 |
| 0 | 1 | 4 |
| 1 | 0 | 6 |
| 1 | 1 | 30 |

### A1. Compute $$P ( Y = 1 \mid X_1 = 1 , X_2 = 0 )$$ directly from counts

1. Compute the count of observations with $$X_1 = 1 , X_2 = 0$$.
2. Compute $$P ( Y = 1 \mid X_1 = 1 , X_2 = 0 )$$ as a fraction of counts.
---

### A2. Compute the same probability using Bayes rule (still using the same counts)

Using Bayes rule,
$$P ( Y = 1 \mid X_1 = 1 , X_2 = 0 ) = \frac{ P ( X_1 = 1 , X_2 = 0 \mid Y = 1 ) P ( Y = 1 ) }{ P ( X_1 = 1 , X_2 = 0 ) }.$$

1. Compute $$P ( Y = 1 )$$.
2. Compute $$P ( X_1 = 1 , X_2 = 0 \mid Y = 1 )$$.
3. Compute $$P ( X_1 = 1 , X_2 = 0 )$$.
4. Plug in and verify you get the same answer as A1.

---

### A3. Bayes rule with a conditional independence approximation

Assume $$X_1$$ and $$X_2$$ are conditionally independent given $$Y$$:
$$P ( X_1 = 1 , X_2 = 0 \mid Y = 1 ) = P ( X_1 = 1 \mid Y = 1 ) P ( X_2 = 0 \mid Y = 1 ).$$

1. Compute $$P ( Y = 1 )$$.
2. Compute $$P ( X_1 = 1 \mid Y = 1 )$$ and $$P ( X_2 = 0 \mid Y = 1 )$$.
3. Use the conditional independence assumption to compute $$P ( X_1 = 1 , X_2 = 0 \mid Y = 1 )$$.
4. Compute $$P ( X_1 = 1 , X_2 = 0 )$$ directly from the overall table (ignore $$Y$$).
5. Use Bayes rule to compute an *approximation* to the desired probability:
   $$\widehat{P} ( Y = 1 \mid X_1 = 1 , X_2 = 0 ) = \frac{ P ( X_1 = 1 , X_2 = 0 \mid Y = 1 ) P ( Y = 1 ) }{ P ( X_1 = 1 , X_2 = 0 ) }.$$
6. Compare your approximation to the true answer from A1.

---

## B. Least squares objective (compute by hand)

Suppose you have three data points:

| $$x$$ | $$y$$ |
|---:|---:|
| 1 | 1 |
| 2 | 2 |
| 3 | 2 |

Consider two candidate prediction rules (two lines):

- **Model A:** $$\hat{y} = 0 + 1 \cdot x$$
- **Model B:** $$\hat{y} = 1 + 0.5 \cdot x$$

For each model, compute the **sum of squared errors** (SSE):
$$\text{SSE} = \sum_{i=1}^N ( y_i - \hat{y}_i )^2.$$

1. For Model A, compute $$\hat{y}_i$$ for each point, then compute SSE.
2. For Model B, compute $$\hat{y}_i$$ for each point, then compute SSE.
3. Which model fits better under the least squares objective?

---

## C. Calibration (true/false)

Mark each statement as **True** or **False**.

### C1.
If a classifier is calibrated, then among cases where it predicts probability 0.70, about 70% should actually have $$Y = 1$$.

### C2.
A “calibration plot” (reliability curve) compares predicted probabilities to the actual fraction of $$Y=1$$ within bins of similar predicted probability.

### C3.
Naive Bayes can be useful for classification even if its predicted probabilities are miscalibrated.

---

# Answers

## A. Bayes rule vs naive Bayes

First compute some totals:

- Total with $$Y = 1$$: $$10 + 6 + 14 + 10 = 40$$.
- Total with $$Y = 0$$: $$20 + 4 + 6 + 30 = 60$$.
- Total observations: $$N = 40 + 60 = 100$$.

### A1.
1. Count with $$X_1 = 1 , X_2 = 0$$ is $$14 + 6 = 20$$.
2. $$P ( Y = 1 \mid X_1 = 1 , X_2 = 0 ) = 14 / 20 = 0.700$$.

### A2.
1. $$P ( Y = 1 ) = 40 / 100 = 0.400$$.
2. $$P ( X_1 = 1 , X_2 = 0 \mid Y = 1 ) = 14 / 40 = 0.350$$.
3. $$P ( X_1 = 1 , X_2 = 0 ) = 20 / 100 = 0.200$$.
4. Bayes rule gives:
   $$P ( Y = 1 \mid X_1 = 1 , X_2 = 0 ) = \frac{ 0.350 \cdot 0.400 }{ 0.200 } = \frac{ 0.140 }{ 0.200 } = 0.700.$$

### A3.
1. $$P ( Y = 1 ) = 40 / 100 = 0.400$$.
2. $$P ( X_1 = 1 \mid Y = 1 ) = (14 + 10) / 40 = 24 / 40 = 0.600$$ and $$P ( X_2 = 0 \mid Y = 1 ) = (10 + 14) / 40 = 24 / 40 = 0.600$$.
3. Conditional independence approximation:
   $$P ( X_1 = 1 , X_2 = 0 \mid Y = 1 ) \approx 0.600 \cdot 0.600 = 0.360.$$
4. $$P ( X_1 = 1 , X_2 = 0 ) = 20 / 100 = 0.200$$.
5. Bayes rule approximation:
   $$\widehat{P} ( Y = 1 \mid X_1 = 1 , X_2 = 0 ) \approx \frac{ 0.360 \cdot 0.400 }{ 0.200 } = 0.720.$$
6. Comparison: the true probability is $$0.700$$ (A1) and the conditional-independence-based approximation gives $$0.720$$.

---

## B. Least squares objective

### Model A: $$\hat{y} = x$$

- When $$x=1$$: $$\hat{y}=1$$, residual $$1-1=0$$, squared error $$0$$.
- When $$x=2$$: $$\hat{y}=2$$, residual $$2-2=0$$, squared error $$0$$.
- When $$x=3$$: $$\hat{y}=3$$, residual $$2-3=-1$$, squared error $$1$$.

So $$\text{SSE}_A = 1$$.

### Model B: $$\hat{y} = 1 + 0.5x$$

- When $$x=1$$: $$\hat{y}=1.5$$, residual $$1-1.5=-0.5$$, squared error $$0.25$$.
- When $$x=2$$: $$\hat{y}=2$$, residual $$2-2=0$$, squared error $$0$$.
- When $$x=3$$: $$\hat{y}=2.5$$, residual $$2-2.5=-0.5$$, squared error $$0.25$$.

So $$\text{SSE}_B = 0.50$$.

Model B fits better because it has the smaller SSE.

---

## C. Calibration (true/false)

### C1.
True.

### C2.
True.

### C3.
True.
