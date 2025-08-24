# 📊 Retail Performance Intelligence — Sales, Profit, Returns 

_Unifying retail data to track revenue, profit, orders, and return rates with an executive-ready Power BI experience._

***

## 📌 Table of Contents
- <a href="#overview">Overview</a>
- <a href="#business-problem">Business Problem</a>
- <a href="#dataset">Dataset</a>
- <a href="#tools--technologies">Tools & Technologies</a>
- <a href="#project-structure">Project Structure</a>
- <a href="#data-cleaning--preparation">Data Cleaning & Preparation</a>
- <a href="#data-modeling--dax">Data Modeling & DAX</a>
- <a href="#dashboard-pages">Dashboard Pages</a>
- <a href="#how-to-run-this-project">How to Run This Project</a>
- <a href="#results--conclusion">Results & Conclusion</a>
- <a href="#future-work">Future Work</a>
- <a href="#author--contact">Author & Contact</a>

***

<h2><a class="anchor" id="overview"></a>Overview</h2>

This project consolidates customer, product, store/region, calendar, transactions, and returns data (2020–2022) into a governed star schema and delivers an interactive Power BI report. Leaders can monitor KPIs, drill into brands and geographies, compare revenue vs targets, and quickly surface risks like elevated return rates or underperforming categories.

***

<h2><a class="anchor" id="business-problem"></a>Business Problem</h2>

Retail teams lacked a single, trustworthy view of downstream performance. Key questions included:
- Which products and regions drive revenue, profit, and orders?
- What is the return rate trend and where are outliers?
- Are we meeting monthly targets and YTD goals?
- How do weekends, seasons, and markets influence results?

***

<h2><a class="anchor" id="dataset"></a>Dataset</h2>

- Structured CSV files located in `/data/`:
  - Customers, Products, Stores, Regions, Calendar, Transactions, Returns (2020–2022)
- Transactions from multiple yearly files combined into a single fact table
- Date formatting standardized (M/d/yyyy), currency formatting for price and cost fields

***

<h2><a class="anchor" id="tools--technologies"></a>Tools & Technologies</h2>

- Power BI Desktop (Power Query, Model View, DAX)
- Power Query (M) for cleaning and shaping
- DAX for KPIs, time intelligence, and iterator-based calculations
- GitHub for versioning and documentation

***

<h2><a class="anchor" id="project-structure"></a>Project Structure</h2>

```
retail-performance-intelligence/
│
├── README.md
├── .gitignore
│
├── data/                         # CSV sources (2020–2022)
│   ├── customers.csv
│   ├── products.csv
│   ├── stores.csv
│   ├── regions.csv
│   ├── calendar.csv
│   ├── transactions_2020.csv
│   ├── transactions_2021.csv
│   └── transactions_2022.csv
│
├── dashboard/                    # Power BI file
│   └── Retail_Performance_Intelligence.pbix
│
├── screenshots/                  # Images used in README
│   ├── Exec-Dashboard.jpg
│   ├── Customer-Detail.jpg
│   ├── Product-Detail.jpg
│   └── Maps.jpg
```

***

<h2><a class="anchor" id="data-cleaning--preparation"></a>Data Cleaning & Preparation</h2>

- Promoted headers; enforced data types (IDs = whole numbers; SKUs/codes = text)
- Merged and standardized yearly transaction files (2020–2022)
- Created helper/conditional columns:
  - Customer full_name, birth_year, weekend flag (Calendar)
  - Product price tier; discount price formatting
  - Store full_address, area_code
- Handled nulls in boolean/category fields; applied currency and date formats
- Categorized geographic columns (City, State/Province, Country/Region, Address)

***

<h2><a class="anchor" id="data-modeling--dax"></a>Data Modeling & DAX</h2>

- Star/snowflake schema with shared lookup tables:
  - Lookups: Customers, Products, Stores → Regions, Calendar
  - Facts: Transaction_Data, Return_Data
- One‑to‑many relationships, single-direction filters; inactive stock_date relationship for alternate date logic
- Hidden foreign keys for a clean report layer

Key DAX measures (selection):
- Quantity Sold, Quantity Returned, Total Transactions, Total Returns
- Total Revenue, Total Cost, Total Profit, Profit Margin
- YTD Revenue, 60‑Day Rolling Revenue
- Weekend Transactions and % Weekend Transactions
- Last Month metrics and Revenue Target (+5% MoM)
- Unique Products

***

<h2><a class="anchor" id="dashboard-pages"></a>Dashboard Pages</h2>

- Executive Dashboard (Main)  
  One-stop KPI view with Revenue, Profit, Orders, Return Rate, revenue trending vs goal, category breakdown, Top 10 Products with return% heat, and monthly KPI cards.
  
  <img width="1518" height="845" alt="Exec Dashboard" src="https://github.com/user-attachments/assets/a734573b-bd2d-44c8-a69e-42725a8db777" />


- Customer Detail  
  Total customers and average revenue per customer, time-series selector (customers vs revenue per customer), Top 100 customers table, year slicers, spotlight card for top customer, and insight note.
   
  <img width="1510" height="841" alt="Customer Detail" src="https://github.com/user-attachments/assets/4a446ee6-23f7-473a-a7c5-45fecead9aaf" />


- Product Detail  
  Product selector with scenario slider (percentage adjustment), orders/revenue/profit vs target gauges, profit vs adjusted profit comparison, metric switch (Order/Revenue/Profit/Return/Rate), and long-term trends.
  
  <img width="1516" height="843" alt="Product Detail" src="https://github.com/user-attachments/assets/e1c8900f-96ef-46ae-946a-bcf2690edc9a" />


- Geography (Map)  
  Global map with region buttons (Select all, Europe, North America, Pacific). Bubble size by volume; supports drill and cross-filtering.
  
  <img width="1514" height="847" alt="Maps" src="https://github.com/user-attachments/assets/24883ef2-591d-40fd-b313-9660b4feb8ad" />


***

<h2><a class="anchor" id="how-to-run-this-project"></a>How to Run This Project</h2>

1. Clone or download the repository:
```bash
git clone https://github.com/yourusername/retail-performance-intelligence.git
```
2. Open the Power BI file:
```text
dashboard/Retail_Performance_Intelligence.pbix
```
3. If prompted, update file paths to the local `/data` folder and click Refresh.
4. Explore the “Executive Dashboard” page first, then navigate to the Customer Detail, Product Detail, and Map pages.

***

<h2><a class="anchor" id="results--conclusion"></a>Results & Conclusion</h2>

The solution centralizes fragmented retail data into a governed model and turns it into actionable insights. Stakeholders can:
- Track revenue, profit, orders, and return rates across 2020–2022
- Identify high/low performing brands and geographies
- Compare actuals vs monthly targets and YTD trends
- Quantify weekend/seasonal effects and spot outliers quickly

***

<h2><a class="anchor" id="future-work"></a>Future Work</h2>

- Row‑Level Security (region/store roles) and deployment to Power BI Service with scheduled refresh
- Budget/forecast inputs for variance analysis
- Customer segmentation and cohort/retention views
- Alerts and anomaly detection for sudden KPI shifts

***

<h2><a class="anchor" id="author--contact"></a>Author & Contact</h2>

**Chirag Kadam**  
Data Analyst  
📧 Email: chiragkadam425@gmail.com  
🔗 LinkedIn: www.linkedin.com/in/kadamchirag
