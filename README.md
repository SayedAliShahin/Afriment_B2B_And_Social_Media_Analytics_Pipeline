# Afriment B2B & Social Analytics Pipeline
**Role:** Operational Data Analyst / Pod B Engineering Lead (Afriment Data Analytics Internship)[cite: 1]

---

## 1. Business Context & Challenge
Afriment operates a dual-model ecosystem: training tech talent and connecting verified profiles with B2B employers and partners. Across 5 distinct workstreams (social posts, B2B company pipelines, foundation grants, course markets, and tech communities), raw inputs arrived unstructured, unvalidated, and prone to breaking downstream dashboards. 

Pod B served as the **Data Engine Room**, responsible for validation, data cleaning, relational schema design, deterministic scoring rules, and metric validation.

---

## 2. System Architecture & Workflow
Our team (Pod B) operated in a strict dependency chain to ensure zero data corruption:
*Raw Inputs (Pod A / Exports)* **-->** *Pod B Engine (Clean, Standardize, Rule-Score)* **-->** *Outputs (Pod C Dashboards / SQL Models)*.

* **The Source Rule:** Raw exports in `/00_Source_Data/` were treated as read-only. Nothing was ever edited directly in the source.
* **Quality Gates:** Every data batch underwent a mandatory 15-minute QA check to eliminate trailing spaces, enforce `YYYY-MM-DD` date formats, fix numbers stored as text, and eliminate duplicate entries.

> **Note on Data Privacy:** In compliance with the Afriment internship NDA, all company names, contact emails, and absolute metrics in the sample CSV files have been fully fictionalized or anonymized. The schemas, scoring formulas, and validation rules remain identical to the production pipeline.

---

## 3. Workstream Deep-Dives & Technical Execution

### Workstream 1: Social Media Performance Autopsy (305 Posts)
* **The Problem:** 12 months (2025-09-09 to 2026-08-31) of historical LinkedIn exports lacking standardized classifications like `Media_Format` and `Content_Pillar`, making it difficult to isolate what drove audience growth.
* **The Execution:**
  1. Created `04_Classification_Rules` to tag Media Formats and Content Pillars and classified all posts through strict multi-person reviews.
  2. Built `02_Clean_Posts` to track metrics and utilized median engagement rates per 1,000 impressions to prevent viral anomalies from skewing performance baselines.
  3. Analyzed engagement performance across quarters and post types.
* **Visual Evidence:**
  ![WS1 Engagement Trend](visualisations/ws1_engagement_by_format.png)
* **Key Findings & Strategic Recommendations:**
  * **Finding:** Document carousels outperformed static text and images by 3.2x, with Fall (Sep–Dec 2025) yielding the highest engagement window.
  * **Recommendation:** **Adopt** a 4-week pilot reallocating content creation resources toward educational document carousels and student testimonials.

---

### Workstream 2, 3 & 5: B2B, Foundation & Community Scoring Pipelines
* **The Problem:** Identifying high-intent partner companies, active funding foundations, and aligned career communities without relying on generic web directory lists.
* **The Execution:** Designed live weighted scoring models (`02_Scoring_Rules`) to rank companies and foundations based on online social presence, evidence of recent activity, active funding windows, grant sizes, and verified decision-maker channels. For communities, applied a non-negotiable filter to drop paid-training competitors.
* **Key Findings & Strategic Recommendations:**
  * **Finding:** Yielded a verified pipeline of 40 Tier-1 companies, 19 contactable foundation sponsors, and 33 pitch-ready communities.
  * **Recommendation:** **Adopt** value-led joint event partnerships with pitch-ready communities, and prioritize Tier-1 enterprise leads for Pod C executive pitch briefs.

---

### Workstream 4: Skills Market Intelligence Model
* **The Problem:** A structural market gap between tech academies' course offerings and actual employer hiring demands across 6 African countries[cite: 1].
* **The Execution:**
  1. Ingested employer job postings and academy course catalogs[cite: 1].
  2. Modeled demand vs. supply metrics to compute skill heat ratings and categorized them into a 2x2 matrix (*Hot Cakes, The Gap, Oversupplied, Dormant*)[cite: 1].
* **Visual Evidence:**
  ![WS4 Market Matrix](visualisations/ws4_demand_supply_matrix.png)
* **Key Findings & Strategic Recommendations:**
  * **Finding:** Generic Data Analytics suffers from severe market oversupply, whereas Business Analysis, Project Management, and No-Code/Automation sit firmly in "The Gap" and "Hot Cake" quadrants with high heat ratings.
  * **Recommendation:** **Adapt** future curriculum development by blending or pivoting toward high-demand, low-supply domains like Business Analysis and Project Management to maximize graduate placement rates.

---

## 4. Repository Structure & Deliverables
```text
├── README.md                           # Complete project case study (Overview, Methods, Impact)
├── docs/                               # Scoring rubrics, cleaning protocols, and classification rules
│   ├── data_cleaning_protocol.md
│   ├── 02_Scoring_Rules_WS2.md
│   ├── 02_Scoring_Rules_WS3.md
│   └── Verdict_Definition_Criteria.md
├── workstream_1_social/                # WS1 data folder
│   ├── SYNTHETIC_WS1_Posts_SAMPLE.csv
│   └── classification_rules.md
├── workstream_2_company_pipeline/      # WS2 data folder
│   ├── ANONYMIZED_WS2_Pipeline_SAMPLE.csv
│   └── scoring_model.md
└── visualisations/                     # Annotated charts, matrices, and presentation exports
    ├── ws1_engagement_by_format.png
    └── ws4_demand_supply_matrix.png
