
# 📊 Sales Insights Data Analysis Project

**📌 Overview**

This project provides end-to-end sales insights using SQL for data extraction and Power BI for visualization. It is designed to help businesses analyze revenue, customers, markets, and product performance.

**Key highlights:**
* 📂 SQL database with customers, products, markets, transactions, and date dimensions.
* 🛠️ Power BI dashboard for interactive data exploration.
* 💰 Updated schema includes profit margins & cost price for deeper analysis.

---

**🛠️ Tech Stack**<br/>
* **SQL (MySQL)** – Database & queries
* **Power BI** – Data visualization & reporting
* **Power Query** – Currency normalization & transformations

---

**⚙️ Setup Instructions**

**1. Database Setup**<br/>
Install MySQL on your system and import the database using the provided dump file:
```
sql
mysql -u root -p sales_insights < db_dump_version_2.sql
```

**2. Run SQL Queries**<br/>
Here are some example queries:

```
-- Show all customers
SELECT * FROM customers;

-- Show transactions in Chennai market
SELECT * FROM transactions WHERE market_code = 'Mark001';

-- Total revenue in 2020
SELECT SUM(transactions.sales_amount)
FROM transactions
INNER JOIN date ON transactions.order_date = date.date
WHERE date.year = 2020;
```
👉 The full set of queries is available in: queries/analysis.sql.


**3. Power BI Dashboard**<br/>
Open dashboard.pbix in Power BI Desktop. Currency normalization was applied using Power Query:

```
= Table.AddColumn(#"Filtered Rows", "norm_amount",
      each if [currency] = "USD" or [currency] ="USD#(cr)"
      then [sales_amount]*75 else [sales_amount], type any)
```

**📊 Dashboard Insights**

**🔹 Dashboard Overview**<br/>
Provides a high-level view of KPIs, revenue trends, market performance, top customers, and top products.<br/>
**🔹 Revenue Trends**<br/>
Shows the revenue growth trend over months in 2020, highlighting seasonality and sales performance.<br/>

**🔹 Profit Analysis**<br/>
Focuses on profitability, showing profit margins, cost price, and high-margin products.<br/>

**📂 Repository Structure**

Sales-Insights-Data-Analysis/<br/>
│── README.md<br/>
│── db_dump_version_2.sql<br/>
│── dashboard.pbix<br/>
│── /screenshots<br/>
│     ├── dashboard_overview.png<br/>
│     ├── revenue_trends.png<br/>
│     └── profit_analysis.png<br/>
│── /queries<br/>
│     └── analysis.sql<br/>

�**� Resources**

Install MySQL

Download Power BI Desktop

✨ With this repo, you can explore customer behavior, market performance, and profitability all in one place.
