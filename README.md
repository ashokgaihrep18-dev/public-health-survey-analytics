# Public Health Survey Analytics Dashboard

## 📋 Executive Project Summary
This project transforms a complex household dataset (**300 survey responses, 111 attributes**) into a highly responsive, relational Power BI data model. The 7-page interactive dashboard tracks core public health metrics, isolating the behavioral, environmental, and clinical factors that drive maternal care, child illness, and immunization success rates.

---

## 🖥️ Dashboard Page-by-Page Breakdown

### 📊 Page 1: Overview
An introductory landing page providing a high-level summary of the surveyed cohort, helping public health managers filter metrics by regions instantly.

<img width="1232" height="707" alt="image" src="https://github.com/user-attachments/assets/1cbd8152-981a-4964-8287-deb241c4501e" />


*   **Visuals Implemented:**
    *   **Card Visuals:** Total households surveyed, average maternal age, and child gender distributions.
    *   **Clustered Bar Chart:** Breaks down survey volume across different localized geographic data clusters.
    *   **Slicers:** Interactive filters for Interviewer Name, Cluster No., and Mother's Education levels.
*   **Key Data Insight:** Establishes a baseline baseline of 300 surveyed families. This page acts as the main filter hub where all subsequent disease and treatment rates can be cross-analyzed by regional clusters or maternal education groups.

---

### 🩺 Page 2: Health Analysis
Focuses on general disease exposure and vector tracking, exposing critical healthcare challenges across households.

<img width="1225" height="684" alt="image" src="https://github.com/user-attachments/assets/bb41a944-fe0a-4afc-ada3-7bfefd13fc1e" />


*   **Visuals Implemented:**
    *   **100% Stacked Bar Chart:** Tracks regional variations in bed-net ownership across clusters, highlighting structural supply-chain distribution.
    *   **Side-by-Side KPI Cards:** Compares the total percentage of households that *own* bed-nets vs. the actual percentage of children who *slept under them* the previous night.
    *   **Treemap:** Segregates the common treatment options sought out by caregivers when a child falls ill.
*   **Key Data Insight:** While physical bed-net ownership is remarkably high at over 85%, cross-analysis reveals a usage gap. High-ownership clusters frequently report children not sleeping under them, pointing to a clear need for localized community education alongside inventory drops.

---

### 🧪 Page 3: Diarrhea Comparative Analysis
Focuses specifically on environmental health factors, analyzing how clean water access and handwashing habits impact early childhood illness.

<img width="1220" height="680" alt="image" src="https://github.com/user-attachments/assets/8edeba1e-dea9-416d-8f28-2f62e2d7a3af" />


*   **Visuals Implemented:**
    *   **Clustered Bar Chart:** Cross-references specific handwashing habits (e.g., washing hands before preparing food vs. after cleaning a child) directly against active diarrhea cases.
    *   **Donut Chart:** Breaks down the absolute percentage distribution of diarrhea cases (Yes vs. No) in the last two weeks.
    *   **Multi-Row KPI Cards:** Displays summaries of drinking water sources and seasonal water availability.
*   **Key Data Insight:** Over 26% of the surveyed children experienced diarrhea within the last two weeks. The data shows a sharp drop-off in active illness for households where caregivers practice handwashing specifically **before preparing food** compared to general household sanitization.

---

### ⏱️ Page 4: Time Analysis
Tracks timeline-based clinical behaviors, measuring caregiver delay times before seeking formal medical care for severe symptoms.

<img width="1209" height="682" alt="image" src="https://github.com/user-attachments/assets/5bff88b2-6a8b-4bde-8754-a021dcbf4bf1" />


*   **Visuals Implemented:**
    *   **Stacked Column Chart:** Measures caregiver delay times (e.g., Same Day, Next Day, 2+ Days) before seeking medical advice for a sick child.
    *   **Trend/Line Chart:** Visualizes dynamic timing patterns of survey interviews and reporting across the collection period.
*   **Key Data Insight:** Reveals a significant bottleneck in early care-seeking: a notable percentage of caregivers wait until the "Next Day" or later to seek medical assistance for acute symptoms like high fevers or severe coughs, pinpointing exactly where localized clinical access awareness is needed.

---

### 🎓 Page 5: Education Analysis
Cross-analyzes social determinants of health, mapping how a mother's formal education level directly influences household healthcare compliance.

<img width="1217" height="679" alt="image" src="https://github.com/user-attachments/assets/fe4f4603-be2d-4f98-b8f6-3782c38b4ffe" />


*   **Visuals Implemented:**
    *   **Clustered Column Chart:** Compares health awareness variables, disease prevention actions, or survey responses grouped by maternal education milestones (No Education, Primary, Secondary, Higher).
    *   **Matrix Visual:** Provides drill-down capabilities for granular cluster tracking based on awareness vs. educational status.
*   **Key Data Insight:** Highlights a clear protective correlation: households where mothers have higher educational backgrounds demonstrate significantly stronger compliance with preventive health practices (like vaccine timeline adherence and sanitization standards).

---

### 🤰 Page 6: Breastfeeding Analysis
Evaluates neonatal nutritional habits directly following labor and tracks maternal care patterns.

<img width="1210" height="681" alt="image" src="https://github.com/user-attachments/assets/0dea9072-03ba-4fa3-9442-ee305ccc8e0b" />


*   **Visuals Implemented:**
    *   **Bar Chart:** Tracks the timing of initial breastfeeding actions ("Within First Hour" vs. "After First Hour").
    *   **Donut Chart:** Classifies birth assistance categories (e.g., Doctors/Midwives vs. Traditional Birth Attendants) relative to early feeding decisions.
    *   **Line Chart:** Plots infant birth weight trends against ongoing exclusive breastfeeding durations.
*   **Key Data Insight:** Demonstrates the impact of professional medical staff support, showing that infants delivered with the assistance of doctors or nurses have a significantly higher rate of starting breastfeeding within the critical first hour of life.

---

### 💉 Page 7: Immunization Deep Dive
A clinical monitoring page mapping vaccination completion pathways chronologically to pinpoint programmatic drop-offs as children age.


<img width="1215" height="690" alt="image" src="https://github.com/user-attachments/assets/72ca9bc2-b837-4787-ab8d-a4911480d6fc" />


*   **Visuals Implemented:**
    *   **Funnel Chart:** Showcases sequential drop-offs across chronological vaccine milestones, starting from birth (BCG, Polio 0) through DPT rounds to Measles.
    *   **Matrix Visual:** Allows deep-dive filtering by cluster and interviewer names to track physical vaccine card availability rates.
*   **Key Data Insight:** Tracking immunizations sequentially exposes a clear attrition pattern. While initial birth doses show high compliance, completion rates decline by the time final booster targets (like Measles) are due, highlighting where health teams should focus outreach campaigns.

---

## 🛠️ Data Modeling & Engineering Architecture
To prevent slow performance and filter-bleeding, this project moves away from a "flat table" format and applies standard relational modeling:
*   **The Star Schema:** Centralizes the core survey transactions (`Sample_Survey_Data`) and links them to detached dimension lookup tables.
*   **Calculated Measures:** Built an explicit `_All Measures` table to house core public health indicators using advanced DAX logic (e.g., `DIVIDE` and `CALCULATE` functions to isolate complex survey strings safely).
