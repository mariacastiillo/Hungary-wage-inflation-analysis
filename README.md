# Purchasing Power Analysis: Wages vs. Inflation in Hungary (2014-2025)

## Executive Summary
* **Business Problem:** Hungary faced record-breaking inflation in 2023, raising the question: Did wage increases during election cycles protect citizen wealth, or did they fuel a cost-of-living crisis?
* **Solution:** A cloud-based analytical model (BigQuery) that correlates CPI (Inflation) and Wage indices to calculate the "Real Growth Gap."
* **Key Steps:** Data extraction (KSH), ETL/Sanitization (Excel), Relational Modeling (SQL), and Trend Visualization.
* **Impact:** Identified a 3.6% net loss in purchasing power for 2023, providing a data-driven baseline for future fiscal strategy and labor cost forecasting.

---

## 1. Business Problem
In 2023, Hungary’s inflation surged to 17.6%. For organizations and policymakers, nominal wage growth figures were misleading. The goal of this project was to quantify the "Real Growth"—the actual purchasing power remaining after accounting for inflation—to identify the true economic impact on the population and business environments.

## 2. Methodology
1. **Extraction:** Raw data acquisition from the Hungarian Central Statistical Office (KSH).
2. **Cleaning (ETL):** Used Microsoft Excel for delimiter normalization (`;`), header translation, and data type casting.
3. **Processing:** Implemented SQL JOINs in Google BigQuery to unify independent datasets into a single analytical view.

## 3. Skills Demonstrated
* Cloud Data Warehousing (BigQuery)
* ETL & Data Cleaning (Excel)
* Macroeconomic KPI Calculation
* SQL Relational Logic

## 4. SQL Implementation
```sql
SELECT 
  s.Year, 
  s.Avg_Salary_Index AS Salary_Index, 
  i.Total_CPI AS Inflation_Index,
  ROUND(s.Avg_Salary_Index - i.Total_CPI, 2) AS Real_Growth_Gap
FROM `hungary_economy.Salaries` AS s
JOIN `hungary_economy.inflation_data` AS i ON s.Year = i.Year
ORDER BY 1;
```
## 5. Results & Analysis
* **The 2023 Deficit:** Despite a 14% nominal wage increase, the 17.6% inflation rate created a negative real growth of -3.6%, marking the most significant wealth contraction in the analyzed period.
* **Electoral Cycle Peak:** Analysis confirms that 2022 (election year) saw the highest nominal wage spike (+17.6%), which was later neutralized by the 2023 post-election inflationary surge.
* **Recovery (2024):** A sharp 9.5% rebound in real growth suggests successful economic stabilization and a restoration of consumer confidence.

---

## 6. Business Recommendation
Based on the -3.6% contraction identified in 2023, organizations should anticipate upward pressure on wage demands as labor markets seek to recover lost purchasing power. For strategic fiscal planning, I recommend indexing long-term salary budgets against a 3-year rolling average of the CPI to mitigate the impact of volatile inflation spikes and maintain operational stability.

