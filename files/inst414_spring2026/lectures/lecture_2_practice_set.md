# Lecture 2 Practice Problems (Probability Distributions + Event Spaces)

---

## Questions

### A. Probability distributions (one variable)

1. $$X$$ can take on values of either 0 or 1, where $$X=1$$ means “FTA” and $$X=0$$ means “No FTA.”

   You are told $$P(X=1)=0.148$$.
   
   1.1. What is $$P(X=0)$$?
     
   1.2. What property must the outcomes $$\{0,1\}$$ satisfy for this to define a valid distribution?

2. $$Y$$ is a random variable that takes three values \{0, 1, 2}\.
  
   A proposed distribution for $$Y$$ is:
   - $$P(Y=0)=0.40$$
   - $$P(Y=1)=0.35$$
   - $$P(Y=2)=0.35$$

   2.1. Is this a valid probability distribution?  
   2.2. If not, fix it by changing **only one** probability.

3. In a dataset of 500 website visits, 74 visits resulted in a purchase.
  
   $$W$$ is random variabale that can be either 0 or 1, where $$W=1$$ means “purchase” and $$W=0$$ means “no purchase.”  

   3.1. Compute $$P(W=1)$$ and $$P(W=0)$$.  

---

### B. Event spaces (two attributes)

4. A standard 52-card deck. Consider two attributes:
   - $$Color$$ can be Red or Black
   - $$Value$$ can be   \{Ace,2,...,10,Jack,Queen,King\}

   4.1. How many outcomes are in the event space (Color, Value)?  
   4.2. How many outcomes are in the event space (Color) if Value is **included**?

---

### C. Joint probability tables, marginals, and conditionals

5. A bag contains 20 marbles with two attributes: **Color** $$\in \{\text{Red}, \text{Blue}\}$$ and **Size** $$\in \{\text{Small}, \text{Large}\}$$.  
   The counts are:

|                | $$Size=Small$$ | $$Size=Large$$ | Total |
|---|---:|---:|---:|
| $$Color=Red$$  | 6 | 4 | 10 |
| $$Color=Blue$$ | 3 | 7 | 10 |
| **Total**      | 9 | 11 | 20 |

   5.1. Convert the **counts** table into a **joint probability** table for $$P(Color, Size)$$. (Make a new 2×2 table of probabilities.)  
   5.2. Compute the marginal probability $$P(Color=\text{Red})$$.  
   5.3. Compute the marginal probability $$P(Size=\text{Small})$$.  

6. Let $$A \in \{0,1\}$$ and $$B \in \{0,1\}$$ be two binary variables. You’re given the following **joint probability table**:

|        | $$B=0$$ | $$B=1$$ | Total |
|---|---:|---:|---:|
| $$A=0$$ | 0.50 | 0.10 | 0.60 |
| $$A=1$$ | 0.20 | 0.20 | 0.40 |
| **Total** | 0.70 | 0.30 | 1.00 |

   6.1. Verify that this is a valid joint probability distribution.  
   6.2. Compute the marginal distribution of $$A$$ (i.e., $$P(A=0)$$ and $$P(A=1)$$).  
   6.3. Compute the marginal distribution of $$B$$ (i.e., $$P(B=0)$$ and $$P(B=1)$$).  
   
---

### D. Joint distributions

Suppose you’re looking at a (hypothetical) forecasting model for the 2028 U.S. elections. The model outputs a **joint probability distribution** over who controls the House and who controls the Senate after the election. Let:

- $$H \in \{D,R\}$$ denote which party wins the House (Democrats/Republicans)
- $$S \in \{D,R\}$$ denote which party wins the Senate

You are told:
- $$P(H=D, S=D)=0.4$$
- $$P(H=R, S=D)=0.1$$
- $$P(H=D, S=R)=0.2$$

7. Fill in the missing joint probability $$P(H=R, S=R)$$ and write the full joint table:

|        | $$S=D$$ | $$S=R$$ | Total |
|---|---:|---:|---:|
| $$H=D$$ | 0.4 | 0.2 | ? |
| $$H=R$$ | 0.1 | ? | ? |
| **Total** | ? | ? | 1.0 |

8. Compute the marginal probability $$P(H=D)$$.

9. Compute the marginal probability $$P(S=R)$$.

---

## Answers

### A. Probability distributions (one variable)

1.1. $$P(X=0)=1-0.148=0.852$$.  
1.2. The outcomes must be **mutually exclusive** (can’t both happen) and **collectively exhaustive** (one of them must happen).

2.1. Not valid, because the probabilities sum to $$0.40+0.35+0.35=1.10$$, which is greater than 1.  
2.2. One fix: change $$P(Y=2)$$ from $$0.35$$ to $$0.25$$ so the total is $$0.40+0.35+0.25=1.00$$.  
(Any single-probability change that makes the sum exactly 1 and keeps probabilities between 0 and 1 is acceptable.)

3.1. $$P(W=1)=74/500=0.148$$ and $$P(W=0)=426/500=0.852$$.  

---

### B. Event spaces (two attributes)

4.1. Corresponds to the full deck: **52** outcomes.  
4.2. Corresponds to $$2$$ colors/outcomes.

---

### C. Joint probability tables, marginals, and conditionals

5.1. Divide each cell by 20:

|                | $$Size=Small$$ | $$Size=Large$$ | Total |
|---|---:|---:|---:|
| $$Color=Red$$  | $$6/20=0.30$$ | $$4/20=0.20$$ | $$10/20=0.50$$ |
| $$Color=Blue$$ | $$3/20=0.15$$ | $$7/20=0.35$$ | $$10/20=0.50$$ |
| **Total**      | $$9/20=0.45$$ | $$11/20=0.55$$ | 1.00 |

5.2. $$P(Color=\text{Red})=10/20=0.50$$.  
5.3. $$P(Size=\text{Small})=9/20=0.45$$.  


6.1. All probabilities are between 0 and 1, and the four joint cells sum to
$$0.50+0.10+0.20+0.20=1.00$$, so it’s valid.  
6.2. $$P(A=0)=0.60$$ and $$P(A=1)=0.40$$ (from the row totals).  
6.3. $$P(B=0)=0.70$$ and $$P(B=1)=0.30$$ (from the column totals).  

---

### D. Joint distributions (2028 Election Cycle)

7. First compute the missing cell:
$$P(H=R,S=R)=1-(0.4+0.1+0.2)=1-0.7=0.3.$$  
Now the completed joint table is:

|        | $$S=D$$ | $$S=R$$ | Total |
|---|---:|---:|---:|
| $$H=D$$ | 0.4 | 0.2 | 0.6 |
| $$H=R$$ | 0.1 | 0.3 | 0.4 |
| **Total** | 0.5 | 0.5 | 1.0 |

8. $$P(H=D)=0.4+0.2=0.6$$.  
9. $$P(S=R)=0.2+0.3=0.5$$.  

