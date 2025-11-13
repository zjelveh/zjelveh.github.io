# Lecture 9: Merging DataFrames Design Document

**Date:** 2025-11-13
**Target Duration:** 75-90 minutes
**Prerequisites:** Lectures 1-8 (pandas filtering, groupby, datetime operations)

## Overview

This lecture teaches students how to combine information from different sources using pandas merge operations. Students will learn fundamental merge concepts through simple examples, then apply these skills to real NYPD arrest data to answer meaningful criminological questions.

## Design Constraints

### Code Constraints
- **ONLY use concepts already taught:** filtering, groupby, size(), reset_index(), merge, value_counts()
- **NO advanced concepts:** apply, lambda, advanced indexing, pivot tables
- **Clean code:** minimal comments, clear variable names, show dataframes after operations

### Pedagogical Constraints
- **Include visualizations** for each concept (bar charts, simple diagrams)
- **Build from simple to complex:** toy examples → real data pattern 1 → real data pattern 2
- **Standard practice balance:** 50% demonstration, 50% guided practice

## Lecture Structure

### Part 1: Merge Fundamentals (20 minutes)

**Objective:** Understand merge mechanics and types

**Content:**
1. **Motivation (2 min)**
   - Question: "We have arrest data. How do we add context like 'is this a high-crime area'?"
   - Need to combine different datasets

2. **One-to-one merge (5 min)**
   - Example: Program enrollment + income data
   - Each person appears once in each dataset
   - Syntax: `pd.merge(df1, df2, on='person_id')`
   - Visualization: Simple diagram showing row matching

3. **One-to-many merge (8 min)**
   - Example: Program enrollment (1 row per person) + monthly income (multiple rows per person)
   - Show: Program info repeats for each income record
   - Key insight: One record becomes many
   - Visualization: Before/after dataframes side-by-side

4. **Merge types (5 min)**
   - Scenario: Some people only in program data, some only in arrest data
   - Show all 4 types with same data:
     - `how='inner'` - only matches
     - `how='left'` - all from left
     - `how='right'` - all from right
     - `how='outer'` - all from both
   - Visualization: Venn diagram + resulting dataframes
   - NaN handling: Show what happens to non-matches

**Source material:** Lab 10 toy examples (program_df, income_df, arrest_df)

---

### Part 2: NYPD Pattern 1 - Aggregate Then Merge Back (25 minutes)

**Objective:** Add aggregated context to individual records

**Scenario:** "Which arrests happened in high-crime boroughs?"

**Steps:**

1. **Explore data (5 min)**
   - Load NYPD arrest data (pullback dataset from Lecture 8)
   - `df.groupby('ARREST_BORO').size()` - see arrest counts
   - Bar chart: arrests by borough

2. **Create borough statistics (8 min)**
   - Calculate arrests per borough using groupby
   - Reset index to make mergeable
   - Calculate arrest rate (arrests / days in dataset)
   - Show aggregated dataframe (5 rows)

3. **Merge back (8 min)**
   - Left merge: `arrests.merge(boro_stats, on='ARREST_BORO', how='left')`
   - Show before: arrest-level data
   - Show after: arrest-level + borough context columns
   - Key insight: Borough totals repeat for every arrest in that borough
   - Visualization: Highlight repeated values in first 10 rows

4. **Use merged data (4 min)**
   - Create boolean flag: `high_crime_boro` (True if above median)
   - Answer question: "What % of violent arrests in high-crime boroughs?"
   - Use filtering + value_counts on merged dataset

**Code pattern:**
```python
# Step 1: Aggregate
boro_stats = df.groupby('ARREST_BORO').size().reset_index(name='boro_total_arrests')

# Step 2: Merge back
arrests_with_context = arrests.merge(boro_stats, on='ARREST_BORO', how='left')

# Step 3: Use the merged data
arrests_with_context['high_crime_boro'] = arrests_with_context['boro_total_arrests'] > median_value
```

---

### Part 3: NYPD Pattern 2 - Merge Two Aggregations (25 minutes)

**Objective:** Compare statistics from different aggregations

**Scenario:** "Do certain offense types concentrate in specific boroughs?"

**Steps:**

1. **First aggregation - Borough stats (8 min)**
   - Count arrests by borough
   - Calculate percentage of total
   - Reset index, clear column names
   - Dataframe: 5 rows (one per borough)
   - Bar chart: borough distribution

2. **Second aggregation - Offense stats (8 min)**
   - Count arrests by offense description
   - Filter to top 5 most common
   - Calculate percentage of total
   - Reset index, clear column names
   - Dataframe: 5 rows (top offenses)
   - Bar chart: offense distribution

3. **Create cross-tabulation (5 min)**
   - Group by BOTH: `df.groupby(['ARREST_BORO', 'OFNS_DESC']).size()`
   - Reset index to create mergeable format
   - This is the "bridge" connecting the two aggregations
   - Show dataframe structure: multiple rows per borough

4. **Merge aggregations (4 min)**
   - Merge cross-tab with boro_stats on 'ARREST_BORO'
   - Merge result with offense_stats on 'OFNS_DESC'
   - Final dataframe has: borough info + offense info + counts
   - Answer: "Which combinations over-represented?"

**Code pattern:**
```python
# Two separate aggregations
boro_stats = df.groupby('ARREST_BORO').size().reset_index(name='boro_total')
offense_stats = df.groupby('OFNS_DESC').size().reset_index(name='offense_total')

# Cross-tabulation
cross_tab = df.groupby(['ARREST_BORO', 'OFNS_DESC']).size().reset_index(name='count')

# Merge both
merged_stats = cross_tab.merge(boro_stats, on='ARREST_BORO')
merged_stats = merged_stats.merge(offense_stats, on='OFNS_DESC')
```

---

### Part 4: Practice Exercises (15 minutes)

**Exercise 1: Pattern 1 practice**
- Calculate daily arrest rates by borough during pullback period
- Merge back to identify arrests in boroughs that saw biggest drops
- Use filtering + merged data to answer targeted question

**Exercise 2: Pattern 2 practice**
- Create day-of-week statistics
- Create offense-type statistics
- Merge to identify offense-day patterns

**Exercise 3: Applied question**
- Identify arrests for "high-frequency" offenses
- Compare characteristics of high vs low frequency offense arrests
- Requires: filtering on merged data

---

## Visualizations Required

1. **Merge concept diagrams:**
   - Row matching visualization (how merge finds matches)
   - Venn diagrams for merge types

2. **Data visualizations:**
   - Bar chart: arrests by borough
   - Bar chart: arrests by offense type
   - Before/after dataframe comparisons

3. **Pattern visualizations:**
   - Side-by-side: original data vs merged data
   - Highlighting: show how values repeat in merge

## Key Teaching Points

### What Makes a Good Merge
1. **Identify the matching column(s)** - What connects the datasets?
2. **Check units of analysis** - Are they the same or different?
3. **Choose merge type** - Do you want all records or only matches?
4. **Verify results** - Does row count make sense?

### Common Patterns
- **Aggregate-merge-back:** Add context to individual records
- **Merge-two-aggregations:** Compare summary statistics

### Student Misconceptions to Address
- "Merge adds columns, not rows" (not always - depends on unit of analysis)
- "Inner merge is always safest" (no - depends on question)
- NaN values after merge mean "error" (no - they mean "no match")

## Implementation Notes

### Data Requirements
- NYPD arrest data from Lecture 8 (already familiar to students)
- Keep same dataset throughout for consistency
- Filter to manageable timeframe if needed (e.g., 2014-2015)

### Code Style Guidelines
- Variable names: descriptive, not abbreviated (`boro_stats` not `bs`)
- Show dataframe after each operation
- One concept per cell when demonstrating
- Comments only for "why" not "what"

### Assessment Preparation
- Code review questions: "Walk me through this merge"
- Modification questions: "How would you add offense stats?"
- Interpretation questions: "What does this NaN mean?"

## Success Criteria

Students should be able to:
1. Choose appropriate merge type for a given scenario
2. Create aggregated statistics using groupby + reset_index
3. Merge aggregations back to original data
4. Merge two separate aggregations together
5. Interpret merged dataframes (including NaN values)
6. Use merged data to answer comparative questions

## Deviations from Source Material

**From Lab 10:**
- ✅ Keep: toy examples, merge type comparisons
- ✅ Keep: one-to-many example with monthly data
- ❌ Skip: Detailed sorting explanation (already taught)
- ❌ Skip: Maryland court data (use NYPD instead)

**From Lab 11:**
- ❌ Skip: Advanced unit of analysis discussion
- ❌ Skip: Pitfall examples (too complex for this level)
- ❌ Skip: Multiple charge aggregations (save for advanced topics)

**New additions:**
- ✅ NYPD-based scenarios throughout
- ✅ Two distinct merge patterns clearly labeled
- ✅ More visualizations at each step
- ✅ Cleaner code with fewer comments

## Next Steps for Implementation

1. Create notebook structure with 4 parts
2. Build toy example datasets (copy from Lab 10, adapt)
3. Load and explore NYPD data (reuse from Lecture 8)
4. Implement Pattern 1 with step-by-step code
5. Implement Pattern 2 with step-by-step code
6. Create practice exercises with starter code
7. Generate all required visualizations
8. Test all code cells execute in order
9. Create solutions notebook
