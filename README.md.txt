# Retail Performance Intelligence

## Brief One Line Summary
End-to-end Power BI project that unifies retail data to monitor revenue, profit, returns, and product/region trends with interactive, executive-ready insights.

## Overview
This project brings together sales, customers, products, stores, regions, calendar, and returns into a single semantic model in Power BI. Using a clean star schema, DAX measures, and interactive visuals, stakeholders can track KPIs, drill into brands and geographies, compare results vs. targets, and quickly spot risks such as high return rates or underperforming regions.

## Problem Statement
Business teams lacked a single, trustworthy view of performance. Key questions were hard to answer:
- Which brands and regions drive revenue and profit?
- Where are return rates elevated and margins weak?
- Are we meeting monthly targets and YTD trends?
- How do weekends and seasonality affect results?

## Dataset
Structured CSV files:
- Customers, Products, Stores, Regions, Calendar, Returns, Transactions (**2020–2022**)

Data preparation highlights:
- Headers promoted and data types validated (IDs = whole numbers; prices = currency)  
- Created helper columns: full_name, birth_year, address fields, area_code, weekend flag, price_tier, years_since_remodel, etc.  
- Combined multiple transaction CSVs into one fact table; removed extraneous columns; formatted dates (M/d/yyyy)  

## Tools and Technologies
- Power BI Desktop (Power Query, Model view, DAX)  
- Power Query (M) for cleaning and shaping  
- DAX for KPIs, time intelligence, and iterators  
- CSV/Excel as data sources  

## Methods
1. **Connecting & Shaping**  
   - Imported all CSVs, promoted headers, enforced data types, handled nulls  
   - Created custom and conditional columns (e.g., full_name, Weekend, Price_Tier)  
   - Currency and date formatting; geographic data categorization  
   - Combined **2020–2022 transactions** into a single table  

2. **Data Modeling**  
   - Star/snowflake schema: lookup tables (Customers, Products, Stores→Regions, Calendar) above fact tables (Transaction_Data, Return_Data)  
   - One-to-many relationships with one-way filter direction; inactive stock_date relationship for alternative date logic  
   - Hidden foreign keys for a clean report layer  

3. **DAX Measures**  
   - Core volumes: Quantity Sold, Quantity Returned, Total Transactions, Total Returns  
   - Financials: Total Revenue, Total Cost, Total Profit, Profit Margin  
   - Time intelligence: YTD Revenue, 60-Day Rolling Revenue, Last Month metrics, Revenue Target (+5% MoM)  
   - Behavior: Weekend Transactions and % Weekend Transactions  
   - Catalog: Unique Products  

4. **Reporting & UX**  
   - KPI cards for current month vs. last month targets  
   - Matrix by Product Brand with data bars and color scales (margin, return rate)  
   - Map and Treemap for geo insights with drill-down  
   - Weekly Revenue Trending column chart (**2022 filter**)  
   - Gauge for Revenue vs. Target; slicers with “Select All”; bookmarks for saved insights  

## Key Insights
- Clear brand ranking by transactions, profit, and margin  
- High return-rate brands highlighted via conditional formatting  
- Weekend activity share quantified and comparable to total traffic  
- Geographic differences visible at country/state/city levels  
- Rolling and YTD views reveal seasonality and goal attainment  

## Dashboard/Model/Output
- `.pbix` contains:
  - Clean star schema model  
  - Organized measure groups (Sales, Profitability, Returns, Time)  
  - “Topline Performance” page with KPIs, Matrix, Map/Treemap, Weekly Trending, Gauge, and bookmarks  

## How to Run this Project
1. Clone or download the repository.  
2. Open `Retail_Performance_Intelligence.pbix` in Power BI Desktop.  
3. If prompted, update the data source paths to the local `/data` folder.  
4. Refresh the model and explore the “Topline Performance” report page using slicers and bookmarks.  

## Results & Conclusion
The solution centralizes fragmented retail data, enabling fast, reliable decision-making. Teams can track revenue and profit, spot high return rates, compare performance vs. targets, and understand product-region trends—improving actions in merchandising, pricing, and store strategy.

## Future Work
- Add Row-Level Security (RLS) for region/store roles  
- Publish to Power BI Service with scheduled refresh  
- Add budget/forecast for variance analysis  
- Customer segmentation and cohort retention views  
- Automated alerts/anomaly detection for sudden KPI shifts  

## Author & Contact
- **Author:** Chirag Kadam
- **Role:** Data Analyst / BI Developer  
- **Email:** chiragkadam425@gmail.com 
- **LinkedIn:** www.linkedin.com/in/kadamchirag
