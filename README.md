# Healthcare Operations & Financial Intelligence Dashboard

**AnalystLab Africa Data Analytics Internship, Week 3 (Track A)**
Prepared by Safrah Omisanya | October 2026

An interactive Power BI dashboard for hospital decision-makers. It shows encounter patterns, claim costs, payer coverage and procedure utilisation for one hospital (27,891 encounters, 974 patients, 2 January 2011 to 5 February 2022).

## Dashboard pages
| Page | What it shows |
|---|---|
| Overview | Six KPIs, quarterly encounter trend, encounter-class comparison, class share by year, key takeaways |
| Cost & Coverage | Claim cost vs payer coverage by year, coverage rate by payer, average cost by class, payer summary table |
| Procedures | Top 10 most frequent procedures; top 10 highest average cost (minimum 30 procedures) |
| Data Notes | Data-quality notes, misleading-metric warnings, KPI definitions |

All pages share Year, Encounter Class and Payer slicers and a page navigator.

## Key findings
- 27,891 encounters, $101.5M in claims, average $3,640 per encounter.
- Payers are recorded as covering 30.6% of claim cost; 48.7% of encounters show zero coverage.
- Ambulatory (44.9%) and outpatient (22.6%) make up two thirds of encounters.
- Urgent care is 13.1% of encounters but 23.0% of claim cost.
- Uninsured encounters are 31.6% of volume but 48.5% of claim cost.
- Humana, Anthem, Aetna, UnitedHealthcare and Cigna show about 0% recorded coverage, which looks like a recording gap.

## Documents in this repository
| File | Purpose |
|---|---|
| `Data_Quality_Assessment.docx` | Sources, relationships, quality checks, transformations, assumptions |
| `KPI_Definition_Sheet.docx` | DAX definitions for every KPI, plus answers to all 8 operations questions |
| `Validation_Evidence.docx` | Independent checks, filter tests, discrepancies found and fixed, misleading metrics |
| `Executive_Summary.docx` | Business problem, findings, 5 evidence-based recommendations |
| Power BI file (`Hospital_Dashboard.pbix`) | Provided in the submission Drive folder, not on GitHub, because the file embeds the source data |
| `screenshots/` | Dashboard page images and validation screenshots |

## How to reproduce
1. Load the five hospital CSV files (encounters, patients, procedures, payers, organizations) into Power BI Desktop.
2. In Power Query, set data types and add: Start Time and Stop Time (UTC text converted with the time zone removed, not shifted), Duration Hours, Duration Band, Zero Coverage flag, Year, Quarter, Year-Quarter and Year-Month.
3. Add a Calendar table in DAX and create the relationships (many to one, single direction): encounters[PATIENT] to patients[Id], encounters[PAYER] to payers[Id], procedures[ENCOUNTER] to encounters[Id], Calendar[Date] to the encounter start date.
4. Create the measures listed in the KPI definition sheet.

## Data and privacy
The source data contains patient names and addresses. These fields are never displayed in the dashboard, and **the raw CSV files are not published in this repository**.

## Limitations
One hospital only; 2022 is a partial year; private-payer coverage appears under-recorded; procedure BASE_COST is a list price, not a billed amount.

#AnalystLabAfrica
