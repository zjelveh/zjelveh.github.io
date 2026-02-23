# Lecture 5 Practice Problems (Naive Bayes + Performance Metrics)

> **How to use this:** Try these before the quiz. If you get stuck, write down what part is confusing:  
> (1) defining variables/events, (2) setting up the right probability expression, or (3) arithmetic.

> **Notation + rounding reminders:**
> - Throughout, $$P ( A , B )$$ means the joint probability $$P ( A \\cap B )$$.  
> - Use “given” to read conditionals: $$P ( A \\mid B )$$.  
> - Unless otherwise stated, round final probabilities to **3 decimals**.

---

## A. Naive Bayes

### A1. Translate words into probability notation (warm-up)
An app wants to classify short videos as either **sports** or **pets**.

Let $$Y$$ be the topic, where:
- $$Y = 1$$ means sports
- $$Y = 0$$ means pets

Let $$X_1$$ be whether the word “stadium” appears in the caption, and $$X_2$$ be whether the word “fetch” appears in the caption. Each feature is either 0 or 1.

For each sentence, write the probability expression:

1. “Among sports videos, what fraction contain the word stadium?”  
2. “Among videos that contain stadium and fetch, what is the probability the video is sports?”  
3. “What fraction of all videos are sports?”  
4. “Among pet videos, what fraction contain fetch?”

---

### A2. Compute conditional probabilities from counts
You look at a labeled training set of 400 videos:
- 60 are sports and 340 are pets.
- Among the 60 sports videos, 18 contain “stadium”.
- Among the 340 pet videos, 34 contain “stadium”.

1. Compute $$P ( Y = 1 )$$ and $$P ( Y = 0 )$$.  
2. Compute $$P ( X_1 = 1 \\mid Y = 1 )$$.  
3. Compute $$P ( X_1 = 1 \\mid Y = 0 )$$.  
4. In one sentence: what does it mean if $$P ( X_1 = 1 \\mid Y = 1 )$$ is much larger than $$P ( X_1 = 1 \\mid Y = 0 )$$?

---

### A3. Naive Bayes classification with two features (core)
You estimate these probabilities from data:

- $$P ( Y = 1 ) = 0.08$$  
- $$P ( X_1 = 1 \\mid Y = 1 ) = 0.35$$  
- $$P ( X_2 = 1 \\mid Y = 1 ) = 0.20$$  
- $$P ( X_1 = 1 \\mid Y = 0 ) = 0.05$$  
- $$P ( X_2 = 1 \\mid Y = 0 ) = 0.18$$

Assume conditional independence given $$Y$$:
$$P ( X_1 = 1 , X_2 = 1 \\mid Y = y ) = P ( X_1 = 1 \\mid Y = y ) P ( X_2 = 1 \\mid Y = y ).$$

For a new video with $$X_1 = 1$$ and $$X_2 = 1$$:

1. Compute the *unnormalized* score for sports:
   $$\\text{score}_1 = P ( Y = 1 ) P ( X_1 = 1 \\mid Y = 1 ) P ( X_2 = 1 \\mid Y = 1 ).$$
2. Compute the *unnormalized* score for pets:
   $$\\text{score}_0 = P ( Y = 0 ) P ( X_1 = 1 \\mid Y = 0 ) P ( X_2 = 1 \\mid Y = 0 ).$$
3. Which class would naive Bayes predict using the “pick the bigger score” rule?  
4. In one sentence: what is the role of the base rate $$P ( Y = 1 )$$ in the decision?

---

### A4. Turn scores into a probability (normalizing)
Using your scores from A3, compute:
$$P ( Y = 1 \\mid X_1 = 1 , X_2 = 1 ) = \\frac{ \\text{score}_1 }{ \\text{score}_1 + \\text{score}_0 }.$$

Interpret this probability in one sentence.

---

### A5. When conditional independence is wrong (transfer)
Suppose that for sports videos, the two words “stadium” and “fetch” are **not** conditionally independent.

You are told:
- $$P ( Y = 1 ) = 0.08$$  
- $$P ( X_1 = 1 , X_2 = 1 \\mid Y = 1 ) = 0.04$$  
- $$P ( X_1 = 1 \\mid Y = 0 ) = 0.05$$  
- $$P ( X_2 = 1 \\mid Y = 0 ) = 0.18$$

1. Compute the sports score using the *joint* term:
   $$\\text{score}_1 = P ( Y = 1 ) P ( X_1 = 1 , X_2 = 1 \\mid Y = 1 ).$$
2. Compute the pets score using the naive Bayes product (still assume independence for $$Y = 0$$):
   $$\\text{score}_0 = P ( Y = 0 ) P ( X_1 = 1 \\mid Y = 0 ) P ( X_2 = 1 \\mid Y = 0 ).$$
3. Compare your answer to A3: how can violating conditional independence change predictions?

---

## B. Performance Metrics

### B1. From confusion matrix cells to probability statements (warm-up)
Let $$y$$ be the true label and $$\\hat{y}$$ be the predicted label (both 0 or 1).

For each quantity, write it as a probability:

1. True positive rate (recall): TPR  
2. Precision (positive predictive value): PPV  
3. False positive rate: FPR  
4. False negative rate: FNR  

---

### B2. Compute metrics from a confusion matrix (core)
You evaluate a classifier on 1,000 items and get:

- True positives: $$TP = 45$$  
- False positives: $$FP = 15$$  
- True negatives: $$TN = 920$$  
- False negatives: $$FN = 20$$

Compute:

1. Accuracy  
2. Precision (PPV)  
3. Recall (TPR)  
4. Specificity (TNR)  
5. False discovery rate (FDR)  
6. False positive rate (FPR)  
7. False negative rate (FNR)

Round each to 3 decimals.

---

### B3. Same accuracy, different behavior (core)
Two classifiers are both evaluated on 200 items (same dataset). Each has accuracy 0.90, but they make different types of errors.

Classifier A:
- $$TP = 10$$, $$FP = 0$$, $$TN = 170$$, $$FN = 20$$

Classifier B:
- $$TP = 25$$, $$FP = 15$$, $$TN = 155$$, $$FN = 5$$

1. Verify both accuracies are 0.90.  
2. Compute precision and recall for each classifier.  
3. Which classifier would you prefer if false negatives are very costly? Why?

---

### B4. Thresholds change precision and recall (core)
A model outputs a score between 0 and 1. Predict $$\\hat{y} = 1$$ if score is at least the threshold.

You have 10 cases:

| Case | Score | True $$y$$ |
|---:|---:|---:|
| 1 | 0.97 | 1 |
| 2 | 0.93 | 0 |
| 3 | 0.88 | 1 |
| 4 | 0.81 | 1 |
| 5 | 0.74 | 0 |
| 6 | 0.63 | 1 |
| 7 | 0.59 | 0 |
| 8 | 0.41 | 1 |
| 9 | 0.32 | 0 |
| 10 | 0.10 | 0 |

1. Using threshold 0.80, compute $$TP$$, $$FP$$, $$TN$$, $$FN$$, then precision and recall.  
2. Using threshold 0.50, compute $$TP$$, $$FP$$, $$TN$$, $$FN$$, then precision and recall.  
3. Which threshold increases recall? Which threshold increases precision?

---

### B5. Choosing a metric depends on the goal (interpretation)
Pick the best metric for each situation and explain in one sentence.

1. A teacher wants to identify students who are at risk of failing, and missing a truly at-risk student is very costly.  
2. A video app wants to avoid showing videos a user will dislike, because showing a bad video makes users leave the app.  
3. A hospital uses a screening test and wants to know: “If the test is positive, what is the probability the patient truly has the condition?”

---

# Answers

## A. Naive Bayes

### A1.
1. $$P ( X_1 = 1 \\mid Y = 1 )$$  
2. $$P ( Y = 1 \\mid X_1 = 1 , X_2 = 1 )$$  
3. $$P ( Y = 1 )$$  
4. $$P ( X_2 = 1 \\mid Y = 0 )$$

### A2.
1. $$P ( Y = 1 ) = 60 / 400 = 0.150$$ and $$P ( Y = 0 ) = 340 / 400 = 0.850$$.  
2. $$P ( X_1 = 1 \\mid Y = 1 ) = 18 / 60 = 0.300$$.  
3. $$P ( X_1 = 1 \\mid Y = 0 ) = 34 / 340 = 0.100$$.  
4. “Stadium” is much more common in sports videos than pet videos, so it is a useful feature for classification.

### A3.
1. $$\\text{score}_1 = 0.08 \\cdot 0.35 \\cdot 0.20 = 0.0056$$.  
2. $$P ( Y = 0 ) = 1 - 0.08 = 0.92$$, so $$\\text{score}_0 = 0.92 \\cdot 0.05 \\cdot 0.18 = 0.00828$$.  
3. Predict $$Y = 0$$ (pets) because $$0.00828 > 0.0056$$.  
4. The base rate pushes predictions toward the class that is more common overall unless the features strongly outweigh it.

### A4.
$$P ( Y = 1 \\mid X_1 = 1 , X_2 = 1 ) = \\frac{ 0.0056 }{ 0.0056 + 0.00828 } \\approx 0.403$$.  
Interpretation: among videos with both words, the model estimates about a 40.3% chance the video is sports.

### A5.
1. $$\\text{score}_1 = 0.08 \\cdot 0.04 = 0.0032$$.  
2. $$\\text{score}_0 = 0.92 \\cdot 0.05 \\cdot 0.18 = 0.00828$$.  
3. If the true joint probability differs a lot from the product, the naive Bayes score can be too big or too small, which can flip the predicted class.

---

## B. Performance Metrics

### B1.
1. $$TPR = P ( \\hat{y} = 1 \\mid y = 1 )$$  
2. $$PPV = P ( y = 1 \\mid \\hat{y} = 1 )$$  
3. $$FPR = P ( \\hat{y} = 1 \\mid y = 0 )$$  
4. $$FNR = P ( \\hat{y} = 0 \\mid y = 1 )$$

### B2.
Let $$N = TP + FP + TN + FN = 1{,}000$$.

1. Accuracy $$= ( TP + TN ) / N = ( 45 + 920 ) / 1000 = 0.965$$.  
2. Precision $$= TP / ( TP + FP ) = 45 / 60 = 0.750$$.  
3. Recall $$= TP / ( TP + FN ) = 45 / 65 = 0.692$$.  
4. Specificity $$= TN / ( TN + FP ) = 920 / 935 = 0.984$$.  
5. FDR $$= FP / ( TP + FP ) = 15 / 60 = 0.250$$.  
6. FPR $$= FP / ( TN + FP ) = 15 / 935 = 0.016$$.  
7. FNR $$= FN / ( TP + FN ) = 20 / 65 = 0.308$$.

### B3.
1. Classifier A accuracy: $$( 10 + 170 ) / 200 = 0.900$$.  
   Classifier B accuracy: $$( 25 + 155 ) / 200 = 0.900$$.  
2. Classifier A: precision $$= 10 / ( 10 + 0 ) = 1.000$$, recall $$= 10 / ( 10 + 20 ) = 0.333$$.  
   Classifier B: precision $$= 25 / ( 25 + 15 ) = 0.625$$, recall $$= 25 / ( 25 + 5 ) = 0.833$$.  
3. If false negatives are very costly, prefer Classifier B because it has much higher recall (it misses fewer true positives).

### B4.
Threshold 0.80:
- Predicted positives: cases 1, 2, 3, 4.  
- $$TP = 3$$ (1, 3, 4), $$FP = 1$$ (2), $$FN = 2$$ (6, 8), $$TN = 4$$ (5, 7, 9, 10).  
- Precision $$= 3 / 4 = 0.750$$, recall $$= 3 / 5 = 0.600$$.

Threshold 0.50:
- Predicted positives: cases 1, 2, 3, 4, 5, 6, 7.  
- $$TP = 4$$ (1, 3, 4, 6), $$FP = 3$$ (2, 5, 7), $$FN = 1$$ (8), $$TN = 2$$ (9, 10).  
- Precision $$= 4 / 7 = 0.571$$, recall $$= 4 / 5 = 0.800$$.

3. Lowering the threshold increases recall and decreases precision in this example.

### B5.
1. Recall (TPR), because you want to catch as many truly at-risk students as possible.  
2. Precision (PPV), because among the videos you show, you want a high fraction to be ones the user will actually like.  
3. Precision (PPV), because it is exactly $$P ( y = 1 \\mid \\hat{y} = 1 )$$.

