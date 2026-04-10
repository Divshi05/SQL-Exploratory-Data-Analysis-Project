# 🔍 SQL Exploratory Data Analysis Project

An end-to-end **EDA project using PostgreSQL** on a retail sales dataset, progressing through 12 analytical stages — from schema inspection to production-ready reporting views.

---

## 📁 Project Structure

```
SQL-Exploratory-Data-Analysis-Project/
│
├── EDA_scripts/
│   ├── 0-Load_Data.sql                  # Load CSVs into PostgreSQL
│   ├── 1-Database_Exploration.sql       # Schema & metadata inspection
│   ├── 2-Dimension_Exploration.sql      # Categorical dimension profiling
│   ├── 3-Date_Exploration.sql           # Date range & customer age analysis
│   ├── 4-Measures_Exploration.sql       # Core KPIs summary
│   ├── 5-Magnitude_Analysis.sql         # Group-level aggregations
│   ├── 6-Ranking_Analysis.sql           # Top/bottom product & customer rankings
│   ├── 7-Change_Over_Time_Analysis.sql  # Monthly sales trends
│   ├── 8-Cumulative_Analysis.sql        # Running totals & moving averages
│   ├── 9-Performance_Analysis.sql       # Year-over-year product performance
│   ├── 10-Part_To_Whole_Analysis.sql    # Category % contribution to revenue
│   ├── 11A-Data_Segmentation.sql        # Product cost-range segmentation
│   ├── 11B-Data_Segmentation.sql        # Customer lifecycle segmentation
│   ├── 12-Customer_Report.sql           # Final customer analytics view
│   └── 12-Product_Report.sql            # Final product analytics view
│
└── README.md
```

---

## 🗄️ Database Schema

A **Gold layer** star schema in the `gold` schema:

| Table | Type | Description |
|---|---|---|
| `gold.dim_customers` | Dimension | Name, country, gender, birthdate |
| `gold.dim_products` | Dimension | Name, category, subcategory, cost |
| `gold.fact_sales` | Fact | Order date, quantity, sales amount, price |

---

## 📋 Analysis Stages

| Stage | Script | What It Does |
|---|---|---|
| 0 | Load Data | `COPY` CSVs into `gold` schema tables |
| 1 | Database Exploration | `INFORMATION_SCHEMA` table & column inspection |
| 2 | Dimension Exploration | Distinct countries, product category hierarchy |
| 3 | Date Exploration | Sales date range in years/months; customer age extremes |
| 4 | Measures Exploration | KPI summary — sales, quantity, price, orders, customers |
| 5 | Magnitude Analysis | Revenue & customer counts grouped by country, gender, category |
| 6 | Ranking Analysis | Top/bottom 5 products and top 10 customers by revenue; `RANK()` |
| 7 | Change Over Time | Monthly trends via `EXTRACT`, `DATE_TRUNC`, `TO_CHAR` |
| 8 | Cumulative Analysis | Running sales total & avg price per year using `SUM/AVG OVER()` |
| 9 | Performance Analysis | YoY product comparison using `LAG()` and avg deviation |
| 10 | Part-to-Whole | Category % share of total revenue via `SUM() OVER()` |
| 11A | Product Segmentation | Cost buckets: Below 100 / 100–500 / 500–1000 / Above 1000 |
| 11B | Customer Segmentation | VIP / Regular / New based on lifespan and spend |
| 12 | Reports (Views) | `gold.report_customers` and `gold.report_products` with full KPIs |

---

## 📊 Final Report Views

### `gold.report_customers`
Customer demographics, VIP/Regular/New segment, and KPIs: **recency**, **average order value**, **average monthly spend**.

### `gold.report_products`
Product attributes, High Performer / Mid-Range / Low Performer segment, and KPIs: **recency**, **average order revenue**, **average monthly revenue**.

Both views use a **3-layer CTE pattern**: base query → aggregation → final output.

---

## 🛠️ SQL Techniques Used

Window functions (`RANK`, `LAG`, `SUM/AVG OVER`), CTEs, `LEFT JOIN`, `UNION ALL`, `CASE WHEN`, `DATE_TRUNC`, `EXTRACT`, `AGE`, `TO_CHAR`, `NULLIF`, `CREATE VIEW`

---

## 🚀 Getting Started

**Prerequisites:** PostgreSQL v12+, pgAdmin or DBeaver

```bash
git clone https://github.com/Divshi05/SQL-Exploratory-Data-Analysis-Project.git
```

1. Create the `gold` schema and tables in PostgreSQL
2. Update file paths in `0-Load_Data.sql` to your local CSV locations
3. Run scripts in order from `0` to `12`

---

## 👤 Author

**Divshi05** — [GitHub Profile](https://github.com/Divshi05)
