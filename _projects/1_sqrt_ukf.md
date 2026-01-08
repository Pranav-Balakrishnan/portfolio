---
layout: post
title: Vehicle Tracking with Sqrt-UKF
description: Robust state estimation for autonomous vehicles using the Square-Root Unscented Kalman Filter (Sqrt-UKF). This project benchmarks advanced motion models to effectively handle complex maneuvers and implements differentiable parameter learning to automate noise parameter tuning.
image: /media/bicycle.png  # Replace with a specific project image later
---

**Author:** Pranav Balakrishnan  
**Context:** University of Massachusetts Amherst  
**Report:** [Download PDF](https://drive.google.com/file/d/185LDURtipDJYSWhLRFc-3scuCF-fsy4i/view?usp=drive_link)

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
Single-object tracking is fundamental for autonomous navigation, yet it remains challenging when dealing with non-linear motion, sensor noise, and "blind spots" in distributed camera networks.

This project investigates the **Square-Root Unscented Kalman Filter (Sqrt-UKF)** as a robust estimation framework. We specifically focus on how the choice of **Motion Model** impacts tracking accuracy during critical failures—such as when a vehicle performs an abrupt turn while momentarily invisible to sensors.

### Methodology
We evaluated tracking performance on a dataset featuring three vehicle types (Bus, Truck, Car) with varying trajectory complexities.

* **Models Benchmarked:**
    1.  **Constant Velocity (CV):** Assumes straight-line motion (baseline).
    2.  **Constant Turn Rate & Velocity (CTRV):** Accounts for yaw rate but assumes simple turning.
    3.  **Bicycle Kinematics Model:** To capture physical reality and improve density estimation, I incorporated domain-specific inductive biases by adopting a non-linear bicycle kinematic motion model. I derived a closed-form linearization of the stochastic differential equations governing state evolution to enable a differentiable update rule.

    ![Bicycle Kinematics Model]({{ site.baseurl }}/media/bicycle.png)
    <div class="caption">Figure: The purple object of length L having its center of gravity at $(x_1,x_2)$ at a distance of $l_r$ from the rear wheel is moving with a heading angle $\theta$ and has a steering angle of $\delta$. $\beta$ is the slip angle and S is the distance of the Instantaneous center of rotation (ICR) to the real wheels and R is the distance of the ICR to the center of gravity.</div>

* **Differentiable Parameter Learning:**
    To avoid the tedious process of manual tuning, we developed an end-to-end framework to learn motion model parameters (specifically acceleration noise) from data. By making the Sqrt-UKF fully differentiable, we optimized these parameters by minimizing the Negative Log Likelihood (NLL) of ground truth observations using gradient-based optimization.

### Key Findings
* **Superiority of Bicycle Kinematics:** While all models performed similarly on simple straight paths (Bus scenario), the **Bicycle Kinematics model** significantly outperformed others in the complex "Car" scenario. It successfully maintained trajectory coherence during missed detections in sharp turns, whereas the CV and CTRV models diverged.
* **Quantitative Improvement:** In the most challenging scenario, the Bicycle model achieved a **Root Mean Square Error (RMSE) of 0.5135**, compared to 0.9009 for the Constant Velocity model.
* **Learning Insights:** The gradient-based parameter learning successfully converged for smooth trajectories but faced challenges with the "rugged" loss landscapes of erratic trajectories, highlighting that while learning automates tuning, it requires stable optimization landscapes to be effective.

[← Back to Home]({{ site.baseurl }}/)
