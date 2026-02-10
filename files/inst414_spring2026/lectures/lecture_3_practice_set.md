# Lecture 3 Practice Problems (Conditional Probability)

> **How to use this:** Try these *before* looking at the answers. If you get stuck, write down what part is confusing:
> (1) defining events/variables, (2) finding the right numerator/denominator, or (3) arithmetic.

> **Notation + rounding reminders:**
> - Throughout, P(A,B) means the joint probability P(Acap B).
> - Unless otherwise stated, **round conditional probabilities to 3 decimals**.

---

## A. Warm-ups: joint vs marginal (quick reps)

### A1.
Let Xin{0,1} and Yin{0,1} have the joint distribution below.

|        | Y=0 | Y=1 |
|--------|-----------|-----------|
| X=0 | 0.10      | 0.40      |
| X=1 | 0.20      | 0.30      |

1. Verify this is a valid joint probability distribution.
2. Compute the marginal P(X=0) and P(X=1).
3. Compute the marginal P(Y=0) and P(Y=1).

### A2.
Using the table in A1, compute:
1. P(X=1, Y=0)
2. P(X=1  or  Y=0)

### A3.
A student says: “P(Y=1) is the *same thing* as P(Y=1 $$\mid$$ X=1).”
Is this always true? If not, give a one-sentence explanation of what’s different.

---

## B. Risk Level × Sex (this mirrors the lecture example)

A risk algorithm categorizes people as **Low** or **High** risk. You observe the following **counts** in a sample of 200 people:

|                 | Sex = Male | Sex = Female | Total |
|-----------------|------------|--------------|-------|
| Risk Level = Low  | 80         | 24           | 104   |
| Risk Level = High | 76         | 20           | 96    |
| **Total**          | 156        | 44           | 200   |

### B1.
Convert the count table into a joint probability table P(Risk Level, Sex).

### B2.
Compute the marginals:
1. P(Sex = Male) and P(Sex = Female)
2. P(Risk Level = Low) and P(Risk Level = High)

### B3.
Compute each conditional probability:
1. P(High  $$\mid$$ Male)
2. P(Low  $$\mid$$ Male)
3. P(High  $$\mid$$ Female)
4. P(Male  $$\mid$$ High)
5. P(Female  $$\mid$$ Low)

### B4.
Interpret in a sentence (plain English):
1. P(High  $$\mid$$ Male)
2. P(Male  $$\mid$$ High)

### B5.
Compute:
1. P(High and Male)
2. P(High or Male)

*(Reminder: “or” is union cup.)*

### B7. (Independence check)
Are **Risk Level** and **Sex** independent in this sample?

1. State the condition for independence using probabilities.
2. Use the table to test it (one calculation is enough).

---

## C. Marginal vs joint vs conditional (practice identifying the question)

A COVID test is administered to **200** people. The results are:

|            | Test + | Test - | Total |
|------------|--------|--------|-------|
| COVID +    | 36     | 4      | 40    |
| COVID -    | 32     | 128    | 160   |
| **Total**  | 68     | 132    | 200   |

Let C be the event “COVID+” and T be the event “Test+”.

### C1.
Compute:
1. P(C)
2. P(T)
3. P(C, T)

### C2.
Compute:
1. P(C  $$\mid$$ T)
2. P(T  $$\mid$$ C)

### C3.
Which probability is each sentence asking for? (Just write the expression.)
1. “Among people who test positive, what fraction actually have COVID?”
2. “What fraction of the whole sample tested positive?”
3. “What fraction have COVID and test positive?”
4. “Among people with COVID, what fraction test positive?”

### C4.
In one sentence: why is P(C $$\mid$$ T) usually *very different* from P(T $$\mid$$ C)?

---

## D. Conditioning in a story problem (dice)

Assume fair six-sided dice.

### D1.
Roll two dice in order: X_1 then X_2.
Compute P(X_1+X_2 > 8  $$\mid$$ X_1=5).

### D2.
Compute P(X_1+X_2 $$\ge$$ 10  $$\mid$$ X_1=6).

### D3.
Compute P(X_1+X_2  is even  $$\mid$$ X_1=3).

### D4.
Let A be the event “sum is at least 9” and B be the event “first roll is 4.”
Write P(A $$\mid$$ B) as a probability statement involving only X_2, then compute it.

### D5. (Quick check)
True or false (and give a short reason):
P(X_2=6  $$\mid$$ X_1=2)=P(X_2=6).

---

## E. Relationships: joint, marginal, conditional (the algebra slides)

### E1.
Fill in the blanks:
1. P(A $$\mid$$ B)=dfrac{P(underline{hspace{2cm}})}{P(underline{hspace{2cm}})}
2. P(A,B)=P(A $$\mid$$ B)\,P(underline{hspace{2cm}})
3. P(A,B)=P(B $$\mid$$ A)\,P(underline{hspace{2cm}})

### E2.
You are told P(A)=0.25 and P(B $$\mid$$ A)=0.60.
Compute P(A,B).

### E3.
You are told P(B)=0.40 and P(A $$\mid$$ B)=0.15.
Compute P(A,B).

### E4.
You are told P(A,B)=0.06 and P(A)=0.20.
Compute P(B $$\mid$$ A).

### E5. (Chain rule in words)
In one sentence: what does the identity P(A,B)=P(B $$\mid$$ A)P(A) mean?

---

## F. Marginalizing with conditional probabilities (law-of-total-probability style)

Let Yin{0,1} with P(Y=1)=0.30 (so P(Y=0)=0.70).
You are also told:

- P(X=1 $$\mid$$ Y=1)=0.80
- P(X=1 $$\mid$$ Y=0)=0.20

### F1.
Compute P(X=1) using marginalizing with conditional probabilities.

### F2.
Compute P(X=0) two ways:
1. as 1-P(X=1)
2. by marginalizing directly (write and compute the sum)

### F3.
Now compute P(Y=1 $$\mid$$ X=1).
*(Hint: you will need Bayes’ rule, i.e., the conditional/joint relationship.)*

### F4.
A student says: “Because P(X=1 $$\mid$$ Y=1) is big, P(Y=1 $$\mid$$ X=1) must also be big.”
Is that necessarily true? Use your answer from F3 to support your explanation.

---

## G. More than two random variables (the 3-variable example)

Suppose we have three binary random variables H, S, and P, where **H is binary (R or D)**.
You are told:

- P(H=R, S=D, P=D)=0.05
- P(H=D, S=D, P=D)=0.40

### G1.
Compute P(S=D, P=D).

### G2.
Compute P(H=R  $$\mid$$ S=D, P=D).

### G3.
Interpret P(H=R  $$\mid$$ S=D, P=D) in one sentence.

---

# Answers

## A. Warm-ups

**A1.**
1. Sum: 0.10+0.40+0.20+0.30=1.00 ✅
2. P(X=0)=0.10+0.40=0.50, P(X=1)=0.20+0.30=0.50
3. P(Y=0)=0.10+0.20=0.30, P(Y=1)=0.40+0.30=0.70

**A2.**
1. P(X=1,Y=0)=0.20
2. P(X=1 cup Y=0)=P(X=1)+P(Y=0)-P(X=1,Y=0)=0.50+0.30-0.20=0.60

**A3.** Not always true. P(Y=1) is overall; P(Y=1 $$\mid$$ X=1) is restricted to cases where X=1 and then renormalized.

---

## B. Risk Level × Sex

**B1.** Divide each count by 200:

|                 | Male | Female | Total |
|-----------------|------|--------|-------|
| Low             | 0.40 | 0.12   | 0.52  |
| High            | 0.38 | 0.10   | 0.48  |
| **Total**       | 0.78 | 0.22   | 1.00  |

Check: all four joint cells sum to **1.00**.

**B2.**
- P(M)=156/200=0.78, P(F)=44/200=0.22
- P(Low)=104/200=0.52, P(High)=96/200=0.48

**B3.**
1. P(High $$\mid$$ Male)=76/156 $$\approx$$ 0.487
2. P(Low $$\mid$$ Male)=80/156 $$\approx$$ 0.513
3. P(High $$\mid$$ Female)=20/44 $$\approx$$ 0.455
4. P(Male $$\mid$$ High)=76/96 $$\approx$$ 0.792
5. P(Female $$\mid$$ Low)=24/104 $$\approx$$ 0.231

**B4.**
1. Among males, about 48.7% are high risk.
2. Among high-risk people, about 79.2% are male.

**B5.**
1. P(Highcap Male)=76/200=0.38
2. P(Highcup Male)=0.48+0.78-0.38=0.88

**B6.**
P(High)=0.48 and P(High $$\mid$$ Male) $$\approx$$ 0.487.
So P(High $$\mid$$ Male) is slightly larger.

**B7.**
1. Independence condition: for example, P(Highcap Male)=P(High)P(Male) (equivalently P(High $$\mid$$ Male)=P(High)).
2. Test: P(Highcap Male)=0.38 but P(High)P(Male)=0.48times 0.78=0.3744. Since these differ, the variables are **not independent** in this sample.

---

## C. COVID test table

**C1.**
1. P(C)=40/200=0.20
2. P(T)=68/200=0.34
3. P(C,T)=36/200=0.18

**C2.**
1. P(C $$\mid$$ T)=36/68 $$\approx$$ 0.529
2. P(T $$\mid$$ C)=36/40=0.90


**C3.**
1. P(C $$\mid$$ T)
2. P(T)
3. P(C,T)
4. P(T $$\mid$$ C)

**C4.** They condition on different things: P(C $$\mid$$ T) restricts to test-positives, while P(T $$\mid$$ C) restricts to COVID-positives.

---

## D. Dice

**D1.** Given X_1=5, need X_2>3: 3/6=0.5

**D2.** Given X_1=6, need X_2ge 4: 3/6=0.5

**D3.** Given X_1=3 (odd), sum is even iff X_2 is odd: 3/6=0.5

**D4.** If X_1=4, “sum at least 9” means X_2ge 5.
So P(A $$\mid$$ B)=P(X_2ge 5)=2/6=1/3.

**D5.** True. The dice are independent, so knowing X_1 doesn’t change the distribution of X_2.

---

## E. Relationships

**E1.**
1. P(A $$\mid$$ B)=(P(A,B))/(P(B))
2. P(A,B)=P(A $$\mid$$ B)P(B)
3. P(A,B)=P(B $$\mid$$ A)P(A)

**E2.** P(A,B)=0.60times 0.25=0.15

**E3.** P(A,B)=0.15times 0.40=0.06

**E4.** P(B $$\mid$$ A)=0.06/0.20=0.30

**E5.** “The probability that both A and B happen equals the probability A happens, times the probability B happens given that A happened.”

---

## F. Marginalizing with conditionals

**F1.**

P(X=1)=P(X=1 $$\mid$$ Y=1)P(Y=1)+P(X=1 $$\mid$$ Y=0)P(Y=0)
=0.80(0.30)+0.20(0.70)=0.24+0.14=0.38.

**F2.**
1. P(X=0) = 1 - 0.38 = 0.62
2. P(X=0) = P(X=0 $$\mid$$ Y=1) P(Y=1) + P(X=0 $$\mid$$ Y=0) P(Y=0)
   
   where 
     - P(X=0 $$\mid$$ Y=1)=0.20, 
     - P(X=0 $$\mid$$ Y=0)=0.80.
   
   So: 0.20 (0.30) + 0.80 (0.70) = 0.06 + 0.56 = 0.62.

**F3.**

P(Y=1 $$\mid$$ X=1) = $$\frac{ P(X=1 \mid Y=1) P(Y=1)}{P(X=1)}$$ = $$\frac{0.80(0.30)}{0.38}$$ = $$\frac{0.24}{0.38}$$ $$\approx$$ 0.632.

**F4.** Not necessarily. Here it ends up being about 0.632 (which *is* fairly big), but in general P(Y=1 $$\mid$$ X=1) also depends on how common Y=1 is overall.

---

## G. 3 variables

**G1.**
Because H is binary (R or D), the event (S=D, P=D) can occur only with H=R or H=D. So:
P(S=D, P=D) = 0.40 + 0.05 = 0.45

**G2.**
P(H=R $$\mid$$ S=D,P=D)=0.05/0.45 $$\approx$$ 0.111 (about 11.1%)

**G3.** Among cases where S=D and P=D, about 11% have H=R.
