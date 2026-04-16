# Lecture 11 Practice Problems (Fairness Metrics + Sources of Bias I)

> **How to use this:** Try these before class. If you get stuck, write down what part is confusing:
> (1) what quantity you are supposed to compute, (2) which denominator to use, or (3) what the result means.

> **Notation reminders:**
> - In this set, “positive” means $$y = 1$$ and “negative” means $$y = 0$$.
> - $$\text{FPR} = \frac{\text{FP}}{\text{FP} + \text{TN}}$$
> - $$\text{FNR} = \frac{\text{FN}}{\text{FN} + \text{TP}}$$
> - $$\text{PPV} = \frac{\text{TP}}{\text{TP} + \text{FP}}$$

---

## A. Group-Specific Fairness Metrics

### A1. Compute fairness metrics by group

Suppose a prediction model produces the following confusion matrices. In these tables, rows are **predicted** outcomes and columns are **actual** outcomes.

#### Group A

|  | Actual $$Y=0$$ | Actual $$Y=1$$ |
|---|---:|---:|
| Predicted $$Y=0$$ | 50 | 10 |
| Predicted $$Y=1$$ | 20 | 20 |

#### Group B

|  | Actual $$Y=0$$ | Actual $$Y=1$$ |
|---|---:|---:|
| Predicted $$Y=0$$ | 30 | 5 |
| Predicted $$Y=1$$ | 30 | 35 |

1. Compute the **false positive rate** for each group.
2. Compute the **false negative rate** for each group.
3. Compute the **positive predictive value** for each group.
4. Based on your answers, does the model look equally fair across groups under all three criteria?

---

## B. Threshold Choice and Tradeoffs

### B1. One model, two thresholds

Suppose the same risk model is used with two different thresholds. A lower threshold reaches more people with the intervention, while a higher threshold reaches fewer people.

- **Threshold 1** labels more people as high risk.
- **Threshold 2** labels fewer people as high risk.

For **Group A**, the confusion matrices are:

#### Threshold 1

|  | Actual $$Y=0$$ | Actual $$Y=1$$ |
|---|---:|---:|
| Predicted $$Y=0$$ | 30 | 5 |
| Predicted $$Y=1$$ | 20 | 45 |

#### Threshold 2

|  | Actual $$Y=0$$ | Actual $$Y=1$$ |
|---|---:|---:|
| Predicted $$Y=0$$ | 42 | 18 |
| Predicted $$Y=1$$ | 8 | 32 |

1. Under which threshold are **more people** labeled high risk?
2. Compute the **false positive rate** under each threshold.
3. Compute the **false negative rate** under each threshold.
4. Compute the **positive predictive value** under each threshold.
5. If the intervention is costly and you want to avoid reaching too many people unnecessarily, which threshold looks better?
6. If missing truly high-risk people is especially costly, which threshold looks better?

---

## C. Building the Model

### C1. What changes as the model changes?

Suppose we are predicting a binary outcome $$Y$$ using the following sequence of linear probability models.

**Model 1**
$$
\hat{Y} = \beta_0
$$

**Model 2**
$$
\hat{Y} = \beta_0 + \beta_1 X
$$

**Model 3**
$$
\hat{Y} = \beta_0 + \beta_1 X + \beta_2 G
$$

**Model 4**
$$
\hat{Y} = \beta_0 + \beta_1 X + \beta_2 G + \beta_3 (X \times G)
$$

Here:
- $$X$$ is a predictor
- $$G$$ is a group indicator

1. In Model 1, what does $$\beta_0$$ represent?
2. What new kind of difference can Model 3 capture that Model 2 cannot?
3. What new kind of difference can Model 4 capture that Model 3 cannot?
4. In Model 3, does the effect of $$X$$ have to be the same for both groups? In Model 4, does it have to be the same?

---

## D. Different Base Rates

### D1. Why fairness criteria can conflict

Suppose:
- $$P(Y=1 \mid \text{Group A}) = 0.20$$
- $$P(Y=1 \mid \text{Group B}) = 0.50$$

1. If the two groups have different base rates, why might it be difficult for a model to have both:
   - equal positive predictive value across groups, and
   - equal error rates across groups?
2. You do not need to prove this algebraically. Explain in words.

---

# Answers

## A. Group-Specific Fairness Metrics

### A1.

**Group A**
- $$\text{FPR} = \frac{20}{20 + 50} = \frac{20}{70} \approx 0.286$$
- $$\text{FNR} = \frac{10}{10 + 20} = \frac{10}{30} \approx 0.333$$
- $$\text{PPV} = \frac{20}{20 + 20} = \frac{20}{40} = 0.50$$

**Group B**
- $$\text{FPR} = \frac{30}{30 + 30} = \frac{30}{60} = 0.50$$
- $$\text{FNR} = \frac{5}{5 + 35} = \frac{5}{40} = 0.125$$
- $$\text{PPV} = \frac{35}{35 + 30} = \frac{35}{65} \approx 0.538$$

So the model does **not** look equally fair across groups under all three criteria.
- Group B has a higher FPR,
- Group B has a lower FNR,
- and Group B has a slightly higher PPV.

---

## B. Threshold Choice and Tradeoffs

### B1.

1. **Under which threshold are more people labeled high risk?**  
   Threshold 1, because $$20 + 45 = 65$$ people are labeled high risk under Threshold 1, while $$8 + 32 = 40$$ are labeled high risk under Threshold 2.

2. **False positive rate**  
   - Threshold 1: $$\frac{20}{20 + 30} = \frac{20}{50} = 0.40$$
   - Threshold 2: $$\frac{8}{8 + 42} = \frac{8}{50} = 0.16$$

3. **False negative rate**  
   - Threshold 1: $$\frac{5}{5 + 45} = \frac{5}{50} = 0.10$$
   - Threshold 2: $$\frac{18}{18 + 32} = \frac{18}{50} = 0.36$$

4. **Positive predictive value**  
   - Threshold 1: $$\frac{45}{45 + 20} = \frac{45}{65} \approx 0.692$$
   - Threshold 2: $$\frac{32}{32 + 8} = \frac{32}{40} = 0.80$$

5. **If the intervention is costly and you want to avoid reaching too many people unnecessarily, which threshold looks better?**  
   Threshold 2 looks better because it labels fewer people high risk, has a lower false positive rate, and has a higher PPV.

6. **If missing truly high-risk people is especially costly, which threshold looks better?**  
   Threshold 1 looks better because it has the lower false negative rate.

---

## C. Building the Model

### C1.

1. **In Model 1, what does $$\beta_0$$ represent?**  
   $$\beta_0$$ is the overall average outcome rate, or base rate.

2. **What new kind of difference can Model 3 capture that Model 2 cannot?**  
   Model 3 can allow the average predicted probability to differ across groups.

3. **What new kind of difference can Model 4 capture that Model 3 cannot?**  
   Model 4 can allow the relationship between $$X$$ and $$Y$$ to differ across groups.

4. **In Model 3, does the effect of $$X$$ have to be the same for both groups? In Model 4, does it have to be the same?**  
   In Model 3, yes: the effect of $$X$$ is the same for both groups. In Model 4, no: the interaction term allows the effect of $$X$$ to differ across groups.

---

## D. Different Base Rates

### D1.

1. **Why might it be difficult to have both equal PPV and equal error rates when base rates differ?**  
   If the groups have different base rates, then the same predictions can imply different shares of true positives and false positives across groups. That makes it hard to make all fairness quantities line up at once.

2. **Plain-language explanation**  
   When one group has a higher outcome rate than another, the same prediction rule will usually produce different mixes of true positives, false positives, false negatives, and true negatives across groups. That is why matching PPV and matching error rates can pull in different directions.
