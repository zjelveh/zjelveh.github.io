---
title: "Applications of Data Science for Criminology"
collection: teaching
type: "Undergraduate course"
permalink: /teaching/ccjs418e
---

**Note:** This page serves as an overview of the topics discussed in *Applications of Data Science for Criminology* which are likely to be new to a number of students. Thus, the purpose of this page is to shed light on what is covered in the course so that prospective students can make informed decisions about whether it's the right course for them. 

---

Actors in the criminal justice system are often tasked with making decisions that involve a prediction about the future For example, the following decisions are made (in part) on the basis of a prediction about future behavior:  
 - Judges make release/jail decisions based on an assessment of a defendant's likelihood of showing up at future court dates if released.  
 - Police officers make patrollings decisions based on a prediction of where crime is likely to happen
 - Domestic violence shelter providers make housing allocations based on an assessment of survivors near-term risk of re-victimization
 - Prison security designations are based on the likelihood that an inmate will commit an infraction.
 
At the same time, we know very little about the quality of  predictions made by humans in these contexts. 
 - Are they accurate?
 - Are they fair? 
 - Do they lead to intended outcomes? (e.g. Do patrolling decisions lead to lower crime rates, do detention decisions lead to more appearances overall, do they have unintended consequences on labor and eductional outcomes, etc ) 
 - Can they be improved through the use of administrative data and prediction algorithms. 
 
 At the same time, there is great controversy around the use of algorithms in the criminal justice system. Central to this controversy is the fear that data commonly used in these algorithms (e.g. arrest, court, and victimization records) contain human bias, and thus that the predictions from these algorithms will reinforce those biases. 

Through the lens of [pretrial risk assessments](https://advancingpretrial.org/pretrial-justice/pretrial-justice/)  this course asks and attempts to provide answers to the following questions:
 - What does it mean to make a prediction?
 - How do we know if our predictions are accurate? 
 - How do we know if our predictions are fair and equitable?

### What is a prediction?
In part 1 of the course, we will discuss what it means to make a prediction from data. To do that, we will go over the basics of probability theory (laws of probability, difference between joint/marginal/conditional probabilities, Bayes theorem). At the end of this section, you will learn that when we are talking about generating a prediction like the one made by a judge, we are talking about estimating a [conditional probability](https://www.khanacademy.org/commoncore/grade-HSS-S-CP). A conditional probability tells us about the probability of an event happening GIVEN that something else has already happened. For example, a prediction about whether a defendant will show up to their next court date will likely be different if the defendant had zero prior missed court appearances as opposed to having ten prior missed appearances. In other words, the probability of missing a court date GIVEN zero prior misses is likely to be lower than GIVEN ten prior misses. What using data and algorithms gives us here is an explicit estimate of these conditional probabilities.  

### Generating accurate conditional probabilities
In part 2 of the course, we will learn that what prediction algorithms aim to do is to estimate these conditional probabilities using data. We will cover a sequence of machine learning models that generate predictions: Naive Bayes, Linear/Logistic Regression, Random Forest, and Gradient Boosting. 

In the process we will discuss where each algorithm comes up short in our goal of estimating accurate (or calibrated) probabilities and how the subsequent algorithm overcomes that limitation. 

### Bias in, bias out?
After discussing what a prediction is and how machine learning algorithms generate their predictions, we will next turn to the problem of biased data. In this part of the course, we will discuss three different definitions of bias/fairness and how, unfortunately, it is impossible to satisfy all three of them in nearly all cases. We will next cover what types of bias are potentially correctable with data. And what types are not. 

### Hands-on skills
Throughout the course, we will ground the concepts we cover during lectures through problems sets, quizzes, a midterm, and a final exam. A central part of the course will be learning how to code some of the concepts that we discuss using the Python programming language and Jupyter Notebooks. No prior knowledge of coding is assumed, and thus, we will work through the coding slowly, but it should be reiterated that it is a major part of the course. 



