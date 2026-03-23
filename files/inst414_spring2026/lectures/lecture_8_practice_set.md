# Lecture 8 Practice Problems (Decision Trees)

> **How to use this:** Try these before the quiz. If you get stuck, write down what part is confusing:
> (1) what the question is asking, (2) what quantity you should compute/compare, or (3) arithmetic.

> **Notation reminders:**
> - Throughout, $$P ( A , B )$$ means the joint probability $$P ( A \cap B )$$.
> - Use “given” to read conditionals: $$P ( A \mid B )$$.

---

## A. Interaction effects (why trees help)

An **interaction effect** (informal definition for this class) means:

> The relationship between $$X_1$$ and $$Y$$ depends on the value of $$X_2$$.

### A1. Check for an interaction using conditional probabilities

You observe the following counts:

| $$X_1$$ | $$X_2$$ | $$y=1$$ count | $$y=0$$ count |
|---:|---:|---:|---:|
| 0 | 0 | 2 | 18 |
| 1 | 0 | 6 | 14 |
| 0 | 1 | 14 | 6 |
| 1 | 1 | 8 | 12 |

1. Compute $$P(y=1 \mid X_1=x_1, X_2=x_2)$$ for each of the four combinations.
2. Compute the effect of changing $$X_1$$ from 0 to 1 **when $$X_2=0$$**:
   $$P(y=1 \mid X_1=1, X_2=0) - P(y=1 \mid X_1=0, X_2=0).$$
3. Compute the effect of changing $$X_1$$ from 0 to 1 **when $$X_2=1$$**:
   $$P(y=1 \mid X_1=1, X_2=1) - P(y=1 \mid X_1=0, X_2=1).$$
4. Based on (2) and (3), would you say there is an interaction between $$X_1$$ and $$X_2$$ for predicting $$y$$? Explain in 1–2 sentences.

---

### A2. XOR pattern (a classic interaction)

Suppose a dataset has the following counts:

| $$X_1$$ | $$X_2$$ | $$y=1$$ count | $$y=0$$ count |
|---:|---:|---:|---:|
| 0 | 0 | 0 | 25 |
| 0 | 1 | 25 | 0 |
| 1 | 0 | 25 | 0 |
| 1 | 1 | 0 | 25 |

1. Describe the pattern in words: when does $$y=1$$ happen?
2. Draw a depth-2 decision tree (root split, then one more level of splits) that perfectly predicts $$y$$ from $$X_1$$ and $$X_2$$.
3. Using the leaf-rate rule, what are the leaf probabilities $$\widehat{P}(y=1 \mid \text{leaf})$$ for each terminal leaf in your tree?

---

## B. Trees as probability models (leaf rates)

In a **classification** tree, a common prediction rule is:

- In each terminal leaf, estimate $$\widehat{P}(y=1 \mid x)$$ as the **fraction of training examples in that leaf with** $$y=1$$.
- Classify as $$\hat{y}=1$$ if $$\widehat{P}(y=1 \mid x) \ge 0.5$$ (you can use 0.5 unless told otherwise).

Suppose a decision tree routes a new person with features $$x$$ into a leaf that contains the following **training counts**:

| Outcome in the leaf | Count |
|---|---:|
| $$y=1$$ | 18 |
| $$y=0$$ | 42 |

### B1.
1. Compute $$\widehat{P}(y=1 \mid x)$$.
2. What class does the tree predict for this person using a 0.5 threshold?

---

## C. Choosing splits (Gini impurity)

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

### C1.
1. Compute the Gini impurity of the **parent** node.
2. Compute the Gini impurity of the **left** child and **right** child.
3. Compute the **weighted average** Gini impurity after the split.
4. Compute the **Gini reduction** from the split (parent impurity minus weighted child impurity).

---

## D. Regression trees: splits that reduce SSE

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

### D1.
1. Compute the left-leaf prediction (mean $$y$$ for $$x \le 3$$) and the right-leaf prediction (mean $$y$$ for $$x > 3$$).
2. Compute the total SSE for this 2-leaf regression tree.

### D2. (Conceptual)
In 1–2 sentences: why can a regression tree overfit if we keep splitting until each leaf has very few points?

---

## E. Overfitting and tree depth

You train decision trees of different max depths and evaluate accuracy on training and test sets:

| Max depth | Training accuracy | Test accuracy |
|---:|---:|---:|
| 1 | 0.69 | 0.67 |
| 2 | 0.76 | 0.73 |
| 3 | 0.83 | 0.75 |
| 4 | 0.92 | 0.71 |
| 6 | 0.99 | 0.65 |

### E1.
1. Which max depth would you choose if your goal is out-of-sample performance?
2. Which model looks the most overfit? Why?
3. Which model looks the most underfit? Why?

---

## F. True/False (quick checks)

Mark each statement as **True** or **False**.

### F1.
If you increase max depth, training error for a decision tree cannot increase.

### F2.
Decision trees can represent interaction effects (where the relationship between a feature and $$y$$ depends on another feature) without you manually creating interaction terms.

### F3.
A good way to pick max depth is to choose the depth with the best validation-set (or cross-validated) performance.

---

# Answers

## A. Interaction effects

### A1.
1. Compute conditional probabilities:
   - $$P(y=1 \mid X_1=0, X_2=0) = 2/(2+18) = 2/20 = 0.10.$$
   - $$P(y=1 \mid X_1=1, X_2=0) = 6/(6+14) = 6/20 = 0.30.$$
   - $$P(y=1 \mid X_1=0, X_2=1) = 14/(14+6) = 14/20 = 0.70.$$
   - $$P(y=1 \mid X_1=1, X_2=1) = 8/(8+12) = 8/20 = 0.40.$$
2. When $$X_2=0$$, the effect of changing $$X_1: 0 \\to 1$$ is:
   $$0.30 - 0.10 = 0.20.$$
3. When $$X_2=1$$, the effect of changing $$X_1: 0 \\to 1$$ is:
   $$0.40 - 0.70 = -0.30.$$
4. Yes: the effect of $$X_1$$ depends on $$X_2$$ (it even changes sign), which is exactly what we mean by an interaction in this class.

### A2.
1. $$y=1$$ happens when exactly one of $$X_1$$ and $$X_2$$ is 1 (i.e., they are different).
2. One correct depth-2 tree:
   - Split on $$X_1$$ at the root.
   - Then split on $$X_2$$ in each child node.
3. Each terminal leaf is “pure” in this dataset, so the leaf probabilities are either 0 or 1:
   - Leaf ($$X_1=0, X_2=0$$): $$\widehat{P}(y=1)=0.$$
   - Leaf ($$X_1=0, X_2=1$$): $$\widehat{P}(y=1)=1.$$
   - Leaf ($$X_1=1, X_2=0$$): $$\widehat{P}(y=1)=1.$$
   - Leaf ($$X_1=1, X_2=1$$): $$\widehat{P}(y=1)=0.$$

---

## B. Leaf rates

### B1.
1. $$\widehat{P}(y=1 \mid x) = 18 / (18 + 42) = 18/60 = 0.30.$$
2. Since $$0.30 < 0.5$$, the predicted class is $$\hat{y}=0$$.

---

## C. Gini impurity

### C1.
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

## D. Regression trees and SSE

### D1.
Left leaf ($$x \le 3$$) has $$y = \{1, 1, 2\}$$ so the mean is:
$$
\hat{y}_L = (1+1+2)/3 = 4/3 \approx 1.333.
$$

Right leaf ($$x > 3$$) has $$y = \{8, 9, 9\}$$ so the mean is:
$$
\hat{y}_R = (8+9+9)/3 = 26/3 \approx 8.667.
$$

### D1 (cont.).
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

### D2.
If we keep splitting until leaves contain very few points, the tree can “memorize” noise in the training set (very low training error) but generalize poorly to new data (higher test error).

---

## E. Depth and overfitting

### E1.
1. Choose max depth **3** (best test accuracy, 0.75).
2. Max depth **6** looks the most overfit: training accuracy is almost perfect (0.99) but test accuracy is the worst (0.65).
3. Max depth **1** looks the most underfit: it is the least flexible and has relatively low training and test accuracy.

---

## F. True/False

- F1: True.
- F2: True.
- F3: True.
