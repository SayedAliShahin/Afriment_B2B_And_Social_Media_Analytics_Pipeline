# Workstream 4: Verdict Definition & Criteria (`Verdict_Definition_Criteria`)
**Author:** Pod B

---

## 1. Overview & Purpose
To categorize and rank skill domains objectively, Pod B utilized a 2x2 market matrix comparing **Employer Demand** against **Training Supply Share**. Every skill is assigned one of four definitive verdicts to guide Afriment's curriculum strategy.

---

## 2. The Four Verdict Categories

### A. The Gap (Highest Priority)
* **Condition:** High Employer Demand AND Low Supply Share.
* **Definition:** Employers actively recruit for these skills, but few academies teach them. 
* **Strategic Action:** Prime commercial opportunity; highest priority for Afriment to build and launch courses.

### B. Hot Cake
* **Condition:** High Employer Demand AND High Learner/Supply Demand.
* **Definition:** High hiring volume matched with high market interest.
* **Strategic Action:** Highly profitable, but faces fierce competition from existing bootcamps.

### C. Oversupplied
* **Condition:** Low Employer Demand AND High Supply Share.
* **Definition:** Academies are heavily marketing and selling courses that do not translate into actual job openings.
* **Strategic Action:** Avoid or pivot away from these domains to protect student outcomes.

### D. Dormant
* **Condition:** Low Employer Demand AND Low Learner Demand.
* **Definition:** Minimal employer hiring and low student interest.
* **Strategic Action:** Ignore entirely.

---

## 3. Excel Automation Formula Reference
To automate verdicts programmatically in `02_Demand_vs_Supply`:
```excel
=IF(AND(I2>=MEDIAN($I$2:$I$20), D2<MEDIAN($D$2:$D$20)), "The Gap", IF(AND(I2>=MEDIAN($I$2:$I$20), G2>=MEDIAN($G$2:$G$20)), "Hot Cake", 
 IF(AND(D2>=MEDIAN($D$2:$D$20), I2<MEDIAN($I$2:$I$20)), "Dormant"))) "Oversupplied", ```>
