# A little bit about me

## Education


## Work Experience
****                                                                                                        




## Projects
### 


### Autonomous Human Following Robot
-	Architected and deployed a real-time human-following system on a 3-wheeled omnidirectional robot, leveraging ROS for control, an NVIDIA Jetson Nano for onboard computation, and an RGB-D camera for perception.
-	Enhanced target persistence by integrating a Simple Online Realtime Tracking (SORT) algorithm with a custom-developed re-identification module, using color histogram features to successfully maintain tracking through temporary occlusions.
-	Optimized the control system by implementing a Proportional (P) controller, achieving a low system latency of 1.2 seconds and enabling smooth, continuous tracking of targets moving at speeds up to 10 m/s.

### Exploring Noise Schedulers in Diffusion Models
-	Conducted a comparative analysis of noise schedulers (Cosine, Sine, Laplace) to benchmark their impact on the training efficiency and final sample quality of Denoising Diffusion Probabilistic Models (DDPMs).
-	Designed a novel sine-based noise scheduler that demonstrated superior performance over the standard cosine scheduler, resulting in a significant improvement in generated image quality (FID/IS scores) and a reduction in model training time.


## Publications
### IEEE MILCOM 2025 - GPU-GLMB: Assessing the Scalability of GPU-Accelerated Multi-Hypothesis Tracking
-	Created the first fully vectorized and scalable implementation of a Random Finite Set (RFS) based Multi Sensor Sequential Monte Carlo (SMC) Generalized Labelled Multi Bernoulli filter capable of handling one or more detections from each sensor per object. 
-	Innovated a novel, measurement-focused Categorical sampling method to replace the computationally expensive and sequential Gibbs sampling bottleneck, enabling massive parallelization of the track-to-measurement assignment step.
-	Achieved unprecedented computational efficiency by leveraging GPU parallel processing, demonstrating that a 100x increase in scenario complexity resulted in only a 3x increase in processing time.
-	Benchmarked the filter's performance across diverse CPUs and GPUs, quantifying significant speed improvements on modern GPUs and validating its effectiveness for deployment on resource-constrained edge devices.
