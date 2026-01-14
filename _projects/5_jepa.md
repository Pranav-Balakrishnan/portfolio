---
layout: post
title: "Probing Spatial Reasoning in VLMs: Adapting I-JEPA for VQA"
description: "Adapting the I-JEPA World Model for Visual Question Answering to test if geometric pre-training improves spatial reasoning."
image: /media/jepa_arch.png
---

**Authors:** Pranav Balakrishnan and Sidisha Shyam Barik  
**Context:** University of Massachusetts Amherst  
**Report:** [Download PDF](https://drive.google.com/file/d/1aUxKnIX5W5loZg-nFqoUWmjjLe9_GxRO/view?usp=sharing)

---
<script>
  window.MathJax = {
    tex: {
      inlineMath: [['$', '$'], ['\\(', '\\)']],
      displayMath: [['$$', '$$'], ['\\[', '\\]']]
    }
  };
</script>
<script type="text/javascript" id="MathJax-script" async
  src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js">
</script>

<style>
/* 2. Link and Heading Colors (Changing from Blue) */
a {
    color: #678953 !important; /* A warm amber for links */
    text-decoration: none;
}
a:hover {
    text-decoration: underline;
}
h1, h2, h3 {
    color: #91b859 !important; /* A slightly deeper orange for headings */
}

</style>

### Overview
Standard Vision-Language Models (like LLaVA) rely on encoders like CLIP, which are trained to match images to text. While excellent at identifying *what* an object is, these models often struggle with *where* things are, lacking fine-grained spatial understanding.

This project explores a radically different approach: using a **World Model** (specifically **I-JEPA**) as the visual foundation. I-JEPA is trained via masked prediction to understand geometry and structure without ever seeing a single word of text. Our goal was to determine if this rich structural understanding could be translated into language to solve spatial reasoning tasks better than semantic models.

### Methodology
We successfully architected a custom multimodal pipeline fusing a frozen I-JEPA encoder with the **Qwen2.5-7B** Large Language Model.

* **Architecture:** We built a custom translation layer (MLP Projector) to map I-JEPA's 1280-dimensional geometric features to the LLM's embedding space.
* **Training Strategy:**
    1.  **Feature Alignment:** Trained the projector on 25,000 COCO image-caption pairs to teach the model basic vocabulary.
    2.  **Visual Instruction Tuning:** Used **LoRA (Low-Rank Adaptation)** to fine-tune both the LLM and the Vision Encoder on 30,000 complex instruction-following samples from LLaVA-Instruct.
* **Engineering Challenge:** We implemented a hybrid precision strategy (Float32 for vision, BFloat16 for projection) to solve numerical overflow issues caused by I-JEPA's unbounded feature magnitudes.

### Key Findings
We evaluated the model on the **POPE (Polling on Object Permanence)** benchmark to test for hallucinations and spatial grounding.

[← Back to Home]({{ site.baseurl }}/)

* **Successful Translation:** The model achieved **68.0% accuracy**, significantly outperforming the random chance baseline of 50.0%. [cite_start]This proves that non-semantic, geometric features can indeed be translated into the semantic space of an LLM[cite: 5282, 5355].
* [cite_start]**The "Completion" Bias:** While the model could "see," it exhibited a high **Yes-Ratio of 80%**[cite: 5294]. [cite_start]Because I-JEPA is trained to predict missing image parts, the model tended to hallucinate contextually plausible objects (e.g., imagining a toothbrush in a bathroom) even when they weren't visible[cite: 5317].
* [cite_start]**Conclusion:** World Models offer a promising path for spatial intelligence, but their generative nature requires specialized alignment techniques (like hard-negative mining) to unlearn the habit of "completing" the scene[cite: 5360].
