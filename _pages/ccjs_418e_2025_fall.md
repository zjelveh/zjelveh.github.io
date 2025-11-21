---
toc: true
layout: splash
author_profile: false
title: "CCJS 418E: Coding for Criminology (Fall 2025)"
collection: teaching
permalink: /teaching/ccjs_418e_2025_fall
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


# CCJS 418E: Coding for Criminology (Fall 2025)
<div class="compact-info" markdown="1">
**Location:** [SQH 1117](https://25live.collegenet.com/pro/umd#!/home/location/2377/details)

**Time:** Tuesday (Online) / Thursdays (SQH) 3.30 to 4.45 p.m. 

**Instructor:** Zubin Jelveh (zjelveh@umd.edu)

**Office:** 2220F LeFrak

**Office Hours:** [Tue 12:30 to 1:30pm](https://umd.instructure.com/courses/1389501/external_tools/44833)

</div>

## Course Description
This course introduces criminology students to data analysis using Python programming and artificial intelligence tools. Criminal justice increasingly relies on data for major decisions—from setting bail to deploying patrols. This course teaches you to analyze that data using modern tools while understanding what's happening behind the scenes.

We begin with computational thinking, which is essentially a structured way to approach complex problems. You'll learn to break big questions into smaller pieces and identify patterns in data. These mental tools matter whether you're investigating crime trends or evaluating whether a new policy actually works. They're useful on their own but become essential once we start programming.

After computational thinking, we move to Python programming. Python has become the standard language for data analysis in many fields. You'll learn the fundamentals through real examples from criminal justice—instead of printing "Hello World," you'll be calculating crime rates. Instead of abstract math problems, you'll analyze actual arrest data. Most of the course focuses on pandas, Python's data manipulation library, covering data cleaning, filtering, aggregation, and data visualization.

We embrace AI tools like ChatGPT and Claude from day one because they're becoming standard in programming work. These tools excel at both writing and explaining code. However, using these tools without understanding what they produce is like using Google Translate without knowing if the translation makes sense. The assessments in this class ensure you develop real understanding alongside AI assistance.

You'll complete three problem sets throughout the semester plus a final project and presentation. You're encouraged to use AI tools to help complete these assignments. However, grading happens through one-on-one code reviews where you'll walk me through your solution and explain what your code does. During these 5-minute conversations, you should be prepared to answer questions about how your code works, what would happen if we changed certain parts, and interpret your results. These collaborative discussions focus on making sure you understand the tools you are using.


## Course Objectives
After completing this course, students will be able to:
1. Write and modify Python code to load, clean, and analyze criminal justice datasets
2. Use pandas to calculate statistics, identify patterns, and answer specific research questions about crime data
3. Create meaningful visualizations that communicate findings from criminological data
4. Collaborate effectively with AI tools while understanding what the generated code actually does
5. Explain their code and analytical choices in plain English during code review discussions
6. Adapt existing code to answer new questions when research needs change

## Prerequisites
No prior programming experience is required. This course is designed for students with no coding background who want to learn how to use data analysis and AI tools in criminology.

## Technical Requirements
Students will need:
- A laptop 
- Access to AI tools (free tiers of ChatGPT, Claude, or similar - we'll discuss options in class)
- No software purchases required - we'll use free, open-source tools



## Assessment
<details>
<summary class="section-heading">Problem Sets (60% total - 20% each)</summary>
You will complete three problem sets throughout the semester that build on each other:
<ul>
    <li><strong>Problem Set 1 (9/28)</strong> </li>
    <li><strong>Problem Set 2 (10/19)</strong> </li>
    <li><strong>Problem Set 3 (11/23)</strong> </li>
</ul>
<strong>How Problem Sets Work:</strong>
<ul>
<li>You submit working code on the Sunday that it is due (use any resources, including AI tools)</li>
<li>The next Tuesday, you'll have a 5 minute code review session with me during class</li>
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
Due November 2nd, you'll submit a 2-3 page proposal for your final project. The project will require you to find a dataset set to analyze, an overall question you want to explore, and demonstration of computational thinking in how you will explore this question. Further details on the proposal to come. 
</details>
<details>
<summary class="section-heading">Final Project (30%)</summary>
Presentations will be held in the last week of class and projects will be due 12/17. Details to come.
</details>

## Weekly Schedule

[**Links to Lecture Videos**](https://umd.instructure.com/courses/1389501/pages/video-links)

### Week 1: Introduction to Computational Thinking (9/4)
- Slides: [Introduction](/files/cfc/lecture_1.pptx)

Resources: 
- [BBC Bitesize: Computational Thinking](https://www.bbc.co.uk/bitesize/topics/z7tp34j)
- [Video: Making Cocount Stew](https://www.youtube.com/watch?v=dHWmnayy8MY)
- [Canaries in the Coal Mine? Six Facts about the Recent Employment Effects of Artificial Intelligence](https://digitaleconomy.stanford.edu/publications/canaries-in-the-coal-mine/)

---

### Week 2: Introduction to Python, AI Tools and Prompt Engineering (9/9, 9/11)
- Jupyter Notebook: [Intro to Jupyter and Python](https://github.com/zjelveh/zjelveh.github.io/blob/master/files/cfc/1_intro_to_jupyter_and_python.ipynb), [Solutions](https://github.com/zjelveh/zjelveh.github.io/blob/master/files/cfc/1_intro_to_jupyter_and_python_solutions.ipynb)

- Slides: [Intro to Jupyter and Python](/files/cfc/Intro_to_Python_and_Jupyter.pptx)

Resources:
- [Resources for Learning Python](https://umd.instructure.com/courses/1389501/pages/resources-for-learning-python)

---

### Week 3: Python Basics I (9/16, 9/18)
- Jupyter Notebook: [Loops](https://github.com/zjelveh/zjelveh.github.io/blob/master/files/cfc/2_loops.ipynb), [Solutions](https://github.com/zjelveh/zjelveh.github.io/blob/master/files/cfc/2_loops_solutions.ipynb)
- Jupyter Notebook: [Functions](https://github.com/zjelveh/zjelveh.github.io/blob/master/files/cfc/3_functions.ipynb), [Solutions](https://github.com/zjelveh/zjelveh.github.io/blob/master/files/cfc/3_functions_solutions.ipynb)

Resources:
- 30-Days-of-Python: [Loops](https://github.com/Asabeneh/30-Days-Of-Python/blob/master/10_Day_Loops/10_loops.md)
- 30-Days-of-Python: [Functions](https://github.com/Asabeneh/30-Days-Of-Python/blob/master/11_Day_Functions/11_functions.md)
- GeeksforGeeks: [Functions](https://www.geeksforgeeks.org/python/python-functions/)

---

### Week 4: Python Basics II (9/23, 9/25)
- Final Project: [Example Datasets and Stories](https://umd.instructure.com/courses/1389501/pages/final-project-example-datasets-and-stories)
- Final Project: [Crime Data Analysis Ideas](https://umd.instructure.com/courses/1389501/pages/final-project-crime-data-analysis-ideas)
- Final Project: [Proposal Guidelines](https://umd.instructure.com/courses/1389501/pages/final-project-proposal-guide)

**Problem Set 1 Due: 9/28 11:59am** (covers Weeks 2-4)
**Code Review: 9/30** (Tuesday class - 5 min sessions)
{: style="color: red"}

---

### Week 5: Introduction to Pandas and Data Manipulation (9/30, 10/2)
- Slides: [Intro to Pandas](/files/cfc/Intro_to_Pandas.pptx) 
- Jupyter Notebook: [Intro to Pandas](https://github.com/zjelveh/zjelveh.github.io/blob/master/files/cfc/4_pandas_intro_lecture.ipynb) | [Solutions](https://github.com/zjelveh/zjelveh.github.io/blob/master/files/cfc/4_pandas_intro_lecture_solutions.ipynb)

Resources:
- [Resources for Learning Pandas](https://umd.instructure.com/courses/1389501/pages/resources-for-learning-pandas)

---

### Week 6: Pandas - Filtering (10/7, 10/9)
- Jupyter Notebook: [Filtering](https://github.com/zjelveh/zjelveh.github.io/blob/master/files/cfc/5_pandas_filtering_lecture.ipynb) | [Solutions](https://github.com/zjelveh/zjelveh.github.io/blob/master/files/cfc/5_pandas_filtering_lecture_solutions.ipynb)

Resources:
- Kaggle: [Filtering and Sorting](https://www.kaggle.com/code/residentmario/indexing-selecting-assigning-reference)
- Real Python: [Pandas DataFrames](https://realpython.com/pandas-dataframe/)

---

### Week 7: Pandas - Groupby (10/14, 10/16)
- Jupyter Notebook: [Groupby](https://github.com/zjelveh/zjelveh.github.io/blob/master/files/cfc/6_groupby.ipynb) | [Solutions](https://github.com/zjelveh/zjelveh.github.io/blob/master/files/cfc/6_groupby_solutions.ipynb)

Resources:
- Kaggle: [Grouping and Sorting](https://www.kaggle.com/code/residentmario/grouping-and-sorting-reference)
- Real Python: [Pandas GroupBy](https://realpython.com/pandas-groupby/)

---

### Week 8: Data Visualization with Seaborn (10/21, 10/23)
- Jupyter Notebook: [Visualization](https://github.com/zjelveh/zjelveh.github.io/blob/master/files/cfc/7_visualization.ipynb)

Resources:
- Seaborn Tutorial: [Introduction to Seaborn](https://seaborn.pydata.org/tutorial/introduction.html)
- Real Python: [Python Plotting with Seaborn](https://realpython.com/python-seaborn/)
- Storytelling with Data: [Chart Chooser](https://www.storytellingwithdata.com/chart-guide)
- Kaggle: [Data Visualization](https://www.kaggle.com/learn/data-visualization)

---

### Week 9: Pandas - Answering Questions with Data (10/28, 10/30)

**Problem Set 2 Due: 10/26 11:59am** (covers Weeks 5-8)
**Code Review: 10/28** (Tuesday class - 5 min sessions)
{: style="color: red"}

---

### Week 10: Data Visualization (11/4, 11/6)

**Project Proposal Due: 11/2 11:59am** ([Proposal Guidelines](https://umd.instructure.com/courses/1389501/pages/final-project-proposal-guide))
{: style="color: red"}


---

### Week 11: To be determined (11/11, NO CLASS 11/13)


---

### Week 12: Final Project Example & Work Session (11/18, 11/20)
- PowerPoint: [Yankees Noise Analysis Example](/files/cfc/Yankees_Noise_Analysis_Presentation.pptx)
- Jupyter Notebook: [Complete Analysis Demo](https://github.com/zjelveh/zjelveh.github.io/blob/master/files/cfc/class_demo_notebook_complete.ipynb)

Complete final project example demonstrating:
- Structuring analysis with multiple comparisons
- Translating Jupyter notebook results into presentation slides
- Using only functions covered in class

**Problem Set 3 Due: 11/23 11:59am** (covers Weeks 8-12)
**Code Review: 11/25** (Tuesday class - 5 min sessions)
{: style="color: red"}

---

### Week 13: To be determined (11/25)

---

### Week 14: To be determined (12/2, 12/4)

---

### Week 15: **FINAL PRESENTATIONS** (12/9, 12/11)


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



