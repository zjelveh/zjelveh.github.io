---
layout: splash
author_profile: false
title: "Syllabus for INST 798/808: A.I.-Powered Research Assistants"
collection: teaching
permalink: /teaching/inst_808_syllabus
classes: wide
---


**Location + Time:** [TWS 0207](https://25live.collegenet.com/pro/umd#!/home/location/2426/details), Thursdays 2 to 4.45p.m. 

## Course Description
This course explores how Large Language Models (LLMs) can transform labor-intensive research tasks in the social sciences. Using the challenge of tracing ideas and concepts through text as our primary lens, we examine how these powerful tools can aid both qualitative and quantitative research methodologies. Measuring the evolution of ideas through text presents uniquely complex challenges - concepts may be expressed through varied language, their meaning often shifts over time, and understanding them requires deep contextual knowledge that has traditionally relied heavily on human expertise.

The course begins by examining traditional approaches to concept measurement, from word embeddings to early neural architectures, before exploring how transformer-based models have revolutionized our ability to detect and track complex ideas in text. We then delve into recent advances in mechanistic interpretability to understand how these models internally represent and manipulate concepts, providing crucial insights into both their capabilities and limitations. This foundation allows us to evaluate various approaches to concept tracing, from using LLMs to scale up qualitative research methods to exploring how modern neural topic modeling can capture evolving ideas across large corpora.

Throughout the course, we maintain a strong focus on validation and methodology, culminating in an examination of how to properly conduct downstream analyses using LLM-processed data. Through paper presentations, class discussions, hands-on labs, and a research paper, students will develop both theoretical understanding and practical experience applying these tools to real research problems.

By the course's end, students will be equipped to evaluate when and how to effectively integrate LLMs into their research workflows, understand the methodological implications of using these tools, and implement appropriate validation strategies for LLM-assisted research. Most importantly, they will develop a critical perspective on both the transformative potential and the limitations of using LLMs as research assistants in the social and information sciences.

## Course Objectives
After completing this course, students will be able to:
1. Understand the fundamental concepts of natural language processing and their evolution
2. Evaluate the capabilities and limitations of AI research tools
3. Implement proper validation and error analysis techniques
4. Design research workflows that appropriately incorporate AI assistance

## Prerequisites
While students aren't expected to have deep expertise in all areas, you should be comfortable with the following:
- Python programming fundamentals (working with common data structures, functions, pandas)
- Basic linear algebra. Understanding how language models represent and manipulate text requires familiarity with vector and matrix operations (addition, multiplication, transpose, distance, similarity).
- Basic machine learning concepts (supervised vs unsupervised learning, common evaluation metrics)
- Fundamental probability concepts (conditional probability, independence)

## Technical Requirements
This course explores cutting-edge AI technologies, but we'll be working within practical computational constraints. While large language models like GPT-4 or Claude 3.5 require significant computing resources, we'll focus on working with smaller, more manageable models that can run on personal computers. Students will need a laptop capable of running Python and handling lightweight language models (8GB RAM minimum, 16GB+ recommended). We'll use TerpAI for tasks requiring more computational power, but part of the learning experience will involve understanding how to conduct meaningful research within resource limitations. The course will emphasize understanding core concepts and developing practical workflows that can scale from limited to abundant computational resources.


<style>
.section-heading {
    font-size: 1.2em;
    font-weight: bold;
    margin-top: 1em;
    margin-bottom: 1em;
}
</style>

## Assessment
<details>
<summary class="section-heading">Weekly questions/reflections (20%)</summary>

Students will submit weekly questions or reflections (maximum 500 words) by <b>Tuesday at 5pm</b> before each class. These submissions serve two purposes: they help shape our class discussion and demonstrate your engagement with the Reading. These submissions will be used to guide our class discussions, so be prepared to elaborate on your question or reflection during class. Your submission should do one of the following:

<ul>
<li>Pose a substantive question sparked by the Reading. This could be about methodology, implications, connections to other work, or potential applications. Questions should go beyond basic clarification to engage with the material's concepts or implications.</li>

<li>Offer a reflection that connects multiple Reading, relates the material to your own research, or critically examines the methodology or assumptions. Your reflection might consider how different papers approach similar problems, identify potential limitations, or propose new applications.</li>

<li>Express and explore areas of confusion in the Reading. Some of our papers are technically challenging, and identifying what you don't understand is an important part of the learning process. When discussing confusing aspects, please:
  <ul>
    <li>Describe your current understanding of the concept</li>
    <li>Identify specifically what aspect is unclear</li>
  </ul>
</li>
</ul>

</details>

<details>
<summary class="section-heading">Presentations (20%)</summary>

Throughout the semester, you will present assigned papers to the class. These 20-minute presentations should have 12-15 minutes of content and 5-8 minutes of discussion leading. Additionally, the presentations should:
<ul>
<li>Clearly state the paper's main contribution and why it matters</li>
<li>Walk through one or two illustrative examples from the paper</li>
<li>Discuss limitations and potential extensions</li>
<li>Prepare 2-3 discussion questions for the class</li>
<li>Be ready to facilitate brief discussion of these questions</li>
</ul>
</details>

<details>
<summary class="section-heading">Research Project Proposal (20%)</summary>

The research proposal (3-5 pages) outlines your planned investigation into either evaluating LLMs for specific research tasks or using LLMs to study a substantive research question. Before submitting your proposal, you must schedule a meeting with me to discuss your ideas. You can work by yourself or with one other student in the course, which I highly encourage. Prepare a one-paragraph summary of your idea and 2-3 specific questions for our discussion. This meeting should take place at least one week before the proposal deadline.
<strong>The proposal is due in week 8 of the class (3/20).</strong>

Your proposal should be structured as follows:

<ul>
<li><strong>Introduction</strong> (~1 page)<br>
Present your core research question or evaluation task. Whether you're assessing LLM capabilities or studying a substantive topic, explain why this question matters and how LLMs offer unique insights for addressing it. For instance, you might explore how LLMs could help trace the evolution of methodological discussions in your field, or evaluate how well they can identify theoretical frameworks in academic papers.</li>

<li><strong>Proposed Methodology</strong> (1-2 pages)<br>
Detail your research design, including:
    <ul>
        <li>Data sources</li>
        <li>Which models or tools you'll use</li>
        <li>Your analytical approach</li>
        <li>Why your chosen methods are appropriate for your question</li>
    </ul>
For example, if you're studying how newspaper coverage of artificial intelligence has evolved, explain why concept tracing with LLMs might capture subtle shifts in framing better than traditional content analysis.</li>

<li><strong>Validation Strategy</strong> (~1 page)<br>
Describe how you'll verify your results and ensure methodological rigor. This might include:
    <ul>
        <li>Comparison with human coding</li>
        <li>Use of multiple models</li>
        <li>Development of benchmarks</li>
        <li>Strategies for addressing potential biases</li>
    </ul>
Acknowledge the limitations of your approach and explain how you'll address them.</li>

<li><strong>Timeline and Feasibility</strong> (~0.5 page)<br>
Provide a realistic schedule showing how you'll complete the work within the semester. Include key milestones such as:
    <ul>
        <li>Data collection</li>
        <li>Initial analysis</li>
        <li>Validation steps</li>
        <li>Writing and revision</li>
    </ul></li>
</ul>

</details>


<details>
<summary class="section-heading">Final Paper (40%)</summary>
The Final Paper will be due on the first day of finals period.
</details>


## Weekly Schedule

### Week 1: Introduction to Natural Language Processing
**Required Reading:**
- Textbook: [Jurafsky & Martin (2025). Speech and Language Processing](https://web.stanford.edu/~jurafsky/slp3/)
   - Chapter 3: 3.1 to 3.3, 3.7
   - Chapter 4: 4.1, 4.6 to 4.8
   - Chapter 5: 5.1 to 5.5
   - Chapter 6: 6.1 to 6.4, 6.8 to 6.12


### Week 2: Word Embeddings (No Class)
**Required Reading:**
- [Rodriguez & Spirling (2022). Word Embeddings: What Works, What Doesn't, and How to Tell the Difference for Applied Research](https://www.journals.uchicago.edu/doi/full/10.1086/715162)
- [Kutuzov et al. (2018). Diachronic word embeddings and semantic shifts: a survey](https://arxiv.org/abs/1806.03537)
- [Hofmann et al. (2021). Dynamic Contextualized Word Embeddings](https://arxiv.org/abs/2010.12684)

**Optional Reading:**
- [Hamilton et al. (2018). Diachronic Word Embeddings Reveal Statistical Laws](https://arxiv.org/abs/1605.09096)
- [Yao et al. (2018). Dynamic Word Embeddings for Evolving Semantic Discovery](https://arxiv.org/abs/1703.00607)
- [Charlesworth et al. (2022). Historical representations of social groups](https://www.pnas.org/doi/10.1073/pnas.2121798119)


### Week 3: Neural Networks & Transformers
**Required Reading:**
- Textbook: [Jurafsky & Martin (2025). Speech and Language Processing](https://web.stanford.edu/~jurafsky/slp3/)
   - Chapters 7 to 9
- [Alammar (2018). The Illustrated Transformer](http://jalammar.github.io/illustrated-transformer/)
- [Rush (2018). The Annotated Transformer](https://nlp.seas.harvard.edu/2018/04/03/attention.html)

**Highly Recommended Videos:**
- [StatQuest: Neural Networks](https://www.youtube.com/playlist?list=PLblh5JKOoLUIxGDQs4LFFD--41Vzf-ME1)
- [3Blue1Brown: Neural Networks](https://youtube.com/playlist?list=PLZHQObOWTQDNU6R1_67000Dx_ZCJB-3pi&si=99t8gHU7x_4_0lxm)
- [Serrano.Academy: The Attention Mechanism in Large Language Models](https://www.youtube.com/watch?v=OxCpWwDCDFQ&t=0s)

**Recommended Videos:**
- [Transformer explanation](https://www.youtube.com/watch?v=bCz4OMemCcA&list=PLqS2w6oyI17endIeNur8KQxw2zz1Qy_af&index=19)
- [AI Coffee Break: Deepdive into transformers](https://www.youtube.com/watch?v=BprirYymXrg&list=PLqS2w6oyI17endIeNur8KQxw2zz1Qy_af&index=16)
- [Neel Nanda: What is a Transformer](https://www.youtube.com/watch?v=BprirYymXrg&list=PLqS2w6oyI17endIeNur8KQxw2zz1Qy_af&index=16)

**Optional Reading:**
- [Devlin et al. (2019). BERT: Pre-training of Deep Bidirectional Transformers](https://arxiv.org/abs/1810.04805)
- [Vaswani et al. (2017). Attention Is All You Need](https://arxiv.org/abs/1706.03762)


### Week 4: Mechanistic Interpretability Week I
**Required Reading:**
- [Park et al. (2024). The Linear Representation Hypothesis and  the Geometry of Large Language Models](https://arxiv.org/abs/2311.03658)
- [Engels et al. (2024). Not All Language Model Features Are Linear](http://arxiv.org/abs/2405.14860)
- [Tennenholtz et al. (2024). Demystifying Embedding Spaces using Large Language Models](https://arxiv.org/abs/2310.04475)
- [Luo et al. (2024). PaCE: Parsimonious Concept Engineering for Large Language Models](http://arxiv.org/abs/2406.04331)


### Week 5: Mechanistic Interpretability Week II
**Required Reading:**
- [Park et al. (2024). The Geometry of Categorical and Hierarchical Concepts in Large Language Models](https://arxiv.org/abs/2406.01506)
- [Ahuja et al. (2024). Learning Syntax Without Planting Trees: Understanding When and Why  Transformers Generalize Hierarchically](https://openreview.net/forum?id=YwLgSimUIT)
- [Valios et al. (2024). Frame Representation Hypothesis: Multi-Token LLM Interpretability and Concept-Guided Text Generation](http://arxiv.org/abs/2412.07334)
- [Rajendran et al. (2024). Learning Interpretable Concepts: Unifying Causal Representation Learning and Foundation Models](http://arxiv.org/abs/2402.09236)

**Optional Reading:**
- [Jiang et al. (2024). On the Origins of Linear Representations in Large Language Models](http://arxiv.org/abs/2403.03867)
- [Karvonen et al. (2024). Evaluating Sparse Autoencoders](https://arxiv.org/abs/2411.18895)
- [Lieberum et al. (2024). Gemma Scope: Open Sparse Autoencoders](https://arxiv.org/abs/2408.05147)
- [Csordas et al. (2024). Recurrent Neural Networks Learn to Store and Generate Sequences using Non-Linear Representations](http://arxiv.org/abs/2408.10920)
- [Huben et al. (2023). Sparse Autoencoders Find Highly Interpretable Features in Language Models](https://openreview.net/forum?id=F76bwRSLeK)

### Week 6: Modern Topic Modeling
**Required Reading:**
- [Hoyle et al. (2022). Are Neural Topic Models Broken?](https://arxiv.org/abs/2210.16162)
- [We et al. (2024). FASTopic: Pretrained Transformer is a Fast, Adaptive, Stable, and Transferable Topic Model](http://arxiv.org/abs/2405.17978)
- [Pham et al. (2024). TopicGPT: A Prompt-based Topic Modeling Framework](https://arxiv.org/abs/2311.01449)

**Optional Reading:**
- [Hastings & Pesando (2024). What's a parent to do?](https://www.sciencedirect.com/science/article/pii/S0049089X24000966)
- [Egger & Yu (2022). A Topic Modeling Comparison Between LDA, NMF, Top2Vec, and BERTopic to Demystify Twitter Posts](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC9120935/)

### Week 7: Qualitative Coding with LLMs I 
**Required Reading:**
- [Zhang et al. (2024). When Qualitative Research Meets Large Language Model: Exploring the Potential of QualiGPT as a Tool for Qualitative Coding](http://arxiv.org/abs/2407.14925)
- [Eschrich & Sterman (2024). A Framework For Discussing LLMs as Tools for Qualitative Analysis](https://arxiv.org/abs/2407.11198)
- [Pangakis et al. (2023). Automated Annotation with Generative AI Requires Validation](https://arxiv.org/abs/2306.00176)

**Optional Reading:**
- [Chew et al. (2023). LLM-Assisted Content Analysis](https://arxiv.org/abs/2306.14924)


### Week 8: Qualitative Coding with LLMs II
**Required Reading:**
- [Rasheed et al. (2024). Can Large Language Models Serve as Data Analysts? A Multi-Agent Assisted Approach for Qualitative Data Analysis](http://arxiv.org/abs/2402.01386)
- [Dunivin (2024). Scalable Qualitative Coding with LLMs: Chain-of-Thought Reasoning Matches Human Performance in Some Hermeneutic Tasks](http://arxiv.org/abs/2401.15170)
- [Arlinghaus et al. (2024). Inductive Coding with ChatGPT - An Evaluation of Different GPT Models  Clustering Qualitative Data into Categories](https://osf.io/gpnye)

**Optional Reading:**
- [De Paoli (2024). Further Explorations on the Use of Large Language Models for Thematic Analysis. Open-Ended Prompts, Better Terminologies and Thematic Maps](https://www.qualitative-research.net/index.php/fqs/article/view/4196)


### Week 9: Error Analysis and Validation
**Required Reading:**
- [Pangakis et al. (2023). Automated Annotation with Generative AI Requires Validation](http://arxiv.org/abs/2306.00176)
- [Ludwig et al. (2024). Large Language Models: An Applied Econometric Framework](https://arxiv.org/abs/2412.07031)
- [Carlson et al. (2024). The Use of LLMs to Annotate Data in Management Research: Warnings, Guidelines, and an Application to Organizational Communication](https://papers.ssrn.com/abstract=4836620)

**Optional Reading:**
- [Barrie et al. (2024). Replication for Large Language Models](https://arthurspirling.org/documents/BarriePalmerSpirling_TrustMeBro.pdf)
- [Thalken et al. (2023). Modeling Legal Reasoning: LM Annotation at the Edge of Human Agreement](https://arxiv.org/abs/2310.18440)
- [Egami et al. (2024). Using Imperfect Surrogates for Downstream Inference](https://arxiv.org/abs/2306.04746)


### Week 10: Concept Tracing I
**Required Reading:**
- [Nascimento et al. (2022). Concept Detection in Philosophical Corpora](https://www.digitalstudies.org/article/id/8106/)
- [Li (2024). Tracing the Genealogies of Ideas with Large Language Model Embeddings](https://arxiv.org/abs/2402.01661)

- [Ganguli et al. (2024). Mapping Inventions in the Space of Ideas, 1836–2022:  Representation, Measurement, and Validation](https://congress-files.s3.amazonaws.com/2024-07/Innovation_similarity%2520%25281%2529-compressed.pdf?VersionId=Kv5xhUL2ZVVFYG6zh.JnVVouAP4RIV8B)

**Optional Reading:**
- [Vicinanza et al. (2022). Deep-learning model of prescient ideas demonstrates that they emerge from the periphery](https://academic.oup.com/pnasnexus/article/2/1/pgac275/6874776)
- [Lucy et al. (2023). Words as Gatekeepers](https://arxiv.org/abs/2212.09676)
- [Rosin et al. (2022). Time Masking for Temporal Language Models](https://doi.org/10.1145/3488560.3498529)



### Week 11: Concept Tracing II
**Required Reading:**
- [Garg & Fetzer (2025). Causal Claims in Economics](https://arxiv.org/abs/2501.06873)
- [Cong et al. (2024). Textual Factors: A Scalable, Interpretable, and Data-driven Approach to Analyzing Unstructured Information](https://www.nber.org/papers/w33168)
- [Lam et al. (2024). Concept Induction: Analyzing Unstructured Text with High-Level Concepts Using LLooM](https://dl.acm.org/doi/10.1145/3613904.3642830)


### Week 12-14: To Be Determined

<!-- ## Course Policies
[Standard policies about attendance, late work, academic integrity, etc. to be added] -->

<!-- ## Technical Support
Instructions for getting help with technical issues, office hours information, etc. -->

