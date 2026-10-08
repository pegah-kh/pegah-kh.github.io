---
title: "When Prompts Override Vision: Prompt-Induced Hallucinations in LVLMs "
subtitle: ""
layout: project
permalink: /projects/prompts-override-vision/
authors:
  - name: Pegah Khayatan
    url: https://pegah-kh.github.io/
  - name: Jayneel Parekh
    url: https://jayneelparekh.github.io/
  - name: Mustafa Shukor
    url: https://scholar.google.com/citations?hl=en&user=lhp9mRgAAAAJ&view_op=list_works&sortby=pubdate
  - name: Arnaud Dapogny
    url: https://scholar.google.fr/citations?user=2HDcyrUAAAAJ&hl=fr
  - name: Alasdair Newson
    url: https://sites.google.com/site/alasdairnewson/
  - name: Matthieu Cord
    url: https://cord.isir.upmc.fr/
affiliation: ISIR, Sorbonne Université, France
hero_image: /images/halluscope_logo.png
hero_alt: HalluScope logo
# paper_url: https://arxiv.org/abs/2406.08074
# code_url: https://github.com/mshukor/xl-vlms
---

<style>
  /* ---------- Scoped styles for this page only (prefix: po-) ---------- */
  .po {
    --scope: #2f6fdb;        /* HalluScope accent (blue)  */
    --scope-soft: #eaf1fd;
    --dpo: #1f9d6b;          /* HalluVL-DPO accent (green) */
    --dpo-soft: #e6f6ef;
    --warn: #c0392b;
    --ink: #1d2433;
    --muted: #5b6475;
    --line: #e3e7ee;
    --card: #ffffff;
    --bg-soft: #f6f8fb;
    color: var(--ink);
  }
  .po img { max-width: 100%; height: auto; }

  /* Buttons / link pills */
  .po-links { display: flex; flex-wrap: wrap; justify-content: center; gap: 10px; margin: 0.5em 0 2em; }
  .po-btn {
    display: inline-flex; align-items: center; gap: 6px;
    padding: 7px 16px; border-radius: 999px;
    background: var(--ink); color: #fff !important; text-decoration: none !important;
    font-size: 0.9rem; font-weight: 600; line-height: 1.2;
    transition: transform .15s ease, box-shadow .15s ease;
  }
  .po-btn:hover { transform: translateY(-1px); box-shadow: 0 4px 12px rgba(0,0,0,.15); }
  .po-btn.scope { background: var(--scope); }
  .po-btn.dpo   { background: var(--dpo); }
  .po-btn.soon  { background: #b9c0cc; pointer-events: none; }
  .po-btn small { font-weight: 400; opacity: .85; }

  /* TL;DR card */
  .po-tldr {
    background: linear-gradient(135deg, var(--scope-soft), var(--dpo-soft));
    border: 1px solid var(--line); border-radius: 16px;
    padding: 22px 26px; margin: 0 0 2.5em;
  }
  .po-tldr .po-kicker { margin-bottom: 6px; }
  .po-tldr p { margin: 0.4em 0; }

  .po-kicker {
    display: inline-block; font-size: 0.72rem; font-weight: 700; letter-spacing: .12em;
    text-transform: uppercase; color: var(--muted);
  }

  /* Two-step roadmap */
  .po-roadmap { display: grid; grid-template-columns: 1fr auto 1fr; gap: 14px; align-items: stretch; margin: 0 0 3em; }
  .po-step {
    display: block; text-decoration: none !important; color: inherit !important;
    background: var(--card); border: 1px solid var(--line); border-radius: 14px;
    padding: 18px 20px; border-top: 5px solid var(--scope);
    transition: transform .15s ease, box-shadow .15s ease;
  }
  .po-step:hover { transform: translateY(-2px); box-shadow: 0 8px 22px rgba(20,30,60,.08); }
  .po-step.dpo { border-top-color: var(--dpo); }
  .po-step h3 { margin: 4px 0 6px; font-size: 1.15rem; }
  .po-step p  { margin: 0; font-size: 0.92rem; color: var(--muted); line-height: 1.5; }
  .po-arrow { align-self: center; font-size: 1.8rem; color: #aab2c0; }
  @media (max-width: 640px) {
    .po-roadmap { grid-template-columns: 1fr; }
    .po-arrow { transform: rotate(90deg); justify-self: center; }
  }

  /* Part headers */
  .po-part { margin: 3.5em 0 1.2em; padding: 0 0 12px; border-bottom: 2px solid var(--line); }
  .po-part .po-tag {
    display: inline-block; padding: 3px 12px; border-radius: 999px;
    font-size: 0.75rem; font-weight: 700; letter-spacing: .08em; text-transform: uppercase;
    background: var(--scope-soft); color: var(--scope);
  }
  .po-part.dpo .po-tag { background: var(--dpo-soft); color: var(--dpo); }
  .po-part h2 { margin: 10px 0 2px; font-size: 1.7rem; display: flex; align-items: center; gap: 10px; border: 0; }
  .po-part h2 img { height: 42px; width: auto; }
  .po-part .po-q { margin: 0; color: var(--muted); font-style: italic; }

  /* "What we do" numbered list */
  .po-steps { counter-reset: s; list-style: none; padding: 0; margin: 1.2em 0 2em; }
  .po-steps li {
    counter-increment: s; position: relative; padding: 10px 14px 10px 52px; margin: 8px 0;
    background: var(--bg-soft); border-radius: 10px; line-height: 1.5;
  }
  .po-steps li::before {
    content: counter(s); position: absolute; left: 14px; top: 50%; transform: translateY(-50%);
    width: 26px; height: 26px; border-radius: 50%; display: grid; place-items: center;
    background: var(--scope); color: #fff; font-weight: 700; font-size: 0.85rem;
  }
  .po-steps.dpo li::before { background: var(--dpo); }

  /* Generic card grid */
  .po-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(200px, 1fr)); gap: 14px; margin: 1.2em 0 2em; }
  .po-card {
    background: var(--card); border: 1px solid var(--line); border-radius: 14px; padding: 18px;
    box-shadow: 0 1px 2px rgba(20,30,60,.04);
  }
  .po-card .po-emoji { font-size: 1.7rem; line-height: 1; }
  .po-card h4 { margin: 8px 0 4px; font-size: 1rem; }
  .po-card p  { margin: 0; font-size: 0.9rem; color: var(--muted); line-height: 1.5; }
  .po-card .po-stat { font-size: 1.5rem; font-weight: 800; color: var(--scope); margin: 6px 0 2px; }
  .po-card.hot { border-color: #f1c6c0; background: #fff7f6; }
  .po-card.hot .po-stat { color: var(--warn); }

  /* Figures */
  .po-fig { margin: 1.8em 0; text-align: center; }
  .po-fig img { border-radius: 10px; border: 1px solid var(--line); display: block; margin: 0 auto; }
  .po-fig figcaption { font-size: 0.88rem; color: var(--muted); margin-top: 8px; }

  /* Callout */
  .po-callout {
    border-left: 4px solid var(--scope); background: var(--scope-soft);
    padding: 14px 18px; border-radius: 0 10px 10px 0; margin: 1.5em 0;
  }
  .po-callout.dpo { border-left-color: var(--dpo); background: var(--dpo-soft); }

  /* Examples carousel */
  .po-carousel { position: relative; margin: 1.2em 0 2.5em; }
  .po-track {
    display: flex; overflow-x: auto; scroll-snap-type: x mandatory; scroll-behavior: smooth;
    gap: 16px; padding-bottom: 6px; scrollbar-width: thin;
  }
  .po-slide {
    flex: 0 0 100%; scroll-snap-align: center; margin: 0;
    background: var(--bg-soft); border: 1px solid var(--line); border-radius: 14px; padding: 14px;
  }
  .po-slide img { display: block; margin: 0 auto; border-radius: 8px; }
  .po-slide figcaption { font-size: 0.88rem; color: var(--muted); margin-top: 8px; text-align: center; }
  .po-nav { display: flex; justify-content: center; align-items: center; gap: 12px; margin-top: 10px; }
  .po-nav button {
    border: 1px solid var(--line); background: #fff; border-radius: 50%;
    width: 34px; height: 34px; cursor: pointer; font-size: 1rem; color: var(--ink);
  }
  .po-nav button:hover { background: var(--bg-soft); }
  .po-dots { display: flex; gap: 6px; }
  .po-dots span { width: 8px; height: 8px; border-radius: 50%; background: #cfd5df; cursor: pointer; }
  .po-dots span.on { background: var(--scope); }

  /* Legend chips for example types */
  .po-legend { display: flex; flex-wrap: wrap; gap: 8px; justify-content: center; margin: 0.6em 0 0; font-size: 0.82rem; }
  .po-chip { padding: 3px 10px; border-radius: 999px; font-weight: 600; }
  .po-chip.real { background: #e7f3e3; color: #3b7a2a; }
  .po-chip.rand { background: #fdf0e3; color: #b8651b; }
  .po-chip.adv  { background: #f8e4e4; color: #9e2a2a; }

  /* Dataset panel */
  .po-dataset {
    display: flex; flex-wrap: wrap; align-items: center; justify-content: space-between; gap: 12px;
    border: 1px dashed var(--scope); border-radius: 14px; padding: 16px 20px; margin: 1.5em 0 2em;
    background: var(--scope-soft);
  }
  .po-dataset.dpo { border-color: var(--dpo); background: var(--dpo-soft); }
  .po-dataset p { margin: 0; font-size: 0.92rem; }

  .po hr { border: 0; border-top: 1px solid var(--line); margin: 3em 0; }
</style>

<div class="po">

<!-- ================= Links ================= -->
<div class="po-links">
  <!-- <a class="po-btn" href="https://arxiv.org/abs/XXXX.XXXXX">📄 Paper</a> -->
  <a class="po-btn soon">💻 Code <small>coming soon</small></a>
  <!-- TODO: replace href with the HalluScope HF dataset link and remove the "soon" class -->
  <a class="po-btn scope soon" href="#">🤗 HalluScope <small>benchmark</small></a>
  <!-- TODO: replace href with the HalluVL-DPO HF dataset link and remove the "soon" class -->
  <a class="po-btn dpo soon" href="#">🤗 HalluVL-DPO <small>training data</small></a>
</div>

<!-- ================= TL;DR ================= -->
<div class="po-tldr">
  <span class="po-kicker">TL;DR</span>
  <p>Large vision-language models (LVLMs) still <em>hallucinate</em>. But why? We find that the main culprit is <strong>not the vision backbone</strong>: it's the model trusting <strong>what the prompt says</strong> over <strong>what the image shows</strong>.</p>
  <p>We <strong>diagnose</strong> this with a new benchmark, <strong>HalluScope</strong>, and <strong>fix</strong> it with a preference-optimization method, <strong>HalluVL-DPO</strong>, which reduces instruction-driven hallucinations while keeping performance strong on other benchmarks.</p>
</div>

<!-- ================= Roadmap ================= -->
<div class="po-roadmap">
  <a class="po-step" href="#part1">
    <span class="po-kicker">Part 1 · Diagnose</span>
    <h3>🔬 HalluScope</h3>
    <p>A benchmark that separates <em>where</em> hallucinations come from: perception, co-occurrence priors, or the prompt itself.</p>
  </a>
  <div class="po-arrow">➜</div>
  <a class="po-step dpo" href="#part2">
    <span class="po-kicker">Part 2 · Fix</span>
    <h3>🛠️ HalluVL-DPO</h3>
    <p>A weighted DPO fine-tuning recipe and dataset that teach the model to prefer grounded answers over hallucinated ones.</p>
  </a>
</div>

<!-- ================= Motivation ================= -->
<figure class="po-fig">
  <img src="/images/prompt_override_1.png" alt="Prompt-induced hallucination example" width="900">
  <figcaption>The model correctly answers direct questions about the image, but once the prompt <em>assumes</em> a non-existent object (a traffic light), it goes along with it.</figcaption>
</figure>

<p>Hallucinations in LVLMs increasingly arise from <em>conflicts between language priors and visual information</em>, rather than from perceptual limitations alone. Yet existing benchmarks (POPE, CHAIR, SHR, MMHal-Bench) do not tell apart hallucinations caused by perception failures, learned object co-occurrence priors, or presuppositions introduced by the instruction itself.</p>


<!-- =============================================================== -->
<!-- ========================= PART 1 ============================== -->
<!-- =============================================================== -->
<div class="po-part" id="part1">
  <span class="po-tag">Part 1 · Diagnose</span>
  <h2>HalluScope <img src="/images/prompt_override_2.png" alt="HalluScope logo"></h2>
  <p class="po-q">Where do LVLM hallucinations actually come from?</p>
</div>

<p><strong>What we do.</strong> HalluScope asks the same model about the same image in different ways, so that each question isolates one possible cause of hallucination:</p>

<div class="po-grid">
  <div class="po-card">
    <div class="po-emoji">👁️</div>
    <h4>Perception failures</h4>
    <p>Can the model correctly see what is in the image? <br><em>Real</em> &amp; <em>random</em> object recognition.</p>
  </div>
  <div class="po-card">
    <div class="po-emoji">🔗</div>
    <h4>Co-occurrence priors</h4>
    <p>Does it claim objects that usually appear in such scenes but are absent here? <br><em>Adversarial</em> recognition.</p>
  </div>
  <div class="po-card">
    <div class="po-emoji">💬</div>
    <h4>Instruction presuppositions</h4>
    <p>Does it accept a false assumption stated in the prompt? <br><em>Adversarial presupposition</em>.</p>
  </div>
</div>

<figure class="po-fig">
  <img src="/images/prompt_override_3.png" alt="HalluScope construction pipeline" width="900">
  <figcaption>How HalluScope is built: from annotated images to present, random, and adversarial (absent but plausible) objects, and the questions asked about each.</figcaption>
</figure>

<h3>🔍 Examples from HalluScope</h3>
<p>Each image comes with four kinds of questions. Use the arrows to browse.</p>
<div class="po-legend">
  <span class="po-chip real">Real recognition</span>
  <span class="po-chip rand">Random recognition</span>
  <span class="po-chip adv">Adversarial recognition</span>
  <span class="po-chip adv">Adversarial presupposition</span>
</div>

<div class="po-carousel" data-carousel>
  <div class="po-track">

    <figure class="po-slide">
      <img src="/images/prompt_override_6.png" alt="HalluScope examples">
      <figcaption>A baseball scene and a living room, with the questions generated for each.</figcaption>
    </figure>

    <!--
    ➕ To add another HalluScope example, copy this block (outside the comment) and change the image + caption:

    <figure class="po-slide">
      <img src="/images/halluscope_example_N.png" alt="HalluScope example">
      <figcaption>Short description of the example.</figcaption>
    </figure>
    -->

  </div>
  <div class="po-nav">
    <button type="button" data-prev aria-label="Previous example">‹</button>
    <div class="po-dots"></div>
    <button type="button" data-next aria-label="Next example">›</button>
  </div>
</div>

<h3>✨ What we found</h3>
<div class="po-grid">
  <div class="po-card">
    <div class="po-emoji">🎯</div>
    <h4>Vision is not the bottleneck</h4>
    <div class="po-stat">&gt; 85%</div>
    <p>Recognition accuracy on present and random absent objects stays high across all models.</p>
  </div>
  <div class="po-card">
    <div class="po-emoji">🕸️</div>
    <h4>Co-occurrence priors hurt</h4>
    <div class="po-stat">−8 to −37%</div>
    <p>Accuracy drops on objects that are absent but likely to appear in such scenes.</p>
  </div>
  <div class="po-card hot">
    <div class="po-emoji">💬</div>
    <h4>The prompt hurts the most</h4>
    <div class="po-stat">−25 to −85%</div>
    <p>When the question presupposes an absent object, performance drops the most: at least 15% more than co-occurrence alone.</p>
  </div>
</div>

<div class="po-callout">
  <strong>Takeaway:</strong> hallucinations in modern LVLMs mostly come from <strong>over-reliance on textual instruction presuppositions</strong> and <strong>learned semantic priors</strong>, not from limitations of visual perception.
</div>

<div class="po-dataset">
  <p>🤗 <strong>HalluScope benchmark</strong> is available on Hugging Face.</p>
  <!-- TODO: replace href with the HalluScope HF dataset link and remove the "soon" class -->
  <a class="po-btn scope soon" href="#">Get the dataset <small>coming soon</small></a>
</div>


<!-- =============================================================== -->
<!-- ========================= PART 2 ============================== -->
<!-- =============================================================== -->
<div class="po-part dpo" id="part2">
  <span class="po-tag">Part 2 · Fix</span>
  <h2>HalluVL-DPO 🛠️</h2>
  <p class="po-q">Can we teach the model to trust the image over the prompt?</p>
</div>

<p><strong>What we do.</strong> We fine-tune off-the-shelf LVLMs with a variant of Direct Preference Optimization (DPO) that targets prompt-induced hallucinations:</p>

<ol class="po-steps dpo">
  <li><strong>Build preference pairs.</strong> For each image and question, we create a <strong>preferred</strong> (visually grounded) answer and a <strong>rejected</strong> (hallucinated) one.</li>
  <li><strong>Weight each sample.</strong> Pairs are weighted by their <em>semantic gap</em>, so that the most informative pairs count more during training.</li>
  <li><strong>Fine-tune with DPO.</strong> The model learns to prefer grounded answers, even when the prompt pushes it the other way.</li>
</ol>

<figure class="po-fig">
  <img src="/images/prompt_override_4.png" alt="HalluVL-DPO training samples" width="900">
  <figcaption>Sample instances from the HalluVL-DPO training dataset: preferred (grounded) vs. rejected (hallucinated) responses.</figcaption>
</figure>

<figure class="po-fig">
  <img src="/images/prompt_override_5.png" alt="Semantic-gap weighting" width="900">
  <figcaption>Sample-specific weighting based on the semantic gap between preferred and rejected responses.</figcaption>
</figure>

<div class="po-dataset dpo">
  <p>🤗 <strong>HalluVL-DPO training dataset</strong> is available on Hugging Face.</p>
  <!-- TODO: replace href with the HalluVL-DPO HF dataset link and remove the "soon" class -->
  <a class="po-btn dpo soon" href="#">Get the dataset <small>coming soon</small></a>
</div>

<h3>📈 Results</h3>

<div class="po-callout dpo">
  On Qwen2-VL-7B, accuracy on HalluScope's <strong>adversarial presupposition</strong> subset (AdP) rises from <strong>57.96 → 82.83</strong>, while the other recognition settings stay on par.
</div>

<figure class="po-fig">
  <img src="/images/prompt_override_8.png" alt="HalluScope results" width="560">
  <figcaption>Results on HalluScope. HalluVL-DPO<sup>w</sup> is the semantic-gap weighted variant.</figcaption>
</figure>

<p>The improvement doesn't come at the expense of other abilities: the fine-tuned model stays competitive or improves on other hallucination benchmarks and general multimodal evaluations.</p>

<figure class="po-fig">
  <img src="/images/prompt_override_9.png" alt="Results on other benchmarks" width="900">
  <figcaption>Results on other hallucination benchmarks (POPE, HallusionBench, CPBench, CHAIR) and general benchmarks (MME, ScienceQA, MMVet).</figcaption>
</figure>

<figure class="po-fig">
  <img src="/images/prompt_override_10.png" alt="Qualitative results" width="900">
  <figcaption>Qualitative results before and after HalluVL-DPO fine-tuning.</figcaption>
</figure>

</div>

<script>
  // Examples carousel: arrows + dots, auto-built from the slides present.
  document.querySelectorAll('[data-carousel]').forEach(function (c) {
    var track = c.querySelector('.po-track');
    var slides = track.querySelectorAll('.po-slide');
    var dots = c.querySelector('.po-dots');
    var nav = c.querySelector('.po-nav');
    if (slides.length < 2) { nav.style.display = 'none'; return; }
    var go = function (i) { track.scrollTo({ left: slides[i].offsetLeft - track.offsetLeft, behavior: 'smooth' }); };
    var current = function () { return Math.round(track.scrollLeft / track.clientWidth); };
    slides.forEach(function (_, i) {
      var d = document.createElement('span');
      d.addEventListener('click', function () { go(i); });
      dots.appendChild(d);
    });
    var update = function () {
      var k = current();
      dots.querySelectorAll('span').forEach(function (d, i) { d.classList.toggle('on', i === k); });
    };
    c.querySelector('[data-prev]').addEventListener('click', function () { go(Math.max(0, current() - 1)); });
    c.querySelector('[data-next]').addEventListener('click', function () { go(Math.min(slides.length - 1, current() + 1)); });
    track.addEventListener('scroll', function () { window.requestAnimationFrame(update); });
    update();
  });
</script>
