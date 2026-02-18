# 📦 Supply Chain Insights: Product Performance, Brand Value, Supplier Trends

This project presents an end-to-end SQL analysis for an electronics company, using products, inventory, and suppliers datasets to address three key business questions related to stock management and sales performance.

<div align="center">

### 🛠️ SQL Functions & Features Used
`SUM()` • `AVG()` • `JOIN()` • `WHERE()` • `BETWEEN()` • `GROUP BY()` • `HAVING()` • `CTEs` • `RANK()` • `ROW_NUMBER()` • `LAG()` • `ORDER BY()` • `CASE` • `Subquery` • `ROUND()` • Filtering Logic

</div>

---

## 📊 Database Schema

The `SQL_Portfolio` database was created with five tables to address the business questions of the electronics company:

| **Dimension Tables** | **Fact Tables** |
|---------------------|-----------------|
| • product | • received_purchase_orders |
| • suppliers | • stock_level |
| • datetime | |

### 📈 Data Generation Plan
All tables, except the datetime table, were populated from the staging database, where four external Excel files related to product, suppliers, received_orders, and stock_level had been previously uploaded. The datetime table was created using a SQL script that generates dates from January 1, 2025, to December 31, 2025.

*The following figure depicts the database tables along with the data generation plan used to populate them.*

![Data Generation Plan](https://github.com/Fahim0729/Supply-Chain-Analytics-Using-SQL-Inventory-Sales-Supplier-Insights/blob/9926429eb37e25222dc4a0924a6475671eb8c358/Data_Generation_Plan.png)

### 🔗 Database Diagram
Every fact table connects to each of the three dimension tables.

*The next figure presents the database diagram, illustrating the relationships between the fact table and the dimension tables.*

![Database Diagram](https://github.com/Fahim0729/Supply-Chain-Analytics-Using-SQL-Inventory-Sales-Supplier-Insights/blob/29b2e9fcb6568ae46ca4417bcb80b131f7e53269/Database_Diagram.png)

---

## 📋 Business Questions & SQL Functions

The questions have been solved using SQL queries, and the SQL functions applied to solve them are listed below:

### 📌 Q1. Brand Inventory Value Analysis
**Identify brands with significant restocking activity (>50 units) in the second half of 2025 (July-December) and analyze their average shelf inventory value to optimize supply chain planning for next year.**

![Q1](https://github.com/Fahim0729/Supply-Chain-Analytics-Using-SQL-Inventory-Sales-Supplier-Insights/blob/28f41ad3b6e538d1e7a947c404e91475f4f7f43f/Q1.png)


🔹 SQL Functions: SUM(), AVG(), JOIN, BETWEEN, WHERE, GROUP BY, HAVING

### 📌 Q2. Product Sales Velocity
**Identify the top 5 products by total quantity sold and categorize them as High, Medium, or Low velocity to understand sales performance trends.**

![Q2](https://github.com/Fahim0729/Supply-Chain-Analytics-Using-SQL-Inventory-Sales-Supplier-Insights/blob/28f41ad3b6e538d1e7a947c404e91475f4f7f43f/Q2.png)

🔹 SQL Functions: CTEs, JOIN, RANK(), ORDER BY, CASE

### 📌 Q3. Supplier Restocking Trend Analysis
**Identify the top 3 suppliers with the largest positive change in received quantity by comparing their most recent delivery to their previous delivery, to understand suppliers with significant restocking trends.**

![Q3](https://github.com/Fahim0729/Supply-Chain-Analytics-Using-SQL-Inventory-Sales-Supplier-Insights/blob/28f41ad3b6e538d1e7a947c404e91475f4f7f43f/Q3.png)

🔹 SQL Functions: Subquery, JOIN, LAG, ROW_NUMBER, RANK, ROUND, Filtering Logic


---

## 🚀 Key Insights

| Analysis | Business Impact |
|----------|-----------------|
| **Brand Value Analysis** | Optimize inventory planning for 2026 |
| **Product Performance** | Identify sales velocity trends for top products |
| **Supplier Trends** | Recognize improving supplier relationships |

---

<div align="center">
  
**[⬆ Back to Top](#-supply-chain-insights-product-performance-brand-value-supplier-trends)**

</div>
