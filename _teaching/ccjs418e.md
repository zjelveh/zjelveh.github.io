---
layout: single-no-sidebar
author_profile: false
title: "Applications of Data Science for Criminology"
collection: teaching
permalink: /teaching/ccjs418e
---

**Note:** This page serves as an overview of *Applications of Data Science for Criminology* a relativley new course in the Department of Criminology and Criminal Justice at the University of Maryland. The purpose of this page is to give students thinking about enrolling in the course a preview of what to expect. Please feel free to reach out to [me directly](mailto:zjelveh@umd.edu) if you have any questions about the content of the course.
{: .notice}

---

Actors in the criminal justice system are often tasked with making consequential decisions that rely on an assessment, or prediction,  of what will happen in the future. Examples of these decisions that hinge (at least in part) on a prediction include:  
 > - **Decision**: A judge releasing or jailing an arrestee. 
 > - **Prediction**: Chance that a defendant will skip future court dates, or be charged with a new crime. 


 > - **Decision**: Police officers patrolling of different parts of their beat. 
 > - **Prediction**: Chance that a particular geographic area will experience relatively higher levels of crime. 


 > - **Decision**: Shelters allocating scarce housing units to victims and survivors of domestic violence. 
 > - **Prediction**: Chance that a survivor is at high risk of re-victimization in the near term. 
 
 
At the same time, we know very little about the quality of  predictions made by humans in these contexts. 
 - Are they accurate?
 - Are they fair? 
 - Do they lead to the intended outcomes? (e.g. Do patrolling decisions lead to lower crime rates, do detention decisions lead to more appearances overall, etc.) 
 - Can they be improved through the use of administrative data and prediction algorithms (a.k.a. data science)? 
 
 But the use of algorithms in these high-stakes contexts is controversial. Central to this controversy is the fear that data commonly used in these algorithms (e.g. arrest, court, and victimization records) contain human bias, and thus that the predictions from these algorithms will reproduce and reinforce those biases. 

Through the lens of [pretrial risk assessments](https://advancingpretrial.org/pretrial-justice/pretrial-justice/)  this course asks and attempts to provide answers to the following questions:
 - What does it mean to make a prediction?
 - How do we know if our predictions are accurate? 
 - How do we know if our predictions are fair and equitable?

### What is a prediction?
In part one of the course, we will discuss what it means to make a prediction from data. To do that, we will go over the basics of probability theory (laws of probability, difference between joint/marginal/conditional probabilities, Bayes theorem). At the end of this section, you will learn that when we are talking about generating a prediction like the one made by a judge, we are talking about estimating a [conditional probability](https://www.khanacademy.org/commoncore/grade-HSS-S-CP). 

A conditional probability tells us about the probability of an event happening given that something else has already happened. For example, a prediction about whether a defendant will show up to their next court date will (most likely) be different if the defendant had *zero* prior missed appearances as opposed to *ten* prior missed appearances. In other words, the chance, or probability, of missing a court date *given* zero prior misses is lower than the chance of missing court *given* ten prior misses. What using data and algorithms gives us here is an explicit estimate of these conditional probabilities. 

And this is where the data science begins.

### Generating accurate conditional probabilities
In part two of the course, we will learn that what prediction algorithms aim to do is to estimate these conditional probabilities using data. We will cover a sequence of machine learning models that generate these predictions: Naive Bayes, Linear/Logistic Regression, Random Forest, and Gradient Boosting. 

In the process we will discuss where each algorithm comes up short in our goal of estimating accurate (or [calibrated](https://projects.fivethirtyeight.com/checking-our-work/)) probabilities and how the subsequent algorithm overcomes that limitation. 

We will conclude this section with a discussion about the great challenge in evaluating whether these algorithms actually produce predictions that are more accurate than human assessments.  

### Bias in, bias out?
After discussing what a prediction is and how machine learning algorithms generate them, we will next turn to the problem of biased data. In this final part of the course, we will discuss three different definitions of bias/fairness and how, unfortunately, it is impossible to satisfy all three of them in nearly all cases. We will conclude with a discussion on the types of bias that are potentially correctable with data, and the types that are not. 

### Hands-on skills
Throughout the course, we will ground the concepts we cover during lectures through problem sets, quizzes, a midterm, and a final exam. A central part of the course will be learning how to code some of the concepts that we discuss using the Python programming language and Jupyter Notebooks. (In particular, we will become very familiar with pandas DataFrames). No prior knowledge of Python is assumed, and thus, we will work through the coding slowly, but it should be reiterated that it is a major part of the course. To that end, some prior coding experience will likely make the learning curve in the first part of the course easier to traverse. But if you don't have it, that's also OK --- a number of students with little programming background have done well in the course with the appropriate investment. (i.e. making sure to keep up with the coding labs each week.) 

### What this course is NOT
This is an introductory course with the aim of introducing students to the topics mentioned above. If you have prior Python experience and are very comfortable coding, you may find the class (in particular the significant hands on component) not all that fulfilling. [Email me](mailto:zjelveh@umd.edu) if you have any questions about your particular situation.


