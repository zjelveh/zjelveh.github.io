# INST 414 — Lab 9 Notes

## Visualization for Fairness and Model Evaluation

These notes go with **Lab 9: Visualization for Fairness and Model Evaluation** and focus on the plotting side of the week.

Main topics:

- the difference between `seaborn` and `matplotlib`
- what the most common plotting functions are doing
- why we convert date-like strings with `pd.to_datetime(...)`
- how plotting choices connect to the question we are asking
- how to read calibration plots

---

## The bail reform context for the datasets

Both datasets in this lab come from the broader **Maryland pretrial / bail reform** context.

In **November 2016**, Maryland changed its pretrial system to reduce routine reliance on cash bail. Before the reform, many defendants could be detained because they could not afford the amount set by the court. The reform pushed decision-making toward clearer release and detention categories rather than automatic use of money bail.

The first dataset tracks county-level shares of outcomes such as:

- release on recognizance (`ROR`)
- held detained on bail (`HDOB`)
- held without bail (`HWOB`)

The second dataset stays in that same broader pretrial setting, but moves to the **individual level**. It lets us study predicted rearrest risk, observed outcomes, and subgroup patterns in the kinds of model outputs that show up in fairness discussions.

So the policy setting is the same across the whole lab. What changes is the level of analysis and the question we are asking:

- county-month trends around a reform
- individual-level predictions, outcomes, and calibration

---

## Main plot types in this lab

This lab covers:

- line plots for variables measured over time
- bar plots for comparing groups or periods
- histograms for single-variable distributions
- scatter plots for two numeric variables
- what `sns.regplot(...)` adds relative to `sns.scatterplot(...)`
- calibration plots
- what the `plt...` lines are doing in a plot

---

## 1) `seaborn` versus `matplotlib`

In many plots, you will see both `sns...` and `plt...` used together. They usually play different roles.

### `seaborn`

`seaborn` is the library we are using to **make the actual statistical plot**.

Examples:

- `sns.lineplot(...)`
- `sns.barplot(...)`
- `sns.histplot(...)`
- `sns.scatterplot(...)`
- `sns.regplot(...)`

When you see one of those lines, that is usually the line that answers:

> What kind of plot are we making?

### `matplotlib`

`matplotlib` is the library we are using to **control how the figure looks**.

Examples:

- `plt.figure(...)`
- `plt.title(...)`
- `plt.xlabel(...)`
- `plt.ylabel(...)`
- `plt.legend(...)`
- `plt.axvline(...)`
- `plt.tight_layout()`
- `plt.show()`

When you see one of those lines, that is usually answering:

> How should the plot be labeled, sized, or cleaned up?

### Reading a plot command

One useful way to read a plot command is:

```python
sns.lineplot(...)   # create the plot from the data
plt.title(...)      # name the plot
plt.xlabel(...)     # label x-axis
plt.ylabel(...)     # label y-axis
plt.show()          # display it cleanly
```

So the `sns` line is usually the main plot, and the `plt` lines are usually there to make it readable.

---

## 2) What `plt.figure(figsize=(...))` is doing

A common setup line is:

```python
plt.figure(figsize=(12, 6))
```

This creates a blank plotting canvas.

### `figsize`

The argument `figsize=(12, 6)` means:

- width = 12 inches
- height = 6 inches

This matters because if the figure is too small:

- labels may overlap
- legends may cover the data
- long category names may get cut off

So `plt.figure(...)` is not making the statistical graph itself. It is just creating the space that the graph will be drawn on.

---

## 3) Why we use `pd.to_datetime(...)`

In the bail dataset, `year_month_str` starts as text. `pd.to_datetime(...)` converts it into a real datetime variable:

```python
bail['year_month'] = pd.to_datetime(bail['year_month_str'])
```

That matters because datetimes sort correctly and work cleanly in time-based plots.

### Two time variables

The two time variables serve different purposes:

- `year_month`: calendar sequence
- `months_from_reform`: reform-centered sequence

The lab includes a short example with `year_month`. For before/after reform comparisons, `months_from_reform` is often easier to read because `0` marks the reform month directly.

---

## 4) Common `seaborn` function pattern

Many `seaborn` lines follow the same structure:

```python
sns.some_plot_type(data=df, x='column1', y='column2', hue='group_column')
```

You should get used to reading that as:

- `data=`: which DataFrame contains the data
- `x=`: which column goes on the x-axis
- `y=`: which column goes on the y-axis
- `hue=`: optional grouping variable used to split by color

This is the main pattern used throughout the lab.

---

## 5) `sns.lineplot(...)`

Example:

```python
sns.lineplot(data=county_df, x='months_from_reform', y='pct_ror', marker='o')
```

### What the plot shows

This makes a line plot where:

- x-axis = `months_from_reform`
- y-axis = `pct_ror`
- each point is connected in order by a line

### When to use it

Line plots are especially useful when:

- the x-axis is ordered time
- we care about the direction and shape of a trend

### What `marker='o'` does

That argument adds visible point markers on top of the line.

This is useful because it lets you see both:

- the overall trend
- the actual observed points

If you remove `marker='o'`, the plot becomes cleaner, but you lose some visibility into the underlying observed values.

A vertical reference line can be useful when there is a specific event month or policy change you want to mark.

For example, a line at `x = 0` can mark the reform month and separate:

- before reform
- after reform

---

## 6) `sns.barplot(...)`

Example:

```python
sns.barplot(data=county_period_avg, x='county', y='pct_ror', hue='period')
```

### What the plot shows

This makes grouped bars.

- x-axis = county
- y-axis = average `pct_ror`
- hue = before/after period

So each county gets two bars:

- one for `Before`
- one for `After`

### When to use it

Bar plots are good when:

- the x-axis is categorical
- we want to compare average values across categories

### Optional ordering

By default, the county order may be arbitrary or alphabetical. That is fine for a first grouped comparison.

If you want a more interpretable order, you can pass an `order=` argument. In the lab, one optional version sorts counties by the average `Before` ROR value.

### Why we rotate x-axis labels

Because county names are long, we use:

```python
plt.xticks(rotation=45, ha='right')
```

This rotates the labels so they do not overlap.

Again, that is a `matplotlib` cleanup step, not the plot itself.

---

## 7) `sns.histplot(...)`

Example:

```python
sns.histplot(data=bail, x='pct_ror', bins=20, kde=True)
```

### What the plot shows

A histogram shows the distribution of one variable.

Here, the variable is `pct_ror`.

The histogram answers questions like:

- Are most values clustered in one range?
- Is the distribution wide or narrow?
- Is it skewed?
- Are there extreme values?

### What `bins=20` means

The histogram groups values into 20 buckets.

- fewer bins = smoother, more general picture
- more bins = more detail, but sometimes more noise

Changing `bins` changes the appearance of the histogram a lot.

### What `kde=True` does

This adds a smooth density curve on top of the histogram.

That curve is not showing counts directly. It is a smoothed summary of the distribution.

It can help you see the general shape of the data more easily.

---

## 8) `sns.scatterplot(...)`

Example:

```python
sns.scatterplot(data=bail, x='pct_felony', y='pct_ror', alpha=0.5, s=50)
```

### What the plot shows

A scatter plot puts one numeric variable on each axis.

Each point is one observation.

Here:

- x-axis = `pct_felony`
- y-axis = `pct_ror`

### When to use it

Scatter plots are useful when we want to see:

- whether two variables move together
- whether the relationship looks positive or negative
- whether there are outliers
- whether there are clusters

### What `alpha=0.5` does

This makes the points partly transparent.

That helps when many points overlap. If points were fully opaque, dense regions could hide how much overlap there is.

### What `s=50` does

This controls point size.

- smaller `s` = less visual clutter
- larger `s` = easier to see individual points

---

## 9) `sns.regplot(...)`

Example:

```python
sns.regplot(
    data=bail,
    x='pct_felony',
    y='pct_ror',
    scatter_kws={'alpha': 0.3, 's': 30},
    line_kws={'color': 'red'}
)
```

### What the plot shows

This combines:

- a scatter plot
- a fitted trend line

### When to use it

Sometimes a scatter plot alone is noisy. A fitted line gives a quick visual summary of the relationship.

### What `scatter_kws` means

This is short for “scatter keyword arguments.”

It passes settings to the scatter-point part of the plot.

Here:

- `alpha: 0.3` makes the points more transparent
- `s: 30` makes the points smaller

### What `line_kws` means

This passes settings to the fitted line.

Here:

- `color: 'red'` makes the line red so it stands out

`regplot` is a more customized `seaborn` plot.

---

## 10) Calibration plots: why they are different

The calibration section feels more code-heavy than the earlier plots. That is because we are not directly plotting raw columns from a DataFrame.

Instead, we first compute summary points using:

```python
calibration_curve(y_true, y_prob)
```

### What `calibration_curve(...)` returns

It returns two arrays:

- the observed outcome rate within each bin
- the average predicted probability within each bin

Those are the points we plot.

So the structure is:

1. take predicted probabilities and true outcomes
2. bin the predictions
3. compute observed and predicted values by bin
4. plot those computed values

### Why this is important conceptually

A calibration plot is about this question:

> When the model says “about 30%,” do about 30% actually have the outcome?

That is different from ranking or classification.

---

## 11) The 45-degree line in a calibration plot

A common reference line is:

```python
plt.plot([0, 1], [0, 1], 'k--', label='Perfect Calibration')
```

This draws a dashed diagonal line from `(0, 0)` to `(1, 1)`.

That line represents perfect calibration.

Why?

Because on that line:

- predicted probability = observed outcome rate

So points close to that line suggest better calibration.

---

## 12) Calibration by group

For by-group calibration, we compute calibration separately for each subgroup.

That helps answer a question like:

> Does the model seem equally calibrated for different groups?

One model can look fine overall while still behaving differently across subgroups.

---
