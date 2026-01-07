---
layout: post
title: Exploring Noise Schedulers in Diffusion Models
description: A comprehensive benchmark of noise schedulers (Cosine, Sine, Laplace) in Diffusion Models. This project investigates how different noise level distributions impact training efficiency and image generation quality (FID scores) on the CIFAR-10 dataset.
image: /media/noise_schedule.png  # Replace with a specific project image later
---

**Authors:** Pranav Balakrishnan and Sidisha Shyam Barik  
**Context:** Course Project (UMass Amherst)  
**Report:** [Download PDF](https://drive.google.com/file/d/1tbiMq69XlXGulkmMFHxsccPNf_mQGrDl/view?usp=drive_link)

---
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
Diffusion models have gained massive attention for their high-quality generative capabilities. However, the "noise schedule", which defines the amount and timing of noise added during training, plays a critical, often overlooked role in performance.

This project investigates how different noise schedulers impact both the training and sampling of Denoising Diffusion Probabilistic Models (DDPMs). We evaluated performance under two distinct formulations:
1.  **Variance-Preserving (VP)**
2.  **Sub-Variance-Preserving (Sub-VP)**

### Methodology
We utilized the **CIFAR-10** dataset to evaluate various noise schedulers, focusing on their "scaled" and "shifted" counterparts to identify the best approach for a given formulation.

* **Schedulers Tested:** We compared the baseline **Cosine** noise schedule against **Sine** (introduced for Sub-VP) and **Laplace** noise schedulers.
* **Samplers Evaluated:** We tested Cosine, Laplace, Left-Shifted Cosine, and EDM samplers to see if focusing on specific noise levels improved generation.
* **Evaluation:** We used **FID scores** (Fréchet Inception Distance) to measure image quality. To iterate quickly, we also implemented a custom image quality metric tuned for CIFAR-10.

### Key Findings
* **Sampler Performance:** Our experiments showed that the **Cosine** and **EDM** samplers yielded the best results in terms of FID-3k scores and visual quality.
* **Sine Schedule:** We derived and implemented a **Sine-based noise scheduler** specifically for the Sub-VP formulation, as the standard Cosine schedule does not directly translate to Sub-VP.
* **Focus on Noise Levels:** While recent literature suggests that aggressively focusing on specific (mid-range) noise levels improves training, our results found that broader distributions (like Cosine/Sine) remained highly competitive and often outperformed aggressive focusing (like Laplace) in our specific experimental setup.

[← Back to Home]({{ site.baseurl }}/)
