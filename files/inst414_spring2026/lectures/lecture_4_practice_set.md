# Lecture 4 Practice Problems (Independence + Bayes Theorem)

> **How to use this:** Try these before the quiz. If you get stuck, write down what part is confusing:  
> (1) defining events/variables, (2) picking the right numerator and denominator, or (3) arithmetic.

> **Notation + rounding reminders:**
> - Throughout, $$ P ( A , B ) $$ means the joint probability $$ P ( A \cap B ) $$.  
> - Use “given” to read conditionals: $$ P ( A \mid B ) $$.  
> - Unless otherwise stated, round final probabilities to **3 decimals**.

---

## A. Independence (concept + checking with tables)

### A1. Dependence vs independence (studying and passing)
Let $$ S $$ be “studied” and $$ P $$ be “passed”, where $$ S , P \in \{ 0 , 1 \} $$.  

You are told:
- $$ P ( P = 1 ) = 0.48 $$
- $$ P ( P = 1 \mid S = 1 ) = 0.62 $$
- $$ P ( P = 1 \mid S = 0 ) = 0.28 $$

1. Are $$ P $$ and $$ S $$ independent? Explain in one sentence using probabilities.  
2. In plain English: what does it mean that $$ P ( P = 1 \mid S = 1 ) $$ is bigger than $$ P ( P = 1 ) $$?

---

### A2. Chain rule check (warm-up)
Fill in the blanks:

1. $$ P ( A , B ) = P ( A \mid B ) \, P ( \_\_\_\_ ) $$  
2. $$ P ( A , B ) = P ( B \mid A ) \, P ( \_\_\_\_ ) $$

---

### A3. Independence check from a joint table
Let $$ X , Y \in \{ 0 , 1 \} $$ have the joint probability table:

|        | $$ Y = 0 $$ | $$ Y = 1 $$ | Total |
|---|---:|---:|---:|
| $$ X = 0 $$ | 0.20 | 0.30 | 0.50 |
| $$ X = 1 $$ | 0.30 | 0.20 | 0.50 |
| **Total** | 0.50 | 0.50 | 1.00 |

1. Compute $$ P ( X = 1 ) $$ and $$ P ( Y = 1 ) $$.  
2. Compute $$ P ( X = 1 , Y = 1 ) $$.  
3. Are $$ X $$ and $$ Y $$ independent? Use one calculation to justify.

---

### A4. Two coins (independence does not require fair coins)
Two coins are flipped. Let $$ C_1 $$ be the outcome of coin 1 and $$ C_2 $$ be the outcome of coin 2.

You are told:
- $$ P ( C_1 = H ) = 0.60 $$
- $$ P ( C_2 = H ) = 0.40 $$
- The flips are independent.

1. Compute $$ P ( C_1 = H , C_2 = H ) $$.  
2. Compute $$ P ( C_1 = H , C_2 = T ) $$.  
3. Write the independence statement that justifies the step $$ P ( C_2 = T \mid C_1 = H ) = P ( C_2 = T ) $$.

---

### A5. Independence can fail (election table)
Let $$ S \in \{ D , R \} $$ be the Senate outcome and $$ H \in \{ D , R \} $$ be the House outcome.

You are given the joint probabilities:
- $$ P ( S = R , H = R ) = 0.25 $$
- $$ P ( S = R , H = D ) = 0.15 $$
- $$ P ( S = D , H = R ) = 0.20 $$
- $$ P ( S = D , H = D ) = 0.40 $$

1. Compute $$ P ( S = D ) $$ and $$ P ( H = D ) $$.  
2. Test independence using the cell $$ S = D $$ and $$ H = D $$.

---

## B. Bayes theorem (pre-test and post-test probability)

### B1. Identify what each probability means
Let $$ C $$ be “has cancer” and $$ T $$ be “test is positive”, where $$ C , T \in \{ 0 , 1 \} $$.

For each sentence, write the probability expression:

1. “Among people who test positive, what fraction actually have cancer?”  
2. “Among people who have cancer, what fraction test positive?”  
3. “What fraction of the whole population has cancer?”  
4. “Among people who do not have cancer, what fraction test negative?”

---

### B2. Pre-test and post-test (compute with Bayes)
You are told:
- $$ P ( C = 1 ) = 0.03 $$  (3% prevalence)
- $$ P ( T = 1 \mid C = 1 ) = 0.85 $$  (sensitivity)
- $$ P ( T = 0 \mid C = 0 ) = 0.90 $$  (specificity)

1. Compute $$ P ( T = 1 \mid C = 0 ) $$.  
2. Compute the overall probability of a positive test, $$ P ( T = 1 ) $$, using marginalizing with conditional probabilities:
   $$ P ( T = 1 ) = P ( T = 1 \mid C = 1 ) P ( C = 1 ) + P ( T = 1 \mid C = 0 ) P ( C = 0 ) $$.  
3. Compute the post-test probability $$ P ( C = 1 \mid T = 1 ) $$.  
4. Interpret $$ P ( C = 1 \mid T = 1 ) $$ in one sentence.

---

## C. The low base-rate problem

### C1. A “very good” test can still have a low post-test probability
You are told:
- $$ P ( C = 1 ) = 0.0005 $$  (0.05% prevalence)
- $$ P ( T = 1 \mid C = 1 ) = 0.99 $$
- $$ P ( T = 0 \mid C = 0 ) = 0.99 $$

1. Compute $$ P ( T = 1 ) $$.  
2. Compute $$ P ( C = 1 \mid T = 1 ) $$.  
3. Explain in 2 to 3 sentences why the post-test probability is not close to 1, even though the test is very accurate.

---

# Answers

## A. Independence

### A1.
1. Not independent, because $$ P ( P = 1 \mid S = 1 ) $$ is not equal to $$ P ( P = 1 ) $$ (0.62 vs 0.48).  
2. Studying is associated with a higher chance of passing than the overall average.

### A2.
1. $$ P ( A , B ) = P ( A \mid B ) \, P ( B ) $$  
2. $$ P ( A , B ) = P ( B \mid A ) \, P ( A ) $$

### A3.
1. $$ P ( X = 1 ) = 0.50 $$ and $$ P ( Y = 1 ) = 0.50 $$.  
2. $$ P ( X = 1 , Y = 1 ) = 0.20 $$.  
3. Not independent, because $$ P ( X = 1 ) P ( Y = 1 ) = 0.50 \cdot 0.50 = 0.25 $$, which does not equal $$ 0.20 $$.

### A4.
1. $$ P ( C_1 = H , C_2 = H ) = P ( C_1 = H ) P ( C_2 = H ) = 0.60 \cdot 0.40 = 0.24 $$.  
2. Because $$ P ( C_2 = T ) = 1 - P ( C_2 = H ) = 0.60 $$, we get:  
   $$ P ( C_1 = H , C_2 = T ) = P ( C_1 = H ) P ( C_2 = T ) = 0.60 \cdot 0.60 = 0.36 $$.  
3. Independence means conditioning does not change probabilities, for example:
   $$ P ( C_2 = T \mid C_1 = H ) = P ( C_2 = T ) $$.

### A5.
1. $$ P ( S = D ) = 0.20 + 0.40 = 0.60 $$.  
   $$ P ( H = D ) = 0.15 + 0.40 = 0.55 $$.  
2. If independent, we would have $$ P ( S = D , H = D ) = P ( S = D ) P ( H = D ) = 0.60 \cdot 0.55 = 0.33 $$.  
   But the joint is $$ 0.4 $$, so they are not independent.

---

## B. Bayes theorem

### B1.
1. $$ P ( C = 1 \mid T = 1 ) $$  
2. $$ P ( T = 1 \mid C = 1 ) $$  
3. $$ P ( C = 1 ) $$  
4. $$ P ( T = 0 \mid C = 0 ) $$

### B2.
1. $$ P ( T = 1 \mid C = 0 ) = 1 - 0.90 = 0.10 $$.  
2. $$ P ( T = 1 ) = 0.85 ( 0.03 ) + 0.10 ( 0.97 ) = 0.0255 + 0.097 = 0.1225 $$, so $$ P ( T = 1 ) = 0.123 $$.  
3. $$ P ( C = 1 \mid T = 1 ) = \\frac{ P ( T = 1 \mid C = 1 ) P ( C = 1 ) }{ P ( T = 1 ) } = \\frac{ 0.85 ( 0.03 ) }{ 0.1225 } \\approx 0.208 $$.  
4. Among people who test positive, about 20.8% actually have cancer.

---

## C. Low base rate

### C1.
1. $$ P ( T = 1 ) = 0.99 ( 0.0005 ) + 0.01 ( 0.9995 ) = 0.000495 + 0.009995 = 0.01049 $$, so $$ P ( T = 1 ) \approx 0.010 $$.  
2. $$ P ( C = 1 \mid T = 1 ) = \\frac{ 0.99 ( 0.0005 ) }{ 0.01049 } \\approx 0.047 $$.  
3. Even with a very accurate test, most people do not have cancer when the base rate is tiny. That means there are many more opportunities for false positives than true positives. As a result, a positive test does not guarantee a high post-test probability.
