---
layout: archive
title: "Projects"
permalink: /projects/
author_profile: true
redirect_from:
  - /projects
---

{% include base_path %}

<style>
.projects-list {
  display: flex;
  flex-direction: column;
  gap: 20px;
  margin-top: 1.5rem;
}

.proj-card {
  display: flex;
  gap: 24px;
  align-items: flex-start;
  background: #ffffff;
  border-radius: 12px;
  border: 1px solid #e0e0e0;
  padding: 20px;
  box-shadow: 0 1px 4px rgba(0,0,0,0.05);
}

.proj-img {
  width: 210px;
  min-width: 210px;
  height: 140px;
  border-radius: 8px;
  overflow: hidden;
  background: #f4f4f4;
  border: 1px solid #e0e0e0;
  display: flex;
  align-items: center;
  justify-content: center;
}

.proj-img img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  display: block;
}

.proj-body {
  flex: 1;
  min-width: 0;
}

.proj-title {
  font-size: 16px;
  font-weight: 600;
  color: #1a1a1a;
  margin: 0 0 6px 0;
  line-height: 1.4;
}

.proj-authors {
  font-size: 13.5px;
  color: #555;
  font-style: italic;
  margin: 0 0 10px 0;
  line-height: 1.5;
}

.proj-desc {
  font-size: 13.5px;
  color: #444;
  margin: 0 0 14px 0;
  line-height: 1.65;
}

.proj-links {
  display: flex;
  gap: 8px;
  flex-wrap: wrap;
}

.proj-btn {
  font-size: 13px;
  font-weight: 500;
  padding: 7px 18px;
  border-radius: 6px;
  background: #5a9e8f;
  color: #ffffff !important;
  border: none;
  cursor: pointer;
  text-decoration: none !important;
  display: inline-block;
  transition: background 0.15s ease;
}

.proj-btn:hover {
  background: #4a8a7c;
  text-decoration: none !important;
}

@media (max-width: 640px) {
  .proj-card {
    flex-direction: column;
  }
  .proj-img {
    width: 100%;
    min-width: unset;
    height: 180px;
  }
}
</style>

<div class="projects-list">

  <div class="proj-card">
    <div class="proj-img">
      <img src="../images/analyze_shift.png" alt="Fine-tuning representation shift diagram">
    </div>
    <div class="proj-body">
      <p class="proj-title">Analyzing Fine-tuning Representation Shift for Multimodal LLMs Steering alignment</p>
      <p class="proj-authors">Pegah Khayatan, Mustafa Shukor, Jayneel Parekh, Arnaud Dapogny, Matthieu Cord · ICCV 2025</p>
      <p class="proj-desc">We systematically analyze the evolution of hidden state representations to reveal how fine-tuning alters the internal structure of a model to specialize in new multimodal tasks. Using concept-based shift vectors, we can recover fine-tuned concepts and steer model behaviors without any training.</p>
      <div class="proj-links">
        <a class="proj-btn" href="https://arxiv.org/pdf/2501.03012" target="_blank">Paper</a>
        <a class="proj-btn" href="https://github.com/mshukor/xl-vlms" target="_blank">Code</a>
      </div>
    </div>
  </div>

  <div class="proj-card">
    <div class="proj-img">
      <img src="../images/CoX_LMM_system.png" alt="Concept-based explainability framework diagram">
    </div>
    <div class="proj-body">
      <p class="proj-title">A Concept-Based Explainability Framework for Large Multimodal Models</p>
      <p class="proj-authors">Jayneel Parekh, Pegah Khayatan, Mustafa Shukor, Alasdair Newson, Matthieu Cord · NeurIPS 2024</p>
      <p class="proj-desc">A novel framework for interpreting large multimodal models using dictionary learning applied to token representations. The learned dictionary elements correspond to well-grounded multimodal concepts, evaluated for disentanglement and visual-textual grounding quality.</p>
      <div class="proj-links">
        <a class="proj-btn" href="https://arxiv.org/abs/2406.08074" target="_blank">Paper</a>
        <a class="proj-btn" href="https://github.com/mshukor/xl-vlms" target="_blank">Code</a>
      </div>
    </div>
  </div>

  <div class="proj-card">
    <div class="proj-img">
      <img src="../images/induced_collisions.png" alt="Adversarial driving scenario">
    </div>
    <div class="proj-body">
      <p class="proj-title">Adversarial Corner Case Generation for Motion Planning</p>
      <p class="proj-authors">Pegah Khayatan, et al.</p>
      <p class="proj-desc">A framework to stress-test vehicle planners by generating safety-critical driving scenarios using the nuPlan simulator, exposing potential collision risks. Adapted from Han et al. 2022 to support a wider range of agents and behaviors.</p>
      <div class="proj-links">
        <a class="proj-btn" href="https://github.com/pegah-kh/kinematic_adversary_agents/blob/main/report.pdf" target="_blank">Report</a>
        <a class="proj-btn" href="https://github.com/pegah-kh/kinematic_adversary_agents" target="_blank">Code</a>
      </div>
    </div>
  </div>

  <div class="proj-card">
    <div class="proj-img">
      <img src="../images/ezgif.com-gif-maker.gif" alt="Velocity skinning animation demo">
    </div>
    <div class="proj-body">
      <p class="proj-title">Simplified Velocity Skinning</p>
      <p class="proj-authors">Pegah Khayatan</p>
      <p class="proj-desc">A course project making animations more realistic by adding exaggerated deformation triggered by skeletal velocity on top of standard skinning. Built using a CGP library and based on a simplification of the Velocity Skinning paper.</p>
      <div class="proj-links">
        <a class="proj-btn" href="https://github.com/pegah-kh/Simple-Velocity-Skinning" target="_blank">Code</a>
        <a class="proj-btn" href="https://github.com/pegah-kh/Simple-Velocity-Skinning/tree/master/report_and_demonstration" target="_blank">Report</a>
      </div>
    </div>
  </div>

  <div class="proj-card">
    <div class="proj-img">
      <img src="../images/clothing_landmark.gif" alt="Clothing landmark detection demo">
    </div>
    <div class="proj-body">
      <p class="proj-title">Landmark Localization for a Fashion Dataset: A PIFPAF Plugin</p>
      <p class="proj-authors">Pegah Khayatan</p>
      <p class="proj-desc">An OpenPifPaf plugin for detecting key landmarks — such as sleeve ends in shirts — across various clothing items in a fashion dataset.</p>
      <div class="proj-links">
        <a class="proj-btn" href="https://github.com/pegah-kh/pifpaf_deepfashion" target="_blank">Code</a>
      </div>
    </div>
  </div>

</div>