🏢 Company Overview
Vrinda Manufacturing & Distribution Ltd. is a mid-sized Indian manufacturing company with operations across 6 states — Tamil Nadu, Karnataka, Maharashtra, Delhi, Gujarat, and Kerala. The company operates 8 business units and processes thousands of financial transactions monthly across raw materials, finished goods, logistics, and services.

❗ Business Problem
The finance and MIS team relied entirely on manual Excel reports compiled each month end, which caused:

📌 3–4 days of delay in generating monthly MIS reports
📌 No real-time KPI visibility for senior management
📌 Frequent errors in vendor reconciliation and budget tracking
📌 No standardised format across departments and regions
📌 Zero forecasting capability for proactive decision-making


🎯 Objective
Design and deliver a complete automated Financial MIS Reporting System that provides:

Automated KPI dashboards replacing manual monthly reports
Department-wise profitability and expense tracking
Budget vs. Actual variance monitoring
Region-wise performance benchmarking
Vendor spend analysis and payment mode tracking
Revenue forecasting with trend analysis


🛠️ Tools & Technologies Used
ToolPurposeMicrosoft Excel 2021+KPI dashboards, pivot analysis, formulas, forecastingPower BI DesktopExecutive dashboards, DAX measures, drill-through reportsMySQL 8.0Data storage, aggregation queries, stored proceduresPython (pandas, openpyxl)Data generation, cleaning, Excel automationGitHubVersion control, portfolio presentation

📂 Repository Structure
Financial-MIS-Dashboard/
│
├── Dataset/
│   ├── 01_Raw_Dataset.csv            ← 1,130 rows with intentional data quality issues
│   ├── 02_Cleaned_Dataset.csv        ← 1,100 rows validated and standardised
│   └── 03_Dashboard_Ready_Dataset.csv ← Enriched with KPI, forecast & aging columns
│
├── Excel/
│   └── Financial_MIS_Dashboard_FY2024.xlsx
│       ├── 01_Raw_Dataset
│       ├── 02_Cleaned_Dataset
│       ├── 03_KPI_Summary
│       ├── 04_Department_Analysis
│       ├── 05_Region_Analysis
│       ├── 06_Monthly_Trend
│       ├── 07_Formula_Reference
│       ├── 08_Executive_Dashboard
│       └── 09_Vendor_Summary
│
├── PowerBI/
│   └── PowerBI_DAX_Reference.md     ← Full DAX measures & data model guide
│
├── SQL/
│   └── Financial_MIS_Dashboard_SQL.sql  ← DDL, DML, analytical queries, stored proc
│
├── Reports/
│   └── Business_Insights_Report.md
│
└── README.md

📊 Dataset Information
AttributeDetailsRows (Clean)1,100 transactionsTime PeriodFY 2024 (Jan – Dec)DepartmentsSales, Operations, HR, Finance, IT, Logistics, Procurement, Customer SupportRegionsTamil Nadu, Karnataka, Maharashtra, Delhi, Gujarat, KeralaCurrencyIndian Rupees (₹)Vendors28 real Indian conglomerates (Tata Steel, Reliance, Infosys, etc.)
Raw Dataset Intentional Errors (for data cleaning practice)

❌ 50+ missing values in Vendor, Department, Revenue, GSTIN columns
❌ 30 duplicate Transaction IDs
❌ Mixed date formats: YYYY-MM-DD, DD/MM/YYYY, DD-MMM-YYYY
❌ Department name typos: "Saless", "Operatons", "H.R"
❌ Inconsistent vendor casing: "TATA STEEL LTD", "tata steel ltd"
❌ Invalid GSTIN formats: "INVALID-XXXX" entries
❌ Leading/trailing spaces in Transaction_IDs


📈 Key KPIs — FY 2024 Results
KPIValueTotal Revenue₹100.8 CroreTotal Expenses₹79.8 CroreNet Profit₹21.0 CroreProfit Margin %20.8%Budget Variance %−2.4%Expense Ratio %79.2%Best Revenue DepartmentSalesBest Performing RegionKeralaHighest Expense DepartmentSales

🔧 Excel Features Used
FeatureApplicationXLOOKUPFetch Revenue/Expense by Transaction_IDVLOOKUPDepartment-wise data retrievalINDEX MATCHFlexible exact-match lookupsSUMIFSMulti-condition revenue aggregationIFERRORZero-division and error guardsCOUNTIFSTransaction counting by dept + regionPivot TablesDept × Region revenue matrixPivot ChartsBar, Line, Pie visualisationsConditional FormattingProfit status colour bandsSlicersDynamic filtering by quarter/deptFORECAST.ETSSeasonal revenue forecasting

📐 Power BI DAX Measures
daxTotal Revenue     = SUM(fact_transactions[Revenue])
Net Profit        = SUM(fact_transactions[Profit])
Profit Margin %   = DIVIDE([Net Profit], [Total Revenue], 0) * 100
Budget Variance % = DIVIDE(SUM(Revenue) - SUM(Budget), SUM(Budget), 0) * 100
Revenue YTD       = CALCULATE([Total Revenue], DATESYTD(dim_date[Date]))
MoM Growth %      = DIVIDE(CurrentMonth - PriorMonth, PriorMonth, 0) * 100
Dept Profit Rank  = RANKX(ALL(Department), [Net Profit], , DESC, DENSE)

🗄️ SQL Highlights

CREATE TABLE with generated/computed columns (Profit, Variance, PM%)
GROUP BY aggregations across Dept, Region, Quarter, Month
Window Functions: RANK(), SUM() OVER, ROWS UNBOUNDED PRECEDING
CASE statements for Profitability Band classification
JOINs with dimension tables for enriched reporting
Stored Procedure sp_dept_profitability for parameterised quarter reports
Executive Summary VIEW for single-query board reporting


💡 Key Business Insights

Sales is the highest revenue-generating department (₹~25 Cr) but also the highest cost centre — presenting a cost optimisation opportunity.
Kerala leads all regions in revenue contribution despite being a smaller geography, indicating strong distribution efficiency.
HR and IT departments show budget overruns in Q2 and Q3 — flagged for budget reallocation review.
Procurement maintains the most consistent budget adherence across all four quarters.
NEFT and RTGS dominate payment modes (>65%), indicating healthy digital payment adoption.
Q4 profitability dips by ~4% vs Q1–Q3 average, suggesting seasonal demand softness in year-end.


📉 Business Impact
Before ProjectAfter Project3–4 days for monthly MISSame-day automated report generationManual error-prone ExcelValidated, standardised data pipelineNo KPI visibilityReal-time executive KPI dashboardNo budget monitoringLive budget vs. actual variance trackingNo forecastingRevenue & expense forecasting enabledSiloed department reportsUnified multi-department view

Estimated time saving: 60% reduction in MIS reporting effort (from ~12 person-hours/month to ~5 person-hours/month)


📸 Dashboard Screenshots

Add screenshots to /Screenshots/ folder after building the Power BI / Excel dashboards

ScreenshotDescription01_executive_dashboard_overview.pngFull Power BI executive summary page02_kpi_cards.pngRevenue, Profit, PM%, Budget Variance KPI cards03_monthly_trend_chart.pngLine chart — Revenue vs Expense by month04_dept_comparison_bar.pngBar chart — Department revenue comparison05_region_map.pngFilled map — Region-wise profitability06_excel_pivot_table.pngPivot table with slicers07_sql_query_output.pngSQL profitability query result08_formula_bar.pngExcel XLOOKUP / SUMIFS formula bar

🔮 Future Improvements

 Connect Power BI to live MySQL database for real-time refresh
 Add row-level security (RLS) in Power BI by department
 Integrate AP/AR aging dashboard for cash flow monitoring
 Add GST reconciliation module (GSTR-1 vs GSTR-2A matching)
 Build Python automation script to auto-generate monthly reports
 Implement anomaly detection for unusual expense spikes


📚 Learning Outcomes

End-to-end MIS project lifecycle: raw data → cleaned data → dashboard
Real-world data quality issues and cleaning strategies
Corporate financial KPI design and calculation logic
Advanced Excel formulas for dynamic financial models
Power BI data modelling (star schema) and DAX measure development
SQL analytical queries with window functions and stored procedures
Executive dashboard design principles for business stakeholders
👤 Author
Nandhini Nikil
MIS Analyst | Finance & Reporting | Power BI | Excel | SQL
