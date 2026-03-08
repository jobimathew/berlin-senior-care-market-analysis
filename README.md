# Berlin Senior Care Market — GTM Strategy & ML Lead Scoring

> **Portfolio project.** End-to-end data science engagement for a Berlin-based senior care advisory use case. Client anonymised.

---

## Business Problem

Berlin has a rapidly growing senior population. Many elderly residents are eligible for **Pflegegrad (care level support)** but do not apply due to lack of awareness, administrative complexity, or lack of advisory support.

As a result, a large share of seniors who qualify for care services **never enter the system**, creating a gap between available benefits and actual utilization.

This project analyzes Berlin demographic and care infrastructure data to identify **neighborhoods with the highest untapped advisory demand.**

---

## Solution

This project integrates multiple German public datasets to:

• identify districts with high senior population density  
• estimate care demand gaps  
• measure competition from existing care providers  
• prioritize neighborhoods for advisory outreach  

Using machine learning and demographic modeling, the project builds a **Lead Opportunity Index (LOI)** to rank Berlin districts and planning areas based on unmet care demand.

---

## Impact

The analysis evaluates **537 Berlin planning areas (PLR)** and ranks them according to potential advisory demand.

Key insights:

• **Steglitz-Zehlendorf identified as the highest opportunity district**  
• **4 demographic market segments discovered using ML clustering**  
• Estimated **150–250 potential leads per month after scaling**

---

## Overview

Berlin has **747,667 seniors (65+)**, of whom an estimated **45% lack an active Pflegegrad** despite being entitled to one.

This project uses three official German public datasets to:

• identify neighbourhoods with highest advisory demand  
• segment the senior care market  
• design a **€0-budget go-to-market strategy**

---

## Results

| Metric | Value |
|---|---|
| Top district identified | Steglitz-Zehlendorf (LOI: 94.8) |
| PLR areas scored | 537 |
| Market clusters found | 4 (K-Means) |
| Gradient Boosting model accuracy | R² = 0.999 |
| Projected leads/month (month 12) | 150–250+ |
| Location coverage | 100% (PLR → neighbourhood + postcode) |

---


Main files:

• **berlin_senior_care_gtm.ipynb** — full analysis notebook  
• **GTM_Strategy_Portfolio_EN.docx** — strategy report  
• **plr_priority_EN.csv** — top planning areas ranked by lead score  

---

## Methodology

### 1 Data Integration

Three datasets merged into a master dataframe covering **12 Berlin districts and 537 planning areas.**

| Dataset | Source | Key Features |
|---|---|---|
| EWR-Basisdaten-LOR-2025 | Amt für Statistik Berlin-Brandenburg | Age, widowhood, housing quality |
| Pflegestatistik 22411-01-02-4 | Statistisches Bundesamt | Ambulant services, nursing beds |
| Pflegestatistik 22411-02-05-4 | Statistisches Bundesamt | Care recipients by service type |

---

### 2 Feature Engineering


competition_density = ambulant_services / senior_count * 1000
pflegegrad_gap = (senior_count * 0.45) - care_recipients
care_penetration = care_recipients / senior_count * 100


Main files:

• **berlin_senior_care_gtm.ipynb** — full analysis notebook  
• **GTM_Strategy_Portfolio_EN.docx** — strategy report  
• **plr_priority_EN.csv** — top planning areas ranked by lead score  

---

## Methodology

### 1 Data Integration

Three datasets merged into a master dataframe covering **12 Berlin districts and 537 planning areas.**

| Dataset | Source | Key Features |
|---|---|---|
| EWR-Basisdaten-LOR-2025 | Amt für Statistik Berlin-Brandenburg | Age, widowhood, housing quality |
| Pflegestatistik 22411-01-02-4 | Statistisches Bundesamt | Ambulant services, nursing beds |
| Pflegestatistik 22411-02-05-4 | Statistisches Bundesamt | Care recipients by service type |

---

### 2 Feature Engineering


competition_density = ambulant_services / senior_count * 1000
pflegegrad_gap = (senior_count * 0.45) - care_recipients
care_penetration = care_recipients / senior_count * 100

Key signals engineered:

• care demand gap
• provider competition density
• care system penetration rate

### 3 Lead Opportunity Index (LOI)

Six demographic and infrastructure signals combined into a 0–100 opportunity score.

LOI = (pct_65plus * 0.28) + (pflegegrad_gap * 0.20) + (pct_widowed * 0.18)
    + ((1 - competition_density) * 0.15) + (pct_good_housing * 0.10) + (avg_age * 0.09)
Higher LOI = stronger advisory market potential.

### 4 K-Means Clustering

Districts segmented using StandardScaler + KMeans (k=4).

Cluster	Districts	Profile
HIGH-AGE	Steglitz-Zehlendorf	Highest senior share + lowest competition
AFFLUENT	Charlottenburg-Wilmersdorf	High housing quality
LOW-COMP	Treptow-Köpenick, Pankow	Low provider competition
PIPELINE	Reinickendorf, Tempelhof, Marzahn	Growth markets

### 5 Gradient Boosting Lead Scoring

Model trained on 537 planning areas.

GradientBoostingRegressor(
    n_estimators=200,
    max_depth=4,
    learning_rate=0.05
)

Model accuracy:

R² = 0.999

Most important predictor:

% population aged 65+

### Location Enrichment

All 8-digit RAUMID planning area codes mapped to:

• neighbourhood name
• postcode range

Result:

537 / 537 areas matched (100%)

without external geocoding APIs.

Skills Demonstrated
Technical

• Python / pandas
• scikit-learn (Gradient Boosting, KMeans, PCA)
• feature engineering
• demographic modelling

Visualization

• matplotlib
• heatmaps
• bubble charts
• PCA plots

Business

• GTM strategy design
• market segmentation
• zero-budget acquisition modelling

Compliance

• GDPR / DSGVO awareness
• German healthcare advertising regulation

Data Sources

All datasets are publicly available.

LOR Planning Areas Berlin — Amt für Statistik Berlin-Brandenburg

Pflegestatistik 2023 — Statistisches Bundesamt

Setup

Install dependencies:

pip install pandas numpy scikit-learn matplotlib openpyxl

Run notebook:

jupyter notebook berlin_senior_care_gtm.ipynb

Place the three .xlsx datasets in the same directory before running.

Author

Jobi Mathew
MSc Data Science— Berlin

Portfolio project for data science, product analytics, and growth strategy roles.



