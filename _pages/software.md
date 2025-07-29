---
layout: archive
title: "Software"
permalink: /software/
author_profile: true
---

{% if author.googlescholar %}
  You can also find my articles on <u><a href="{{author.googlescholar}}">my Google Scholar profile</a>.</u>
{% endif %}

{% include base_path %}


## Record Linkage
- [Name Match](https://github.com/urban-labs/namematch) 
  - Python-based tool for probabilistically linking the records of individual entities (e.g. people) within and across datasets.
  - [End-to-end Tutorial](https://github.com/urban-labs/namematch/blob/main/examples/end_to_end_tutorial.ipynb)

## Causal Inference
- [staggeredpower](https://github.com/zjelveh/staggeredpower) 
  - R-package for conducting simulated power analysis with heterogeneity-robust estimators. 

- [SCMs](https://github.com/zjelveh/SCMs) 
  - R-package for conducting explainable specification curve analysis for Synthetic Controls with one treated unit. Allows for assessment of sensitivity to variation in matching variable construction, penalization, bias correction, etc.