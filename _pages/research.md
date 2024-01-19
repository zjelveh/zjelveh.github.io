---
layout: archive
title: "Research"
permalink: /research/
author_profile: true
---

{% if author.googlescholar %}
  You can also find my articles on <u><a href="{{author.googlescholar}}">my Google Scholar profile</a>.</u>
{% endif %}

{% include base_path %}



## Peer-Reviewed
- [Political Language in Economics](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=2535453) (Forthcoming *Economic Journal*, 2023)
  - **With**: Bruce Kogut and Suresh Naidu  
  - **Abstract**: Do empirical estimates in economics reflect the political orientation of economists? We show that policy-relevant parameters are correlated with economist partisanship as predicted from the text of published academic papers. Specifically, we predict observed political behavior of a subset of economists using the phrases from their academic articles, obtain good out-of-sample fit, and then predict partisanship for all economists. We show considerable sorting of economists into fields of research by predicted partisanship, and yet can detect differences in partisanship among economists even within a field, even across those estimating the same theoretical parameter. Using policy-relevant parameters collected from previous meta-analyses we then show that imputed partisanship is correlated with estimated parameters, such that the implied policy prescription is consistent with partisan leaning. For example, we find that going from the most left-wing authored estimate of the taxable top income elasticity to the most right-wing authored estimate decreases the optimal tax rate from 84% to 58%.


- [No Ground Truth? No Problem: Improving Administrative Data Linking Using Active Learning and a Little Bit of Guile](https://journals.plos.org/plosone/article?id=10.1371/journal.pone.0283811) (*PLOS ONE*, 2023)
  - **With**: Sarah Tahamont, Melissa McNeill, Shi Yan, Aaron Chalfin, and Benjamin Hansen
  - **Abstract**: While linking records across large administrative datasets [“big data”] has the potential to revolutionize empirical social science research, many administrative data files do not have common identifiers and are thus not designed to be linked to others. To address this problem, researchers have developed probabilistic record linkage algorithms which use statistical patterns in identifying characteristics to perform linking tasks. Naturally, the accuracy of a candidate linking  In this paper, we investigate the value of providing groundtruth examples via active learning for linking performance. We confirm popular intuition that data linking can be dramatically improved with the availability of ground truth examples. But critically, in many real-world applications, only a relatively small number of tactically-selected ground-truth examples are needed to obtain most of the achievable gains. With a modest investment in ground truth, researchers can approximate the performance of a supervised learning algorithm that has access to a large database of ground truth examples using a readily available off-the-shelf tool.


- [Dude, Where’s My Treatment Effect? Errors in Administrative Data Linking and the Destruction of Statistical Power in Randomized Experiments](https://link.springer.com/article/10.1007/s10940-020-09461-x) (*Journal of Quantitative Criminology*, 2020)
  - **With**: Sarah Tahamont, Aaron Chalfin, Shi Yan, and Benjamin Hansen
  - **Abstract**: The increasing availability of large administrative datasets has led to an exciting innovation in social policy research—using administrative data to measure experimental outcomes in lieu of costly primary data collection. We demonstrate that this type of randomized experiment can have an unfortunate consequence: the destruction of statistical power. Combining experimental data with administrative records to track outcomes of interest typically requires linking datasets without a common identifier. In order to minimize mistaken linkages, researchers often use stringent linking rules like “exact matching” to ensure that speculative matches do not lead to errors in an analytic dataset. We show that this, seemingly conservative, approach leads to underpowered experiments, leaves real treatment effects undetected, and can therefore have profound implications for entire experimental literatures.


- [Detecting latent ideology in expert text: Evidence from academic papers in economics](https://aclanthology.org/D14-1191.pdf) (*EMNLP* Proceedings, 2014)
  - **With**: Bruce Kogut and Suresh Naidu 
  - **Abstract**: Previous work on extracting ideology from text has focused on domains where expression of political views is expected, but it’s unclear if current technology can work in domains where displays of ideology are considered inappropriate. We present a supervised ensemble n-gram model for ideology extraction with topic adjustments and apply it to one such domain: research papers written by academic economists. We show economists’ political leanings can be correctly predicted, that our predictions generalize to new domains, and that they correlate with public policy-relevant research findings. We also present evidence that unsupervised models can under-perform in domains where ideological expression is discouraged.
 

- [Profiting from filesharing: A measurement study of economic incentives in cyberlockers](https://ieeexplore.ieee.org/abstract/document/6335811/)  (*P2P* Proceedings, 2012)
  - **With**: Keith Ross
  - **Abstract**: This paper explores the incentive schemes that have been used by cyberlockers, and examines to what extent they have helped to foster the current environment. This short paper also presents a preliminary economic analysis of incentives in cyberlockers based on measurement results from three different types of sites related to cyberlockers- a search engine, a discussion forum, and a popular cyberlocker site.


- [Facebook users have become much more private: A large-scale study](https://ieeexplore.ieee.org/iel5/6192378/6197445/06197508.pdf) (*PerCom* Proceedings, 2012)
  - **With**: Ratan Dey and Keith Ross
  - **Abstract**: We investigate whether Facebook users have become more private by crawling the public profile pages of 1.4 million New York City (NYC) Facebook users in March 2010 and again in June 2011. We found that NYC users in our sample became dramatically more private during this period. For example, in March 2010 only 17.2% of users in our sample hid their friend lists, whereas in June 2011, just 15 months later, 52.6% of the users hid their friend lists. We explore privacy trends for several personal attributes including friend list, networks, relationship, high school name and graduation year, gender, and hometown.



## Working Papers
- [The Impact of Targeted Interventions on High-Risk Domestic Violence Victims](https://crimelab.uchicago.edu/resources/working-paper-targeted-interventions-for-high-risk-domestic-violence-victims/)
  - **With**:  Ashna Arora, Xander Beberman, and Ashley Motta
  - **Abstract**: Domestic violence (DV) accounts for 50% of female homicides in the U.S. The criminal justice system -- with which the majority of DV homicide victims initiate contact in the years leading up to their deaths --  may be uniquely suited to intervene and prevent the escalation of this violence. Identifying these victims, however, remains a needle in the haystack problem, as the vast majority of these victims will not go on to be homicide victims. Targeted approaches -- which attempt to identify high-risk victims and intervene effectively -- offer a solution, but have not been rigorously evaluated. We study this approach in Chicago, where DV victims gauged to be at highest risk by prosecutors are selected for additional outreach as well as prosecutorial and advocacy resources. Leveraging variation in prosecutors' tendencies to classify cases as high risk, we show that this approach rapidly and persistently lowers the likelihood of homicide by 71% for those on the margin of inclusion. Additionally, prosecutors are efficient at targeting this resource, consistently outperforming standard machine learning algorithms that predict homicide risk. 

- [Machine Learning Can Predict Shooting Victimization Well Enough to Help Prevent It](https://www.nber.org/papers/w30170)   
  - **With**: Sara Heller, Benjamin Jakubowski, and Max Kapustin
  - **Abstract**: This paper shows that shootings are predictable enough to be preventable. Using arrest and victimization records for almost 644,000 people from the Chicago Police Department, we train a machine learning model to predict the risk of being shot in the next 18 months. We address central concerns about police data and algorithmic bias by predicting shooting victimization rather than arrest, which we show accurately captures risk differences across demographic groups despite bias in the predictors. Out-of-sample accuracy is strikingly high: of the 500 people with the highest predicted risk, 13 percent are shot within 18 months, a rate 130 times higher than the average Chicagoan. Although Black male victims more often have enough police contact to generate predictions, those predictions are not, on average, inflated; the demographic composition of predicted and actual shooting victims is almost identical. There are legal, ethical, and practical barriers to using these predictions to target law enforcement. But using them to target social services could have enormous preventive benefits.

- Contrasting approaches to identify people at-risk of behavioral health  crises involving first-responders
  - **With**: Andrea Tentner, Xander Beberman, and Harold Pollack
  - **Abstract**: Prevention or de-escalation of dangerous police encounters with community members experiencing behavioral health challenges are central public health and safety challenges. A complementary approach that leverages emergency response data to predict which individuals are at highest risk for these encounters may be an important tool in the implementation of targeted prevention and service interventions. In this study, we use emergency response data to show that behavioral health-indicated encounters with police can be reliably predicted. Both simple and complex modeling approaches are able to identify small populations at extreme risk, though a machine learning approach is more accurate, especially when targeting larger groups. And ML can also identify opportunities for prevention. Fully 28% of individuals identified in our top 1% risk-group had no prior BH-police-involved emergency encounters. Both approaches, when combined with rich administrative data may also aid in tailoring pertinent interventions.

- P-Hacking in Academic Clinical Trials 
  - **With**: Jorge Guzman and Bruce Kogut
  - **Abstract**: A common belief in the history of science is that institutions matter.  They incentivize individual scientists to commit to the norms of open science, e.g., transparency, rigor, and accountability in return for reputation.  However, historically, the violation of these norms, e.g.,  the reproducibility of research findings, have raised questions about the effectiveness of institutions.  Using both distribution and density tests, we document statistically significant p-hacking in U.S. academic clinical trials but not in the trials registered by commercial laboratories.We analyze the impact of the 2013 SPIRIT statement--a checklist defining the minimal requirements of clinical trial protocols which was adopted by leading journals--as a type of treatment that could potentially diminish the incentives for p-hacking in clinical trial research.  Focusing then on academic trials, we ask whether p-hacking decreased after the introduction of SPIRIT. We show that the dissemination of protocols sharply increased after the introduction of SPIRIT. Clinical trials started after the introduction of SPIRIT show lower levels of p-hacking, with the effects stronger for those trials whose plan more closely resembles the textual language of the SPIRIT guidance. In contrast, SPIRIT did not reduce p-hacking in trials already underway when introduced. Our analysis emphasizes the significance of institutional innovations to counter the consequences of over-incentivizing academic scientists to promote effort that sometimes favors career concerns over normative goals of open science.


## Works in Progress
- Domain Adaptation for Record Linkage 
  - **With**: Melissa McNeill and Sarah Tahamont

- Predicting Domestic Violence in New York City
  - **With**: Aaron Chalfin and Melissa McNeill

## Other
- [Productivity and selection of human capital with machine learning](https://www.aeaweb.org/articles?id=10.1257/aer.p20161029) (*AER P&P*)
  - **With**: Aaron Chalfin, Oren Danieli, Andrew Hillis, Michael Luca, Jens Ludwig, Sendhil Mullainthan)
  
- Towards Diagnosing Accuracy Loss in Discrimination-Aware Classification: An Application to Predictive Policing (*FATML*)
  - **With**: Michael Luca