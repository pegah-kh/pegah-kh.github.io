---
title: "Analyzing Fine-tuning Representation Shift for Multimodal LLMs Steering"
subtitle: "ICCV 2025"
layout: project
permalink: /projects/lmm-explainability/
authors:
  - name: Jayneel Parekh
    url: https://jayneelparekh.github.io/
  - name: Pegah Khayatan
    url: https://pegah-kh.github.io/
  - name: Mustafa Shukor
    url: https://geogroup.ai/author/mustafa-shukor/
  - name: Alasdair Newson
    url: https://sites.google.com/site/alasdairnewson/
  - name: Matthieu Cord
    url: https://cord.isir.upmc.fr/
affiliation: ISIR, Sorbonne Université, France
paper_url: https://arxiv.org/abs/2406.08074
code_url: https://github.com/mshukor/xl-vlms
---


<!-- ---
title: "A Concept-Based Explainability Framework for Large Multimodal Models for Large Multimodal Models"
layout: project
permalink: /projects/lmm-explainability/
authors: Jayneel Parekh, Pegah Khayatan, Mustafa Shukor, Alasdair Newson, Matthieu Cord
affiliation: ISIR, Sorbonne Université, France
paper_url: https://arxiv.org/abs/2406.08074
code_url: https://github.com/mshukor/xl-vlms
# method_image: /assets/images/lmm-method.png
--- -->

<!-- ---
title: "A Concept-Based Explainability Framework for Large Multimodal Models"
permalink: /projects/lmm-explainability/
layout: default
--- -->

<!-- <script type="text/javascript" src="https://www.maths.nottingham.ac.uk/plp/pmadw/LaTeXMathML.js"></script>
<script src="https://polyfill.io/v3/polyfill.min.js?features=es6"></script>
<script id="MathJax-script" async
        src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js"></script> -->


---

## Abstract

Multimodal LLMs (MLLMs) have reached remarkable levels of proficiency in understanding multimodal inputs. However, understanding and interpreting the behavior of such complex models is a challenging task, not to mention the dynamic shifts that may occur during fine-tuning, or due to covariate shift between datasets. In this work, we apply concept-level analysis towards MLLM understanding. More specifically, we propose to map hidden states to interpretable visual and textual concepts. This enables us to more efficiently compare certain semantic dynamics, such as the shift from an original and fine-tuned model, revealing concept alteration and potential biases that may occur during fine-tuning. We also demonstrate the use of shift vectors to capture these concepts changes. These shift vectors allow us to recover fine-tuned concepts by applying simple, computationally inexpensive additive concept shifts in the original model. Finally, our findings also have direct applications for MLLM steering, which can be used for model debiasing as well as enforcing safety in MLLM output. All in all, we propose a novel, training-free, ready-to-use framework for MLLM behavior interpretability and control. Code will be released publicly to facilitate reproducibility and future research.

---

## Method

<!-- ![System Figure](images/sys_fig_v4.jpg) -->

*Given a pretrained LMM for captioning and a target token (e.g., "Dog")...*

$\mathbf{Z} = [z_1,...,z_M] \in \mathbb{R}^{B \times M}$

...

---

## Multimodal Concept Grounding

Text: Top 5 words from $W_U u_k$  
Visual: Top activating samples $\mathbf{X}_{k, MAS}$

<!-- ![Grounding](images/grounding_2_v3.png) -->

---

## Experiments

We evaluate the framework using DePALM with ViT-L/14 + OPT-6.7B...

### Inference Analysis

<!-- ![Inference](images/inference_tab.png) -->

### Overlap Between Concepts

<!-- ![Overlap](images/overlap_tab.png) -->

---

## Qualitative Results

### Multimodal concept dictionaries (Dog, Cat)
<!-- 
![Dog Concepts](images/hey_dog.jpg)  
![Cat Concepts](images/hey_cat.jpg) -->

### Understanding test representations

<!-- ![Test Understanding](images/local_intp_fig_v2.jpg) -->

