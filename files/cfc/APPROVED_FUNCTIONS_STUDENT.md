# CCJS 418E: Python & Pandas Quick Reference Guide

**What is this?** A complete reference of all the Python and Pandas functions you've learned in this course. Use this when:
- Working on problem sets and need to remember syntax
- Preparing for code review sessions
- Writing your final project
- Reviewing what you've learned

**How to use this guide:**
- Use Ctrl+F (or Cmd+F on Mac) to search for specific functions
- Each section corresponds to topics from the lectures
- Examples show how to use each function

**Last Updated**: 2025-01-13

---

## 1. Python Fundamentals

### Built-in Functions
- `print()` - Display output to console
- `type()` - Check data type of a value
- `len()` - Get length of list or string
- `sum()` - Add up all numbers in a list
- `min()` - Find smallest value in a list
- `max()` - Find largest value in a list
- `range()` - Generate sequence of numbers for loops
- `enumerate()` - Get both index and value when looping
- `round()` - Round numbers to specified decimal places
- `int()` - Convert to integer
- `float()` - Convert to float
- `str()` - Convert to string
- `sorted()` - Return sorted version of a list

### Operators
- **Arithmetic**: `+`, `-`, `*`, `/`, `**` (power)
- **Comparison**: `==`, `!=`, `>`, `<`, `>=`, `<=`
- **Logical**: `and`, `or`, `not`
- **Membership**: `in`, `not in`

### String Formatting
- **f-strings**: `f"Text {variable} more text"` - Format strings with variables

---

## 2. Lists

### List Methods
- `.append(item)` - Add item to end of list
- `.count(item)` - Count occurrences of item
- `.remove(item)` - Remove first occurrence of item
- `.sort()` - Sort list in place
- `.copy()` - Create a copy of list
- `.index(item)` - Find position of item in list

---

## 3. Strings

### String Methods
- `.lower()` - Convert to lowercase
- `.upper()` - Convert to uppercase
- `.replace(old, new)` - Replace substring
- `.strip()` - Remove leading/trailing whitespace

---

## 4. Control Flow

### Conditionals
- `if` / `elif` / `else` - Conditional branching

### Loops
- `for item in list:` - Iterate through list
- `while condition:` - Loop until condition is False

### Common Loop Patterns
- **Filtering**: Use `if` inside loop to select items
- **Counting**: Initialize counter before loop, increment inside
- **Accumulating**: Initialize total before loop, add to it inside
- **Collecting**: Initialize empty list, `.append()` items inside loop

---

## 5. Functions

### Defining Functions
- `def function_name(parameters):` - Define a function
- `return value` - Return value from function

### Docstrings
- Triple-quoted strings after `def` line for documentation

---

## 6. Pandas: Data Loading & Inspection

### Loading Data
- `pd.read_csv(filepath_or_buffer='path')` - Load CSV file into DataFrame

### Inspection
- `df.head(n=5)` - View first n rows (default 5)
- `df.tail(n=5)` - View last n rows
- `df.info()` - Show column types and non-null counts
- `df.shape` - Get (rows, columns) as tuple
- `df.columns` - Get column names
- `df.describe()` - Statistical summary of numeric columns

---

## 7. Pandas: Selection

### Column Selection
- `df['column']` - Select single column (returns Series)
- `df[['col1', 'col2']]` - Select multiple columns (returns DataFrame)

### Row Selection by Position
- `df.iloc[0]` - Select first row by position
- `df.iloc[1]` - Select second row by position
- `df.iloc[-1]` - Select last row by position
- `df.iloc[0:3]` - Select first 3 rows by position (slicing)

### Conditional Assignment
- `df.loc[condition, 'column'] = value` - Assign values to filtered rows

**Example**:
```python
# Create column with default value
df['period'] = 'Before'
# Update specific rows based on condition
df.loc[df['date'] >= cutoff_date, 'period'] = 'After'
```

---

## 8. Pandas: Column/Series Methods

### Statistical Methods
- `.mean()` - Calculate average
- `.max()` - Maximum value
- `.min()` - Minimum value
- `.sum()` - Total sum
- `.count()` - Count non-null values

### Unique Values
- `.nunique()` - Count unique values
- `.unique()` - Get array of unique values
- `.value_counts()` - Count frequency of each value

### Membership
- `.isin(list)` - Check if values are in a list

---

## 9. Pandas: Sorting

### Sorting Methods
- `df.sort_values(by='column')` - Sort by column (ascending by default)
- `df.sort_values(by='column', ascending=False)` - Sort descending
- `df.sort_values(by=['col1', 'col2'])` - Sort by multiple columns
- `df.nlargest(n, 'column')` - Get top n rows by column value
- `df.nsmallest(n, 'column')` - Get bottom n rows by column value

---

## 10. Pandas: Filtering (Boolean Indexing)

### Basic Filtering
- `df[df['col'] == value]` - Filter rows where column equals value
- `df[df['col'] != value]` - Filter rows where column not equal to value
- `df[df['col'] > value]` - Greater than
- `df[df['col'] < value]` - Less than
- `df[df['col'] >= value]` - Greater than or equal
- `df[df['col'] <= value]` - Less than or equal

### Combining Conditions
- `df[(condition1) & (condition2)]` - AND (both must be True)
- `df[(condition1) | (condition2)]` - OR (at least one must be True)
- `df[~(condition)]` - NOT (flip condition)

**Important**: Always use parentheses around each condition when combining!

### Range Filtering
- `df[df['col'].between(val1, val2)]` - Filter by range (inclusive)

### Multiple Values
- `df[df['col'].isin([val1, val2, val3])]` - Filter where column is in list

---

## 11. Pandas: Creating & Modifying Columns

### Creating New Columns
- `df['new_col'] = calculation` - Create column from calculation
- `df['new_col'] = df['col1'] + df['col2']` - Add columns
- `df['new_col'] = df['col1'] - df['col2']` - Subtract columns
- `df['new_col'] = df['col1'] * df['col2']` - Multiply columns
- `df['new_col'] = df['col1'] / df['col2']` - Divide columns
- `df['new_col'] = (df['col1'] / df['col2']) * 100` - Calculate percentages

### Removing Columns
- `df.drop(columns=['col1', 'col2'])` - Remove columns
- `df.drop(columns=['col'], inplace=True)` - Remove and modify DataFrame in place

---

## 12. Pandas: GroupBy Operations

### Grouping
- `df.groupby('column')` - Group by single column
- `df.groupby(['col1', 'col2'])` - Group by multiple columns

### Aggregation Methods (after groupby)
- `.size()` - Count rows in each group
- `.mean()` - Average for each group
- `.sum()` - Sum for each group
- `.max()` - Maximum value for each group
- `.min()` - Minimum value for each group
- `.count()` - Count non-null values for each group

### Converting Results
- `.reset_index()` - Convert grouped result back to regular DataFrame

**Example**:
```python
# Count by category
df.groupby('category').size()

# Average by category, convert to DataFrame
df.groupby('category')['value'].mean().reset_index()
```

---

## 13. Pandas: DateTime Operations

### Converting to DateTime
- `pd.to_datetime(column)` - Convert string column to datetime

### Extracting Date Components
- `.dt.year` - Extract year
- `.dt.month` - Extract month (1-12)
- `.dt.day` - Extract day of month
- `.dt.day_name()` - Get day of week name ('Monday', 'Tuesday', etc.)

### Creating Time Periods
- `.dt.to_period('M')` - Convert to monthly period (2014-01, 2014-02, etc.)
- `.dt.to_period('Q')` - Convert to quarterly period (2014Q1, 2014Q2, etc.)
- `.dt.to_period('Y')` - Convert to yearly period
- `.dt.to_timestamp()` - Convert period back to timestamp

### Date Filtering
- `df['date_col'].between(start_date, end_date)` - Filter dates in range

### Time Differences
- `.days` - Get number of days from timedelta (when subtracting datetime objects)

**Example**:
```python
# Convert string to datetime
df['date'] = pd.to_datetime(df['date'])

# Extract year
df['year'] = df['date'].dt.year

# Calculate days between dates
days_diff = (end_date - start_date).days
```

---

## 14. Data Visualization: Seaborn

### Core Parameters (used in all plot types)
- `data=` - DataFrame to use
- `x=` - Column name for x-axis
- `y=` - Column name for y-axis
- `hue=` - Column to split by color/groups
- `alpha=` - Transparency (0=invisible, 1=solid)

### Plot Types
- `sns.lineplot()` - Line plots for trends over time
- `sns.pointplot()` - Point plots with confidence intervals
- `sns.barplot()` - Bar charts for comparing categories
- `sns.histplot()` - Histograms for distributions
- `sns.scatterplot()` - Scatter plots for relationships between variables
- `sns.regplot()` - Scatter plot with regression line

### Plot-Specific Parameters

**For lineplot and pointplot:**
- `marker=` - Point shape ('o', 's', '^', 'D')

**For histplot:**
- `bins=` - Number of histogram bars (typically 20-40)
- `kde=` - Add smooth density curve (True/False)

**For scatterplot:**
- `s=` - Point size (default ~50)

**For barplot:**
- `order=` - Control order of categories on axis

**For regplot:**
- `scatter_kws=` - Dictionary of options for scatter points
- `line_kws=` - Dictionary of options for trend line

---

## 15. Data Visualization: Matplotlib (Optional Customization)

All matplotlib functions are **optional** for styling and customization:

### Figure Setup
- `plt.figure(figsize=(width, height))` - Set canvas size in inches

### Labels and Titles
- `plt.title('Title Text')` - Add title
- `plt.xlabel('Label Text')` - Label x-axis
- `plt.ylabel('Label Text')` - Label y-axis
- `plt.legend()` - Customize legend

### Reference Lines
- `plt.axvline(x=value)` - Add vertical reference line
- `plt.axhline(y=value)` - Add horizontal reference line

### Formatting
- `plt.xticks(rotation=45)` - Rotate x-axis labels
- `plt.tight_layout()` - Adjust spacing to prevent label cutoff

### Display
- `plt.show()` - Display the plot

---

## Quick Reference: Common Tasks

### Load and explore data
```python
import pandas as pd
df = pd.read_csv('file.csv')
df.head()
df.info()
df.shape
```

### Filter and calculate
```python
# Filter
subset = df[df['column'] > 100]

# Calculate statistics
average = df['column'].mean()
total = df['column'].sum()
```

### Group and aggregate
```python
# Count by category
df.groupby('category').size()

# Average by multiple groups
df.groupby(['cat1', 'cat2'])['value'].mean().reset_index()
```

### Create visualization
```python
import seaborn as sns
import matplotlib.pyplot as plt

plt.figure(figsize=(10, 6))
sns.lineplot(data=df, x='year', y='crime_rate', hue='state')
plt.title('Crime Rates Over Time')
plt.show()
```

### Work with dates
```python
# Convert to datetime
df['date'] = pd.to_datetime(df['date'])

# Extract components
df['year'] = df['date'].dt.year
df['month'] = df['date'].dt.month

# Filter by date
recent = df[df['date'] >= pd.to_datetime('2020-01-01')]
```

---

**Remember**: This course is about learning to think computationally and solve problems with data. Don't worry about memorizing every function - focus on understanding the patterns and knowing where to look things up!
