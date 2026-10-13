# Afriment B2B & Social Analytics Pipeline
**Role:** Operational Data Analyst / Pod B Engineering Lead (Afriment Data Analytics Internship)[cite: 1]

## 1. Business Context & Challenge
Afriment operates a dual-model ecosystem: training tech talent and connecting verified portfolios with B2B employers and partners. Across 5 distinct workstreams (social posts, B2B company pipelines, foundation grants, course markets, and tech communities), raw inputs arrived unstructured, unvalidated, and prone to breaking downstream dashboards. 

Pod B served as the **Data Engine Room**, responsible for Validation, data cleaning, relational schema design, deterministic scoring rules, and metric validation.

## 2. System Architecture & Workflow
Our team operated in a strict dependency chain to ensure zero data corruption:
Raw Inputs (Pod A / Exports) **-->** Pod B Engine (Clean, Standardize, Rule-Score) **-->** Outputs (Pod C Dashboards / SQL Models).

* **The Source Rule:** Raw exports in `/00_Source_Data/` were treated as read-only. Nothing was ever edited directly in the source.
* **Quality Gates:** Every data batch underwent a mandatory 15-minute QA check to eliminate trailing spaces, enforce YYYY-MM-DD date formats, fix numbers stored as text, and eliminate duplicate entries.

## 3. Workstream Deep-Dives & Technical Execution

### Workstream 1: Social Media Performance Autopsy (305 Posts)
* **The Problem:** 12 months (2025-09-09 - 2026-8-31) of historical LinkedIn exports lacking standardized classifications such as **Media_Format** and **Content_Pillar** and ...
* **The Execution:**
1.Created `04_Classification_Rules` to tag Media Formats and Content Pillars and classified all 306 posts through manual checking. 2.Built `02_Clean_Posts` to track metrics and utilized median engagement rates per 1,000 impressions to prevent viral anomalies from skewing performance baselines. 3.Analyzed for the best performing Media_Format and Content_Pillar. 4.Broke down the engagement rate trend over 12 months of data.
* **The Output:** A fully cleaned, growing full-year dataset with **Document** the best performing media format and **Students Testimonial** the best content pillar.

### Workstream 2 & 3: B2B & Foundation Scoring Pipelines
* **The Problem:** What Afriment can solve for a list of targeted 53 companies with possible operational problems and among 60 mid-tier foundations who can fund Afriment's interns.
* **The Execution:** Designed a live weighted scoring model (`02_Scoring_Rules`) to rank companies and foundations based on online social presence, evidence of recent activity, active funding windows, grant sizes, and verified decision-maker channels.
* **The Output:** A verified pipeline of 40 Tier-1 pitch ready companies (Score >= 80) for potential partnership and 19 active funds to be approached.

### Workstream 4: Skills Market Intelligence Model
* **The Problem:** A market disconnect between academy course offerings and actual employer hiring demands across the region[cite: 1].
* **The Execution:** Ingested employer job postings and academy course catalogs[cite: 1]. Modeled demand vs. supply metrics to compute skill heat ratings and categorized them into a 2x2 matrix (*Hot Cakes, The Gap, Oversupplied, Dormant*)[cite: 1].
* **The Output:** Strategic curriculum adjustments identifying high-demand execution skills[cite: 1].

## 4. Key Insights & Strategic Recommendations
* **Content Strategy:** Educational carousels generated significantly higher sustainable engagement than standard promotional single images[cite: 1].
* **Curriculum Pivot:** Shifted focus away from oversaturated generic tech tracks toward high-demand, low-supply domains identified in the supply-demand matrix[cite: 1].
