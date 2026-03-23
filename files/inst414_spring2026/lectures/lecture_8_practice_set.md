# Lecture 8 Practice Problems (Decision Trees)

> **How to use this:** Try these before the quiz. If you get stuck, write down what part is confusing:
> (1) what the question is asking, (2) what quantity you should compute/compare, or (3) arithmetic.

> **Notation reminders:**
> - Throughout, $$P ( A , B )$$ means the joint probability $$P ( A \cap B )$$.
> - Use “given” to read conditionals: $$P ( A \mid B )$$.

---

## A. Trees as probability models (leaf rates)

In a **classification** tree, a common prediction rule is:

- In each terminal leaf, estimate $$\widehat{P}(y=1 \mid x)$$ as the **fraction of training examples in that leaf with** $$y=1$$.
- Classify as $$\hat{y}=1$$ if $$\widehat{P}(y=1 \mid x) \ge 0.5$$ (you can use 0.5 unless told otherwise).

Suppose a decision tree routes a new person with features $$x$$ into a leaf that contains the following **training counts**:

| Outcome in the leaf | Count |
|---|---:|
| $$y=1$$ | 18 |
| $$y=0$$ | 42 |

### A1.
1. Compute $$\widehat{P}(y=1 \mid x)$$.
2. What class does the tree predict for this person using a 0.5 threshold?

---

## B. Choosing splits (Gini impurity)

For a node with binary outcomes:

- $$\hat{p}_1$$ = fraction with $$y=1$$ in the node
- $$\hat{p}_0$$ = fraction with $$y=0$$ in the node

The **Gini impurity** is:
$$
G = 1 - \hat{p}_1^2 - \hat{p}_0^2.
$$

You are at a parent node with 40 training examples:

- 16 have $$y=1$$
- 24 have $$y=0$$

You consider splitting on a binary feature $$X$$ into **left** ($$X=0$$) and **right** ($$X=1$$):

- Left child ($$X=0$$): 10 with $$y=1$$, 10 with $$y=0$$ (20 total)
- Right child ($$X=1$$): 6 with $$y=1$$, 14 with $$y=0$$ (20 total)

### B1.
1. Compute the Gini impurity of the **parent** node.
2. Compute the Gini impurity of the **left** child and **right** child.
3. Compute the **weighted average** Gini impurity after the split.
4. Compute the **Gini reduction** from the split (parent impurity minus weighted child impurity).

---

## C. Regression trees: splits that reduce SSE

For a **regression** tree, the prediction in each leaf is often the **average** $$\hat{y}$$ of the training outcomes in that leaf.

This makes tree fitting closely connected to minimizing the **least squares objective**:
$$
\text{SSE} = \sum_i (y_i - \hat{y}_i)^2.
$$

You have 6 training points with a single feature $$x$$ and numeric outcome $$y$$:

| i | $$x_i$$ | $$y_i$$ |
|---:|---:|---:|
| 1 | 1 | 1 |
| 2 | 2 | 1 |
| 3 | 3 | 2 |
| 4 | 4 | 8 |
| 5 | 5 | 9 |
| 6 | 6 | 9 |

Consider a split that sends $$x \le 3$$ to the left leaf and $$x > 3$$ to the right leaf.

### C1.
1. Compute the left-leaf prediction (mean $$y$$ for $$x \le 3$$) and the right-leaf prediction (mean $$y$$ for $$x > 3$$).
2. Compute the total SSE for this 2-leaf regression tree.

### C2. (Conceptual)
In 1–2 sentences: why can a regression tree overfit if we keep splitting until each leaf has very few points?

---

## D. Overfitting and tree depth

You train decision trees of different max depths and evaluate accuracy on training and test sets:

| Max depth | Training accuracy | Test accuracy |
|---:|---:|---:|
| 1 | 0.69 | 0.67 |
| 2 | 0.76 | 0.73 |
| 3 | 0.83 | 0.75 |
| 4 | 0.92 | 0.71 |
| 6 | 0.99 | 0.65 |

### D1.
1. Which max depth would you choose if your goal is out-of-sample performance?
2. Which model looks the most overfit? Why?
3. Which model looks the most underfit? Why?

---

## E. True/False (quick checks)

Mark each statement as **True** or **False**.

### E1.
If you increase max depth, training error for a decision tree cannot increase.

### E2.
Decision trees can represent interaction effects (where the relationship between a feature and $$y$$ depends on another feature) without you manually creating interaction terms.

### E3.
A good way to pick max depth is to choose the depth with the best validation-set (or cross-validated) performance.

---

# Answers

## A. Leaf rates

### A1.
1. $$\widehat{P}(y=1 \mid x) = 18 / (18 + 42) = 18/60 = 0.30.$$
2. Since $$0.30 < 0.5$$, the predicted class is $$\hat{y}=0$$.

---

## B. Gini impurity

### B1.
Parent node: $$\hat{p}_1 = 16/40 = 0.40$$, $$\hat{p}_0 = 24/40 = 0.60$$.

1. Parent Gini:
   $$
   G_\text{parent} = 1 - 0.40^2 - 0.60^2 = 1 - 0.16 - 0.36 = 0.48.
   $$

Left child: $$\hat{p}_1 = 10/20 = 0.50$$, $$\hat{p}_0 = 10/20 = 0.50$$.

2. Left Gini:
   $$
   G_L = 1 - 0.50^2 - 0.50^2 = 1 - 0.25 - 0.25 = 0.50.
   $$

Right child: $$\hat{p}_1 = 6/20 = 0.30$$, $$\hat{p}_0 = 14/20 = 0.70$$.

Right Gini:
   $$
   G_R = 1 - 0.30^2 - 0.70^2 = 1 - 0.09 - 0.49 = 0.42.
   $$

3. Weighted child Gini:
   $$
   G_\text{children} = (20/40)G_L + (20/40)G_R = 0.5(0.50) + 0.5(0.42) = 0.46.
   $$

4. Gini reduction:
   $$
   G_\text{parent} - G_\text{children} = 0.48 - 0.46 = 0.02.
   $$

---

## C. Regression trees and SSE

### C1.
Left leaf ($$x \le 3$$) has $$y = \{1, 1, 2\}$$ so the mean is:
$$
\hat{y}_L = (1+1+2)/3 = 4/3 \approx 1.333.
$$

Right leaf ($$x > 3$$) has $$y = \{8, 9, 9\}$$ so the mean is:
$$
\hat{y}_R = (8+9+9)/3 = 26/3 \approx 8.667.
$$

### C1 (cont.).
SSE is the sum of squared errors within each leaf.

Left SSE:
$$
(1-4/3)^2 + (1-4/3)^2 + (2-4/3)^2
= ( -1/3 )^2 + ( -1/3 )^2 + (2/3)^2
= 1/9 + 1/9 + 4/9 = 6/9 = 2/3.
$$

Right SSE:
$$
(8-26/3)^2 + (9-26/3)^2 + (9-26/3)^2
= ( -2/3 )^2 + (1/3)^2 + (1/3)^2
= 4/9 + 1/9 + 1/9 = 6/9 = 2/3.
$$

Total SSE:
$$
\text{SSE} = 2/3 + 2/3 = 4/3 \approx 1.333.
$$

### C2.
If we keep splitting until leaves contain very few points, the tree can “memorize” noise in the training set (very low training error) but generalize poorly to new data (higher test error).

---

## D. Depth and overfitting

### D1.
1. Choose max depth **3** (best test accuracy, 0.75).
2. Max depth **6** looks the most overfit: training accuracy is almost perfect (0.99) but test accuracy is the worst (0.65).
3. Max depth **1** looks the most underfit: it is the least flexible and has relatively low training and test accuracy.

---

## E. True/False

- E1: True.
- E2: True.
- E3: True.

