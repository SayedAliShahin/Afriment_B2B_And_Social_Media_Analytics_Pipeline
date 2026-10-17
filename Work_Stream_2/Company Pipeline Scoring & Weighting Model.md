# Workstream 2: Company Pipeline Scoring & Weighting Model (02_Scoring_Rules)
**Author:** Pod B

---

## 1. Overview & Purpose
To transform raw company entries from Pod A into an actionable B2B partnership pipeline, Pod B implemented a deterministic, weighted scoring model (02_Scoring_Rules). 

This model removes subjective bias by grading every company across **five core operational criteria** totaling 100 points, ensuring that only high-intent, highly qualified leads reach Pod C for executive pitch briefs.

---

## 2. Weighted Scoring Criteria & Breakdown

### A. ICP Match Strength (Max Weight: 30%)
Evaluates how closely the target organization aligns with Afriment's ideal customer/partner profile.
* **Startup Builder (0–3 years old, founder-led, 1–20 staff, missing operational documentation):** 30 points
* **Resource-Constrained SME:** 25 points
* **Growth-Focused Startup:** 20 points
* **Scaling Ops Leader:** 15 points
* **No clear match:** 0 points

### B. Number of Verified Pain Signals (Max Weight: 25%)
Quantifies the presence of visible operational bottlenecks that Afriment products can solve. *(Note: Signals must include verifiable evidence links to qualify).*
* **3 verified signals:** 25 points
* **2 verified signals:** 17 points
* **1 verified signal:** 8 points
* **No verified signals:** 0 points

### C. Decision-Maker Reachability (Max Weight: 20%)
Measures the directness and accessibility of the contact channel for outreach.
* **Named person with an active LinkedIn profile:** 20 points
* **Named person, but no direct channel:** 12 points
* **Generic info/support address only:** 5 points
* **No contact details available:** 0 points

### D. Recency of Activity (Max Weight: 15%)
Ensures target companies are active businesses rather than dormant operations.
* **Any public activity within the last 30 days:** 15 points
* **Activity within 90 days:** 9 points
* **Activity older than 180 days (classified as dormant):** 0 points

### E. Size Fit / Headcount Alignment (Max Weight: 10%)
Rewards companies falling directly into the optimal operating headcount band.
* **Inside the ICP headcount band (1–20 staff):** 10 points
* **One band out:** 5 points
* **Far out (Enterprise scale):** 0 points

---

## 3. Pipeline Banding & Action Thresholds
Once total weighted scores (0–100) are calculated automatically via Excel formulas, companies are immediately routed into operational tiers:

| Total Score Range | Priority Tier | Operational Action & Destination |
| :--- | :--- | :--- |
| **80 – 100** | **Tier 1** | Top of the outreach list; immediately routed to Pod C for Executive Pitch Brief creation. |
| **60 – 79** | **Tier 2** | Active pipeline target for secondary wave outreach. |
| **40 – 59** | **Tier 3** | Maintained in backup inventory for future follow-up. |
| **Below 40** | **Rejected** | Excluded from active pipeline; logged with rationale in `03_Rejected_And_Why` to prevent duplicate research. |

---

## 4. Excel Implementation Formula Reference
The composite score and tiers were automated in the master workbook using standardized logic:
* **Priority Score Calculation:** `=SUM([@[ICP_Score]:[Size_Fit_Score]])`
* **Automated Tier Assignment:** `=IF(ISBLANK([@Priority_Score]), "", IFS([@Priority_Score]>=80, "Tier 1", [@Priority_Score]>=60, "Tier 2", [@Priority_Score]>=40, "Tier 3", TRUE, "Rejected"))`
