# Final Project Presentation Guide
## CCJS 418E - Coding for Criminology

**Template:** [final_project_presentation_template.pptx](/files/ccjs418e_fall2025/final_project_presentation_template.pptx)

---

## Overview

Your final project has two parts:

1. **Presentation (12/9 or 12/11):** Present your PLAN (Slides 1-9) for 10 minutes
2. **Final Submission (12/17):** Submit complete slide deck with RESULTS (all slides)

This guide walks you through each slide with examples and tips.

---

## PART 1: Presentation Slides (Present in Class)

These slides focus on your **PLAN** - what you're investigating and how you'll do it. You may not have results yet - that's expected!

---

### Slide 1: Title Slide

**What to include:**
- Your research question as the title
- Your name
- Course name and date

---

### Slide 3: Research Question & Why It Matters

**Time:** ~2 minutes

**What to cover:**
1. State your research question clearly
2. Explain why anyone should care
3. Connect to a real-world problem or policy decision

**Example:**
> **Main Research Question:**
>   Do noise complaints increase on days when the Yankees play home games?
>
> **Why This Question Matters:**
>   - Helps NYPD allocate resources
>   - Informs stadium community relations
>   - Shows how major events affect neighborhoods

---

### Slide 4: My Dataset

**Time:** ~1 minute

**What to cover:**
- Data source (be specific!)
- Time period
- Dataset size

**Example:**
> **Data Source:**
>   NYC 311 Service Requests (NYC Open Data)
>
> **Time Period:**
>   January 1, 2023 - December 31, 2023
>
> **Dataset Size:**
>   265,638 noise complaints

---

### Slide 5: My Dataset: Key Variables

**Time:** ~1 minute

**What to cover:**
- Which columns you're using (use exact names!)
- Any data cleaning you did

**Example:**
> **Key Variables I'm Using:**
>   - `created_date` - When complaint was filed
>   - `borough` - BRONX, BROOKLYN, etc.
>   - `complaint_type` - Type of noise
>
> **Data Cleaning:**
>   Filtered to noise complaints only

---

### Slide 6: My Analysis Strategy

**Time:** ~2 minutes

**THIS SLIDE TELLS THE STORY.** Write this as a narrative (no bullets) explaining how each comparison builds your case.

**Example:**
> First, I'll compare game days to non-game days across all of NYC to establish whether a basic pattern exists. If there's no difference at all, we can stop here.
>
> Then, I'll look at the percent increase by day of week. This helps rule out "it's just the weekend" as an alternative explanation, since games happen on different days.
>
> Finally, I'll compare the change in the Bronx to the change in Brooklyn using diff-in-diff. This rules out citywide trends and shows the localized stadium effect.

**Key insight:** Each comparison should build on the previous one, ruling out alternative explanations.

---

### Slides 7, 8, 9: Comparison Deep Dives

**Time:** ~1 minute each

These slides explain the **mechanics** of each comparison.

**What to cover:**
1. What you're calculating (specific metric)
2. How you'll calculate it (pandas operations)
3. Visualization (chart type and axes)

**Example (Comparison #1):**
> **Comparison #1: Game Days vs Non-Game Days**
>
> **What I'm calculating:**
>   Average noise complaints per day for each group
>
> **How I'll calculate it:**
>   Filter → Count → Divide by number of days
>
> **Visualization:**
>   Bar chart (X: Day Type, Y: Average Complaints)

**Tips:**
- It's okay to show code snippets
- Duplicate slides if you have more than 3 comparisons
- Delete Comparison #3 slide if you only have 2

---

### Slides 10-11: Early Results Preview (OPTIONAL)

Skip these slides if you haven't started analysis yet.

If you have early results:
- **Slide 10:** Your visualization (chart only)
- **Slide 11:** Key numbers, what it means, how it advances your story

---

## PART 2: Results Slides (Due 12/17)

Each result has **TWO slides**:
1. **Visualization slide** - Just the chart
2. **Interpretation slide** - What it means

---

### Slides 13-18: Results (Visualization + Interpretation pairs)

**Visualization Slide:**
> **Result #1: [Finding Title]**
>
> [INSERT YOUR CHART HERE]
>
> (Just the visualization - no text needed)

**Interpretation Slide:**
> **Result #1: What This Tells Us**
>
> **Key Numbers:**
>   - Game days: 900 complaints/day average
>   - Non-game days: 677 complaints/day average
>   - **33% increase** on game days
>
> **What This Means:**
>   Major sporting events do increase noise complaints
>
> **How This Advances My Story:**
>   This establishes the basic pattern exists

**Tips:**
- Export chart from Jupyter: right-click → Save Image As
- Always include specific numbers
- Duplicate these slide pairs for more results
- Delete Result #3 pair if only 2 results

---

### Slide 19: Challenges

**What to cover:**
- Problems you encountered during your analysis
- Be specific about what went wrong

**Example:**
> **Challenge #1:**
>   Matching dates between different data formats
>
> **Challenge #2:**
>   Understanding what diff-in-diff actually measures
>
> **Challenge #3:**
>   Choosing the right comparison group

---

### Slides 20-21: Summary (Two Slides)

**Slide 20 - Summary:**
> **Research Question:**
>   [Restate your research question]
>
> **Main Findings:**
>   - Finding #1: [Key result with specific numbers]
>   - Finding #2: [Key result with specific numbers]
>   - Finding #3: [Key result with specific numbers]

**Slide 21 - Why It Matters:**
> **Policy Implications:**
>   [What should decision-makers know?]
>
> **What I Learned:**
>   [Key takeaway from this analysis]
>
> Thank you! Questions?

---

## Quick Checklist

### Before Your Presentation (12/9 or 12/11):
- [ ] Slides 1-9 are complete
- [ ] Analysis strategy is narrative (no bullets)
- [ ] Analysis strategy explains WHY each comparison matters
- [ ] Each comparison deep dive explains HOW you'll calculate it
- [ ] Practiced (~10 minutes)

### Before Final Submission (12/17):
- [ ] All 21 slides complete
- [ ] Each result has visualization + interpretation slides
- [ ] Interpretation slides include "How This Advances My Story"
- [ ] Specific numbers throughout
- [ ] Challenges show honest reflection

---

## Getting Help

**Office Hours:** Tue 12:30-1:30pm
**Email:** zjelveh@umd.edu

---

**Good luck with your presentations!**
