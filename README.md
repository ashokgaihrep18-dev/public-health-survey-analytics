# Public Health Survey Analytics Dashboard

## 📋 Executive Project Summary
This project transforms a complex household dataset (**300 survey responses, 111 attributes**) into a structured, relational Power BI data model. The dashboard tracks core public health metrics, isolating the behavioral, environmental, and clinical factors that drive child health outcomes, disease transmission, and immunization success rates.

---

## 🖥️ Dashboard Page-by-Page Breakdown

### 🩺 Page 1: Diarrheal Disease & Wash Hygiene Tracking
*Focuses on environmental health factors, analyzing how clean water access and handwashing habits impact early childhood illness.*

<table>
  <tr>
    <td width="50%">
      <!-- REPLACE THE SOURCE PATH BELOW WITH YOUR ACTUAL IMAGE PATH ON GITHUB -->
      <img src="images/your_page_1_screenshot.png" alt="Diarrhea & Wash Dashboard Page" width="100%"/>
    </td>
    <td width="50%" valign="top">
      <h4>📊 Visuals Implemented:</h4>
      <ul>
        <li><b>Clustered Bar Chart:</b> Cross-references specific handwashing habits (e.g., washing hands before preparing food vs. after cleaning a child) directly against active diarrhea cases.</li>
        <li><b>Donut Chart:</b> Breaks down the absolute percentage distribution of diarrhea cases in the last two weeks.</li>
        <li><b>Multi-Row KPI Cards:</b> Displays high-level summaries of main drinking water sources and seasonal water availability.</li>
      </ul>
      <h4>💡 Key Data Insight:</h4>
      <p>Over 26% of the surveyed children experienced diarrhea within the last two weeks. The data shows a sharp drop-off in active illness for households where caregivers practice handwashing specifically <b>before preparing food</b> compared to general household sanitization.</p>
    </td>
  </tr>
</table>

---

### 🦟 Page 2: Malaria Exposure & Preventive Bed-Net Gaps
*Focuses on disease exposure and vectors, exposing critical gaps where physical medical inventory does not translate to protective household behaviors.*

<table>
  <tr>
    <td width="50%">
      <!-- REPLACE THE SOURCE PATH BELOW WITH YOUR ACTUAL IMAGE PATH ON GITHUB -->
      <img src="images/your_page_2_screenshot.png" alt="Malaria & Bed-Net Dashboard Page" width="100%"/>
    </td>
    <td width="50%" valign="top">
      <h4>📊 Visuals Implemented:</h4>
      <ul>
        <li><b>100% Stacked Bar Chart:</b> Tracks regional variations in bed-net ownership across clusters, highlighting structural supply-chain distribution.</li>
        <li><b>Side-by-Side KPI Cards:</b> Compares the total percentage of households that <i>own</i> bed-nets vs. the actual percentage of children who <i>slept under them</i> the previous night.</li>
        <li><b>Treemap:</b> Segregates the common malaria treatment options sought out by caregivers.</li>
      </ul>
      <h4>💡 Key Data Insight:</h4>
      <p>While physical bed-net ownership is remarkably high at over 85%, cross-analysis reveals a usage gap. High-ownership clusters frequently report children not sleeping under them, pointing to a clear need for localized community education alongside inventory drops.</p>
    </td>
  </tr>
</table>

---

### 💉 Page 3: Infant Immunization Funnel Drop-off Analysis
*A clinical monitoring page mapping vaccination completion pathways chronologically to pinpoint programmatic drop-offs as children age.*

<table>
  <tr>
    <td width="50%">
      <!-- REPLACE THE SOURCE PATH BELOW WITH YOUR ACTUAL IMAGE PATH ON GITHUB -->
      <img src="images/your_page_3_screenshot.png" alt="Immunization Funnel Dashboard Page" width="100%"/>
    </td>
    <td width="50%" valign="top">
      <h4>📊 Visuals Implemented:</h4>
      <ul>
        <li><b>Funnel Chart:</b> Showcases sequential drop-offs across chronological vaccine milestones, starting from birth (BCG, Polio 0) through DPT rounds to Measles.</li>
        <li><b>Matrix Visual:</b> Allows deep-dive filtering by cluster and interviewer names to track physical vaccine card availability rates.</li>
      </ul>
      <h4>💡 Key Data Insight:</h4>
      <p>Tracking immunizations sequentially exposes a clear attrition pattern. While initial birth doses show high compliance, completion rates decline by the time final booster targets (like Measles) are due, highlighting where health teams should focus outreach campaigns.</p>
    </td>
  </tr>
</table>

---

## 🛠️ Data Modeling & Engineering Architecture
To prevent slow performance and filter-bleeding, this project moves away from a "flat table" format and applies standard relational modeling:
* **The Star Schema:** Centralizes the core survey transactions (`Sample_Survey_Data`) and links them to detached dimension lookup tables.
* **Calculated Measures:** Built an explicit `_All Measures` table to housing core public health indicators using advanced DAX logic (e.g., `DIVIDE` and `CALCULATE` functions to isolate complex survey strings safely).
