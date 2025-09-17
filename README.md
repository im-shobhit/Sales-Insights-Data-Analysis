📊 Sales Insights Data Analysis Project

📌 Overview

This project provides end-to-end sales insights using SQL for data extraction and Power BI for visualization.



It is designed to help businesses analyze revenue, customers, markets, and product performance.

Key highlights:



📂 SQL database with customers, products, markets, transactions, and date dimensions

🛠️ Power BI dashboard for interactive data exploration

💰 Updated schema includes profit margins & cost price for deeper analysis

🛠️ Tech Stack

SQL (MySQL) – Database & queries

Power BI – Data visualization & reporting

Power Query – Currency normalization & transformations

⚙️ Setup Instructions

1. Database Setup

Install MySQL on your system (tutorial)

Import the database:





mysql -u root -p sales_insights < db_dump_version_2.sql

2. Run SQL Queries

Some examples:





-- Show all customersSELECT * FROM customers;-- Show transactions in Chennai marketSELECT * FROM transactions WHERE market_code = 'Mark001';-- Total revenue in 2020SELECT SUM(transactions.sales_amount)FROM transactionsINNER JOIN date ON transactions.order_date = date.dateWHERE date.year = 2020;

👉 Full set of queries is available in: queries/analysis.sql



3. Power BI Dashboard

Open dashboard.pbix in Power BI Desktop.

Currency normalization applied:





= Table.AddColumn(#"Filtered Rows", "norm_amount",

each if [currency] = "USD" or [currency] ="USD#(cr)"

then [sales_amount]*75 else [sales_amount], type any)

📊 Dashboard Insights

🔹 Dashboard Overview



High-level view of KPIs, revenue trends, market performance, top customers, and top products.🔹 Revenue Trends



Revenue growth trend over months in 2020, highlighting seasonality and sales performance.🔹 Profit Analysis



Profitability analysis showing profit margins, cost price, and high-margin products.📂 Repository Structure



Sales-Insights-Data-Analysis/

│── README.md

│── db_dump_version_2.sql

│── dashboard.pbix

│── /screenshots

│ ├── dashboard_overview.png

│ ├── revenue_trends.png

│ └── profit_analysis.png

│── /queries

│ └── analysis.sql

📸 Screenshots

Additional dashboard visuals are available in the /screenshots folder.

🔗 Resources

Install MySQL

Download Power BI Desktop

✨ With this repo, you can explore customer behavior, market performance, and profitability all in one place.
