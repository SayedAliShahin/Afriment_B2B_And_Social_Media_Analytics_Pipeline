# Afriment B2B & Social Analytics Pipeline
**Role:** Operational Data Analyst / Pod B Engineering Lead (Afriment Data Analytics Internship)[cite: 1]

## 1. Business Context & Challenge
Afriment operates a dual-model ecosystem: training tech talent and connecting verified portfolios with B2B employers and partners[cite: 1]. Across 5 distinct workstreams (social posts, B2B company pipelines, foundation grants, course markets, and tech communities), raw inputs arrived unstructured, unvalidated, and prone to breaking downstream dashboards[cite: 1]. 

Pod B served as the **Data Engine Room**, responsible for data cleaning, relational schema design, deterministic scoring rules, and metric validation[cite: 1].

## 2. System Architecture & Workflow
Our team operated in a strict dependency chain to ensure zero data corruption:
Raw Inputs (Pod A / Exports) ---> Pod B Engine (Clean, Standardize, Rule-Score) ---> Outputs (Pod C Dashboards / SQL Models)[cite: 1]

* **The Source Rule:** Raw exports in `/00_Source_Data/` were treated as read-only. Nothing was ever edited directly in the source[cite: 2].
* **Quality Gates:** Every data batch underwent a mandatory 15-minute QA check to eliminate trailing spaces, enforce YYYY-MM-DD date formats, fix numbers stored as text, and eliminate duplicate entries[cite: 2].

## 3. Workstream Deep-Dives & Technical Execution

### Workstream 1: Social Media Performance Autopsy (~305 Posts)
* **The Problem:** 12 months of historical LinkedIn exports lacking standardized taxonomy and containing broken text rows due to raw caption line breaks[cite: 1, 2].
* **The Execution:** Created `04_Classification_Rules` to tag Media Formats and Content Pillars[cite: 1, 2]. Built `02_Clean_Posts` to track metrics and utilized median engagement rates per 1,000 impressions to prevent viral anomalies from skewing performance baselines[cite: 1, 2].
* **The Output:** A fully cleaned, growing full-year dataset and teardowns of top and bottom-performing posts[cite: 1, 2].

### Workstream 2 & 3: B2B & Foundation Scoring Pipelines
* **The Problem:** Unfiltered lists of target enterprises and grant providers lacking qualification or contact verification[cite: 1].
* **The Execution:** Designed a live weighted scoring model (`02_Scoring_Rules`) to rank companies and foundations based on active funding windows, grant sizes, and verified decision-maker emails[cite: 1].
* **The Output:** A verified pipeline of Tier-1 company partners ($Score \ge 80$) and a 12-month grant funding calendar[cite: 1].

### Workstream 4: Skills Market Intelligence Model
* **The Problem:** A market disconnect between academy course offerings and actual employer hiring demands across the region[cite: 1].
* **The Execution:** Ingested employer job postings and academy course catalogs[cite: 1]. Modeled demand vs. supply metrics to compute skill heat ratings and categorized them into a 2x2 matrix (*Hot Cakes, The Gap, Oversupplied, Dormant*)[cite: 1].
* **The Output:** Strategic curriculum adjustments identifying high-demand execution skills[cite: 1].

## 4. Key Insights & Strategic Recommendations
* **Content Strategy:** Educational carousels generated significantly higher sustainable engagement than standard promotional single images[cite: 1].
* **Curriculum Pivot:** Shifted focus away from oversaturated generic tech tracks toward high-demand, low-supply domains identified in the supply-demand matrix[cite: 1].
