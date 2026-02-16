# INST 414 — Lab 3 Notes

## GroupBy, `apply`, and `lambda` (and why we use them for conditional probabilities)

These notes are meant to be read alongside **Lab 3 (GroupBy)** *the notebook*. The goal is to help you build an intuition for:

- what `groupby` does (split → apply → combine),
- when `.mean()` is a probability,
- and why `apply(lambda ...)` shows up when we want to do slightly more custom calculations.

In the Lab 3 notebook, you’ll use these ideas on the Titanic dataset to compute quantities like:
- `P(survived=1 | pclass)`
- `P(survived=1 | sex, pclass)` (conditioning on more than one variable)
- conditional joint distributions like `P(sex, pclass | survived)`

---

## What you should be able to do after reading this

By the end, you should be able to:

- Compute averages “within groups” using `groupby`
- Compute conditional probabilities like `P(survived=1 | pclass)`
- Condition on more than one variable (e.g., `sex` and `pclass`)
- Use `apply(lambda grp: ...)` to compute custom summaries by group
- Recognize when you’re accidentally using the wrong denominator

---

## 1) The mental model: “split → apply → combine”

When you write:

```py
titanic.groupby("sex").age.mean()
```

Pandas is doing something like:

1. **Split** the dataset into separate tables, one for each value of `sex`
2. **Apply** the same operation to each table (here: take the mean of `age`)
3. **Combine** the results back into a single output (usually a Series)

This is one of the most common patterns in data science.

---

## 2) Why “mean of a boolean” is a probability

If you create an indicator like:

```py
titanic["is_child"] = titanic["age"] < 18
```

then `is_child` is `True`/`False`. In Python and Pandas:

- `True` behaves like `1`
- `False` behaves like `0`

So the average of the indicator is:

```py
titanic["is_child"].mean()
```

which equals:

> fraction of rows where `is_child` is True

That’s exactly a probability estimated from data.

---

## 3) Conditional probability as a grouped mean

The question:

> Among passengers in each class, what fraction survived?

is:

> `P(survived=1 | pclass)`

In Pandas, the direct way to compute that is:

```py
titanic.groupby("pclass")["survived"].mean()
```

Interpretation:

- For each `pclass` group, take the mean of `survived` (which is 0/1)
- That mean is the share that survived within the group

---

## 4) Three equivalent ways to compute `P(A | B)`

In the notebook, you’ll compute conditional probabilities using three equivalent “methods.” Pick the one you can explain clearly.

### Method A: numerator / denominator (probabilities)

```py
numerator = ((B) & (A)).mean()   # P(A and B)
denominator = (B).mean()        # P(B)
numerator / denominator         # P(A | B)
```

### Method B: numerator / denominator (counts)

```py
numerator_ct = ((B) & (A)).sum()  # count(A and B)
denominator_ct = (B).sum()        # count(B)
numerator_ct / denominator_ct
```

### Method C: “filter first” (direct)

```py
df_B = df[B]
df_B[A].mean()
```

They are the same idea; Method C is usually the easiest to read.

---

## 5) Conditioning on more than one variable

If you want:

> `P(survived=1 | sex, pclass)`

you can group by *both* variables:

```py
titanic.groupby(["sex", "pclass"])["survived"].mean()
```

This produces one survival rate for each `(sex, pclass)` combination.

---

## 6) Why `apply(lambda grp: ...)` shows up

Sometimes you want an operation that isn’t just “take a column and call `.mean()`”.

Example: computing a probability that requires creating an indicator inside each group, or using a more complex logical expression.

That’s where `apply` comes in:

```py
titanic.groupby(["sex", "pclass"]).apply(
    lambda grp: (grp["age"] < 18).mean()
)
```

Read this left to right:

- `titanic.groupby(["sex", "pclass"])`: split into groups
- `.apply(lambda grp: ...)`: run the function on each group-table
- inside the lambda: compute a number for that group

---

## 7) Common pitfalls 

### Pitfall 1: Wrong denominator

If the question is “given male”, your denominator must be **only males**.

### Pitfall 2: Missing ages (`NaN`)

Expressions like `(age < 18)` become `False` when `age` is missing, so means can be biased downward if many ages are missing.

If you want “among known ages”, do:

```py
known = titanic[titanic["age"].notna()]
(known["age"] < 18).mean()
```

### Pitfall 3: Dropping missing values with `dropna`

Pandas has a convenient method for removing rows with missing values: `dropna`.

Use it when the question you’re answering is clearly “**among passengers with known age** …” (or known fare, etc.).

**Core pattern:**

```py
known_age = titanic.dropna(subset=["age"])
```

This keeps only rows where `age` is not missing.

**Example:** `P(age > 50 | survived)` (among known ages)

```py
known_age = titanic.dropna(subset=["age"])

known_age.groupby("survived").apply(
    lambda grp: (grp["age"] > 50).mean()
)
```

**Why this matters:**

If you *don’t* drop missing ages, comparisons like `(titanic["age"] > 50)` treat missing ages as `False`, which can pull probabilities downward.

**A caution:**

When you use `dropna`, you are changing the population you’re describing. If many values are missing, your result may apply to a smaller (and potentially different) subset.

### Pitfall 4: Confusing `.size`, `.shape[0]`, and `.count()`

- `.shape[0]` and `.size` count rows
- `.count()` ignores missing values (depends on the column)

For counts of rows satisfying a condition, `.sum()` on a boolean mask is usually clean:

```py
((titanic["pclass"] == 1) & (titanic["survived"] == 1)).sum()
```

---

## 8) A handy “conditional joint distribution” pattern

Sometimes you want something like:

> `P(survived, pclass | sex)`

One pattern is: group by the conditioning variable, then use `value_counts(normalize=True)` inside each group:

```py
titanic.groupby("sex")[["survived", "pclass"]].value_counts(normalize=True)
```

Interpretation:
- Within each `sex` group, the probabilities across `(survived, pclass)` combinations sum to 1.
