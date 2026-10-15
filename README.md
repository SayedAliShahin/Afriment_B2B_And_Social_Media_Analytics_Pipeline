# Afriment B2B & Social Analytics Pipeline

**Role:** Operational Data Analyst / Pod B Engineering Lead (Afriment Data Analytics Internship)[cite: 1]



## 1. Business Context & Challenge

Afriment operates a dual-model ecosystem: training tech talent and connecting verified portfolios with B2B employers and partners. Across 5 distinct workstreams (social posts, B2B company pipelines, foundation grants, course markets, and tech communities), raw inputs arrived unstructured, unvalidated, and prone to breaking downstream dashboards. 



Pod B served as the **Data Engine Room**, responsible for Validation, data cleaning, relational schema design, deterministic scoring rules, and metric validation.



## 2. System Architecture & Workflow

Our team (Pod B) operated in a strict dependency chain to ensure zero data corruption:

Raw Inputs (Pod A / Exports) **-->** Pod B Engine (Clean, Standardize, Rule-Score) **-->** Outputs (Pod C Dashboards / SQL Models).



**The Source Rule:** Raw exports in `/00_Source_Data/` were treated as read-only. Nothing was ever edited directly in the source.
**Quality Gates:** Every data batch underwent a mandatory 15-minute QA check to eliminate trailing spaces, enforce YYYY-MM-DD date formats, fix numbers stored as text, and eliminate duplicate entries.


**Note on Data Privacy:** In compliance with the Afriment internship NDA, all company names, contact emails, and absolute metrics in the sample CSV files have been fully fictionalized or anonymized. The schemas, scoring formulas, and validation rules remain identical to the production pipeline



## 3. Workstream Deep-Dives & Technical Execution



### Workstream 1: Social Media Performance Autopsy (305 Posts)

**The Problem:** 12 months (2025-09-09 - 2026-8-31) of historical LinkedIn exports lacking standardized classifications such as **Media_Format** and **Content_Pillar** and Afriment wants to know which kind of its content performed the best.

**The Execution:**
- Created `04_Classification_Rules` to tag Media Formats and Content Pillars and classified all 306 posts through manual checking.
- Built `02_Clean_Posts` to track metrics and utilized median engagement rates per 1,000 impressions to prevent viral anomalies from skewing performance baselines.
- Analyzed for the best performing Media_Format and Content_Pillar. 4.Broke down the engagement rate trend over 12 months of data.

**The Output:** A fully cleaned, growing full-year dataset validated and analyzed showing **Document** the best performing media format and **Students Testimonial/Career Advice** the best content pillar; Fall (Sep-Dec 2025) showing the highest engagement rate percent.
- **Visual Evidence:**
  ![WS1 Engagement Trend](Visualizations/WS1_ER_Trend.png)

**Key Finding:** Document carousels outperformed static text and images by 3.2x, with Fall (Sep–Dec 2025) yielding the highest engagement window.

**Recommendation:** Adopt a 4-week pilot reallocating content creation resources toward educational document carousels and student testimonials.


### Workstream 2, 3 & 5: B2B & Foundation Scoring Pipelines

**The Problem:** In these workstreams the primary question is: Which companies and communities are the best option that  Afriment can partner to offer its services or absorb sponsorships and community engagements?  A list of targeted **53 companies** with possible operational problems which talents can be offered, a list of **60 foundations** that can fund  interns & **63 communities** which offers career advice/guidance but not courses which are the best fit for Afriment's courses/trainings partnerships.
**The Execution:** Designed a live weighted scoring model (`02_Scoring_Rules`) to rank companies and foundations based on online social presence, evidence of recent activity, active funding windows, grant sizes, and verified decision-maker channels.
**The Output:** A verified pipeline of **40 Tier-1** companies and **38 confirmed** communities (Score >= 80) for potential partnership and **19 active/contactable foundations** that can be Afriment's interns potential sponsors.


### Workstream 4: Skills Market Intelligence Model

**The Problem:** A market gap between tech academies course offerings and actual employer hiring demands across 6 African countries.
**The Execution:** 1.Ingested employer job postings and academy course catalogs. 2.Modeled demand vs. supply metrics to compute skill heat ratings and categorized them into a 2x2 matrix (*Hot Cakes, The Gap, Oversupplied, Dormant*).
**The Output:** Strategic adjustments recommendations identifying Data Analytics with the highest oversaturated course while the Business Analytics, Project Managements & No-Code/Automation have a high demand but less academies offering them (Hot Cake).


## 4. Key Insights & Strategic Recommendations

**Content Strategy:** Lunch a 4 week pilot project, increasing Document and Student-Testimonial/Career Guide content and validate before large samples**.
**Curriculum Pivot:** Consider blending Data Analytics with Business Analysis, Project Management & No-code/Automation to stand out in the market.
