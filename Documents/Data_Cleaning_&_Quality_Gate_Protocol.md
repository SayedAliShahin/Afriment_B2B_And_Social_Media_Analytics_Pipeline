# Data Cleaning & Quality Gate Protocol
**Role:** Operational Data Analyst / Pod B Engineering Lead (Afriment Data Analytics Internship)

---

## 1. Overview & Operational Principles
Because all data transformations and quality controls were executed in Excel and Google Sheets rather than Python, our team relied on a strict **15-minute Quality Gate checklist** applied to every incoming data batch. 

To prevent data corruption across our multi-workstream ecosystem, raw imports were treated as read-only (`00_Source_Data`), and every working tab passed through rigorous validation rules before export.

---

## 2. Core Data Cleaning & Validation Rules

### A. Eliminating Trailing Spaces (`=TRIM()`)
* **The Problem:** Hidden trailing spaces in text fields cause exact-match lookups, joins, and filters to fail silently.
* **The Solution:** Enforced a uniform application of the `=TRIM()` function across all imported text columns before running cross-workstream aggregations.

### B. Fixing Numbers Stored as Text
* **The Problem:** Numbers formatted as text sit left-aligned in cells and silently break downstream formulas, sums, and median calculations.
* **The Solution:** Forced numeric formatting across quantitative metrics (e.g., engagement counts, headcount estimates) and validated cell formats at the source.

### C. Standardizing Date Formats (`YYYY-MM-DD`)
* **The Problem:** Inconsistent date entries cause Excel to auto-scramble sequences or throw serial number errors across different operating systems.
* **The Solution:** Standardized all date fields to strict `YYYY-MM-DD` compliance to ensure correct chronological sorting and quarterly grouping.

### D. Preventing Inconsistent Taxonomies (Dropdown Enforcement)
* **The Problem:** Free-text entry leads to variations like "Data Analytics", "data analytics", and "Data Analysis" registering as separate categories.
* **The Solution:** Eliminated free-text typing for categories (such as *Content Pillars*, *Media Formats*, and *ICP Matches*) by implementing strict Excel Data Validation dropdown lists.

### E. Duplicate Key Normalization
* **The Problem:** Duplicate entries distort pipeline totals and lead tracking.
* **The Solution:** Performed duplicate checks on normalized unique keys (e.g., lowering company website domains with `www.` stripped and checking exact email strings).

### F. Provenance & Link Auditing
* **The Problem:** Unverified research or broken links compromise executive trust.
* **The Solution:** Maintained strict provenance tracking (`Collected_By`, `Date_Collected`, and `Evidence_URL`) for every row, with random spot-checks to eliminate dead URLs.

---

## 3. The Master Tab Architecture
To maintain absolute auditability, our workbooks were structured into standard operational tabs:
* `00_README`: Workbook metadata, assumptions, and transformation notes.
* `01_Raw_Posts`: Frozen, untouched copy of raw source data (read-only).
* `02_Clean_Posts`: The primary working tab containing cleaned, classified, and rule-scored rows.
* `04_Classification_Rules`: Written definitions ensuring uniform categorization across team members.
