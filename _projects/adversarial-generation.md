---
title: Adversarial corner case generation for motion planning
date: 2024-06-15
links:
  - text: Code
    url: https://github.com/pegah-kh/kinematic_adversary_agents
  - text: Report
    url: https://github.com/pegah-kh/kinematic_adversary_agents/blob/main/report.pdf
image: /images/induced_collisions.png
---


We attempted to develop a framework to stress-test vehicle planners by generating safety-critical driving scenarios. Recognizing that real-world scenarios are rare and costly, we used a realistic simulator, [nuPlan](https://www.nuscenes.org/nuplan) to create scenarios aimed at exposing potential collision risks. Building on the method introduced by [Han et al., 2022](https://arxiv.org/abs/2204.13683), we adapted it to a more complex environment with a wider range of agents and behaviors.


