---
layout: archive
title: "Research"
permalink: /research/
author_profile: true
---

<!-- {% if author.googlescholar %}
  You can also find my articles on <u><a href="{{author.googlescholar}}">my Google Scholar profile</a>.</u>
{% endif %}

{% include base_path %}

{% for post in site.research reversed %}
  {% include archive-single.html %}
{% endfor %} -->

### Peer-Reviewed
#### [Dude, Where’s My Treatment Effect? Errors in Administrative Data Linking and the Destruction of Statistical Power in Randomized Experiments](https://link.springer.com/article/10.1007/s10940-020-09461-x) (w/ Sarah Tahamont, Aaron Chalfin, Shi Yan, and Benjamin Hansen)
The increasing availability of large administrative datasets has led to an exciting innovation in criminal justice research—using administrative data to measure experimental outcomes in lieu of costly primary data collection. We demonstrate that this type of randomized experiment can have an unfortunate consequence: the destruction of statistical power. Combining experimental data with administrative records to track outcomes of interest typically requires linking datasets without a common identifier. In order to minimize mistaken linkages, researchers often use stringent linking rules like “exact matching” to ensure that speculative matches do not lead to errors in an analytic dataset. We show that this, seemingly conservative, approach leads to underpowered experiments, leaves real treatment effects undetected, and can therefore have profound implications for entire experimental literatures.

#### [Detecting latent ideology in expert text: Evidence from academic papers in economics](https://aclanthology.org/D14-1191.pdf) (w/ Bruce Kogut and Suresh Naidu)
Previous work on extracting ideology from text has focused on domains where expression of political views is expected, but it’s unclear if current technology can work in domains where displays of ideology are considered inappropriate. We present a supervised ensemble n-gram model for ideology extraction with topic adjustments and apply it to one such domain: research papers written by academic economists. We show economists’ political leanings can be correctly predicted, that our predictions generalize to new domains, and that they correlate with public policy-relevant research findings. We also present evidence that unsupervised models can under-perform in domains where ideological expression is discouraged.
 
#### [Facebook users have become much more private: A large-scale study](https://ieeexplore.ieee.org/iel5/6192378/6197445/06197508.pdf) (w/ Ratan Dey and Keith Ross)
We investigate whether Facebook users have become more private in recent years. Specifically, we examine if there have been any important trends in the information Facebook users reveal about themselves on their public profile pages since early 2010. To this end, we have crawled the public profile pages of 1.4 million New York City (NYC) Facebook users in March 2010 and again in June 2011. We have found that NYC users in our sample have become dramatically more private during this period. For example, in March 2010 only 17.2% of users in our sample hid their friend lists, whereas in June 2011, just 15 months later, 52.6% of the users hid their friend lists. We explore privacy trends for several personal attributes including friend list, networks, relationship, high school name and graduation year, gender, and hometown. We find that privacy trends have become more pronounced for certain demographics. Finally, we attempt to determine the primary causes behind the dramatic decrease in the amount of information Facebook users reveal about themselves to the general public.

#### [Profiting from filesharing: A measurement study of economic incentives in cyberlockers](https://ieeexplore.ieee.org/abstract/document/6335811/) (w/ Keith Ross)


### Working Papers

#### [Machine Learning Can Predict Shooting Victimization Well Enough to Help Prevent It](https://www.nber.org/papers/w30170) (w/ Sara Heller, Benjamin Jakubowski, and Max Kapustin)
This paper shows that shootings are predictable enough to be preventable. Using arrest and victimization records for almost 644,000 people from the Chicago Police Department, we train a machine learning model to predict the risk of being shot in the next 18 months. We address central concerns about police data and algorithmic bias by predicting shooting victimization rather than arrest, which we show accurately captures risk differences across demographic groups despite bias in the predictors. Out-of-sample accuracy is strikingly high: of the 500 people with the highest predicted risk, 13 percent are shot within 18 months, a rate 130 times higher than the average Chicagoan. Although Black male victims more often have enough police contact to generate predictions, those predictions are not, on average, inflated; the demographic composition of predicted and actual shooting victims is almost identical. There are legal, ethical, and practical barriers to using these predictions to target law enforcement. But using them to target social services could have enormous preventive benefits: predictive accuracy among the top 500 people justifies spending up to $123,500 per person for an intervention that could cut their risk of being shot in half.

#### Contrasting approaches to identify people at-risk of behavioral health  crises involving first-responders (w/ Andrea Tentner, Xander Beberman, and Harold Pollack)
Prevention or de-escalation of dangerous police encounters with community members experiencing behavioral health challenges are central public health and safety challenges. A complementary approach that leverages emergency response data to predict which individuals are at highest risk for these encounters may be an important tool in the implementation of targeted prevention and service interventions. In this  study, we employ and compare two methods for predicting individuals at highest risk for BH-involved encounters with police (BHIP).  We assess the added value of machine learning (ML) versus simpler and transparent “high-user” approaches, and perform “leave-out experiments” that blind the ML model to sensitive police and demographic data. When targeting the top 0.1% of risk, 5 in 10 individuals identified by random forest and 4 in 10 identified by the high-user approach go onto have a BHIP. The relative advantage of the random forest approach grows when targeting larger groups, achieving twice the precision among the top 5% of high-risk individuals. Our results are robust to exclusion of sensitive arrest and demographic data. Behavioral health-indicated encounters with police can be reliably predicted using emergency response data. Both simple and complex modeling approaches are able to identify small populations at extreme risk, though the random forest approach is more accurate, especially when targeting larger groups. An ML can also identify opportunities for prevention. Fully 28% of individuals identified in our top 1% risk-group had no prior BH-police-involved emergency encounters. Both approaches, when combined with rich administrative data may also aid in tailoring pertinent interventions.

#### [No Ground Truth? No Problem: Improving Administrative Data Linking Using Active Learning and a Little Bit of Guile](http://achalfin.weebly.com/uploads/8/5/4/8/8548116/a_little_bit_of_guile.pdf) (w/ Sarah Tahamont, Melissa McNeill, Shi Yan, Aaron Chalfin, and Benjamin Hansen)
While linking records across large administrative datasets [“big data”] has the potential to revolutionize empirical social science research, many administrative data files do not have common identifiers and are thus not designed to be linked to others. To address this problem, researchers have developed probabilistic record linkage algorithms which use statistical patterns in identifying characteristics to perform linking tasks. Naturally, the accuracy of a candidate linking algorithm can be substantially improved when an algorithm has access to “ground-truth” examples — matches which can be validated using institutional knowledge or auxiliary data. Unfortunately, the cost of obtaining these examples is typically high, often requiring a researcher to manually review pairs of records in order to make an informed judgement about whether they are a match. When a pool of ground-truth information is unavailable, researchers can use “active learning” algorithms for linking, which ask the user to provide ground-truth information for select candidate pairs. In this paper, we investigate the value of providing groundtruth examples via active learning for linking performance. We confirm popular intuition that data linking can be dramatically improved with the availability of ground truth examples. But critically, in many real-world applications, only a relatively small number of tactically-selected ground-truth examples are needed to obtain most of the achievable gains. With a modest investment in ground truth, researchers can approximate the performance of a supervised learning algorithm that has access to a large database of ground truth examples using a readily available off-the-shelf tool.

#### [Political Language in Economics](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=2535453) (w/ Bruce Kogut and Suresh Naidu)
Do empirical estimates in economics reflect the political orientation of economists? We show that policy-relevant parameters are correlated with economist partisanship as predicted from the text of published academic papers. Specifically, we predict observed political behavior of a subset of economists using the phrases from their academic articles, obtain good out-of-sample fit, and then predict partisanship for all economists. We show considerable sorting of economists into fields of research by predicted partisanship, and yet can detect differences in partisanship among economists even within a field, even across those estimating the same theoretical parameter. Using policy-relevant parameters collected from previous meta-analyses we then show that imputed partisanship is correlated with estimated parameters, such that the implied policy prescription is consistent with partisan leaning. For example, we find that going from the most left-wing authored estimate of the taxable top income elasticity to the most right-wing authored estimate decreases the optimal tax rate from 84% to 58%.


### Works in Progress
#### P-Hacking in Academic Clinical Trials (w/ Jorge Guzman and Bruce Kogut)

#### The Impact of Targeted Interventions on High-Risk Domestic Violence Victims (w/ Ashna Arora)
 
#### Domain Adaptation for Record Linkage (w/ Melissa McNeill and Sarah Tahamont)

#### Predicting Domestic Violence in New York City (w/ Aaron Chalfin and Melissa McNeill)

### Other
[Productivity and selection of human capital with machine learning](https://www.aeaweb.org/articles?id=10.1257/aer.p20161029)

Towards Diagnosing Accuracy Loss in Discrimination-Aware Classification: An Application to Predictive Policing (w/ Michael Luca)