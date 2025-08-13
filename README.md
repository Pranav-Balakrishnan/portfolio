# A bit about me

## Education
- M.S., Computer Science | University of Massachusetts Amherst (Sep 2024 – May 2026)
- B.S., Data Science and Applications | Indian Institute of Technology Madras, India (Jan 2021 - May 2024)

## Publications
### GPU-GLMB: Assessing the Scalability of GPU-Accelerated Multi-Hypothesis Tracking (IEEE MILCOM 2025)
- Created the world’s first fully vectorized and scalable implementation of a Random Finite Sets (RFS) based Multi Sensor Sequential Monte Carlo (SMC) Generalized Labelled Multi Bernoulli Filter capable of handling one or more detections from each sensor for each object.  
- Enabled massive parallelization of the track-to-measurement assignment step by engineering a novel, measurement-centric Categorical sampling algorithm to overcome the computational bottleneck of sequential Gibbs sampling.  
- Delivered exceptional computational efficiency and scalability by leveraging GPU parallel processing, proven by a 100x increase in scenario complexity yielding only a 3x rise in processing time. 
- Benchmarked the filter's performance across diverse CPUs and GPUs, quantifying significant processing speedups showcasing its effectiveness for deployment on resource-constrained edge devices. 

## Projects
### Vehicle Tracking with Sqrt-UKF and Bicycle Kinematics Motion Model (Jan 2025 – May 2025)
- Implemented a numerically stable Square-Root Unscented Kalman Filter (Sqrt-UKF) to robustly estimate vehicle states from a challenging geospatial dataset, effectively handling intermittent sensor data and complex, non-linear dynamics. 
- Derived and implemented a complex Bicycle Kinematics Motion Model by discretizing the continuous time stochastic differential equation corresponding to the Bicycle Kinematics Model, providing a more accurate representation of real-world vehicle dynamics. 
- Quantified the superiority of the Bicycle Kinematics motion model by benchmarking three distinct models, demonstrating that the Bicycle Kinematics model reduced Root Mean Square Error (RMSE) by 43% over Constant Velocity (CV) and 27% over Constant Velocity and Turn Rate (CTRV) during challenging vehicle maneuvers. 
- Developed an end-to-end, data-driven Machine Learning framework by developing a fully differentiable Sqrt-UKF, enabling the optimization of motion model parameters through gradient-based optimization of the Negative Log Likelihood (NLL). 

### Autonomous Human Following Robot (Mar 2025 – May 2025)                                                     
- Architected and deployed a real-time human-following system on a three-wheeled omnidirectional robot, leveraging ROS for control, an NVIDIA Jetson Nano for onboard computation, and an RGB-D camera for perception. 
- Enhanced target persistence by integrating a Simple Online Realtime Tracking (SORT) algorithm with a custom-developed re-identification module, using color histogram features to successfully maintain tracking through temporary occlusions. 
- Optimized the control system by implementing a Proportional (P) controller, achieving a low system latency of 1.2 seconds and enabling smooth, continuous tracking of targets moving at speeds up to 10 m/s. 
                                                                                 
### Exploring Noise Schedulers in Diffusion Models (Sep 2024 – Dec 2024)
- Conducted a comprehensive analysis of noise schedulers (Cosine, Sine, Laplace) to benchmark their impact on the training efficiency 
and sample quality of Denoising Diffusion Probabilistic Models (DDPMs). 
- Designed and implemented a novel sine-based noise scheduler designed to explore alternative noise distribution strategies beyond 
standard schedulers, showcasing significant improvement in generated image quality (FID scores) and a reduction in model training 
time. 

## Work Experience
**Junior Data Scientist @ Sabio Inc (May 2022 - Mar 2023)**                                                    
- Enhanced Ad Campaign Effectiveness: Architected and deployed advanced predictive models, leveraging K-Means Clustering for audience segmentation and Logistic Regression and XGBoost to forecast user interests. This initiative directly led to a 25% improvement in ad targeting precision, maximizing marketing ROI. 
- Optimized Data Processing: Overhauled the core data pipeline codebase (Scala & Python) for audience segmentation to address performance bottlenecks. The revamped pipeline achieved a 30% reduction in runtime and an 80% increase in processing scale, enabling more complex and larger-scale data analysis. 
- Automated End-to-End Data Integration: Engineered a fully automated data pipeline using on AWS using Apache Airflow and Spark with Scala to ingest, aggregate, and integrate large-scale third-party. This initiative streamlined bi-weekly updates, leading to a 40% reduction in data update times, and a 25% decrease in compute costs.

## Achievements
Gold Medalist, 2016 Indian National Taekwondo Championship (Light Heavyweight)
