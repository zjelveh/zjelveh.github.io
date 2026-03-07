# Lecture 7 Practice Problems (Overfitting + Regularization)

> **How to use this:** Try these before the quiz. If you get stuck, write down what part is confusing:
> (1) what the question is asking, (2) what quantity you should compute/compare, or (3) arithmetic.

> **Notation reminders:**
> - Throughout, $$P ( A , B )$$ means the joint probability $$P ( A \cap B )$$.
> - Use “given” to read conditionals: $$P ( A \mid B )$$.

---

## A. Overfitting: training error vs test error

You fit polynomial regression models of different degrees to the same training set, and then evaluate on a separate test set.

| Model | Degree | Training SSE | Test SSE |
|---|---:|---:|---:|
| A | 1 | 97.4 | 2148.0 |
| B | 2 | 89.4 | 89.6 |
| C | 3 | 87.0 | 14827.0 |
| D | 4 | 86.7 | 10142.0 |

### A1. Model selection using test error

1. Which model would you choose if your goal is **out-of-sample** performance?
2. Which model looks the most overfit? Why?
3. Which model looks the most underfit? Why?

---

### A2. Why training error can be misleading

1. In the table above, training SSE decreases as degree increases. Why doesn’t that guarantee better predictions on the test set?
2. If you did **not** have a test set, what is the usual practical approach for choosing model complexity?

---

## B. Regularization: ridge vs lasso objectives (compute by hand)

You are comparing models using objective functions.

- **OLS objective:** $$\text{SSE} = \sum_i (y_i - \hat{y}_i)^2$$
- **Ridge objective:** $$\text{SSE} + \lambda \sum_j \beta_j^2$$
- **Lasso objective:** $$\text{SSE} + \lambda \sum_j |\beta_j|$$

### B1. Compute ridge and lasso objectives

Suppose a model has:

- $$\text{SSE} = 100$$
- coefficients $$\beta = (2, -1, 0.5)$$ (ignore the intercept for the penalty)
- $$\lambda = 10$$

1. Compute the ridge penalty term $$\lambda \sum_j \beta_j^2$$ and the ridge objective value.
2. Compute the lasso penalty term $$\lambda \sum_j |\beta_j|$$ and the lasso objective value.

---

### B2. Compare two coefficient vectors

Two models fit the training data equally well:

- Model A: $$\text{SSE} = 100$$, $$\beta = (3, 0, 0)$$
- Model B: $$\text{SSE} = 100$$, $$\beta = (1, 1, 1)$$

Let $$\lambda = 10$$.

1. Which model has the smaller **ridge** objective?
2. Which model has the smaller **lasso** objective?

---

## C. Bias–variance tradeoff (small simulation by hand)

Suppose the true value at a point is $$f(x_0) = 0.30$$.

You repeatedly resample a training set and refit a model, and you record the prediction $$\hat{f}(x_0)$$ each time.

### C1. Compute bias and variance (approximately)

**Model L (low complexity):**
$$\hat{f}(x_0) \in \{0.10, 0.12, 0.11, 0.09, 0.13\}$$

**Model H (high complexity):**
$$\hat{f}(x_0) \in \{0.00, 0.65, -0.10, 0.55, 0.40\}$$

For each model:

1. Compute the average prediction $$\overline{\hat{f}(x_0)}$$.
2. Compute the bias estimate: $$\overline{\hat{f}(x_0)} - f(x_0)$$.
3. Compute the variance estimate: the average of $$(\hat{f}(x_0) - \overline{\hat{f}(x_0)})^2.$$
4. Which model has higher bias? Which has higher variance?

---

### C2. Ridge as a bias–variance “dial” (conceptual)

In one or two sentences: how does ridge regularization tend to affect **bias** and **variance** compared to an unregularized high-complexity model?

---

## D. True/False (quick checks)

Mark each statement as **True** or **False**.

### D1.
If you add more polynomial terms (higher degree), the training SSE for OLS cannot increase.

### D2.
If Model X has lower training SSE than Model Y, then Model X must also have lower test SSE than Model Y.

### D3.
Ridge regression can set some coefficients exactly equal to 0.

### D4.
Lasso regression can set some coefficients exactly equal to 0.

### D5.
In `sklearn.LogisticRegression`, increasing `C` makes regularization stronger.

### D6.
A validation set (or cross-validation) helps automate model complexity selection.

---

# Answers

## A. Overfitting: training vs test

### A1.
1. Choose **Model B (degree 2)** because it has the smallest test SSE (89.6).
2. **Model C (degree 3)** looks the most overfit here because its test SSE is extremely large despite low training SSE.
3. **Model A (degree 1)** looks the most underfit here because it has the worst test SSE and is the least flexible model.

### A2.
1. Increasing complexity makes it easier to fit noise in the training data, so training error can go down while out-of-sample error goes up.
2. Use a **validation set** or **cross-validation** to pick complexity based on out-of-sample performance (without using the final test set repeatedly).

---

## B. Regularization objectives

### B1.
1. Ridge penalty: $$10(2^2 + (-1)^2 + 0.5^2) = 10(4 + 1 + 0.25) = 52.5$$.  
   Ridge objective: $$100 + 52.5 = 152.5$$.
2. Lasso penalty: $$10(|2| + |-1| + |0.5|) = 10(2 + 1 + 0.5) = 35$$.  
   Lasso objective: $$100 + 35 = 135$$.

### B2.
- Ridge:
  - Model A penalty: $$10(3^2 + 0^2 + 0^2)=90$$ → objective $$190$$.
  - Model B penalty: $$10(1^2 + 1^2 + 1^2)=30$$ → objective $$130$$.
  - So ridge prefers **Model B**.
- Lasso:
  - Model A penalty: $$10(|3|+0+0)=30$$ → objective $$130$$.
  - Model B penalty: $$10(|1|+|1|+|1|)=30$$ → objective $$130$$.
  - So lasso is a **tie** here.

---

## C. Bias–variance

### C1.
**Model L**

1. Average: $$(0.10 + 0.12 + 0.11 + 0.09 + 0.13)/5 = 0.11.$$
2. Bias estimate: $$0.11 - 0.30 = -0.19.$$
3. Variance estimate:
   - Deviations from 0.11: $$-0.01, 0.01, 0, -0.02, 0.02$$
   - Squared: $$0.0001, 0.0001, 0, 0.0004, 0.0004$$
   - Average: $$0.0010/5 = 0.0002.$$

**Model H**

1. Average: $$(0.00 + 0.65 - 0.10 + 0.55 + 0.40)/5 = 0.30.$$
2. Bias estimate: $$0.30 - 0.30 = 0.$$
3. Variance estimate:
   - Deviations from 0.30: $$-0.30, 0.35, -0.40, 0.25, 0.10$$
   - Squared: $$0.09, 0.1225, 0.16, 0.0625, 0.01$$
   - Average: $$0.445/5 = 0.089.$$

4. Model L has **higher bias** and **lower variance**. Model H has **lower bias** and **higher variance**.

### C2.
Ridge regularization typically **reduces variance** (predictions become less sensitive to the specific training sample) while **increasing bias** (because coefficients are shrunk toward 0).

---

## D. True/False

- D1: True.
- D2: False.
- D3: False.
- D4: True.
- D5: False. (Larger `C` means weaker regularization.)
- D6: True.
