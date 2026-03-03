# Lecture 6 Extra Practice (Independence vs Conditional Independence)

> **How to use this:** Do these *before* looking at the answers. If you get stuck, write down what part is confusing:
> (1) defining events/variables, (2) picking the right numerator/denominator, or (3) arithmetic.

> **Notation + rounding reminders:**
> - Throughout, $$P ( A , B )$$ means the joint probability $$P ( A \cap B )$$.
> - Use “given” to read conditionals: $$P ( A \mid B )$$.
> - Unless otherwise stated, round final probabilities to **3 decimals**.

---

## A. Independence vs conditional independence (by calculation)

Let $$X_1, X_2 \in \{ 0 , 1 \}$$ be two binary variables.

Let $$Z \in \{ 0 , 1 \}$$ be a third binary variable.

You observe the following **counts**.

### When $$Z = 0$$ (100 observations)

|        | $$X_2 = 0$$ | $$X_2 = 1$$ | Total |
|---|---:|---:|---:|
| $$X_1 = 0$$ | 1  | 9  | 10 |
| $$X_1 = 1$$ | 9  | 81 | 90 |
| **Total** | 10 | 90 | 100 |

### When $$Z = 1$$ (100 observations)

|        | $$X_2 = 0$$ | $$X_2 = 1$$ | Total |
|---|---:|---:|---:|
| $$X_1 = 0$$ | 81 | 9 | 90 |
| $$X_1 = 1$$ | 9  | 1 | 10 |
| **Total** | 90 | 10 | 100 |

### A1. Are $$X_1$$ and $$X_2$$ independent?

1. Combine the two tables into a single **overall** count table (ignore $$Z$$).
2. Compute:
   - $$P ( X_1 = 1 )$$
   - $$P ( X_2 = 1 )$$
   - $$P ( X_1 = 1 , X_2 = 1 )$$
3. Check independence using:
   $$P ( X_1 = 1 , X_2 = 1 ) \stackrel{?}{=} P ( X_1 = 1 ) P ( X_2 = 1 ).$$

### A2. Are $$X_1$$ and $$X_2$$ conditionally independent given $$Z$$?

For each value of $$z \in \{ 0 , 1 \}$$, compute:

- $$P ( X_1 = 1 \mid Z = z )$$
- $$P ( X_2 = 1 \mid Z = z )$$
- $$P ( X_1 = 1 , X_2 = 1 \mid Z = z )$$

Then test conditional independence using:
$$P ( X_1 = 1 , X_2 = 1 \mid Z = z ) \stackrel{?}{=} P ( X_1 = 1 \mid Z = z ) P ( X_2 = 1 \mid Z = z ).$$

### A3. Concept check (one sentence)

Does conditional independence given $$Z$$ imply independence (without conditioning)? Use your answers in A1 and A2 to justify.

---

# Answers

## A1.

Overall counts (summing the two $$Z$$ tables):

|        | $$X_2 = 0$$ | $$X_2 = 1$$ | Total |
|---|---:|---:|---:|
| $$X_1 = 0$$ | $$1 + 81 = 82$$ | $$9 + 9 = 18$$ | 100 |
| $$X_1 = 1$$ | $$9 + 9 = 18$$ | $$81 + 1 = 82$$ | 100 |
| **Total** | 100 | 100 | 200 |

So:

- $$P ( X_1 = 1 ) = 100 / 200 = 0.500$$.
- $$P ( X_2 = 1 ) = 100 / 200 = 0.500$$.
- $$P ( X_1 = 1 , X_2 = 1 ) = 82 / 200 = 0.410$$.

Independence check:

- $$P ( X_1 = 1 ) P ( X_2 = 1 ) = 0.500 \cdot 0.500 = 0.250$$.
- But $$P ( X_1 = 1 , X_2 = 1 ) = 0.410$$.

Because $$0.410 \ne 0.250$$, $$X_1$$ and $$X_2$$ are **not** independent.

## A2.

### Given $$Z = 0$$

- $$P ( X_1 = 1 \mid Z = 0 ) = 90 / 100 = 0.900$$.
- $$P ( X_2 = 1 \mid Z = 0 ) = 90 / 100 = 0.900$$.
- $$P ( X_1 = 1 , X_2 = 1 \mid Z = 0 ) = 81 / 100 = 0.810$$.

Product check:

- $$0.900 \cdot 0.900 = 0.810$$.

So $$X_1$$ and $$X_2$$ are conditionally independent given $$Z=0$$.

### Given $$Z = 1$$

- $$P ( X_1 = 1 \mid Z = 1 ) = 10 / 100 = 0.100$$.
- $$P ( X_2 = 1 \mid Z = 1 ) = 10 / 100 = 0.100$$.
- $$P ( X_1 = 1 , X_2 = 1 \mid Z = 1 ) = 1 / 100 = 0.010$$.

Product check:

- $$0.100 \cdot 0.100 = 0.010$$.

So $$X_1$$ and $$X_2$$ are conditionally independent given $$Z=1$$.

Therefore, $$X_1$$ and $$X_2$$ are conditionally independent given $$Z$$.

## A3.

No: this example shows $$X_1$$ and $$X_2$$ are conditionally independent given $$Z$$ (A2) but not independent overall (A1).
