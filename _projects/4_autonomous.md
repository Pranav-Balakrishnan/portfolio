---
layout: post
title: Autonomous Object Following Robot
description: A real-time human-following robot deployed on the Triton platform. Integrates YOLOv3-tiny and SORT with custom HSV-based re-identification to enable robust tracking on edge hardware (Jetson Nano) without GPU acceleration.
image: /media/triton.png  # Replace with a specific project image later
---

**Team:** Nilesh Nayan, Pranav Balakrishnan, Sidisha Barik, Shantanu Todmal, Kamalesh Kumar  
**Context:** CS 603 Robotics (UMass Amherst)  
**Report:** [Download PDF](https://drive.google.com/file/d/1rIGqu7iYvASOX5R_7vlzJoTJ6LY4oY5f/view?usp=drive_link)

---

### Overview
This project involved the development and deployment of an end-to-end autonomous object tracking system on the **Triton robot**. The primary goal was to enable the robot to detect, track, and follow specific human targets in real-time.

A major constraint of the development environment (Dockerized Jetson Nano) was the **unavailability of CUDA (GPU acceleration)**. This necessitated a highly optimized, CPU-efficient pipeline that could still handle complex tasks like occlusion recovery.

### Methodology
We engineered a modular ROS-based architecture comprising three core components:

* **Perception (CPU-Optimized):** We utilized **YOLOv3-tiny** loaded via OpenCV’s DNN module for low-latency detection.
* **Tracking with Re-Identification:** Standard tracking algorithms like DeepSORT utilize heavy deep learning models for re-identification. To adapt to our CPU-only constraint, we integrated the **SORT algorithm** with a custom **HSV color histogram-based re-identification module**. This allowed the robot to recover track identities even after temporary occlusions.
* **Control System:** We implemented a Proportional (P) controller for both angular rotation and lateral strafing, enabling the robot to actively keep the target centered in its field of view.

### Key Results
* **Real-Time Performance:** The full perception stack achieved **10-15 FPS** on the NVIDIA Jetson Nano, with CPU utilization remaining under 70%.
* **Control Responsiveness:** The system achieved a low latency of **1.2 seconds** for re-centering targets moving at moderate speeds.
* **Robustness:** The custom re-identification logic reduced Identity Switches by over 50% compared to the baseline tracker, successfully maintaining target lock during entry/exit scenarios and partial occlusions.

[← Back to Home]({{ site.baseurl }}/)
