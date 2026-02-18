---
toc: true
layout: splash
author_profile: false
title: "INST 414 / SDSI 414: Data Science Techniques (Spring 2026)"
collection: teaching
permalink: /teaching/inst414_spring2026
classes: wide
---

<style>
h3 + p + ul,
h3 + p + ol {
  font-size: 0.9em;
}

h3 + p {
  font-size: 0.9em;
}

.section-heading {
    font-size: 1.1em;
    font-weight: bold;
    margin-top: 1em;
    margin-bottom: 1em;
}

.compact-info p {
  margin-bottom: 0.3em;
  line-height: 1.3;
}

.compact-info p:last-child {
  margin-bottom: 1em;
}
</style>

# INST 414 / SDSI 414: Data Science Techniques (Spring 2026)
<div class="compact-info" markdown="1">
**Format:** Blended — async video lectures (online) + in-person Friday labs

**Lab Location:** BLD4 3321

**Lab Time:** Fridays 9:00 to 10:30 a.m.

**Instructor:** Zubin Jelveh (zjelveh@umd.edu)

**Office Hours:** Thursday 1:00-2:00pm

</div>

## Course Description
This course provides a strong foundation in key data science techniques. As the amount of data available to public- and private-sector organizations continues to grow, it has become critical to have data scientists who can leverage this data to generate insights and enable data-driven decision-making, while ensuring that these decisions are based on fair and ethical principles.

You will learn foundational data science techniques including basic probability and statistics, supervised machine learning algorithms (such as Naive Bayes, linear and logistic regression, decision trees, and random forests), feature engineering, working with Python libraries, principles of model selection and evaluation (including cross-validation), and considerations around fairness and bias in machine learning applications. We'll also touch on text mining techniques and explore generative AI.

**Course format:** Lecture content is delivered asynchronously through video. Friday sessions are hands-on labs where you'll apply techniques to real datasets with instructor support.

**Note:** This course primarily focuses on foundational supervised learning techniques.

**Note:** Knowledge of Python is assumed.

## Course Objectives
After completing this course, students will be able to:
1. Apply basic probability concepts and relate them to uncertainty in predictions
2. Implement standard machine learning algorithms (linear regression, logistic regression, decision trees, random forest)
3. Select and evaluate models using cross-validation and appropriate performance metrics
4. Engineer features from raw data to improve model performance
5. Identify and address fairness considerations in machine learning applications

## Prerequisites
Minimum grade of C- in MATH115 and STAT100; minimum C- in INST126 or GEOG276; minimum C- in INST201, INST301, or BSOS233; minimum C- in a social science course (AASP101, ANTH210, ECON200, GVPT170, PSYC100, SOCY100, etc.); and minimum C- in BSOS233 or INST314.

## Technical Requirements
- A laptop capable of running Python (bring to Friday labs)
- No software purchases required — we use free, open-source tools
- Access to ELMS for async lecture videos, assignments, and announcements

## Working with Lab Notebooks
Lab notebooks open in Google Colab directly from the links below.

**Important:** When you open a lab notebook, immediately click **File → Save a copy in Drive**. This creates your own version in your Google Drive that you can edit and save.

If you skip this step, your work will not be saved.

**Turn off AI assistance:** Go to **Settings → AI Assistance** and uncheck everything. AI-generated code is not allowed on assignments in this course.

## Assessment
<details>
<summary class="section-heading">Homework Assignments (30%)</summary>
Four homework assignments throughout the semester that build on lecture and lab content. Assignments will be distributed and submitted through ELMS.
</details>

<details>
<summary class="section-heading">Weekly Quizzes (20%)</summary>
10 weekly quizzes covering lecture material. These are administered through ELMS.
</details>

<details>
<summary class="section-heading">Midterm Exam (25%)</summary>
Covers material from Weeks 1-8 (probability through random forests). Scheduled for Week 9 (4/3).
</details>

<details>
<summary class="section-heading">Final Project or Exam (25%)</summary>
Details to come.
</details>

## Weekly Schedule

### Week 1 (1/30): Data Science Background
- Video Lecture: [Slides](/files/inst414_spring2026/lectures/lecture_1.pptx) &#124; [Video](https://umd.instructure.com/courses/1401087/pages/lecture-videos)

---

### Week 2 (2/6): Probability
- Video Lecture: [Slides (Part 1: Probability Basics)](/files/inst414_spring2026/lectures/lecture_2_p1.pptx) &#124; [Slides (Part 2: Joint and Marginal Distributions)](/files/inst414_spring2026/lectures/lecture_2_p2.pptx) &#124; [Video](https://umd.instructure.com/courses/1401087/pages/lecture-videos)
- [Practice Problems](https://github.com/zjelveh/zjelveh.github.io/blob/master/files/inst414_spring2026/lectures/lecture_2_practice_set.md)
- Lab: Introduction to Pandas — [Lab 1 Slides](/files/inst414_spring2026/labs/Lab_1.pptx) &#124; [Lab 1 Notebook](https://colab.research.google.com/github/zjelveh/zjelveh.github.io/blob/master/files/inst414_spring2026/labs/Lab_1.ipynb) &#124; [Notes](https://github.com/zjelveh/zjelveh.github.io/blob/master/files/inst414_spring2026/labs/INST%20414%20%E2%80%94%20Lab%201%20Notes.md)
- Resource: [Resources for Learning Pandas](https://umd.instructure.com/courses/1401087/pages/resources-for-learning-pandas)
- Resource: [Web Resources for Probability](https://umd.instructure.com/courses/1401087/pages/web-resources-for-probability?wrap=1)

---

### Week 3 (2/13): Conditional Probability
- Video Lecture: [Slides (Recap)](/files/inst414_spring2026/lectures/lecture_3a_recap.pptx) &#124; [Slides (Conditional Probability)](/files/inst414_spring2026/lectures/lecture_3b_condprob.pptx) &#124; [Slides (Chain Rule / Practice)](/files/inst414_spring2026/lectures/lecture_3c_practice.pptx) &#124; [Video](https://umd.instructure.com/courses/1401087/pages/lecture-videos)
- [Practice Problems](https://github.com/zjelveh/zjelveh.github.io/blob/master/files/inst414_spring2026/lectures/lecture_3_practice_set.md)
- Lab: [Lab 2 Slides](/files/inst414_spring2026/labs/Lab_2.pptx) &#124; [Lab 2 Notebook](https://colab.research.google.com/github/zjelveh/zjelveh.github.io/blob/master/files/inst414_spring2026/labs/Lab_2.ipynb)

**Problem Set 1 Out**
{: style="color: red"}

---

### Week 4 (2/20): Independence + Bayes Theorem / Making Predictions
- Video Lecture: [Slides (Part 1: Independence)](/files/inst414_spring2026/lectures/lecture_4a_independence.pptx) &#124; [Slides (Part 2: Bayes Theorem)](/files/inst414_spring2026/lectures/lecture_4b_bayes_theorem.pptx) &#124; [Video](https://umd.instructure.com/courses/1401087/pages/lecture-videos)
- [Practice Problems](https://github.com/zjelveh/zjelveh.github.io/blob/master/files/inst414_spring2026/lectures/lecture_4_practice_set.md)
- Resource: [3Blue1Brown: Bayes theorem (YouTube)](https://www.youtube.com/watch?v=HZGCoVF3YvM)
- Lab: [Lab 3 Slides](/files/inst414_spring2026/labs/Lab_3_Groupby.pptx) &#124; [Lab 3 Notebook](https://colab.research.google.com/github/zjelveh/zjelveh.github.io/blob/master/files/inst414_spring2026/labs/Lab_3.ipynb) &#124; [Notes](https://github.com/zjelveh/zjelveh.github.io/blob/master/files/inst414_spring2026/labs/INST%20414%20%E2%80%94%20Lab%203%20Notes.md)

---

### Week 5 (2/27): Performance Metrics / Naive Bayes
- Video Lecture: [Slides](/files/inst414_spring2026/lectures/lecture_5.pptx)
- Lab: [Lab 4 Slides](/files/inst414_spring2026/labs/Lab_4.pptx) &#124; [Lab 4 Notebook](https://colab.research.google.com/github/zjelveh/zjelveh.github.io/blob/master/files/inst414_spring2026/labs/Lab_4.ipynb)

**Problem Set 1 Due**
{: style="color: red"}

---

### Week 6 (3/6): Linear and Logistic Regression
- Video Lecture: [Slides](/files/inst414_spring2026/lectures/lecture_6.pptx)
- Lab: [Lab 5 Slides](/files/inst414_spring2026/labs/Lab_5.pptx) &#124; [Lab 5 Notebook](https://colab.research.google.com/github/zjelveh/zjelveh.github.io/blob/master/files/inst414_spring2026/labs/Lab_5.ipynb)

**Problem Set 2 Out**
{: style="color: red"}

---

### Week 7 (3/13): Overfitting / Decision Trees
- Video Lecture: [Slides](/files/inst414_spring2026/lectures/lecture_7.pptx)
- Lab: [Lab 6 Slides](/files/inst414_spring2026/labs/Lab_6.pptx) &#124; [Lab 6 Notebook](https://colab.research.google.com/github/zjelveh/zjelveh.github.io/blob/master/files/inst414_spring2026/labs/Lab_6.ipynb)

---

### Spring Break (3/20): No Class

---

### Week 8 (3/27): Random Forest / Gradient Boosting
- Video Lecture: [Slides](/files/inst414_spring2026/lectures/lecture_8.pptx)
- Lab: [Lab 7 Slides](/files/inst414_spring2026/labs/Lab_7.pptx) &#124; [Lab 7 Notebook](https://colab.research.google.com/github/zjelveh/zjelveh.github.io/blob/master/files/inst414_spring2026/labs/Lab_7.ipynb)

**Problem Set 2 Due**
{: style="color: red"}

---

### Week 9 (4/3): Midterm (No Lab)

---

### Week 10 (4/10): Fairness
- Video Lecture: [Slides](/files/inst414_spring2026/lectures/lecture_10.pptx)
- Lab: [Lab 8 Slides](/files/inst414_spring2026/labs/lab_8.pptx) &#124; [Lab 8 Notebook](https://colab.research.google.com/github/zjelveh/zjelveh.github.io/blob/master/files/inst414_spring2026/labs/Lab_8.ipynb)

**Problem Set 3 Out**
{: style="color: red"}

---

### Week 11 (4/17): Sources of Bias, Part I
- Video Lecture: [Slides](/files/inst414_spring2026/lectures/lecture_11.pptx)
- Lab: [Lab 9 Slides](/files/inst414_spring2026/labs/Lab_9.pptx) &#124; [Lab 9 Notebook](https://colab.research.google.com/github/zjelveh/zjelveh.github.io/blob/master/files/inst414_spring2026/labs/Lab_9.ipynb)

---

### Week 12 (4/24): Sources of Bias, Part II
- Video Lecture: [Slides](/files/inst414_spring2026/lectures/lecture_12.pptx)

**Problem Set 3 Due / Problem Set 4 Out**
{: style="color: red"}

---

### Week 13 (5/1): Text Mining
- Video Lecture: [Slides](/files/inst414_spring2026/lectures/lecture_13.pptx)

---

### Week 14 (5/8): Text Mining / Generative AI
- Video Lecture: [Slides](/files/inst414_spring2026/lectures/lecture_14.pptx)

**Problem Set 4 Due**
{: style="color: red"}

---

## Course Policies

### Communications
**ELMS** — Official course site for video lectures, materials, assignments, announcements, and grades. Make sure your email and announcement notifications are enabled.

**Email** — Administrative requests, quick clarifications. Please prefix the subject line with **[INST414]**. If you haven't received a reply within 2 days, please email again.

**Office Hours** — Complex technical questions.

### Accessibility and Disability Support
The University of Maryland is committed to creating and maintaining a welcoming and inclusive educational, working, and living environment for people of all abilities. Students with disabilities who require accommodations should contact the Accessibility and Disability Service (ADS) at 301-314-7682 or adsfrontdesk@umd.edu. Please inform me of any accommodations as soon as possible, preferably within the first two weeks of the semester.

More information: [https://www.counseling.umd.edu/ads/](https://www.counseling.umd.edu/ads/)

### LLM Policy
While you are allowed and encouraged to use LLMs (ChatGPT, Copilot, etc.) to help you learn the material — for example, to explain concepts, debug error messages, or explore topics in more depth — do not use them to complete assignments. If it is clear that an LLM has been used on an assignment, you will receive an automatic zero.

### UMD Policies
It is our shared responsibility to know and abide by the University of Maryland's policies that relate to all courses, which include topics like academic integrity, student and instructor conduct, accessibility and accommodations, attendance and excused absences, grades and appeals, and copyright and intellectual property.

Please visit [www.ugst.umd.edu/courserelatedpolicies.html](http://www.ugst.umd.edu/courserelatedpolicies.html) for the full list of campus-wide policies.
