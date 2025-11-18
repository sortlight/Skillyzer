# Skillyzer
The career coach app you need ---- built with Amazon Q Business

# Career Coach Assistant 

## Overview
This project documents the design and build process for the Career Coach Assistant, a web‑based application powered by Amazon Q Business. The application automates skill‑gap analysis and training recommendations for Career4All coaches by comparing learner CVs with job descriptions and retrieving relevant courses from multiple data sources.

The goal of this documentation is to provide a clear, professional and technically accurate explanation of how the system was built. 

---
## Project Objectives
- Automate CV and job‑profile comparison.
- Provide consistent skill‑gap analysis across the coaching team.
- Generate personalized training recommendations using course catalogs.
- Integrate both static file uploads and S3‑based catalogs as data sources.
- Apply access control and content moderation to meet organizational standards.
- Share the final application across the coaching team through Amazon Q Business.

---
## Environment Setup
An AWS sandbox environment was used to complete this project. The environment included:
- An AWS account.
- Preconfigured Amazon Q Business resources such as the *CareerCoachAssistant* app, IAM Identity Center users, and groups.
- Preloaded sample files for CVs, job descriptions and course catalogs.


---
## Application Build Process

### 1. Creating the Base Application
The Career Coach Assistant was built using Amazon Q Apps with the following configuration:
- **Input Cards** for CV upload and Job Description upload.
- **Output Cards** for Skill‑Gap Analysis and Training Recommendations.
- Prompts designed to guide the LLM in producing structured, actionable results.
- Verification through the deployed web interface to confirm output quality.

### 2. Customizing the Application
Additional features were added to support coach workflows:
- A **Schedule Recommendation** output card.
- A **Career Coach Recommendation** input card to allow human refinement.
- A Training Recommendation output card.

### 3. Integrating Course Catalog Data
To support training recommendations:
- A PDF course catalog was uploaded into the existing data source index.
- Queries were tested to confirm that Amazon Q retrieved course details accurately.

### 4. Adding an Amazon S3 Data Source
To make course catalog updates scalable:
- An S3 bucket was created in the same region as the Q Business app.
- Additional static catalog files were uploaded.
- The S3 bucket was registered as a new data source.
- A daily synchronization schedule was configured.

### 5. Enhancing Security and Moderation
To align with organizational controls:
- Restricted‑access course files were uploaded to S3.
- An ACL configuration file was created and associated with the data source.
- A keyword‑blocking list was added to filter out inappropriate or prohibited content.

### 6. Sharing the Application
The final step was to share the application across the organization:
- The app was published and shared with all users.
- Categories such as *Marketing*, *Support* and *Operations* were applied.
- The app was marked as *Verified* in the Q Business console.

---
## Repository Structure
```
career-coach-assistant/
│
├── README.md                 # Project documentation
├── images/                   # Screenshots for submission
│   ├── final-app.png
│   ├── data-sources.png
│   ├── skill-gap-prompt.png
│   ├── blocked-words.png
│   └── acl-file.png
│
└── course-files/             # Course files used in testing (sample names only)
    ├── sample_cv.pdf
    ├── job_description.txt
    ├── course_catalog_main.pdf
    └── acl.json
```


---
## Conclusion
The Career Coach Assistant application demonstrates how Amazon Q Business can be used to automate specialized domain workflows without requiring custom code. By integrating structured prompts, dynamic data sources, content moderation, and identity‑based controls, the application delivers consistent, scalable support to Career Coaches.

The final product enables Career4All to provide learners with up‑to‑date training recommendations while maintaining organizational guidelines for data usage and content quality.

