# Milwaukee Police Department: Law Enforcement Analytics & Patrol Resource Allocation Portfolio

An end-to-end law enforcement operations portfolio analyzing **112,283 police incident records** in Milwaukee. This project bridges backend data engineering, temporal analysis, dynamic shift staffing models, and executive command policy reporting to optimize patrol deployment without increasing agency headcount.

---

## Project Directory & Deliverables

* **Live Tableau Dashboard:** [Milwaukee OMAP Tactical Briefing Dashboard](https://public.tableau.com/app/profile/emma.dumonseau/viz/MilwaukeeCrimeOMAPAnalysis/Dashboard1) *(Interactive spatial density, hot-spot clustering, and shift filters)*
* **Executive Policy Brief:** [`deliverables/MPD_Patrol_Staffing_Review.pdf`](https://github.com/emmadumonseau/Milwaukee-Police-Department-Law-Enforcement-Analytics-Patrol-Resource-Allocation-Portfolio/blob/main/Milwaukee%20Police%20Department%20Staffing%20Analysis.pdf) 
* **Executive Excel Workbook:** [`deliverables/Milwaukee_OMAP_Executive_Model.xlsx`](https://github.com/emmadumonseau/Milwaukee-Police-Department-Law-Enforcement-Analytics-Patrol-Resource-Allocation-Portfolio/blob/main/Milwaukee%20Crime%20Analysis%20Summary.xlsx) *(4-tab operational model with KPI scorecards and trend visualizations)*
* **Python Analytics Pipeline:** [`scripts/omap_end_to_end_pipeline.py`](https://github.com/emmadumonseau/Milwaukee-Police-Department-Law-Enforcement-Analytics-Patrol-Resource-Allocation-Portfolio/blob/main/Milwaukee_OMAP_Pipeline.ipynb) *(Automated raw data ingestion, workload modeling, and time-series forecasting)*
* **Full Dataset (112K Incidents):** [Download Milwaukee Crime GeoJSON (Google Drive)](https://drive.google.com/file/d/1j4-NWdgHqqhZbAOyqAmVBkkan1YbDuoy/view?usp=sharing) *(Full production dataset)*
---

## Executive Overview & Problem Statement

This project addresses a core operational challenge: **patrol schedules do not align with actual call-for-service demand.** While officers are distributed evenly across standard shifts, evening and late-night hours experience severe volume concentration. By combining Python data pipelines, Excel operational modeling, and Tableau visualization, this project establishes a scalable framework to rebalance resources and deploy targeted street-level interventions.

---

## Data Pipeline & Methodology

* **Data Ingestion & Cleaning (ETL):** Ingests raw GeoJSON incident records, standardizes schemas, parses timestamps, and extracts temporal attributes (hour, day of week, monthly periods).
* **Shift Workload Distribution:** Aggregated incidents into traditional operational shifts to compute exact workload shares and identify operational friction points.
* **Time-Series & Moving Average Modeling:** Calculated 3-month rolling averages (`3_Month_MA`) to smooth out monthly noise and evaluate long-term seasonal crime trends and recurring summer volume surges.
* **Resource Allocation Modeling:** Developed a dynamic staffing framework based on a 100-officer baseline to simulate empirical force rebalancing.

---

## Analytical Insights & Findings

1. **The Evening Shift Strain:**
   * **2nd Shift (16:00–00:00)** is the primary demand driver, absorbing **41.2% of total citywide incident volume** ($46,261$ calls). Officers experience constant call-to-call friction with limited time for proactive community policing.

2. **The Midnight Call Spike:**
   * **Hour 00:00 (12:00 AM)** is the single busiest hour of the day, accounting for **9.57% of all incidents** ($10,746$ calls), coinciding directly with the 2nd-to-3rd shift handover window.

3. **Predictive Seasonal Rhythms:**
   * Call volume follows a predictable annual curve, climbing steadily through spring (~8% month-over-month) and peaking sharply in **July ($3,700$–$4,500$ calls/month)**—representing a **58% volume increase over winter lows**.

---

## Recommended Interventions & Staffing Model

* **Overlapping "Power Shift" (18:00–02:00):** Establishes a dedicated surge team to absorb the evening rush and midnight call peak without expanding overall headcount.
* **Dynamic Force Rebalancing (100-FTE Baseline):** Shift allocation shifted from rigid equal splits to empirically driven ratios:
  * **1st Shift (Day | 08:00–16:00):** 26 Officers
  * **2nd Shift (Evening | 16:00–00:00):** 34 Officers
  * **Power Shift (Overlay | 18:00–02:00):** 18 Officers
  * **3rd Shift (Night | 00:00–08:00):** 22 Officers
* **Targeted Street Tactics:** Implementation of 15-minute hotspot patrol stops, tactical LED lighting deployment in dark alleys, and rolling field handovers to maintain continuous street coverage.

---
