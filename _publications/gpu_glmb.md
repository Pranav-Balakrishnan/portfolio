---
layout: post
title: "GPU-GLMB: Scalable Multi-Hypothesis Tracking"
description: "Fully vectorized implementation of the GLMB filter, capable of massive parallelization on GPUs."
image: /media/glmb_map_gif.gif
---

**Authors:** Pranav Balakrishnan, Sidisha Barik, Sean M. O'Rourke, and Benjamin M. Marlin  
**Conference:** IEEE MILCOM 2025  
**Paper:** [View on arXiv](https://www.arxiv.org/abs/2512.06230)

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
Multi-object tracking (MOT) is a fundamental capability for autonomous driving, robotics, and surveillance. While the **Generalized Labeled Multi-Bernoulli (GLMB)** filter provides an exact closed-form solution to the multi-target Bayes recursion, its computational cost typically prohibits real-time use in complex scenarios.

**GPU-GLMB** addresses this bottleneck by introducing a modified filter variant that allows **multiple detections per object**. This seemingly minor change breaks the strict inter-detection dependencies of the standard GLMB update step, unlocking the ability to perform hypothesis generation and weight updates in parallel.

<video controls muted playsinline width="100%" style="max-width: 1000px; display: block; margin: 0 auto;">
  <source src="{{ site.baseurl }}media/20_objects_with_road.mp4" type="video/mp4">
  <p>Your browser does not support the video tag. 
     <a href="{{ site.baseurl }}media/20_objects_with_road.mp4">Download the video here</a>.
  </p>
</video>

*Figure: Visualization of the tracker handling complex multi-object scenarios.*

### Key Contributions
* **Fully Vectorized Implementation:** We re-engineered the GLMB filter using **PyTorch**, enabling it to run efficiently on GPU hardware by processing batches of hypotheses simultaneously.
* **Broken Dependencies:** By allowing multiple detections per object (crucial for modern distributed virtual sensors), we eliminated the need for sequential Gibbs sampling in the update step.
* **Massive Scalability:** Experiments demonstrate that the server-grade GPU implementation exhibits very little scaling in run time with respect to the number of hypotheses, maintaining real-time performance (<0.1s per update) even in complex scenarios with 20 objects and 100 hypotheses.
* **Cross-Platform Performance:** Benchmarked across NVIDIA L40S (Server), NVIDIA 2080Ti (Desktop), and NVIDIA Orin NX (Edge) GPUs, proving the system's viability for both high-performance servers and resource-constrained edge devices.

### Performance Results
Our analysis focused on run-time scalability with respect to the number of objects and retained hypotheses ($H_{max}$).

1.  **Server vs. CPU:** On scenarios with 5 or more objects, the server CPU failed to maintain real-time performance (<0.1s per update), whereas the GPU implementation maintained sub-0.1s update times even with 20 objects.
2.  **Tracking Accuracy:** The relative cardinality error remained below **2%** for up to 10 objects, demonstrating that the parallelized approximation does not sacrifice tracking quality.

### Resources
- [**Read the full paper**](https://www.arxiv.org/abs/2512.06230)

[← Back to Home]({{ site.baseurl }}/)
