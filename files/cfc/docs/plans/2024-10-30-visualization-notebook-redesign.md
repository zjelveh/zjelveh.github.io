# Visualization Notebook Redesign

**Date:** 2024-10-30
**Purpose:** Create a lighter, more focused version of the visualization lecture notebook
**Target Audience:** CCJS 418E students learning data visualization with seaborn

## Design Goals

1. **Reduce text density** - Current notebook is very text-heavy; new version should be sparse and scannable
2. **Prioritize parameter clarity** - Most important element is clearly explaining what each parameter does
3. **Integrate pandas practice** - Show the pattern: aggregate/filter data → visualize result
4. **Remove matplotlib dependencies** - Use seaborn's built-in capabilities, avoid `plt` commands where possible
5. **Disable confidence intervals** - Use `errorbar=None` to simplify plots for beginners
6. **Maintain comprehensive coverage** - Keep all exercises (7 total) and core plot types

## Content Structure

### Format Decisions

**Plot Type Explanations:** Brief paragraphs (4-5 sentences) covering:
- What the plot shows
- When to use it
- What patterns to look for

**Parameter Documentation:** Clean markdown tables with two columns:
- Parameter name
- What it does (clear, concise description)

**Code Examples:** Progressive complexity, building from simple to advanced

### Plot Type Sequence

**1. Line Plots** (trends over time)
- Start with simplest case: single county, single variable
- Introduce filtering with pandas
- Add groupby practice: calculate statewide averages
- Layer in `hue` parameter for group comparisons

**2. Bar Charts** (comparing categories)
- Brief intro emphasizing difference from histograms
- **Key distinction taught:** Bar charts = discrete categories; Histograms = continuous distributions
- Pandas practice: `groupby(['county', 'period'])` for aggregation
- Show `order` parameter for meaningful sorting
- Advanced: `.pivot()` for reshaping data

**3. Histograms** (distributions)
- Explain why no groupby needed (plotting raw distributions)
- Show `.apply()` for creating categorical period column
- Demonstrate `bins` parameter impact
- Use `hue` to compare distributions across groups
- Introduce `stat='density'` for normalized comparisons

**4. Scatter Plots** (relationships between variables)
- Plot raw data to show relationships
- Pandas practice: create size categories with groupby + merge
- Layer in `hue` for grouped scatter plots
- Show `sns.regplot()` for trend lines (with parameter tables for both)

## Technical Specifications

### Seaborn Configuration

**Turn off confidence intervals globally:**
```python
# Use errorbar=None in lineplot, barplot, pointplot
sns.lineplot(data=df, x='time', y='value', errorbar=None)
```

**Avoid matplotlib where possible:**
- No `plt.figure()`, `plt.title()`, `plt.xlabel()`, etc.
- Use seaborn's native capabilities
- Exception: May need minimal matplotlib for showing plots in certain environments

### Pandas Integration Pattern

Each plot type section demonstrates:
1. **Filter/select** data with pandas (`.loc`, boolean indexing)
2. **Aggregate** data with groupby when comparing groups
3. **Transform** data (create new columns with `.apply()`, reshape with `.pivot()`)
4. **Visualize** the prepared data with seaborn

This reinforces: "Prepare your data with pandas, then visualize with seaborn"

## Notebook Outline

### Opening Section
- Title: "Data Visualization with Seaborn"
- Learning goals (3-4 bullets)
- Policy context: Maryland pretrial reform (2-3 sentences)
- Load data cell
- Quick data preview

### Main Content

**Part 1: Line Plots - Showing Trends**
- Brief intro (4-5 sentences)
- Parameter table for `sns.lineplot()`
- Example 1: Filter to one county, plot simple trend
- Pandas Practice: `groupby('months_from_reform')` for statewide averages
- Example 2: Plot grouped data with `hue='period'`

**Part 2: Bar Charts - Comparing Categories**
- Brief intro + distinction from histograms
- Parameter table for `sns.barplot()`
- Pandas Practice: `groupby(['county', 'period']).mean()`
- Example 1: Plot county comparisons
- Example 2: Add `hue` for pre/post comparison
- Pandas Practice: `.pivot()` to calculate change, sort with `order=`

**Part 3: Histograms - Understanding Distributions**
- Brief intro (emphasize continuous data)
- Explicit contrast: "Bar charts compare categories; histograms show distributions"
- Parameter table for `sns.histplot()`
- Example 1: Basic distribution, explain `bins`
- Pandas Practice: Create period column with `.apply(lambda x: ...)`
- Example 2: Compare distributions with `hue='period'`

**Part 4: Scatter Plots - Exploring Relationships**
- Brief intro
- Parameter table for `sns.scatterplot()`
- Example 1: Basic scatter plot
- Pandas Practice: Create county size categories (groupby + merge)
- Example 2: Scatter with `hue` for groups
- Parameter table for `sns.regplot()`
- Example 3: Add trend line

### Supporting Sections

**Quick Reference**
- Decision table: "Which plot type when?"
- Common parameter reference

**Exercises**
- All 7 exercises maintained
- Instructions made concise (1-3 sentences each)

**Troubleshooting**
- 3-5 most common errors only
- Brief fix descriptions

## Implementation Notes

### Parameter Tables Format

Example structure:
```markdown
| Parameter | What It Does |
|-----------|--------------|
| `data` | Your DataFrame |
| `x` | Column name for x-axis |
| `y` | Column name for y-axis |
| `hue` | Column to split data into colored groups |
| `errorbar` | Set to `None` to turn off confidence intervals |
```

### Text Reduction Strategy

**Remove from original:**
- Verbose "Understanding What You're Seeing" sections
- Repetitive explanations of concepts already covered
- Long "anatomy of a function" walkthroughs
- Excessive policy interpretation

**Keep from original:**
- Core dataset (Maryland pretrial decisions)
- Policy question framework
- Exercise structure
- Key learning concepts

**Add to new version:**
- Explicit pandas practice sections
- Clear parameter tables for every plot type
- Progressive building approach (simple → complex)

## Success Criteria

Students should be able to:
1. Choose the right plot type for their question
2. Understand what each parameter does by referencing tables
3. Prepare data with pandas before visualizing
4. Create basic visualizations without extensive prose guidance
5. Build from simple examples to complex multi-layered plots

The notebook should feel:
- Scannable (easy to find what you need)
- Reference-friendly (come back later to check parameters)
- Practice-oriented (learn by doing, not reading)
- Streamlined (no unnecessary explanation)
