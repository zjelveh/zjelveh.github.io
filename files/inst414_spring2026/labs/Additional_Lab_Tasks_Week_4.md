# Additional Lab Tasks (Week 4) — Genetic Screening + Probability

These are optional, “lab task” style questions that connect pandas work to Week 4 probability ideas: independence and Bayes theorem (pre-test and post-test probability).

We will work with a genetic screening dataset with these columns:
- `has_variant`: 1 if the person has the genetic variant, 0 otherwise
- `screen_positive`: 1 if the screening test is positive, 0 otherwise
- `age_group`: a category like `Under 50` or `50+`

Unless otherwise stated, report probabilities rounded to 3 decimals.

---

## Task 1 — Load, inspect, and clean
1. Load the dataset into a DataFrame called `df`.
2. Check missing values with `df.isna().sum()` for `has_variant`, `screen_positive`, and `age_group`.
3. Create `df_clean` by dropping rows with missing values in those three columns.
4. Confirm that `has_variant` and `screen_positive` are truly binary (only 0 and 1).
5. Report how many rows you dropped, and give a one-sentence justification.

---

## Task 2 — Base rates (marginal probabilities)
1. Compute the overall pre-test probability $$ P ( has\\_variant = 1 ) $$.
2. Compute the overall positive screening rate $$ P ( screen\\_positive = 1 ) $$.
3. Compute both of these probabilities by `age_group`:
   - $$ P ( has\\_variant = 1 \\mid age\\_group ) $$
   - $$ P ( screen\\_positive = 1 \\mid age\\_group ) $$
4. In one sentence: which `age_group` has the higher pre-test probability, and by how much?

---

## Task 3 — Joint distribution table
1. Create a 2×2 joint probability table for $$ P ( has\\_variant , screen\\_positive ) $$ from `df_clean`.
2. Verify the table sums to 1.
3. Create the same 2×2 joint probability table separately for each `age_group`.

Optional shortcut: use `pd.crosstab(..., normalize=True)` to create the 2×2 joint table and confirm it matches your other method.

---

## Task 4 — Test quality (conditional probabilities)
Compute the following overall, and then compute them again for each `age_group`:

1. Sensitivity: $$ P ( screen\\_positive = 1 \\mid has\\_variant = 1 ) $$
2. Specificity: $$ P ( screen\\_positive = 0 \\mid has\\_variant = 0 ) $$
3. False positive rate: $$ P ( screen\\_positive = 1 \\mid has\\_variant = 0 ) $$

In 1 to 2 sentences: do these quantities look similar across age groups, or do they differ?

---

## Task 5 — Independence check
Overall, test whether `has_variant` and `screen_positive` are independent.

1. Compute $$ P ( has\\_variant = 1 , screen\\_positive = 1 ) $$.
2. Compute $$ P ( has\\_variant = 1 ) \\cdot P ( screen\\_positive = 1 ) $$.
3. Report both numbers and their difference. Conclude: independent or not?

Then repeat the same check within each `age_group` (using group-specific probabilities).

---

## Task 6 — Bayes theorem (post-test probability) + low base-rate effect
1. Compute the post-test probability directly from the data:
   $$ P ( has\\_variant = 1 \\mid screen\\_positive = 1 ) $$
2. Compute it again using Bayes theorem:
   $$ P ( has\\_variant = 1 \\mid screen\\_positive = 1 ) = \\frac{ P ( screen\\_positive = 1 \\mid has\\_variant = 1 ) \\cdot P ( has\\_variant = 1 ) }{ P ( screen\\_positive = 1 ) } $$
3. Confirm the two answers match (up to rounding).
4. Repeat steps 1 to 3 within each `age_group`. In one sentence: why can post-test probability differ across age groups?

Low base-rate check:
5. Pick one `age_group`. Keep its sensitivity and false positive rate fixed, but set a hypothetical prevalence like $$ P ( has\\_variant = 1 ) = 0.0002 $$. Compute the hypothetical post-test probability.
6. In 2 to 3 sentences: explain why the post-test probability can still be low even when the screening test is very accurate.

