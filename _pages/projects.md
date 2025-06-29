-- ---
layout: archive
title: "Projects"
permalink: /projects/
author_profile: true
redirect_from:
  - /projects
---

{% include base_path %}

### [Analyzing Fine-tuning Representation Shift for Multimodal LLMs Steering alignment](https://arxiv.org/pdf/2501.03012)
  
[Code](https://github.com/mshukor/xl-vlms.git),

Multimodal LLMs have reached remarkable levels of proficiency in understanding multimodal inputs, driving extensive research to develop increasingly powerful models. However, much less attention has been paid to understanding and explaining the underlying mechanisms of these models. Most existing explainability research examines these models only in their final states, overlooking the dynamic representational shifts that occur during training. In this work, we systematically analyze the evolution of hidden state representations to reveal how fine-tuning alters the internal structure of a model to specialize in new multimodal tasks. Using a concept-based approach, we map hidden states to interpretable visual and textual concepts, enabling us to trace changes in encoded concepts across modalities as training progresses. We also demonstrate the use of shift vectors to capture these concepts changes. These shift vectors allow us to recover fine-tuned concepts by shifting those in the original model. Finally, we explore the practical impact of our findings on model steering, showing that we can adjust multimodal LLMs behaviors without any training, such as modifying answer types, captions style, or biasing the model toward specific responses. Our work sheds light on how multimodal representations evolve through fine-tuning and offers a new perspective for interpreting model adaptation in multimodal tasks.

![Codebook Image](../images/analyze_shift.png)


### [A Concept-Based Explainability Framework for Large Multimodal Models](https://arxiv.org/abs/2406.08074)
  
[Code](https://github.com/mshukor/xl-vlms.git),

Large multimodal models (LMMs) combine unimodal encoders and large language models (LLMs) to perform multimodal tasks. Despite recent advancements towards the interpretability of these models, understanding internal representations of LMMs remains largely a mystery. In this paper, we present a novel framework for the interpretation of LMMs. We propose a dictionary learning based approach, applied to the representation of tokens. The elements of the learned dictionary correspond to our proposed concepts. We show that these concepts are well semantically grounded in both vision and text. Thus we refer to these as "multi-modal concepts". We qualitatively and quantitatively evaluate the results of the learnt concepts. We show that the extracted multimodal concepts are useful to interpret representations of test samples. Finally, we evaluate the disentanglement between different concepts and the quality of grounding concepts visually and textually.

![Codebook Image](../images/CoX_LMM_system.png)



### [Adversarial corner case generation for motion planning](https://github.com/pegah-kh/kinematic_adversary_agents/blob/main/report.pdf)
  
[Code](https://github.com/pegah-kh/kinematic_adversary_agents),
[Report](https://github.com/pegah-kh/kinematic_adversary_agents/blob/main/report.pdf)

We attempted to develop a framework to stress-test vehicle planners by generating safety-critical driving scenarios. Recognizing that real-world scenarios are rare and costly, we used a realistic simulator, [nuPlan](https://www.nuscenes.org/nuplan) to create scenarios aimed at exposing potential collision risks. Building on the method introduced by [Han et al., 2022](https://arxiv.org/abs/2204.13683), we adapted it to a more complex environment with a wider range of agents and behaviors.

![Codebook Image](../images/induced_collisions.png)




### [Simplified Velocity Skinning](https://github.com/pegah-kh/Simple-Velocity-Skinning)
  
[Code](https://github.com/pegah-kh/Simple-Velocity-Skinning),
[Report](https://github.com/pegah-kh/Simple-Velocity-Skinning/tree/master/report_and_demonstration)

This was a course project that I truly enjoyed. It's about making animation looking more realistic and loose, by adding exagerated deformation triggered by skeletal velocity on top of standard skinning animation.
The code uses a [CGP library](https://github.com/drohmer/CGP) developped by the professor of the course, and is a simplification of the work done in one of his papers, [Velocity Skinning](https://velocityskinning.com/).

![Alt Text](../images//ezgif.com-gif-maker.gif)


### [Landmark Localization for a Fashion Dataset: A PIFPAF Plugin](https://github.com/pegah-kh/pifpaf_deepfashion)
  
[Code](https://github.com/pegah-kh/pifpaf_deepfashion)

This is a simple plugin of [OpenPifPaf](https://openpifpaf.github.io/intro.html) for detecting landmarks (main points of interest such as the end of sleeves in a shirt ...) in various clothing items.


<img src="../images/clothing_landmark.gif" alt="Alt Text" width="250">

