# HR_Analytics_End_To_End
HR Analytics pipeline — SQL → Python → Excel → Power BI | Attrition, Salary &amp; Performance analysis on 1000 employees.
# HR Analytics — End to End Project

HR Analytics pipeline — SQL → Python → Excel → Power BI | Attrition, Salary & Performance analysis on 50 employees across 8 departments.

---

# Project Pipeline

```
Oracle SQL  →  Python  →  Excel  →  Power BI
(Database)    (Analysis)  (Summary)  (Dashboard)
```

| Stage | Tool | Output |
|---|---|---|
| 1 | Oracle SQL | HR Database — 3 tables, 10 analytics queries |
| 2 | Python | 6 visualizations + hr_summary.xlsx |
| 3 | Excel | Dept summary, Pivot Table, Conditional Formatting |
| 4 | Power BI | 2-page interactive dashboard |

---

# Screenshots

# Power BI — Attrition Overview
![Attrition Overview](screenshots/attrition_overview.png)

# Power BI — Salary & Performance
![Salary Performance](screenshots/salary_performance.png)

# Python — Attrition by Department
![Attrition by Dept](charts/v1_attrition_by_dept.png)

# Python — Correlation Heatmap
![Correlation Heatmap](charts/v6_correlation_heatmap.png)

---

# File Structure

```
hr-analytics-end-to-end/
│
├── 01_hr_schema.sql           # Oracle SQL — 3 tables, sequences, indexes
├── 02_hr_insert_data.sql      # 8 departments, 50 employees, 50 reviews
├── 03_hr_queries.sql          # 10 HR analytics queries
├── HR_Analysis.ipynb          # Python — EDA, cleaning, 6 visualizations
├── hr_data.csv                # Dataset exported from Oracle SQL
├── hr_summary.xlsx            # Excel — 3 sheets (Raw, Dept, Role summary)
├── HR_Dashboard.pbix          # Power BI — 2 page dashboard
├── charts/                    # 6 Python chart images
├── screenshots/               # Power BI dashboard screenshots
├── .gitignore
└── LICENSE
```

---

# Stage 1 — Oracle SQL

**3 Tables:**

| Table | Description | Rows |
|---|---|---|
| `departments` | 8 departments with budget | 8 |
| `employees` | Employee master data | 50 |
| `performance_reviews` | Annual review scores | 50 |

**10 Analytics Queries:**

| # | Query | Concepts |
|---|---|---|
| Q1 | Attrition rate by department | CASE WHEN, GROUP BY |
| Q2 | Average salary by job role | AVG, MIN, MAX |
| Q3 | Top 10 performers | RANK(), JOIN, Subquery |
| Q4 | Salary band distribution | CASE WHEN bands |
| Q5 | Tenure analysis | CASE WHEN, GROUP BY |
| Q6 | Gender diversity by dept | Pivot-style CASE WHEN |
| Q7 | High attrition risk employees | Multi-condition WHERE |
| Q8 | Dept salary vs budget | Budget utilization % |
| Q9 | Education vs avg salary | GROUP BY, AVG |
| Q10 | Full HR report | 3-table JOIN |

---

# Stage 2 — Python Analysis

**Libraries:** Pandas, NumPy, Matplotlib, Seaborn

**6 Visualizations:**

| Chart | Type | Insight |
|---|---|---|
| Attrition by Department | Bar + Line | Sales has highest attrition |
| Salary by Department | Box Plot | Research pays highest |
| Age vs Salary | Scatter Plot | Strong positive correlation |
| Performance Distribution | Histogram | Low performers leave more |
| Gender by Department | Grouped Bar | Engineering is male-dominated |
| Correlation Heatmap | Heatmap | Performance best predictor of attrition |

**Feature Engineering:**
- `Salary_Band` — Below 40K / 40K-60K / 60K-80K / 80K-1L / Above 1L
- `Tenure_Group` — 0-2 / 2-5 / 5-10 / 10-20 / 20+ years
- `Attrition_Flag` — 0 or 1 for calculations
- `Risk_Level` — High Risk / Attrited / Safe

---

# Stage 3 — Excel Summary

**hr_summary.xlsx — 3 sheets:**
- **Raw Data** — All 50 employee records
- **Dept Summary** — Headcount, avg salary, performance, attrition by department
- **Role Summary** — Avg salary and performance by job role

**Excel features used:**
- Conditional formatting on attrition rate
- Pivot Table — department wise summary
- Table formatting with filters

---

# Stage 4 — Power BI Dashboard

**2 Report Pages:**

**Page 1 — Attrition Overview**
- 4 KPI cards — Total Employees, Attrition Count, Attrition Rate %, Avg Performance
- Donut chart — Attrition split (Yes/No)
- Bar chart — Attrition rate by department
- Slicer — Department filter

**Page 2 — Salary & Performance**
- Scatter plot — Experience vs Salary by department
- Bar chart — Avg salary by job role
- Table — Employee details with performance scores
- Slicers — Gender, Education filters

**DAX Measures:**
```dax
Total Employees = COUNTROWS('Raw Data')
Attrition Count = CALCULATE(COUNTROWS('Raw Data'), 'Raw Data'[ATTRITION] = "Yes")
Attrition Rate % = DIVIDE([Attrition Count], [Total Employees], 0)
Avg Performance = AVERAGE('Raw Data'[PERFORMANCE_SCORE])
```

---

# Key Findings

1. **Sales and Customer Support** have the highest attrition rates
2. **Performance score** is the strongest predictor of attrition
3. **Research and Engineering** retain employees best due to higher salaries
4. **Salary grows strongly** with age and experience
5. **Gender diversity** is uneven across departments
6. **High risk employees** — low performers still working — need HR intervention

---

# How to Run

```bash
# Step 1 — Run SQL files in Oracle SQL*Plus in order
SET DEFINE OFF
@01_hr_schema.sql
@02_hr_insert_data.sql
@03_hr_queries.sql

# Step 2 — Run Python notebook
cd hr-analytics-end-to-end
jupyter notebook HR_Analysis.ipynb
# Kernel → Restart & Run All

# Step 3 — Open Excel summary
# Open hr_summary.xlsx in Microsoft Excel

# Step 4 — Open Power BI dashboard
# Open HR_Dashboard.pbix in Power BI Desktop
```

---

# Tools & Technologies

![Oracle](https://img.shields.io/badge/Oracle-SQL-red)
![Python](https://img.shields.io/badge/Python-3.10-blue)
![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-green)
![Power BI](https://img.shields.io/badge/Power%20BI-Dashboard-yellow)
![Excel](https://img.shields.io/badge/Microsoft-Excel-darkgreen)

---

# License

This project is licensed under the [MIT License](LICENSE).
