# INST 414 — Lab 5 Notes

## Feature engineering with merges, time windows, and groupby

These notes are meant to be read alongside **Lab 5** (the notebook). The goal of this lab is to practice *feature engineering*: taking raw event-level data and turning it into clean, model-ready columns.

In this lab we build two kinds of features:

- **Current incident features**: information about the *current* arrest (the one in the `universe` table).
- **Prior history features**: information about what happened *before* the current arrest, within a time window.

---

## What you should be able to do after reading this

- Explain the difference between “current incident” vs “prior history” features.
- Create **dummy variables** with `pd.get_dummies`.
- Use `merge(..., how="left")` to add features to the `universe` table without changing which rows are included.
- Use `suffixes` (and `left_on` / `right_on`) to keep merge keys and column names straight.
- Use date filters to keep only events **before** the current arrest and **within** a time window.
- Use `groupby(...).size().reset_index(...)` to create count features.
- Use `fillna(0)` after a left-merge when a missing value really means “zero events”.

---

## The two tables (and why they exist)

In the notebook you load two DataFrames:

- `universe` (1,000 rows): one row per **current arrest** we care about.
  - keys: `arrest_id`, `person_id`
  - date: `filing_date` (treat as the arrest date)
- `arrest_events` (many rows): one row per **arrest event** (current + prior).
  - keys: `arrest_id`, `person_id`
  - date: `filing_date`
  - categories: `charge_degree`, `offense_category`

**Important idea:** `universe` is the “one row per example” table. Feature engineering is mostly about transforming `arrest_events` and then merging the resulting features *into* `universe`.

---

## 0) Always convert dates first

Most “history” logic depends on comparing dates, so do this early:

```py
universe["filing_date"] = pd.to_datetime(universe["filing_date"])
arrest_events["filing_date"] = pd.to_datetime(arrest_events["filing_date"])
```

If you forget, comparisons like `arrest_date < universe_date` may silently behave incorrectly.

---

## 1) Current incident features: merge on `arrest_id`

A current-incident feature should describe the *current arrest* (the row in `universe`), so you typically merge on `arrest_id`.

Example pattern:

1) Create a feature in `arrest_events` (e.g., a dummy for felony).
2) Merge that feature into `universe` on `arrest_id` using a **left join**.

```py
arrest_events = pd.get_dummies(arrest_events, columns=["charge_degree"])

universe = universe.merge(
    arrest_events[["arrest_id", "charge_degree_felony"]],
    on="arrest_id",
    how="left",
)
```

**Why `how="left"`?** It keeps all 1,000 `universe` rows. You should generally expect the number of rows in `universe` to stay at 1,000 after feature merges.

---

## 2) Prior history features: merge on `person_id`, then filter by time

A prior-history feature is about the person’s record **before** the current arrest. The standard recipe is:

1) Create a *temporary* DataFrame by merging `universe` and `arrest_events` on `person_id`.
2) Use suffixes so you can distinguish “current arrest date” vs “event date”.
3) Filter down to events that happened **before** the current arrest.
4) Filter down to a time window (e.g., last 1 year, last 2 years).
5) Group and count.
6) Merge the count back into `universe`.
7) Fill missing values with 0.

### Step 2.1: Build the temporary table

```py
temp_df = universe[["arrest_id", "person_id", "filing_date"]].merge(
    arrest_events,
    on="person_id",
    how="left",
    suffixes=["_univ", "_arr"],
)
```

Now you have both dates:
- `filing_date_univ`: the **current** arrest date
- `filing_date_arr`: the **event** date

### Step 2.2: Keep only events before the current arrest

```py
temp_df = temp_df[temp_df["filing_date_arr"] < temp_df["filing_date_univ"]]
```

This avoids “leaking” future information into a history feature.

### Step 2.3: Keep only events within a window

For “last 1 year”:

```py
temp_df = temp_df[
    temp_df["filing_date_arr"] > (temp_df["filing_date_univ"] - pd.DateOffset(years=1))
]
```

For “last 2 years”, change `years=2`.

### Step 2.4: Count events, then merge back into `universe`

```py
counts = (
    temp_df.groupby(["arrest_id_univ", "person_id"])
    .size()
    .reset_index(name="num_arr_last_year")
)

universe = universe.merge(
    counts,
    left_on=["arrest_id", "person_id"],
    right_on=["arrest_id_univ", "person_id"],
    how="left",
)

universe["num_arr_last_year"] = universe["num_arr_last_year"].fillna(0)
universe.drop(columns=["arrest_id_univ"], inplace=True)
```

**Why fill with 0?** If there are no matching prior events in the window, the left-merge produces `NaN`, but conceptually the count should be zero.

---

## 3) One-hot encoding (and why we don’t merge every category)

When you use `get_dummies`, you often don’t need every category. If you include all categories, one of them is redundant (it’s implied when all the others are 0).

In the Lab Task, you one-hot encode `offense_category` and merge in:
- `drug`
- `property`
- `violent`

and you intentionally *don’t* merge in `other` because it would be redundant.

---

## 4) Common pitfalls (and how to catch them)

- **Row count changes after a merge:** If `universe` stops being 1,000 rows, you probably used the wrong merge keys or did a many-to-many merge unintentionally.
- **Forgetting `suffixes`:** Then you can’t tell which date is which, and you’ll filter incorrectly.
- **Including the current arrest in “prior history”:** Make sure you filter `filing_date_arr < filing_date_univ`.
- **Not converting dates:** Always run `pd.to_datetime` first.
- **Not filling missing counts:** Counts should usually be 0, not `NaN`.

---

## Mental model to keep in mind

Every engineered feature should answer a clear question like:

- “Was the current charge a felony?”
- “How many arrests did this person have in the last 2 years (before today)?”
- “Does this person’s current arrest include a violent offense category?”

If you can’t say the question in one sentence, it’s usually a sign the feature definition needs to be clarified.

