---
toc: true
layout: splash
author_profile: false
title: "CCJS 418E: Coding for Criminology (Fall 2026)"
collection: teaching
permalink: /teaching/ccjs_418e_2026_fall
classes: wide
---

<style>
h3 + p + ul,  /* Targets lists after headings and paragraphs */
h3 + p + ol {
  font-size: 0.9em;
}

/* If you want the "Required Reading:" and "Optional Reading:" text to be smaller too */
h3 + p {
  font-size: 0.9em;
}


.section-heading {
    font-size: 1.1em;
    font-weight: bold;
    margin-top: 1em;
    margin-bottom: 1em;
}

/* Compact styling for the top info section only */
.compact-info p {
  margin-bottom: 0.3em; /* Very tight spacing */
  line-height: 1.3;
}

.compact-info p:last-child {
  margin-bottom: 1em; /* Normal spacing after the last item */
}
</style>


# CCJS 418E: Coding for Criminology (Fall 2026)
<div class="compact-info" markdown="1">
**Location:** [SQH 1117](https://25live.collegenet.com/pro/umd#!/home/location/2377/details)

**Time:** Tuesday (Online) / Thursdays (SQH) 3.30 to 4.45 p.m. 

**Instructor:** Zubin Jelveh (zjelveh@umd.edu)

**Office:** 2220F LeFrak

**Office Hours:** Fridays 1 to 2pm, by appointment through [ELMS](https://umd.instructure.com/courses/1407296)

</div>

## Course Description
This course teaches criminology students to answer questions about crime and criminal justice using data. Criminal justice increasingly relies on data for major decisions—from setting bail to deploying patrols—and the questions that matter are usually easy to ask and hard to answer. Did arrests actually fall after this policy changed? Are some neighborhoods policed differently than others? By the end of the semester you'll be able to take a question like that, work through it with real data, and arrive at an answer you can explain and defend.

We begin with computational thinking, which is essentially a structured way to approach complex problems. A large part of it is decomposition: breaking a question into steps small enough that a computer can carry them out. "Did crime go up?" can't be answered until you've decided what counts as crime, over what stretch of time, and measured how. "High-crime neighborhood" can't be either, until you've decided what counts as high.

Being precise isn't the same as being right. Once a question is exact, you still have to decide what to compare against—last year, the rest of the city, or the same months before a policy took effect. Different comparisons can point in different directions, and this is a judgment the code will not make for you. We start on it in the first weeks of the semester and keep coming back to it.

Once the steps are clear, you need something to carry them out on more data than you could work through by hand, and something that lets you redo the whole thing when the question changes. That's where Python comes in. Python has become the standard language for data analysis in many fields. You'll learn the fundamentals through real examples from criminal justice—instead of printing "Hello World," you'll be calculating crime rates. Instead of abstract math problems, you'll analyze actual arrest data. Most of the course focuses on pandas, Python's data manipulation library, covering data cleaning, filtering, aggregation, and data visualization. Each new piece of pandas arrives when we need it to answer something we couldn't answer the week before.

We embrace AI tools like ChatGPT and Claude from day one because they're becoming standard in programming work. They can help at every stage—from sharpening a question and suggesting comparisons to writing and explaining code. But a fluent answer is not evidence that the analysis is sound. You remain responsible for deciding what you want to know, what should be compared, what the data actually measures, and what the result allows you to say. The assessments in this class are designed to develop that judgment.

You'll complete three problem sets throughout the semester plus a final project and presentation. You're encouraged to use AI tools to help complete these assignments. However, grading happens through one-on-one code reviews where you'll walk me through your solution and explain what your code does. During these conversations, you should be prepared to answer questions about how your code works, what would happen if we changed certain parts, and interpret your results. These collaborative discussions focus on making sure you understand the tools you are using.


## Course Objectives
After completing this course, students will be able to:
1. Turn a broad question about crime or criminal justice into one precise enough to answer with data
2. Write and modify Python code to load, clean, and analyze criminal justice datasets, using pandas to filter, group, aggregate, and merge
3. Create meaningful visualizations that communicate findings from criminological data
4. Work effectively with AI tools while understanding what the generated code actually does
5. Explain their code and analytical choices in plain English during code review discussions, and adapt that code when the question changes

## Prerequisites
No prior programming experience is required. This course is designed for students with no coding background who want to learn how to use data analysis and AI tools in criminology.

## Technical Requirements
Students will need:
- A laptop 
- Access to an AI assistant (free and university-provided options will be discussed in class)
- No software purchases required - we'll use free, open-source tools

## AI Tools and Resources
UMD provides and supports several AI tools for students. See [AI Resources at UMD: Available Services](https://ai-resources.umd.edu/resources/services) for current options, access information, and data privacy guidance.


## Assessment
<details>
<summary class="section-heading">Problem Sets (60% total - 20% each)</summary>
You will complete three problem sets throughout the semester that build on each other:
<ul>
    <li><strong>Problem Set 1 (9/27)</strong> </li>
    <li><strong>Problem Set 2 (10/25)</strong> </li>
    <li><strong>Problem Set 3 (11/22)</strong> </li>
</ul>
<strong>How Problem Sets Work:</strong>
<ul>
<li>You submit working code on the Sunday that it is due (use any resources, including AI tools)</li>
<li>The next Tuesday, you'll have a one-on-one code review session with me</li>
<li>During the review, you'll walk me through your code and answer questions about:
  <ul>
    <li>What specific lines of code do</li>
    <li>What would happen if we changed certain parts</li>
  </ul>
</li>
<li>Grading is based primarily on your explanation and understanding during the review, less on whether the code works</li>
</ul>
</details>
<details>
<summary class="section-heading">Project Proposal (10%)</summary>
Due November 1st, you'll submit a 2-3 page proposal for your final project. The project will require you to find a dataset set to analyze, an overall question you want to explore, and demonstration of computational thinking in how you will explore this question. Further details on the proposal to come. 
</details>
<details>
<summary class="section-heading">Final Project (30%)</summary>
Presentations will be held in the last week of class and projects will be due 12/16. Details to come.
</details>

## Weekly Schedule

<span style="color: #999">**Links to Lecture Videos** (coming soon)</span>
{% comment %}
Restore when the Canvas page exists:
[**Links to Lecture Videos**](https://umd.instructure.com/courses/1407296/pages/video-links)
{% endcomment %}

### Week 1: Questions, Comparisons, and Code (9/3)
- Slides: [Introduction](/files/ccjs418e_fall2026/lecture_1.pptx)

Resources: 
- [BBC Bitesize: Computational Thinking](https://www.bbc.co.uk/bitesize/topics/z7tp34j)
- [Video: Making Cocount Stew](https://www.youtube.com/watch?v=dHWmnayy8MY)
- [Canaries in the Coal Mine? Six Facts about the Recent Employment Effects of Artificial Intelligence](https://digitaleconomy.stanford.edu/publications/canaries-in-the-coal-mine/)

---

### Week 2: Getting Started - Python and Colab (9/8, 9/10)
- Notebook: [Intro to Colab and Python](https://github.com/zjelveh/zjelveh.github.io/blob/master/files/ccjs418e_fall2026/1_intro_to_colab_and_python.ipynb)

- Slides: [Intro to Jupyter and Python](/files/ccjs418e_fall2026/Intro_to_Python_and_Jupyter.pptx)

Resources:
- [Resources for Learning Python](https://umd.instructure.com/courses/1407296/pages/resources-for-learning-python)

---

### Week 3: Doing It for Every Case - Loops and Functions (9/15, 9/17)
- Notebook: [Loops](https://github.com/zjelveh/zjelveh.github.io/blob/master/files/ccjs418e_fall2026/2_loops.ipynb)
- Notebook: [Functions](https://github.com/zjelveh/zjelveh.github.io/blob/master/files/ccjs418e_fall2026/3_functions.ipynb)

Resources:
- 30-Days-of-Python: [Loops](https://github.com/Asabeneh/30-Days-Of-Python/blob/master/10_Day_Loops/10_loops.md)
- 30-Days-of-Python: [Functions](https://github.com/Asabeneh/30-Days-Of-Python/blob/master/11_Day_Functions/11_functions.md)
- GeeksforGeeks: [Functions](https://www.geeksforgeeks.org/python/python-functions/)

---

### Week 4: From Question to Steps (9/22, 9/24)
- Final Project: [Example Datasets and Stories](https://umd.instructure.com/courses/1407296/pages/final-project-example-datasets-and-stories)
- Final Project: [Crime Data Analysis Ideas](https://umd.instructure.com/courses/1407296/pages/final-project-crime-data-analysis-ideas)
- Final Project: [Proposal Guidelines](https://umd.instructure.com/courses/1407296/pages/final-project-proposal-guide)

**Problem Set 1 Due: 9/27 11:59am** (covers Weeks 2-4)
**Code Review: 9/29** (Tuesday session)
{: style="color: red"}

---

### Week 5: Meeting Your Data (9/29, 10/1)
- Slides: [Intro to Pandas](/files/ccjs418e_fall2026/Intro_to_Pandas.pptx) 
- Notebook: [Intro to Pandas](https://github.com/zjelveh/zjelveh.github.io/blob/master/files/ccjs418e_fall2026/4_pandas_intro_lecture.ipynb)

Resources:
- [Resources for Learning Pandas](https://umd.instructure.com/courses/1407296/pages/resources-for-learning-pandas)

---

### Week 6: Building the Two Groups - Filtering (10/6, 10/8)
- Notebook: [Filtering](https://github.com/zjelveh/zjelveh.github.io/blob/master/files/ccjs418e_fall2026/5_pandas_filtering_lecture.ipynb)

Resources:
- Kaggle: [Filtering and Sorting](https://www.kaggle.com/code/residentmario/indexing-selecting-assigning-reference)
- Real Python: [Pandas DataFrames](https://realpython.com/pandas-dataframe/)

---

### Week 7: Comparing Many Groups at Once - Groupby (NO CLASS 10/13 - Fall Break, 10/15)
- Notebook: [Groupby](https://github.com/zjelveh/zjelveh.github.io/blob/master/files/ccjs418e_fall2026/6_groupby.ipynb)

Resources:
- Kaggle: [Grouping and Sorting](https://www.kaggle.com/code/residentmario/grouping-and-sorting-reference)
- Real Python: [Pandas GroupBy](https://realpython.com/pandas-groupby/)

---

### Week 8: Showing a Comparison (10/20, 10/22)
- Notebook: [Visualization](https://github.com/zjelveh/zjelveh.github.io/blob/master/files/ccjs418e_fall2026/7_visualization.ipynb)

Resources:
- Seaborn Tutorial: [Introduction to Seaborn](https://seaborn.pydata.org/tutorial/introduction.html)
- Real Python: [Python Plotting with Seaborn](https://realpython.com/python-seaborn/)
- Storytelling with Data: [Chart Chooser](https://www.storytellingwithdata.com/chart-guide)
- Kaggle: [Data Visualization](https://www.kaggle.com/learn/data-visualization)

---

### Week 9: Compared to What? Choosing a Baseline (10/27, 10/29)

**Problem Set 2 Due: 10/25 11:59am**
**Code Review: 10/27**
{: style="color: red"}

---

### Week 10: Comparing to Yourself - Dates and Time (11/3, 11/5)
- Notebook: [Dates and Time](https://github.com/zjelveh/zjelveh.github.io/blob/master/files/ccjs418e_fall2026/8_datetime_operations.ipynb)

**Project Proposal Due: 11/1 11:59am** ([Proposal Guidelines](https://umd.instructure.com/courses/1407296/pages/final-project-proposal-guide))
{: style="color: red"}

---

### Week 11: Bringing Two Tables Together - Merging (11/10, 11/12)

- Notebook: [Merging](https://github.com/zjelveh/zjelveh.github.io/blob/master/files/ccjs418e_fall2026/9_merging.ipynb)

---

### Week 12: From Comparison to Claim (11/17, 11/19)
- PowerPoint: [Yankees Noise Analysis Example](/files/ccjs418e_fall2026/Yankees_Noise_Analysis_Presentation.pptx)
- Notebook: [Complete Analysis Demo](https://github.com/zjelveh/zjelveh.github.io/blob/master/files/ccjs418e_fall2026/class_demo_notebook_complete.ipynb)

**Problem Set 3 Due: 11/22 11:59am**
**Code Review: 11/24**
{: style="color: red"}

---

### Week 13: Code Review (11/24 - NO CLASS 11/26, Thanksgiving Recess)

---

### Week 14: When the Comparison Breaks (12/1, 12/3)
- Slides: [Anatomy of a Comparison](/files/ccjs418e_fall2026/10_causal_inference.pptx)
- Slides: [What If? From Code to Causality to LLMs](/files/ccjs418e_fall2026/11_what_if_lecture.pptx)
- Notebook: [Causal Inference](https://colab.research.google.com/github/zjelveh/zjelveh.github.io/blob/master/files/ccjs418e_fall2026/10_causal_inference.ipynb)

---

### Week 15: **FINAL PRESENTATIONS** (12/8, 12/10)

**Final Project Presentations Due: 12/7 11:59pm**
**Final Project Due: 12/16 11:59pm**
{: style="color: red"}


---

## Course Policies

### Contacting the Instructor
Students should contact me via email at zjelveh@umd.edu. Please begin your subject line with **"CCJS418E"** or **"Coding for Criminology"** to ensure your email receives prompt attention. I typically respond to emails within 24-48 hours during weekdays.

### Course-Related Policies
Policies relevant to Undergraduate Courses are found [here](https://ugst.umd.edu/courserelatedpolicies.html). Topics that are addressed in these various policies include academic integrity, student and instructor conduct, accessibility and accommodations, attendance and excused absences, grades and appeals, copyright and intellectual property.

### Academic Integrity
The University of Maryland, College Park has a nationally recognized Code of Academic Integrity, administered by the Student Honor Council. This Code sets standards for academic integrity at Maryland for all undergraduate and graduate students. As a student you are responsible for upholding these standards for this course. It is very important for you to be aware of the consequences of cheating, fabrication, facilitation, and plagiarism. For more information on the Code of Academic Integrity or the Student Honor Council, please visit [http://www.studentconduct.umd.edu](http://www.studentconduct.umd.edu).


### Accessibility and Disability Support
The University of Maryland is committed to creating and maintaining a welcoming and inclusive educational, working, and living environment for people of all abilities. The University of Maryland is also committed to the principle that no qualified individual with a disability shall, on the basis of disability, be excluded from participation in or be denied the benefits of the services, programs, or activities of the University, or be subjected to discrimination.

Students with disabilities who require accommodations for this course should contact the Accessibility and Disability Service (ADS) at 301-314-7682 or adsfrontdesk@umd.edu. Please inform me of any accommodations you need as soon as possible, preferably within the first two weeks of the semester.

More information about ADS and accommodations can be found at [https://www.counseling.umd.edu/ads/](https://www.counseling.umd.edu/ads/)


