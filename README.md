# RXO Delivery Hub SLA Performance Tracker

## Overview

An Excel-based operational analytics dashboard that monitors Service Level Agreement (SLA) compliance across delivery hubs and identifies escalation risks. This project demonstrates data analysis, pivot table construction, and executive-level reporting in a transportation logistics context.

**Dataset:** 420 shipment records across 6 delivery hubs (Apr–Jun 2026)  
**Key Finding:** Phoenix hub trails network average by 13 percentage points (84% vs 97%), with disproportionate impact on VIP customer accounts.

---

## Project Structure

### Files Included
- **Hub_SLA_Data_Tracker.xlsx** — Main workbook containing:
  - `Shipments` — Raw shipment data (420 records, 11 columns)
  - `Pivot_Hub_SLA` — SLA compliance by delivery hub
  - `Pivot_Carrier_Breaches` — Breach patterns by carrier
  - `Pivot_VIP_Trend` — VIP breach trend over time
  - `Scorecard` — Executive summary with KPIs, color-coded hub performance, and visualization

---

## Key Findings

| Metric | Value | Insight |
|--------|-------|---------|
| **Overall SLA Compliance** | 90% | 10% breach rate across network |
| **Best Performing Hub** | Chicago (97%) | Reference standard for comparison |
| **Worst Performing Hub** | Phoenix (84%) | 13-point gap vs best-in-class |
| **Secondary Concern** | Newark (85%) | Consistently underperforming |
| **VIP Impact** | 20 of 41 breaches (49%) | Disproportionate escalation risk |
| **Peak Period** | May | VIP breaches nearly double vs April/June |
| **Problem Carrier** | Redline Logistics (83%) | 11 points below network average |

---

## Dataset Details

### Source Data (Shipments sheet)
- **Shipment ID:** Unique identifier
- **Order Date:** Placement date (Apr–Jun 2026)
- **Hub:** Delivery location (Atlanta, Chicago, Dallas, Los Angeles, Newark, Phoenix)
- **Customer:** 12 accounts including VIPs (Walmart, Target, Coca-Cola) and regional accounts
- **Customer Type:** VIP or Standard
- **Carrier:** Transportation provider
- **Service Level:** Standard (3 days), Two-Day, or Express (1 day)
- **Promised Delivery Date:** SLA commitment window
- **Actual Delivery Date:** Real delivery date
- **Status:** Delivered, Late, or Exception
- **Units:** Shipment volume

### Calculated Columns
- **Days Late:** Actual date minus promised date (negative = early, 0 = on-time, positive = late)
- **On-Time?:** Binary SLA status (Met / Breached)
- **Met Flag:** Numeric version (1 = Met, 0 = Breached) — enables pivot table percentages
- **Escalation Risk:** Tiered flag (High = VIP + Breach, Medium = Breach, Low = On-Time)

---

## Analysis Approach

### 1. Pivot Table: Hub SLA Performance (`Pivot_Hub_SLA`)
**Purpose:** Identify which delivery hubs are missing SLA commitments

- **Rows:** Hub names
- **Values:** Average of Met Flag (%), Count of shipments
- **Sort:** Worst-to-best (reveals Phoenix and Newark as outliers)

**Insight:** Phoenix and Newark breach at 2–3x the rate of best-performing hubs.

### 2. Pivot Table: Carrier Breaches (`Pivot_Carrier_Breaches`)
**Purpose:** Determine whether carrier performance is a root cause

- **Rows:** Carrier names
- **Values:** Average of Met Flag (%), Count of shipments
- **Filter:** Breaches only

**Insight:** Redline Logistics carries a disproportionate share of breaches (83% vs 90% network average).

### 3. Pivot Table: VIP Breach Trend (`Pivot_VIP_Trend`)
**Purpose:** Track whether escalation risk is trending up or down

- **Rows:** Order Date (grouped by month)
- **Columns:** Customer Type (VIP vs Standard)
- **Values:** Count of breaches (filtered to "Breached" only)

**Insight:** VIP breaches spike in May (9 VIP breaches vs 4 standard), indicating heightened escalation risk mid-quarter.

### 4. Executive Scorecard (`Scorecard`)
**Purpose:** Present findings in a format suitable for leadership decision-making

- **KPI Cards:** Overall SLA %, total shipments, VIP breaches, worst hub
- **Hub Performance Table:** SLA % by hub with conditional formatting (green 95%+, yellow 90–95%, red <90%)
- **Bar Chart:** Visual ranking of hub performance with data labels

---

## Key Insights & Recommendations

### Finding: Phoenix Hub Performance Gap

Phoenix hub is meeting only **84%** of its SLA commitments versus **97%** at our best hub, Chicago—that's a **13-point gap**. The impact is disproportionately hitting our VIP accounts: in May alone, VIP breaches nearly doubled compared to standard shipments. Across the data, **20 of our 41 total breaches** involved VIP customers, which raises escalation risk with high-value clients.

### Recommended Actions

1. **Carrier Performance Audit at Phoenix**  
   Identify which carriers are driving the SLA miss and whether contract/capacity renegotiation is needed. Redline Logistics shows elevated breach rates network-wide and may be a primary factor.

2. **Temporary VIP Volume Reallocation**  
   Route high-priority VIP shipments to Chicago and Los Angeles (97% and 95% SLA respectively) while Phoenix executes corrective measures.

3. **Root-Cause Analysis**  
   Determine whether the Phoenix underperformance stems from staffing constraints, process gaps, systems/visibility issues, or carrier capacity mismatches.

---

## How to Use This Workbook

### For Analysts
1. Open the `Shipments` sheet to review raw data or add new records
2. Refresh pivots (Data → Refresh All) when new shipment data is added
3. Monitor trends in `Pivot_VIP_Trend` for escalation risk signals
4. Update the Scorecard KPIs monthly to track progress

### For Stakeholders
1. Review the `Scorecard` sheet for a 10-second summary
2. Use the bar chart to visually identify underperforming hubs
3. Reference the "So What?" section for recommended actions
4. Share the scorecard with customer success and operations teams for alignment

### For Interviewers / Hiring Managers
This project demonstrates:
- **Data Analysis:** Structured approach to identifying root causes (hub vs. carrier performance)
- **Excel Proficiency:** PivotTables, calculated columns, conditional formatting, visualization
- **Business Acumen:** Connecting operational metrics (SLA breaches) to customer impact (VIP escalation risk)
- **Storytelling:** Translating data into actionable recommendations
- **Scalability:** Design supports adding new hubs, carriers, or time periods without structural changes

---

## Technical Details

### Tools & Functions Used
- **PivotTables:** Multi-dimensional aggregation and trend analysis
- **Formulas:** IF, AND, COUNTIFS for calculated columns and KPI computation
- **Conditional Formatting:** 3-color scale to highlight performance tiers
- **Charts:** Column chart with data labels for executive communication
- **Table Format:** Structured references and auto-expanding ranges for maintainability

### Data Quality Notes
- All dates validated as real dates (not text)
- Met Flag column (0/1) enables clean percentage calculations in pivots
- No null values; 420 complete records
- Hubs, carriers, and customers are consistent across data period

---

## Portfolio Context

This project was built as a pre-interview exercise for an Associate Analyst, Customer Accounts role at RXO (a $7B+ transportation logistics provider). It demonstrates the core competencies required for the role:

- **Data Analysis:** SLA monitoring and escalation risk identification
- **Reporting:** Executive-ready dashboards and scorecards
- **Stakeholder Management:** Translating operational data for both ops and leadership audiences
- **Problem-Solving:** Structured approach to identifying root causes and recommending actions

---

## Next Steps (Potential Extensions)

- **Time-Series Forecasting:** Predict future breach rates by hub using trend analysis
- **Root-Cause Deep Dive:** Correlate specific carriers, service levels, or customer types with breach patterns
- **Automation:** Connect to live shipment data via API or database for real-time monitoring
- **Power BI Migration:** Migrate to interactive dashboards for broader stakeholder access
- **Geographic Visualization:** Map hub performance by region to identify systemic patterns

---

## Contact & Questions

Built as a data analytics portfolio project in June 2026.  
Questions about methodology, findings, or Excel implementation? Open an issue or reach out.

---

**Skills Demonstrated:** Excel (Advanced) | Data Analysis | PivotTables | Conditional Formatting | Executive Reporting | Business Analytics
