# Time-Based Plotting Recipes: A Troubleshooting Guide
**CCJS 418E: Coding for Criminology**

A practical reference for creating time-based visualizations when working on problem sets.

---

## Foundation: Two Key Patterns You'll Use

### Pattern 1: The reset_index() Pattern

**Why we need it:**
When you use `groupby()`, pandas creates a **Series** with your grouping variable as the **index**. But seaborn's plotting functions expect **columns**, not indexes.

```python
# After groupby - this is a Series with year_month as INDEX
monthly_counts = df.groupby('year_month').size()
# Can't plot this directly with seaborn!

# reset_index() converts the index into a regular column
monthly_counts = df.groupby('year_month').size().reset_index(name='arrests')
# Now you have a DataFrame with columns: year_month, arrests
# Seaborn can plot this!
```

**The rule:** After `groupby().size()`, always use `.reset_index()` before plotting with seaborn.

---

### Pattern 2: The to_period() → to_timestamp() Pattern

**Why we need it:**
- `to_period('M')` creates month periods like `2024-01` which are perfect for grouping
- But plotting libraries (seaborn/matplotlib) need actual **timestamps** (dates) for the x-axis
- `to_timestamp()` converts periods back to timestamps for plotting

```python
# Create monthly periods for grouping
df['year_month'] = df['ARREST_DATE'].dt.to_period('M').dt.to_timestamp()
#                                                      ^^^^^^^^^^^^^^^^^^^^
#                                                      Converts period → timestamp

# Now you can group by year_month AND plot it
monthly_counts = df.groupby('year_month').size().reset_index(name='arrests')
sns.lineplot(data=monthly_counts, x='year_month', y='arrests')  # Works!
```

**The rule:** When creating period columns for plotting, always use `.dt.to_period('M').dt.to_timestamp()`

---

## Recipe 1: Plot Monthly Trend as a Line

**Goal:** Create a line plot showing how arrests (or any count) changed month-by-month

**Complete Code:**
```python
# Step 1: Create monthly period column
df['year_month'] = df['ARREST_DATE'].dt.to_period('M').dt.to_timestamp()

# Step 2: Count arrests by month and reset_index
monthly_arrests = df.groupby('year_month').size().reset_index(name='arrests')

# Step 3: Plot
sns.lineplot(data=monthly_arrests, x='year_month', y='arrests')
```

**Key Steps:**
1. `dt.to_period('M').dt.to_timestamp()` - Creates monthly periods that can be plotted
2. `groupby().size().reset_index(name='arrests')` - Counts per month and makes it a DataFrame
3. `sns.lineplot()` - Creates the line plot (x=time, y=count)

**Common Error:**
```
❌ TypeError: 'Period' objects are not iterable
```
**Fix:** Add `.dt.to_timestamp()` after `.dt.to_period('M')`

---

## Recipe 2: Plot Monthly Counts as Bars

**Goal:** Create a bar chart showing monthly counts (useful for comparing specific months)

**Complete Code:**
```python
# Step 1: Create monthly period column
df['year_month'] = df['ARREST_DATE'].dt.to_period('M').dt.to_timestamp()

# Step 2: Count arrests by month and reset_index
monthly_arrests = df.groupby('year_month').size().reset_index(name='arrests')

# Step 3: Plot as bars
sns.barplot(data=monthly_arrests, x='year_month', y='arrests')
```

**Key Steps:**
Same as Recipe 1, but use `sns.barplot()` instead of `sns.lineplot()`

**When to use bars vs lines:**
- **Line plots:** Show trends over many time periods (months, quarters)
- **Bar plots:** Compare specific time periods (2-8 months)

---

## Recipe 3: Compare Two Time Periods Side-by-Side

**Goal:** Show counts for "before" vs "after" a specific date (e.g., baseline vs pullback)

**Complete Code:**
```python
# Step 1: Define your cutoff date
cutoff_date = pd.to_datetime('2014-12-01')

# Step 2: Create period labels using .loc
df['period'] = 'Before'
df.loc[df['ARREST_DATE'] >= cutoff_date, 'period'] = 'After'

# Step 3: Count arrests by period and reset_index
period_counts = df.groupby('period').size().reset_index(name='arrests')

# Step 4: Plot
sns.barplot(data=period_counts, x='period', y='arrests')
```

**Key Steps:**
1. `pd.to_datetime()` - Creates a datetime object for comparison
2. `.loc[]` assignment - Labels rows based on condition (before/after cutoff)
3. `groupby('period')` - Groups by your labels
4. `sns.barplot()` - Shows the comparison visually

**Note:** If comparing periods of different lengths, calculate daily rates:
```python
# Add this after Step 3:
baseline_days = (cutoff_date - df['ARREST_DATE'].min()).days
after_days = (df['ARREST_DATE'].max() - cutoff_date).days

period_counts['days'] = [baseline_days, after_days]
period_counts['daily_rate'] = period_counts['arrests'] / period_counts['days']

# Plot daily rate instead
sns.barplot(data=period_counts, x='period', y='daily_rate')
```

---

## Recipe 4: Plot Multiple Categories Over Time

**Goal:** Show how different arrest types (or any category) changed over time on the same plot

**Complete Code:**
```python
# Step 1: Create monthly period column
df['year_month'] = df['ARREST_DATE'].dt.to_period('M').dt.to_timestamp()

# Step 2: Count by BOTH month and category, then reset_index
monthly_by_category = df.groupby(['year_month', 'LAW_CAT_CD']).size().reset_index(name='arrests')

# Step 3: Plot with hue parameter
sns.lineplot(data=monthly_by_category, x='year_month', y='arrests', hue='LAW_CAT_CD')
```

**Key Steps:**
1. `groupby(['year_month', 'LAW_CAT_CD'])` - Groups by TWO variables (month AND category)
2. `reset_index()` - Converts both grouping variables into columns
3. `hue='LAW_CAT_CD'` - Creates separate lines for each category (different colors)

**Common Error:**
```
❌ Plot shows only one line even though you have multiple categories
```
**Fix:** Make sure you included both variables in `groupby([...])` and added `hue=` parameter

---

## Recipe 5: Show Before/After with Period Indicators

**Goal:** Compare multiple time periods (e.g., baseline, pullback, recovery) over time

**Complete Code:**
```python
# Step 1: Define period boundaries
pullback_start = pd.to_datetime('2014-12-01')
pullback_end = pd.to_datetime('2015-02-28')

# Step 2: Create three-period labels using .loc (ORDER MATTERS!)
df['period'] = 'Baseline'  # Start with earliest period as default
df.loc[df['ARREST_DATE'].between(pullback_start, pullback_end), 'period'] = 'Pullback'
df.loc[df['ARREST_DATE'] > pullback_end, 'period'] = 'Recovery'

# Step 3: Create monthly period column
df['year_month'] = df['ARREST_DATE'].dt.to_period('M').dt.to_timestamp()

# Step 4: Count by month and period, then reset_index
monthly_by_period = df.groupby(['year_month', 'period']).size().reset_index(name='arrests')

# Step 5: Plot with hue for periods
sns.lineplot(data=monthly_by_period, x='year_month', y='arrests', hue='period')
```

**Key Steps:**
1. Set default label first: `df['period'] = 'Baseline'`
2. Override specific rows with `.loc[]` - **order matters!** (go chronologically)
3. `.between()` method - Clean way to filter date ranges
4. Group by BOTH `year_month` and `period` to see trends within each period
5. Use `hue='period'` to color-code the different periods

**Common Error:**
```
❌ All rows are labeled 'Recovery' (the last label)
```
**Fix:** Make sure you set the default label FIRST, then use `.loc[]` to override specific rows

---

## Recipe 6: Calculate Percentage Change Between Periods

**Goal:** Calculate how much arrests changed from one period to another (e.g., "arrests dropped 26% during pullback")

**Complete Code:**
```python
# Step 1: Create period labels (using Recipe 5 pattern)
pullback_start = pd.to_datetime('2014-12-01')
pullback_end = pd.to_datetime('2015-02-28')

df['period'] = 'Baseline'
df.loc[df['ARREST_DATE'].between(pullback_start, pullback_end), 'period'] = 'Pullback'

# Step 2: Count arrests by period
period_counts = df.groupby('period').size()

# Step 3: Calculate number of days in each period
baseline_days = (pullback_start - df['ARREST_DATE'].min()).days
pullback_days = (pullback_end - pullback_start).days + 1  # +1 to include both endpoints

# Step 4: Calculate daily rates
baseline_daily = period_counts['Baseline'] / baseline_days
pullback_daily = period_counts['Pullback'] / pullback_days

# Step 5: Calculate percentage change
pct_change = ((pullback_daily - baseline_daily) / baseline_daily) * 100

print(f"Percentage change: {pct_change:.1f}%")
```

**Key Steps:**
1. Group by period to get total counts
2. Calculate days using date subtraction: `(end_date - start_date).days`
3. **Always use daily rates when comparing periods of different lengths**
4. Percentage change formula: `((new - old) / old) * 100`
5. Negative percentage = decrease, positive = increase

**When to use this:**
- Comparing a 3-month period to a 12-month period
- Calculating "arrest rate dropped by X%" statements
- Any time periods have different lengths

---

## Recipe 7: Using .iloc to Access Grouped Results

**Goal:** Extract specific values from grouped data when you know the position

**Complete Code:**
```python
# Step 1: Group by period and category (creates MultiIndex)
period_lawcat = df.groupby(['period', 'LAW_CAT_CD']).size()

# The result is ordered alphabetically:
# Position 0: Baseline, F (Felony)
# Position 1: Baseline, M (Misdemeanor)
# Position 2: Pullback, F
# Position 3: Pullback, M
# Position 4: Recovery, F
# Position 5: Recovery, M

# Step 2: Use .iloc to access by position
baseline_felony = period_lawcat.iloc[0]
baseline_misdemeanor = period_lawcat.iloc[1]
pullback_felony = period_lawcat.iloc[2]
pullback_misdemeanor = period_lawcat.iloc[3]

# Step 3: Calculate rates and compare
# (continue with daily rate calculations like Recipe 6)
```

**Key Steps:**
1. When you `groupby()` with multiple variables, results are sorted alphabetically
2. Use `.iloc[position]` to grab specific combinations (0-indexed)
3. Positions follow alphabetical order of your groups

**When to use .iloc:**
- You have a small number of groups and know their order
- You need to extract specific values for calculations
- Alternative: use `.reset_index()` and filter with conditions (more flexible but more code)

**Common Error:**
```
❌ Getting wrong values because groups aren't in the order you expected
```
**Fix:** Print the grouped series first to see the order: `print(period_lawcat)`, then use correct positions

---

## Quick Troubleshooting Guide

### "I can't plot my grouped data"
→ Did you use `.reset_index()` after `groupby().size()`?

### "My x-axis shows weird period labels"
→ Add `.dt.to_timestamp()` after `.dt.to_period('M')`

### "My percentage change is wrong"
→ Are you comparing periods of different lengths? Calculate daily rates first.

### "All my rows have the same period label"
→ Check your `.loc[]` conditions - make sure they're actually filtering different rows

### "I get KeyError when using .iloc"
→ Print your grouped series first to see how many groups you actually have

### "My line plot looks weird/jagged"
→ Make sure your x-axis variable is properly sorted by time (groupby does this automatically)

### "I want to compare felonies vs misdemeanors over time"
→ Use Recipe 4 with `groupby(['year_month', 'LAW_CAT_CD'])`

---

## Summary: The Essential Pattern

For 90% of time-based plotting tasks, follow this sequence:

```python
# 1. Create time period column (if needed)
df['year_month'] = df['date_col'].dt.to_period('M').dt.to_timestamp()

# 2. Create period labels (if comparing before/after)
df['period'] = 'Before'
df.loc[df['date_col'] >= cutoff, 'period'] = 'After'

# 3. Group and reset_index
counts = df.groupby(['year_month', 'period']).size().reset_index(name='count')

# 4. Plot
sns.lineplot(data=counts, x='year_month', y='count', hue='period')
```

**Remember:**
- `reset_index()` after grouping → makes data plottable
- `.dt.to_timestamp()` after `.dt.to_period()` → makes periods plottable
- Daily rates when comparing different length periods → fair comparison
- `.loc[]` for labeling rows → creates before/after indicators

---

## Getting Help from AI

When asking ChatGPT or Claude for help with datetime plotting:

**Good prompt structure:**
```
I have a DataFrame with a date column called 'ARREST_DATE' and I want to
[specific task: plot monthly trends/compare two periods/etc.].

I'm getting this error: [paste error message]

Here's my code so far:
[paste your code]

What am I doing wrong?
```

**Include in your prompt:**
- What you're trying to accomplish (be specific)
- The error message (if any) - copy the whole thing
- Your current code
- What columns your DataFrame has (`df.columns`)

**Common AI follow-up questions to expect:**
- "Is your date column in datetime format?" → Check with `df['date_col'].dtype`
- "Did you reset the index?" → Look for `.reset_index()` in your code
- "What does your grouped data look like?" → Print it: `print(grouped_data.head())`
