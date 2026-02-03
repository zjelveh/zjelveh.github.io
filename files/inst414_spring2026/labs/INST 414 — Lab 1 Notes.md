# INST 414 — Lab 1 Notes

## Introduction to Tables and Pandas

These notes are meant to be read alongside **Lab 1**. The goal is to help you build an intuition for what a dataset *is* (as a table) and how we work with tables in Python using **Pandas**.

### What you should be able to do after reading this

By the end, you should be able to:

- Describe tabular data using **rows**, **columns**, and **values**  
- Explain what **tidy data** is and why it makes analysis easier  
- Load a CSV into Python with Pandas  
- Do quick “first look” checks: `.columns`, `.shape`, `.head()`  
- Answer simple questions using summaries and filters (counts, means, and row selection)

---

## 1\) What counts as “data”?

Data can be almost anything we can record: images, video, audio, text, sensor streams, web logs, and so on. This course will touch a few formats, but we’ll spend a lot of time converting things into a single workhorse format:

**a table.**

Why? Because once information is in a table, we can reliably:

- summarize it,  
- visualize it,  
- and build prediction models from it.

---

## 2\) For this course, data is tabular

A **table** is a rectangle: rows and columns. In data science, we attach meaning to that structure:

- **Rows \= observations** (units of analysis)  
  Examples: a person, a day, a county, a state-year, a transaction, a document.  
    
- **Columns \= variables** (attributes measured about each observation)  
  Examples: age, income, year, treatment, outcome, category.  
    
- **Cells \= values** (the recorded measurement of a variable for one observation)

If you ever feel lost, come back to one question:

**What does one row represent?**

If you can answer that, everything else becomes much easier.

---

## 3\) Tidy data: the standard shape we aim for

“Tidy data” is a set of conventions for structuring a table so analysis is predictable and tools behave the way you expect.

Think of tidy data as a contract between you and your software:

| Tidy rule | What it means |
| :---- | :---- |
| Each variable is a column | Variable names live in the header row |
| Each observation is a row | One row \= one unit of analysis |
| Each value is a cell | No stacking multiple values in one cell |

When data is tidy, a huge range of operations becomes simpler and less error-prone: filtering, grouping, summarizing, plotting, and modeling.

---

## 4\) Values, variables, observations (one mental model)

A dataset is ultimately a collection of **values**. Values can be:

- **quantitative** (numbers: counts, dollars, rates), or  
- **qualitative** (strings/labels: categories like “M/F”, “NY/CA”, “control/treatment”).

Every value belongs to both:

- a **variable** (the column), and  
- an **observation** (the row).

A major benefit of tidy data is **consistency**: once your data is in a tidy table, you can reuse the same mental model and the same code patterns across lots of different problems.

---

## 5\) Missing values (normal, not a disaster)

Real datasets almost always contain missing values: something wasn’t measured, wasn’t recorded, got lost, or doesn’t apply.

Two important points for now:

1. **Missing values are common.**  
2. Many tools have default behaviors for missingness (often “ignore missing values” in simple summaries), but you should always be aware of what’s happening.

Later in the semester we’ll talk about how missingness can create bias. For Lab 1, the goal is simply: recognize missingness and don’t panic.

---

## 6\) Uniqueness and keys: “what should be unique?”

Sometimes we expect certain columns to uniquely identify each row—like an ID.

Example: if a table is supposed to have one row per **person × treatment**, then the pair `(name, treatment)` should be unique.

If it isn’t unique, one of two things is happening:

- you have duplicates / data issues, or  
- you misunderstood the unit of analysis (maybe it’s one row per person per day, or per visit, etc.).

This “what should be unique?” question is one of the most useful debugging tools in real data work.

---

## 7\) The same information can be arranged different ways

Here is a familiar “presentation-style” table:

**Table A: one row per person, columns for each treatment**

| name | treatmentA | treatmentB |
| :---- | ----: | ----: |
| John Smith | — | 2 |
| Jane Doe | 16 | 11 |
| Mary Johnson | 3 | 1 |

Notice: John Smith is missing a value under treatment A.

The *same* information can be rearranged like this:

**Table B: one row per treatment, columns for each person**

|  | John Smith | Jane Doe | Mary Johnson |
| :---- | ----: | ----: | ----: |
| treatmentA | — | 16 | 3 |
| treatmentB | 2 | 11 | 1 |

### Why we care

You’re allowed to rearrange values in many ways, but some layouts are much easier to analyze than others. A big chunk of data cleaning is taking a human-friendly representation and converting it into a tool-friendly representation (usually tidy).

---

## 8\) What we do with tables: basic operations

Once data is in a table, analysis often starts with simple questions:

- How many unique categories appear in a column?  
- How frequent is each category?  
- What’s the average of a numeric column?  
- What happens if we compute the average only for a subset of rows?

Those are “small” operations, but they’re the building blocks for everything else.

---

## 9\) Pandas: working with tables in Python

**Pandas** is the standard Python library for working with tabular data.

### DataFrames and Series

Pandas has two core objects:

- **DataFrame**: a table (rows × columns)  
- **Series**: a single column (or row) of a DataFrame

Rule of thumb:

- selecting **one** column usually gives a **Series**  
- selecting **multiple** columns gives a **DataFrame**

---

## 10\) Your first Pandas workflow (the patterns you’ll reuse constantly)

### Step 1: Load the dataset (`read_csv`)

```py
import pandas as pd
df = pd.read_csv("some_file.csv")
```

Interpretation:

- `pd.read_csv(...)` **returns** a DataFrame.  
- `df = ...` stores it so you can use it.

Common early mistake: forgetting `df =` and then wondering why `df` doesn’t exist.

---

### Step 2: Do the “first look” checks

When you load a dataset, do these immediately:

**(a) Column names**

```py
df.columns
```

**(b) Dataset size**

```py
df.shape
```

This returns `(number_of_rows, number_of_columns)`.

If you want the pieces:

```py
df.shape[0]  # rows
df.shape[1]  # columns
```

**(c) Preview the first rows**

```py
df.head()      # default is 5 rows
df.head(n=10)  # first 10 rows
```

Treat `head()` as a sanity check: Do the columns look right? Do values look plausible?

---

### Step 3: Select a column

```py
df["column_name"]
```

This usually returns a Series.

If you want to store the name in a variable (useful later):

```py
col = "year"
df[col]
```

---

### Step 4: Count unique values and frequencies

**Unique values**

```py
df["year"].unique()
```

**Number of unique values**

```py
df["year"].nunique()
```

**Frequency table**

```py
df["sex"].value_counts()
```

**Proportions instead of counts**

```py
df["sex"].value_counts(normalize=True)
```

`normalize=True` divides by the total number of rows, turning counts into shares.

---

### Step 5: Summarize numeric columns

For numeric columns:

```py
df["some_numeric_col"].sum()
df["some_numeric_col"].mean()
df["some_numeric_col"].max()
df["some_numeric_col"].min()
```

A quiet but important point: these summaries only mean something if the column truly represents a numeric measurement (and you know the unit).

---

### Step 6: Filter rows with logic (the workhorse move)

Filtering means: keep only the rows that satisfy a condition.

Comparison operators:

| Operator | Meaning |
| :---- | :---- |
| `==` | equals |
| `!=` | not equals |
| `>` | greater than |
| `<` | less than |
| `>=` | greater than or equal |
| `<=` | less than or equal |

**One condition**

```py
df[df["year"] == 2019]
```

Read that in English: “Give me the rows where year equals 2019.”

Common pitfall:

- `=` is assignment  
- `==` is comparison

---

### Filter → select column → summarize (a full “analysis sentence”)

Many real analyses look like this:

```py
df[df["year"] == 2019]["result"].mean()
```

Translation:

1. filter to year 2019  
2. select the `result` column  
3. compute the mean

---

### Multiple conditions (the parentheses rule)

Use:

- `&` for “and”  
- `|` for “or”

And **wrap each condition in parentheses**:

```py
df[(df["year"] == 2019) & (df["sex"] == "M")]
```

If you forget parentheses, you’ll often get confusing errors.

---

## Appendix A — The 6 first checks after loading any dataset

| Task | Code |
| :---- | :---- |
| Confirm you have a DataFrame | `type(df)` |
| See columns | `df.columns` |
| Check size | `df.shape` |
| Preview first rows | `df.head()` |
| Quick missingness scan | `df.isna().sum()` |
| Numeric summary | `df.describe()` |

## Appendix B — Selection and filtering patterns

### Column selection

| You want | Pattern |
| :---- | :---- |
| One column (Series) | `df["col"]` |
| Multiple columns (DataFrame) | `df[["col1","col2"]]` |

### Row filtering

| You want | Pattern |
| :---- | :---- |
| One condition | `df[df["col"] == value]` |
| Two conditions (and) | `df[(cond1) & (cond2)]` |
| Two conditions (or) | \`df\[(cond1) |

