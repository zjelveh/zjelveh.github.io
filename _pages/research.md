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

- Predicting behavioral health-involved police encounters: A machine learning approach. (Conditional Accept: *Journal of Quantitative Criminology*, 2025)
  - **With**: Andrea Tentner, Xander Beberman, and Harold Pollack
  <details><summary>Abstract</summary>
  Prevention or de-escalation of dangerous police encounters with community members experiencing behavioral health challenges are central public health and safety challenges. A complementary approach that leverages emergency response data to predict which individuals are at highest risk for these encounters may be an important tool in the implementation of targeted prevention and service interventions. In this study, we use emergency response data to show that behavioral health-indicated encounters with police can be reliably predicted. Both simple and complex modeling approaches are able to identify small populations at extreme risk, though a machine learning approach is more accurate, especially when targeting larger groups. And ML can also identify opportunities for prevention. Fully 28% of individuals identified in our top 1% risk-group had no prior BH-police-involved emergency encounters. Both approaches, when combined with rich administrative data may also aid in tailoring pertinent interventions.
  </details>


- [Machine Learning Can Predict Shooting Victimization Well Enough to Help Prevent It](https://www.nber.org/papers/w30170) (*Review of Economics and Statistics*, 2024)
  - [Working Paper Version](https://www.nber.org/papers/w30170)
  - **With**: Sara Heller, Benjamin Jakubowski, and Max Kapustin
  <details><summary>Abstract</summary>
  This paper shows that shootings are predictable enough to be preventable. Using arrest and victimization records for almost 644,000 people from the Chicago Police Department, we train a machine learning model to predict the risk of being shot in the next 18 months. We address central concerns about police data and algorithmic bias by predicting shooting victimization rather than arrest, which we show accurately captures risk differences across demographic groups despite bias in the predictors. Out-of-sample accuracy is strikingly high: of the 500 people with the highest predicted risk, 13 percent are shot within 18 months, a rate 130 times higher than the average Chicagoan. Although Black male victims more often have enough police contact to generate predictions, those predictions are not, on average, inflated; the demographic composition of predicted and actual shooting victims is almost identical. There are legal, ethical, and practical barriers to using these predictions to target law enforcement. But using them to target social services could have enormous preventive benefits.
  </details>


- [Political Language in Economics](https://sites.santafe.edu/~snaidu/papers/Jelveh_Kogut_Naidu_05232022.pdf) (*Economic Journal*, 2024)
  - [Working Paper Version](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=2535453)
  - **With**: Bruce Kogut and Suresh Naidu
  <details><summary>Abstract</summary>
  Do empirical estimates in economics reflect the political orientation of economists? We show that policy-relevant parameters are correlated with economist partisanship as predicted from the text of published academic papers. Specifically, we predict observed political behavior of a subset of economists using the phrases from their academic articles, obtain good out-of-sample fit, and then predict partisanship for all economists. We show considerable sorting of economists into fields of research by predicted partisanship, and yet can detect differences in partisanship among economists even within a field, even across those estimating the same theoretical parameter. Using policy-relevant parameters collected from previous meta-analyses we then show that imputed partisanship is correlated with estimated parameters, such that the implied policy prescription is consistent with partisan leaning. For example, we find that going from the most left-wing authored estimate of the taxable top income elasticity to the most right-wing authored estimate decreases the optimal tax rate from 84% to 58%.
  </details>


- [No Ground Truth? No Problem: Improving Administrative Data Linking Using Active Learning and a Little Bit of Guile](https://journals.plos.org/plosone/article?id=10.1371/journal.pone.0283811) (*PLOS ONE*, 2023)
  - **With**: Sarah Tahamont, Melissa McNeill, Shi Yan, Aaron Chalfin, and Benjamin Hansen
  <details><summary>Abstract</summary>
  While linking records across large administrative datasets ["big data"] has the potential to revolutionize empirical social science research, many administrative data files do not have common identifiers and are thus not designed to be linked to others. To address this problem, researchers have developed probabilistic record linkage algorithms which use statistical patterns in identifying characteristics to perform linking tasks. Naturally, the accuracy of a candidate linking  In this paper, we investigate the value of providing groundtruth examples via active learning for linking performance. We confirm popular intuition that data linking can be dramatically improved with the availability of ground truth examples. But critically, in many real-world applications, only a relatively small number of tactically-selected ground-truth examples are needed to obtain most of the achievable gains. With a modest investment in ground truth, researchers can approximate the performance of a supervised learning algorithm that has access to a large database of ground truth examples using a readily available off-the-shelf tool.
  </details>


- [Dude, Where's My Treatment Effect? Errors in Administrative Data Linking and the Destruction of Statistical Power in Randomized Experiments](https://link.springer.com/article/10.1007/s10940-020-09461-x) (*Journal of Quantitative Criminology*, 2020)
  - [Working Paper Version](https://www.nber.org/papers/w25657)
  - **With**: Sarah Tahamont, Aaron Chalfin, Shi Yan, and Benjamin Hansen
  <details><summary>Abstract</summary>
  The increasing availability of large administrative datasets has led to an exciting innovation in social policy research—using administrative data to measure experimental outcomes in lieu of costly primary data collection. We demonstrate that this type of randomized experiment can have an unfortunate consequence: the destruction of statistical power. Combining experimental data with administrative records to track outcomes of interest typically requires linking datasets without a common identifier. In order to minimize mistaken linkages, researchers often use stringent linking rules like "exact matching" to ensure that speculative matches do not lead to errors in an analytic dataset. We show that this, seemingly conservative, approach leads to underpowered experiments, leaves real treatment effects undetected, and can therefore have profound implications for entire experimental literatures.
  </details>


- [Detecting latent ideology in expert text: Evidence from academic papers in economics](https://aclanthology.org/D14-1191.pdf) (*EMNLP* Proceedings, 2014)
  - **With**: Bruce Kogut and Suresh Naidu
  <details><summary>Abstract</summary>
  Previous work on extracting ideology from text has focused on domains where expression of political views is expected, but it's unclear if current technology can work in domains where displays of ideology are considered inappropriate. We present a supervised ensemble n-gram model for ideology extraction with topic adjustments and apply it to one such domain: research papers written by academic economists. We show economists' political leanings can be correctly predicted, that our predictions generalize to new domains, and that they correlate with public policy-relevant research findings. We also present evidence that unsupervised models can under-perform in domains where ideological expression is discouraged.
  </details>


- [Profiting from filesharing: A measurement study of economic incentives in cyberlockers](https://ieeexplore.ieee.org/abstract/document/6335811/)  (*P2P* Proceedings, 2012)
  - **With**: Keith Ross
  <details><summary>Abstract</summary>
  This paper explores the incentive schemes that have been used by cyberlockers, and examines to what extent they have helped to foster the current environment. This short paper also presents a preliminary economic analysis of incentives in cyberlockers based on measurement results from three different types of sites related to cyberlockers- a search engine, a discussion forum, and a popular cyberlocker site.
  </details>


- [Facebook users have become much more private: A large-scale study](https://ieeexplore.ieee.org/iel5/6192378/6197445/06197508.pdf) (*PerCom* Proceedings, 2012)
  - **With**: Ratan Dey and Keith Ross
  <details><summary>Abstract</summary>
  We investigate whether Facebook users have become more private by crawling the public profile pages of 1.4 million New York City (NYC) Facebook users in March 2010 and again in June 2011. We found that NYC users in our sample became dramatically more private during this period. For example, in March 2010 only 17.2% of users in our sample hid their friend lists, whereas in June 2011, just 15 months later, 52.6% of the users hid their friend lists. We explore privacy trends for several personal attributes including friend list, networks, relationship, high school name and graduation year, gender, and hometown.
  </details>



## Working Papers

- Crime and the City: Computational Approaches and the Future of Urban Crime Research (Revise and Resubmit at *Nature*)
  - **With**: Gian Maria Campedelli, Bruno Lepri, Patrick Sharkey, Aaron Chalfin, Eric Piza, Ariadna Albors Zumel, and Daniel Semenza
  <details><summary>Abstract</summary>
  Urban environments have long been a central focus for crime researchers across diverse disciplines. Over the past fifteen years, this heterogeneous field has undergone a profound transformation, driven by the emergence of novel datasets and the rise of powerful, flexible computational methods. In this Review, we take stock of this transition and explore the significant potential these developments hold for advancing urban crime research, while also addressing the persistent challenges that continue to shape the field. Building on this overview, we highlight the importance of integrating causal inference beyond mere prediction tasks and outline three key directions for future research to ensure that the promise of new data and computational tools is fully realized. In doing so, we aim to support the production of more rigorous research and the development of more effective policies for safer, more sustainable cities worldwide.
  </details>


- Time is on your side: The benefits of time-sensitive factors in pretrial risk assessments
  - **With**: Greg Stoddard, Melissa McNeill, and Alexandra Chouldechova
  <details><summary>Abstract</summary>
  Risk assessments are used in millions of pretrial hearings per year to guide judges as they weigh public safety risks against the cost of restricting defendant liberties. We show that the time since a prior event matters for its relevance as a risk factor and, as a result, risk models can be significantly improved by using time-sensitive risk factors. Using data from New Jersey, we find that time-sensitive risk models are simultaneously more accurate and less racially disparate than standard time-insensitive risk models. For example, New Jersey's violent risk predictor could be 5% more accurate and 20% less disparate if time-sensitive factors were used. These improvements generalize across six other pretrial risk scales. We present a simple time-sensitive modeling approach called "time-limiting" that is no more complex than time-insensitive risk models and can work in any practical setting. Our results suggest that considering the use of time-sensitive risk factors should be adopted as a best practice in risk assessment development and revalidation.
  </details>


- [Perils and Pitfalls in the Use of Synthetic Control Methods to Study Public Safety Interventions](https://www.dropbox.com/scl/fi/kgt1r2z0mmbqyee31b4q9/scm_variation.pdf?rlkey=zqrkcl87cmhckm1xe0jp4604a&dl=0) (Under review)
  - **With**: Aaron Chalfin
  <details><summary>Abstract</summary>
  The method of synthetic controls, pioneered by Abadie et al. (2010), has generated a paradigm shift in the analysis of case studies. The method selects an appropriate synthetic comparison group by identifying a weighted set of units that closely match the treated unit on the basis of pre-intervention levels and trends. Since Abadie's seminal paper, there has been a proliferation of research expanding and refining the method and a corresponding litany of software packages that provide the means to estimate these models. We show that there can be a shocking lack of correspondence between the estimates produced by commonly used software packages. Even the seemingly innocent choice between using R or Stata to estimate SCM can lead to a meaningful difference in estimated treatment effects. We demonstrate this surprising finding, invoking a recent debate in criminological research concerning a paper on the effects of "de-prosecution" by Hogan (2022) which has been criticized by Kaplan et al. (2022).
  </details>


- Synthetic Data for Systematic Evaluation: How Well Can LLMs Perform Deductive Coding of Economic Concepts?
  - **With**: Zhuohui Chen
  <details><summary>Abstract</summary>
  Identifying concepts, ideas, and topics in text is foundational for advancing knowledge, enabling researchers to trace the evolution of ideas, understand intellectual movements, and map conceptual relationships within and across disciplines. While Large Language Models (LLMs) offer unprecedented opportunities for automated concept detection at scale, evaluating their capabilities faces significant challenges due to scarce evaluation datasets and difficulties in aligning generated topics with ground truth. This study introduces a methodological framework using controlled synthetic data generation to evaluate LLMs' deductive coding performance. We generate 2,880 economics abstracts using real-world topic mixtures, controlling for topic explicitness, stylistic diversity, and vocabulary restrictions. Through systematic experimentation across different codebook configurations and LLM architectures, we find that while recall is generally high, precision in coding is moderate. While apparent false positives initially suggest overprediction, semantic analysis reveals that they likely represent valid emergent topics. Our framework provides a replicable methodology for systematic LLM evaluation and highlights promising possibilities and future research avenues for evaluating LLMs' abilities to trace ideas and concepts across diverse textual domains.
  </details>


- [The Impact of Targeted Interventions on High-Risk Domestic Violence Victims](https://crimelab.uchicago.edu/resources/working-paper-targeted-interventions-for-high-risk-domestic-violence-victims/)
  - **With**: Ashna Arora, Xander Beberman, and Ashley Motta
  <details><summary>Abstract</summary>
  Domestic violence (DV) accounts for 50% of female homicides in the U.S. The criminal justice system -- with which the majority of DV homicide victims initiate contact in the years leading up to their deaths --  may be uniquely suited to intervene and prevent the escalation of this violence. Identifying these victims, however, remains a needle in the haystack problem, as the vast majority of these victims will not go on to be homicide victims. Targeted approaches -- which attempt to identify high-risk victims and intervene effectively -- offer a solution, but have not been rigorously evaluated. We study this approach in Chicago, where DV victims gauged to be at highest risk by prosecutors are selected for additional outreach as well as prosecutorial and advocacy resources. Leveraging variation in prosecutors' tendencies to classify cases as high risk, we show that this approach rapidly and persistently lowers the likelihood of homicide by 71% for those on the margin of inclusion. Additionally, prosecutors are efficient at targeting this resource, consistently outperforming standard machine learning algorithms that predict homicide risk.
  </details>


- [The SPIRIT of Science: Institutional Responses to the P-Hacking Problem in Academic Clinical Trials](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=6226781)
  - **With**: Jorge Guzman and Bruce Kogut
  <details><summary>Abstract</summary>
  All researchers face pressure to demonstrate significance, but whether that pressure distorts findings may depend on how observable their analytic choices are. We examine this in clinical trials, where academic and industry sponsors face similar evidentiary benchmarks but differ in documentation practices and oversight contexts. Using p-value distributions from 10,596 completed randomized clinical trials registered on ClinicalTrials.gov, we test for threshold-driven distortions around p = 0.05. Academic-sponsored trials exhibit an excess of primary-outcome p-values just below 0.05, while industry-sponsored trials show little or no such pattern; secondary outcomes show no comparable distortion for either sponsor type. Internal consistency checks between reported p-values and 95% confidence intervals replicate the same sponsor gap, and a validation exercise using p-values extracted from PubMed Central trial publications yields similar directional differences. The academic–industry gap persists after adjusting for trial characteristics, suggesting that organizational setting itself may matter. We examine the 2013 SPIRIT statement (Standard Protocol Items: Recommendations for Interventional Trials), which standardized protocol documentation for clinical trials. Academic trials initiated after SPIRIT show weaker evidence of threshold-adjacent bunching than those initiated earlier, whereas trials initiated earlier but reported later show no comparable change—a pattern suggestive of protocol design and documentation as a relevant margin.
  </details>


## Other

- [Productivity and selection of human capital with machine learning](https://www.aeaweb.org/articles?id=10.1257/aer.p20161029) (*AER P&P*)
  - **With**: Aaron Chalfin, Oren Danieli, Andrew Hillis, Michael Luca, Jens Ludwig, Sendhil Mullainthan)


- Towards Diagnosing Accuracy Loss in Discrimination-Aware Classification: An Application to Predictive Policing (*FATML*)
  - **With**: Michael Luca
