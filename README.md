# SentinelSec B2B Lead Intake & Revenue Operations Pipeline
## Tara Suleiman 

## Project Overview
An automated Revenue Operations (RevOps) data pipeline designed to streamline B2B customer acquisition. This system eliminates manual data entry by capturing cold lead forms, processing them through automated routing layers, and feeding a live, 3-page executive Power BI application for instant sales and performance tracking.

## The Tech Stack & Architecture
* **Front-End Intake:** Form Automation (Web Form API)
* **Middleware:** Automation Workflows (Zapier)
* **Data Layer & Algorithmic Scoring:** Multi-variable weighted matrix engineered directly at the intake ingestion layer using nested logic arrays to calculate a composite lead value score capped at 100 points.
* **Business Intelligence:** Advanced Power BI Desktop (DAX, Star Schema Data Modeling, UI/UX Optimization)

## Dashboard Architecture & Insights
The reporting interface is structurally divided into three functional layers designed for operational decision-making:
1. **Executive Overview:** High-level visibility into total pipeline volume, past lead generation trends, macro conversion states, and company tier distributions.
2. **Sales Ops / Response Time:** Operational tracking utilizing complex DAX metrics (`SLA_Met` and `SLA_Breaches`) to highlight team response speeds, target response bottlenecks, and isolate a color-coded attention queue of accounts exceeding the 24-hour service-level agreement.
3. **Lead Quality / Scoring:** An algorithmic prioritization application that visualizes the outputs of the custom ingestion scoring engine. It maps the distribution patterns of incoming pipeline health and automatically surfaces a "Top Priority Sales Queue" based on composite lead scores, allowing enterprise account executives to target maximum-value opportunities first.

## User Acceptance Testing (UAT) Matrix

Prior to deploying the Power BI dashboard to production, a comprehensive UAT cycle was executed to validate the data pipeline integrity, automated CRM routing logic, and DAX calculations. 

| Test Case ID | Core Feature / Logic | Execution Steps | Expected System Behavior | Actual Result | Status |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **TC-001** | Lead Intake Automation | Submit a test entry via the Web Form with dummy company details. | Zapier catches payload, creates a new row in the staging spreadsheet within 60 seconds. | Row successfully populated with accurate timestamps. | **PASS** |
| **TC-002** | Tier 1 Routing Logic | Submit form data where `Company Size = '200+'`. | Staging rules automatically flag record as "High Priority" and target for fast sales triage. | Record flagged as High Priority instantly. | **PASS** |
| **TC-003** | Algorithmic Lead Scoring | Ingest a record with Company Size = '200+', corporate email domain, comprehensive text description, and inbound timestamp at 14:00. | Matrix aggregates weighted points across firmographics, intent, domain authority, and timing to compute a high-value score. | Lead correctly aggregated to maximum tier weight, surfacing seamlessly in the top priority queue. | **PASS** |
| **TC-004** | Operational SLA Triage | Input a record where `Response_Time_Hours = 32.5`. | DAX column flags record as "Breached" and increments the "Total SLA Breaches" alert card by 1. | Card incremented from 6 to 7; background conditionally formatted red. | **PASS** |
| **TC-005** | Interactive Visual Cross-Filtering | Click on the "51-200" company tier bar inside the column chart visual. | Every visual on the canvas dynamically updates to display data *only* relative to mid-sized tiers. | Canvas filtered responsively without calculation errors. | **PASS** |
| **TC-006** | Navigation Sidebar UI Continuity | Click the "Sales Ops / Response Time" button in the left navigation layout panel. | Viewport transitions smoothly to Page 2 while preserving identical header canvas alignment. | Page navigation executed seamlessly across all sheets. | **PASS** |

## Key Business Outcomes & ROI
* **Efficiency Realization:** Completely eliminated manual intake entry, reducing lead routing cycle times from hours to real-time execution.
* **SLA Mitigation:** Enabled instantaneous alert identification of high-value client accounts approaching breach thresholds.
