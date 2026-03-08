---
layout: post
title: "Tracking Ground Vehicles with State-Time-Variant Process Noise Models"
description: ""
image: /media/glmb_map_gif.gif
---

**Authors:** Benjamin M. Marlin, Sean M. O’Rourke, Sidisha Barik, Pranav Balakrishnan, and Colin Samplawski
**Conference:** Submitted to International Conference on Information Fusion  

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

Geospatial tracking of ground vehicles using networks of visual sensors such as RGB and depth cameras is a challenging problem due to gaps in sensor coverage that arise from sparse sensor placement and the presence of occluding structures. When tracked objects move in and out of regions of sensor coverage, the accurate propagation of track uncertainty becomes important to tracking accuracy. In this paper, we explore variations on the non-linear constant turn rate and velocity (CTRV) transition model applied to simulated ground vehicle trajectories using the open-source Stone Soup tracking framework. We focus on comparing a version of the CTRV model with a noise process covariance function that varies with both state and time to a version of the CTRV model where the noise process covariance function varies with time. As Stone Soup does not support experimentation with state-time-variant models, we discuss implementation strategies including "smuggling" state via side effects and extending the base class hierarchy to introduce state-time-variant models using a Stone Soup plugin module.

[← Back to Home]({{ site.baseurl }}/)
