# A bit about me

[Work Experience](#work-experience) • [Projects](#projects) • [Publications](#publications) • [Education](#education)

## Education
- M.S., Computer Science | University of Massachusetts Amherst (Sep 2024 – May 2026)
- B.S., Data Science and Applications | Indian Institute of Technology Madras, India (Jan 2021 - May 2024)

## Publications
<div class="project-grid">
  {% for project in site.publications %}
    <a href="{{ project.url | relative_url }}" class="project-card">
      <img src="{{ project.image | relative_url }}" alt="{{ project.title }}">
      <div class="card-content">
        <h3>{{ project.title }}</h3>
        <p>{{ project.description }}</p>
      </div>
    </a>
  {% endfor %}
</div>

## Projects
<div class="project-grid">
  {% for project in site.projects %}
    <a href="{{ project.url | relative_url }}" class="project-card">
      <img src="{{ project.image | relative_url }}" alt="{{ project.title }}">
      <div class="card-content">
        <h3>{{ project.title }}</h3>
        <p>{{ project.description }}</p>
      </div>
    </a>
  {% endfor %}
</div>

## Work Experience
**Junior Data Scientist @ Sabio Inc (May 2022 - Mar 2023)**                                                    
- Enhanced Ad Campaign Effectiveness: Architected and deployed advanced predictive models, leveraging K-Means Clustering for audience segmentation and Logistic Regression and XGBoost to forecast user interests. This initiative directly led to a 25% improvement in ad targeting precision, maximizing marketing ROI. 
- Optimized Data Processing: Overhauled the core data pipeline codebase (Scala & Python) for audience segmentation to address performance bottlenecks. The revamped pipeline achieved a 30% reduction in runtime and an 80% increase in processing scale, enabling more complex and larger-scale data analysis. 
- Automated End-to-End Data Integration: Engineered a fully automated data pipeline using on AWS using Apache Airflow and Spark with Scala to ingest, aggregate, and integrate large-scale third-party. This initiative streamlined bi-weekly updates, leading to a 40% reduction in data update times, and a 25% decrease in compute costs.

## Achievements
🥇 Gold Medalist, 2016 Indian National Taekwondo Championship (Light Heavyweight)
