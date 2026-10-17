# Workstream 3: Foundation Grant & Sponsor Scoring Model (`02_Scoring_Rules`)
**Author:** Pod B

---

## 1. Overview & Purpose
To transform raw mid-tier foundation and sponsor entries into a predictable 12-month funding pipeline, Pod B implemented a deterministic, weighted scoring model. 

This model evaluates potential sponsors across **four core operational criteria** totaling 100 points, ensuring that only high-fit, active funding bodies are prioritized for learner seat sponsorships.

---

## 2. Weighted Scoring Criteria & Breakdown

### A. Sponsorship Fit Alignment / Ask Fit (Max Weight: 35%)
Evaluates whether the organization funds tech skills training, youth employability, and sponsored learner seats directly, rather than providing broad organizational funding.
* **Explicit focus on tech training & sponsored seats:** 35 points
* **Broad youth employment/education focus:** 25 points
* **General community development:** 15 points
* **No clear mission alignment:** 0 points

### B. Recency & Activity Proof (Max Weight: 25%)
Ensures the foundation is actively disbursing funds and has open grant windows, rather than acting as a dormant dead end.
* **Verified public funding activity or open call within the last 30–90 days:** 25 points
* **Activity within 90–180 days:** 15 points
* **Activity older than 180 days (dormant):** 0 points *(Note: Inactive entries drop directly to `03_Rejected_And_Why`)*.

### C. Decision-Maker Reachability (Max Weight: 20%)
Measures the accessibility of a named contact person (e.g., CSR Manager, Program Officer) with a direct communication channel.
* **Named decision-maker with active direct channel/LinkedIn:** 20 points
* **Named contact with general institutional email:** 12 points
* **Generic info/support address only:** 5 points
* **No contact details available:** 0 points

### D. Registration & Eligibility Feasibility (Max Weight: 20%)
Measures whether Afriment can successfully apply without facing complex local registration barriers or restrictive consortium rules.
* **Fully eligible without local registration blockers:** 20 points
* **Eligible via standard international partner structures:** 10 points
* **Complex local registration blockers or giant international-only consortia:** 0 points

---

## 3. Pipeline Banding & Action Thresholds
Once total weighted scores (0–100) are calculated, foundations are immediately sorted into operational tiers:

| Total Score Range | Priority Tier | Operational Action & Destination |
| :--- | :--- | :--- |
| **80 – 100** | **Tier 1** | Top priority; immediately populates the **Top 10 Shortlist Memo** and top 12-month calendar priority. |
| **60 – 79** | **Tier 2** | Active pipeline target; populates the main `01_Foundations` master tab and `02_Funding_Calendar`. |
| **40 – 59** | **Tier 3** | Monitor list for future follow-up when new funding calls open. |
| **Below 40** | **Rejected** | Excluded from active pipeline; logged with rationale in `03_Rejected_And_Why`. |

---

## 4. Excel Implementation Formula Reference
The composite score and tiers were automated in the master workbook using standardized logic:
* **Priority Score Calculation:** `=SUM([@[Ask_Fit_Score]:[Eligibility_Score]])`
* **Automated Tier Assignment:** `=IF(ISBLANK([@Priority_Score]), "", IFS([@Priority_Score]>=80, "Tier 1", [@Priority_Score]>=60, "Tier 2", [@Priority_Score]>=40, "Tier 3", TRUE, "Rejected"))`
