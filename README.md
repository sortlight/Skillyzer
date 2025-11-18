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

## Screenshots
1. Screenshot of final application, showing all the input and output cards.
    <img width="1365" height="671" alt="app_skillyzer" src="https://github.com/user-attachments/assets/e44779c7-5294-400b-a9b1-3743668f0e11" />

2. Screenshot of your data sources, showing the last sync time.
   <img width="1364" height="628" alt="last-sync-time" src="https://github.com/user-attachments/assets/c2bb4c64-e8c9-44a4-bfeb-7f88abeb8284" />

3. Screenshot of the prompt you used for Skill Gap Analysis Output card.
   <img width="285" height="669" alt="skill_Gap_prompt" src="https://github.com/user-attachments/assets/23204437-b4a8-4c0d-a6c1-a6d73caecfaa" />

4. Screenshot of the blocked words.
   <img width="1355" height="596" alt="blocked_words" src="https://github.com/user-attachments/assets/767a7e39-3a07-4fc2-acec-76a509fc16ef" />

5. ACL file you created.
      ```
              [
    {
        "keyPrefix": "s3://course-catalog-career-coach-v1/Data/Security/",
        "aclEntries": [
            {
                "Name": "CareerCoaches",
                "Type": "GROUP",
                "Access": "ALLOW"
            }
        ]
    },
    {
        "keyPrefix": "s3://course-catalog-career-coach-v1/Data/Medicine/",
        "aclEntries": [
            {
                "Name": "career.coach.one",
                "Type": "USER",
                "Access": "ALLOW"
            },
            {
                "Name": " career.coach.two ",
                "Type": "USER",
                "Access": "DENY"
            }
        ]
    }
]

```




## Repository Structure

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

