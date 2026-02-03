# Lecture 2 Practice Problems (Probability Distributions + Event Spaces)

_Source problems include the “2028 Election Cycle” joint-probability table items from the provided practice PDF._

---

## Questions

### A. Probability distributions (one variable)

1. Let \(X\in\{0,1\}\) where \(X=1\) means “FTA” and \(X=0\) means “No FTA.” You are told \(P(X=1)=0.148\).  
   1.1. What is \(P(X=0)\)?  
   1.2. What property must the outcomes \(\{0,1\}\) satisfy for this to define a valid distribution?

2. A proposed distribution for \(Y\) is:
   - \(P(Y=0)=0.40\)
   - \(P(Y=1)=0.35\)
   - \(P(Y=2)=0.35\)

   2.1. Is this a valid probability distribution?  
   2.2. If not, fix it by changing **only one** probability.

3. In a dataset of 500 people, 74 have \(X=1\) (FTA) and the rest have \(X=0\).  
   3.1. Compute \(P(X=1)\) and \(P(X=0)\).  
   3.2. If you draw 10 people at random **with replacement**, what is the expected number with \(X=1\)?

---

### B. Event spaces (two attributes)

4. A standard 52-card deck. Consider two attributes:
   - \(Color \in \{\text{Red}, \text{Black}\}\)
   - \(Value \in \{\text{Ace},2,\dots,10,\text{Jack},\text{Queen},\text{King}\}\)

   4.1. How many outcomes are in the event space \((Color, Value, Suit)\) if suit is included?  
   4.2. How many outcomes are in the event space \((Color, Value)\) if suit is **not** included?

5. Compute the following probabilities for a standard deck:
   5.1. \(P(Color=\text{Red}, Value=\text{King})\)  
   5.2. \(P(Color=\text{Black}, Value=\text{Ace})\)  
   5.3. \(P(Color=\text{Red}, Value\in\{\text{Jack},\text{Queen},\text{King}\})\)

---

### C. Joint distributions (from the practice PDF: “2028 Election Cycle”)

Let \(H\in\{D,R\}\) denote who wins the House (Democrats/Republicans) and \(S\in\{D,R\}\) denote who wins the Senate.

You are told:
- \(P(H=D, S=D)=0.4\)
- \(P(H=R, S=D)=0.1\)
- \(P(H=D, S=R)=0.2\)

6. What is \(P(H=R, S=R)\)?

7. What is \(P(H=D)\)?

8. What is \(P(H=D \text{ OR } S=R)\)?  
   (Interpret “OR” as inclusive OR.)

---

## Answers

### A. Probability distributions (one variable)

1.1. \(P(X=0)=1-0.148=0.852\).  
1.2. The outcomes must be **mutually exclusive** (can’t both happen) and **collectively exhaustive** (one of them must happen).

2.1. Not valid, because the probabilities sum to \(0.40+0.35+0.35=1.10\), which is greater than 1.  
2.2. One fix: change \(P(Y=2)\) from 0.35 to 0.25 so the total is \(0.40+0.35+0.25=1.00\).  
(Any single-probability change that makes the sum exactly 1 and keeps probabilities between 0 and 1 is acceptable.)

3.1. \(P(X=1)=74/500=0.148\); \(P(X=0)=426/500=0.852\).  
3.2. If \(X\sim\text{Bernoulli}(p=0.148)\), then in 10 draws the expected number is \(10\times 0.148=1.48\).

---

### B. Event spaces (two attributes)

4.1. \((Color, Value, Suit)\): this is equivalent to the full deck. There are **52** outcomes.  
4.2. \((Color, Value)\): 2 colors × 13 values = **26** outcomes.

5.1. There are 2 red kings out of 52 cards, so \(2/52=1/26\approx 0.03846\).  
5.2. There are 2 black aces out of 52 cards, so \(2/52=1/26\approx 0.03846\).  
5.3. Red face cards (J/Q/K): 3 values × 2 red suits = 6 cards, so \(6/52=3/26\approx 0.11538\).

---

### C. Joint distributions (2028 Election Cycle)

Given:
- \(P(H=D,S=D)=0.4\)
- \(P(H=R,S=D)=0.1\)
- \(P(H=D,S=R)=0.2\)

6. Use “probabilities add to 1” over the four joint outcomes:
\[
P(R,R)=1-(0.4+0.1+0.2)=1-0.7=0.3.
\]

7. \(P(H=D)=P(H=D,S=D)+P(H=D,S=R)=0.4+0.2=0.6\).

8. Event \((H=D \text{ OR } S=R)\) includes all outcomes except \((H=R,S=D)\).  
So:
\[
P(H=D \text{ OR } S=R)=1-P(H=R,S=D)=1-0.1=0.9.
\]
Equivalently, sum the included joint cells: \(0.4+0.2+0.3=0.9\).

