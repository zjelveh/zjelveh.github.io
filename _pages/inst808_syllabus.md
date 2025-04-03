---
toc: true
layout: splash
author_profile: false
title: "Syllabus for INST 798/808: A.I.-Powered Research Assistants"
collection: teaching
permalink: /teaching/inst_808_syllabus
classes: wide
---

# INST 798/808: A.I.-Powered Research Assistants
**Location + Time:** [TWS 0207](https://25live.collegenet.com/pro/umd#!/home/location/2426/details), Thursdays 2 to 4.45p.m. 

## Course Description
This course explores how Large Language Models (LLMs) can transform labor-intensive research tasks in the social sciences. Using the challenge of tracing ideas and concepts through text as our primary lens, we examine how these powerful tools can aid both qualitative and quantitative research methodologies. Measuring the evolution of ideas through text presents uniquely complex challenges - concepts may be expressed through varied language, their meaning often shifts over time, and understanding them requires deep contextual knowledge that has traditionally relied heavily on human expertise.

The course begins by examining traditional approaches to concept measurement, from word embeddings to early neural architectures, before exploring how transformer-based models have revolutionized our ability to detect and track complex ideas in text. We then delve into recent advances in mechanistic interpretability to understand how these models internally represent and manipulate concepts. This foundation allows us to evaluate various approaches to concept tracing, from using LLMs to scale up qualitative research methods to exploring how modern neural topic modeling can capture evolving ideas across large corpora.

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
[Slides](/files/Lecture_1__Intro.pptx) | [Lab Notebook](/files/inst_808__Lab_1__ngram_lm.ipynb) | [Solutions](/files/inst_808__Lab_1__ngram_lm_sol.html)


**Required Reading:**
- Textbook: [Jurafsky & Martin (2025). Speech and Language Processing](https://web.stanford.edu/~jurafsky/slp3/)
   - Chapter 3: 3.1 to 3.3, 3.7
   - Chapter 4: 4.1, 4.6 to 4.8

**Highly Recommended Video:**
- [3Blue1Brown: Essence of Linear Algebra Course](https://www.youtube.com/playlist?list=PLZHQObOWTQDPD3MizzM2xVFitgF8hE_ab)

**Recommended Video:**
- [Jason Wei: Scaling Paradigms for Large Language Models](https://youtu.be/yhpjpNXJDco?si=4SUMHKS0oWs7f08P)

---

### Week 2: Word Embeddings (No Class)

**Required Reading:**
- [Hofmann et al. (2021). Dynamic Contextualized Word Embeddings](https://arxiv.org/abs/2010.12684)
- [Kutuzov et al. (2018). Diachronic word embeddings and semantic shifts: a survey](https://arxiv.org/abs/1806.03537)
- [Rodriguez & Spirling (2022). Word Embeddings: What Works, What Doesn't, and How to Tell the Difference for Applied Research](https://www.journals.uchicago.edu/doi/full/10.1086/715162)

**Optional Reading:**
- [Charlesworth et al. (2022). Historical representations of social groups](https://www.pnas.org/doi/10.1073/pnas.2121798119)
- [Hamilton et al. (2018). Diachronic Word Embeddings Reveal Statistical Laws](https://arxiv.org/abs/1605.09096)
- [Yao et al. (2018). Dynamic Word Embeddings for Evolving Semantic Discovery](https://arxiv.org/abs/1703.00607)

---

### Week 3: Neural Networks 

**Required Reading:**
- Textbook: [Jurafsky & Martin (2025). Speech and Language Processing](https://web.stanford.edu/~jurafsky/slp3/)
   - Chapter 5: 5.1 to 5.5
   - Chapter 6: 6.1 to 6.4, 6.8 to 6.12   
   - Chapters 7 

**Highly Recommended Videos:**
- [3Blue1Brown: Neural Networks](https://youtube.com/playlist?list=PLZHQObOWTQDNU6R1_67000Dx_ZCJB-3pi&si=99t8gHU7x_4_0lxm)
- [StatQuest: Neural Networks](https://www.youtube.com/playlist?list=PLblh5JKOoLUIxGDQs4LFFD--41Vzf-ME1)
- [ritvikmath: Word2Vec](https://www.youtube.com/watch?v=f7o8aDNxf7k&list=PLvcbYUQ5t0UH2MS_B6maLNJhK0jNyPJUY&index=25)

---

### Week 4: RNNS and Attention
[Slides](/files/Lecture_2__NN.pptx) | [Lab Notebook](/files/inst_808__Lab_2__word2vec.ipynb) | [Solutions](/files/inst_808__Lab_2__word2vec_sol.html)


**Required Reading:**
- Textbook: [Jurafsky & Martin (2025). Speech and Language Processing](https://web.stanford.edu/~jurafsky/slp3/)
   - Chapter 8: 8-8.2.1, 8.3, 8.7 (not 8.7.1), 8.8
   - Chapter 9

**Highly Recommended Videos:**
- [ritvikmath: Recurrent Neural Networks](https://www.youtube.com/watch?v=DFZ1UA7-fxY)
- [3Blue1Brown: Neural Networks - Chapters 5 and 6](https://youtube.com/playlist?list=PLZHQObOWTQDNU6R1_67000Dx_ZCJB-3pi&si=99t8gHU7x_4_0lxm)

**Recommended Videos:**
- [Serrano.Academy: The Attention Mechanism in Large Language Models](https://www.youtube.com/watch?v=OxCpWwDCDFQ&t=0s)
- [Transformer explanation](https://youtu.be/bCz4OMemCcA?si=X3Nh7XiN0Grp74W2)
- [Neel Nanda: What is a Transformer](https://youtu.be/bOYE6E8JrtU?si=dQYy04RmvWriP7Go)

**Optional Reading:**
- [Devlin et al. (2019). BERT: Pre-training of Deep Bidirectional Transformers](https://arxiv.org/abs/1810.04805)
- [Vaswani et al. (2017). Attention Is All You Need](https://arxiv.org/abs/1706.03762)

---

### Week 5: Transformers and Sentence Embeddings
[Slides](/files/Lecture_3__Transformers.pptx) | [Lab Notebook](/files/inst_808__Lab_3__sentence_embeddings.ipynb)


**Required Reading:**
- Textbook: [Jurafsky & Martin (2025). Speech and Language Processing](https://web.stanford.edu/~jurafsky/slp3/)
   - Chapter 11: 11.1 to 11.4
- [Alammar (2018). The Illustrated Transformer](http://jalammar.github.io/illustrated-transformer/)
- [Rush (2018). The Annotated Transformer](https://nlp.seas.harvard.edu/2018/04/03/attention.html)

**Highly Recommended Videos:**
- [AI Coffee Break: Deepdive into transformers](https://youtu.be/BprirYymXrg?si=EtnhWt3ntZZHQAZ3)

**Optional Reading:**
- [Devlin et al. (2019). BERT: Pre-training of Deep Bidirectional Transformers for Language Understanding](https://arxiv.org/abs/1810.04805)
- [Blog Post: Foundation Models, Transformers, BERT and GPT](https://heidloff.net/article/foundation-models-transformers-bert-and-gpt/)

---

### Week 6: Mechanistic Interpretability

**Required Reading:**
- [Bricken et al. (2023). Towards Monosemanticity: Decomposing Language Models With Dictionary Learning](https://transformer-circuits.pub/2023/monosemantic-features/index.html)
- [Tennenholtz et al. (2024). Demystifying Embedding Spaces using Large Language Models](https://arxiv.org/abs/2310.04475)


**Optional Reading:**
- [Ahuja et al. (2024). Learning Syntax Without Planting Trees: Understanding When and Why  Transformers Generalize Hierarchically](https://openreview.net/forum?id=YwLgSimUIT)
- [Csordas et al. (2024). Recurrent Neural Networks Learn to Store and Generate Sequences using Non-Linear Representations](http://arxiv.org/abs/2408.10920)
- [Engels et al. (2024). Not All Language Model Features Are Linear](http://arxiv.org/abs/2405.14860)
- [Huben et al. (2023). Sparse Autoencoders Find Highly Interpretable Features in Language Models](https://openreview.net/forum?id=F76bwRSLeK)
- [Jiang et al. (2024). On the Origins of Linear Representations in Large Language Models](http://arxiv.org/abs/2403.03867)
- [Karvonen et al. (2024). Evaluating Sparse Autoencoders](https://arxiv.org/abs/2411.18895)
- [Lieberum et al. (2024). Gemma Scope: Open Sparse Autoencoders](https://arxiv.org/abs/2408.05147)
- [Luo et al. (2024). PaCE: Parsimonious Concept Engineering for Large Language Models](http://arxiv.org/abs/2406.04331)
- [Park et al. (2024). The Linear Representation Hypothesis and  the Geometry of Large Language Models](https://arxiv.org/abs/2311.03658)
- [Park et al. (2024). The Geometry of Categorical and Hierarchical Concepts in Large Language Models](https://arxiv.org/abs/2406.01506)
- [Rajendran et al. (2024). Learning Interpretable Concepts: Unifying Causal Representation Learning and Foundation Models](http://arxiv.org/abs/2402.09236)
- [Valios et al. (2024). Frame Representation Hypothesis: Multi-Token LLM Interpretability and Concept-Guided Text Generation](http://arxiv.org/abs/2412.07334)

---

### Week 7: Qualitative Coding with LLMs I 
[Slides](/files/Lecture_4__QualCoding.pptx) (Includes Final Project guidelines)

**Required Reading:**
- Textbook: [Jurafsky & Martin (2025). Speech and Language Processing](https://web.stanford.edu/~jurafsky/slp3/)
   - Chapter 12
- [Lam et al. (2024). Concept Induction: Analyzing Unstructured Text with High-Level Concepts Using LLooM](https://dl.acm.org/doi/abs/10.1145/3613904.3642830)
- [Schroeder et al. (2025). Large Language Models in Qualitative Research:
Uses, Tensions, and Intentions](https://arxiv.org/pdf/2410.07362)
- [Zhang et al. (2024). When Qualitative Research Meets Large Language Model: Exploring the Potential of QualiGPT as a Tool for Qualitative Coding](http://arxiv.org/abs/2407.14925)

**Optional Reading:**
- [Chew et al. (2023). LLM-Assisted Content Analysis](https://arxiv.org/abs/2306.14924)
- [Dai et al. (2023). LLM-in-the-loop: Leveraging Large Language Model for Thematic Analysis](https://arxiv.org/abs/2310.15100)
- [Eschrich & Sterman (2024). A Framework For Discussing LLMs as Tools for Qualitative Analysis](https://arxiv.org/abs/2407.11198)
- [Raza et al. (2025). LLM-TA: An LLM-Enhanced Thematic Analysis Pipeline for Transcripts from
Parents of Children with Congenital Heart Disease](https://arxiv.org/pdf/2502.01620)

---

### Week 8: Qualitative Coding with LLMs II
[Lab Notebook - Qualitative Coding with APIs](/files/Lab__qualcode.ipynb) | [Lab Notebook - Analyze Results](/files/Lab__qualcode_analyze.ipynb)

**Required Reading:**
- [Dunivin (2024). Scalable Qualitative Coding with LLMs: Chain-of-Thought Reasoning Matches Human Performance in Some Hermeneutic Tasks](http://arxiv.org/abs/2401.15170)
- [Rasheed et al. (2024). Can Large Language Models Serve as Data Analysts? A Multi-Agent Assisted Approach for Qualitative Data Analysis](http://arxiv.org/abs/2402.01386)
- [Relin et al. (2024). Using Instruction-Tuned Large Language Models to Identify Indicators of Vulnerability in Police Incident Narratives](https://www.crimrxiv.com/pub/vomgw766/release/1)

**Optional Reading:**
- [De Paoli (2024). Further Explorations on the Use of Large Language Models for Thematic Analysis. Open-Ended Prompts, Better Terminologies and Thematic Maps](https://www.qualitative-research.net/index.php/fqs/article/view/4196)
- [Gao et al. (2025). Using Large Language Model to Support Flexible and Structural
Inductive Qualitative Analysis](https://arxiv.org/pdf/2501.00775)   
- [Overney et al. (2025). SenseMate: An Accessible and Beginner-Friendly Human-AI
Platform for Qualitative Data Analysis](https://dl.acm.org/doi/pdf/10.1145/3640543.3645194)

---
### Week 9: Modern Topic Modeling
Lab Notebooks:
  - [Generate Synthetic Abstracts](/files/gt/1_compare_llms.ipynb)
  - [Analyze Abstracts](/files/gt/2_analyze_abstracts.ipynb)
  - [Deductive Coding of Abstracts](/files/gt/3_deductive_coding.ipynb)
  - [Evaluate Deduction](/files/gt/4_evaluate_deduction.ipynb)
  
**Required Reading:**
- [Hoyle et al. (2022). Are Neural Topic Models Broken?](https://arxiv.org/abs/2210.16162)
- [Pham et al. (2024). TopicGPT: A Prompt-based Topic Modeling Framework](https://arxiv.org/abs/2311.01449)
- [We et al. (2024). FASTopic: Pretrained Transformer is a Fast, Adaptive, Stable, and Transferable Topic Model](http://arxiv.org/abs/2405.17978)

**Optional Reading:**
- [Egger & Yu (2022). A Topic Modeling Comparison Between LDA, NMF, Top2Vec, and BERTopic to Demystify Twitter Posts](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC9120935/)
- [Hastings & Pesando (2024). What's a parent to do?](https://www.sciencedirect.com/science/article/pii/S0049089X24000966)

---
### Week 10: Error Analysis and Validation

**Required Reading:**
- [Carlson et al. (2024). The Use of LLMs to Annotate Data in Management Research: Warnings, Guidelines, and an Application to Organizational Communication](https://papers.ssrn.com/abstract=4836620)
- [Ludwig et al. (2024). Large Language Models: An Applied Econometric Framework](https://arxiv.org/abs/2412.07031)
- [Barrie et al. (2024). Replication for Large Language Models](https://arthurspirling.org/documents/BarriePalmerSpirling_TrustMeBro.pdf)

**Optional Reading:**
- [Pangakis et al. (2023). Automated Annotation with Generative AI Requires Validation](http://arxiv.org/abs/2306.00176)
- [Egami et al. (2024). Using Imperfect Surrogates for Downstream Inference](https://arxiv.org/abs/2306.04746)
- [Thalken et al. (2023). Modeling Legal Reasoning: LM Annotation at the Edge of Human Agreement](https://arxiv.org/abs/2310.18440)

---

### Week 11: Concept Tracing I

**Required Reading:**
- [Ganguli et al. (2024). Mapping Inventions in the Space of Ideas, 1836–2022:  Representation, Measurement, and Validation](https://congress-files.s3.amazonaws.com/2024-07/Innovation_similarity%2520%25281%2529-compressed.pdf?VersionId=Kv5xhUL2ZVVFYG6zh.JnVVouAP4RIV8B)
- [Li (2024). Tracing the Genealogies of Ideas with Large Language Model Embeddings](https://arxiv.org/abs/2402.01661)

- [Nascimento et al. (2022). Concept Detection in Philosophical Corpora](https://www.digitalstudies.org/article/id/8106/)

**Optional Reading:**
- [Lucy et al. (2023). Words as Gatekeepers](https://arxiv.org/abs/2212.09676)
- [Rosin et al. (2022). Time Masking for Temporal Language Models](https://doi.org/10.1145/3488560.3498529)
- [Vicinanza et al. (2022). Deep-learning model of prescient ideas demonstrates that they emerge from the periphery](https://academic.oup.com/pnasnexus/article/2/1/pgac275/6874776)

---

### Week 12: Concept Tracing II

**Required Reading:**
- [Cong et al. (2024). Textual Factors: A Scalable, Interpretable, and Data-driven Approach to Analyzing Unstructured Information](https://www.nber.org/papers/w33168)
- [Garg & Fetzer (2025). Causal Claims in Economics](https://arxiv.org/abs/2501.06873)
- [Lam et al. (2024). Concept Induction: Analyzing Unstructured Text with High-Level Concepts Using LLooM](https://dl.acm.org/doi/10.1145/3613904.3642830)

---

### Week 13-14: To Be Determined

