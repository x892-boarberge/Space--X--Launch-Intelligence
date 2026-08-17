# 04 – Methodology

## 1. Overall Approach

This project follows a structured data science methodology focused on capacity analysis and decision support rather than pure prediction.

The analysis is divided into five main stages:

1. Data Collection & Exploration
2. Data Cleaning & Validation
3. Descriptive & Diagnostic Analysis
4. Capacity Modelling
5. Scenario Analysis & Recommendations

## 2. Analytical Framework

The core analytical model examines the interaction between three systems:

- **Starlink Demand System** (subscriber growth → satellite demand → launch demand)
- **Falcon 9 Supply System** (launch cadence + booster reusability)
- **Starship Transition System** (readiness and cadence growth)

The central question is whether Starship can scale fast enough to relieve Falcon 9 capacity pressure.

## 3. Key Analytical Methods

### A. Falcon 9 Cadence & Reusability Analysis
- Calculate monthly and quarterly launch rates
- Measure Starlink share of total Falcon 9 missions over time
- Analyze booster flight count distribution
- Examine turnaround time by reuse bin (1–5, 6–10, 11–20, 21–30, 31+)
- Test whether turnaround time increases with higher flight counts

### B. Starlink Demand Analysis
- Track subscriber growth and ARPU trends
- Estimate satellite deployment rates required for growth and replacement
- Calculate network capacity deployed per launch (adjusted for satellite generation)

### C. Starship Readiness Assessment
- Track success rates by mission phase
- Measure progress on critical milestones (orbital flight, ship catch, payload deployment)
- Calculate flight interval and cadence trends

### D. Capacity Allocation & Bottleneck Detection
- Quantify Falcon 9 capacity allocated to Starlink vs external customers
- Identify periods of high capacity pressure
- Combine quantitative launch data with qualitative backlog evidence

### E. Scenario Analysis
- Model different Starship cadence growth paths
- Estimate impact on Falcon 9 availability for external customers under different timelines

## 4. Tools & Technologies

- **Language**: Python
- **Core Libraries**: pandas, numpy, matplotlib, seaborn
- **Data Storage**: CSV / Parquet files (with possible SQLite later)
- **Version Control**: Git + GitHub
- **Environment**: VS Code + Jupyter Notebooks

## 5. Quality Principles

- Prefer primary sources over secondary reporting
- Clearly separate hard quantitative data from qualitative evidence
- Document all assumptions
- Avoid overclaiming (especially on exact external backlog size)
- Make all analysis reproducible