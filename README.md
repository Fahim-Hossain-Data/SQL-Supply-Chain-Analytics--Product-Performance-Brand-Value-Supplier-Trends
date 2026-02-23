# 📦 Supply Chain Insights: Product Performance, Brand Value, Supplier Trends

This project is an end-to-end SQL analysis of an electronics company, where the three main business questions concerning the management of stock and sales performance are answered using the products, inventory, and suppliers datasets.

<div align="center">

### 🛠️ SQL Functions & Features Used
`SUM()` • `AVG()` • `JOIN()` • `WHERE()` • `BETWEEN()` • `GROUP BY()` • `HAVING()` • `CTEs` • `RANK()` • `ROW_NUMBER()` • `LAG()` • `ORDER BY()` • `CASE` • `Subquery` • `ROUND()` • Filtering Logic

</div>

---

## 📊 Database Schema

The `SQL_Portfolio` database was created with five tables to address the business questions of the electronics company. Three of these are dimension tables, and two are fact tables:

<div align="center">

| **Dimension Tables** | **Fact Tables** |
|:-------------------:|:---------------:|
| • product           | • received_purchase_orders |
| • suppliers         | • stock_level   |
| • datetime          |                |

</div>

### 📈 Data Generation Plan
All tables, except the datetime table, were populated from the `staging database`, where four external Excel files related to [product](https://github.com/Fahim-Hossain-Data/SQL-Supply-Chain-Analytics--Product-Performance-Brand-Value-Supplier-Trends/blob/b0288433ebd1392fcda7940455cbdfd884627fbb/Product_info.xlsx), [suppliers](https://github.com/Fahim-Hossain-Data/SQL-Supply-Chain-Analytics--Product-Performance-Brand-Value-Supplier-Trends/blob/b0288433ebd1392fcda7940455cbdfd884627fbb/Suppliers_info.xlsx), [ received_purchase_orders](https://github.com/Fahim-Hossain-Data/SQL-Supply-Chain-Analytics--Product-Performance-Brand-Value-Supplier-Trends/blob/b0288433ebd1392fcda7940455cbdfd884627fbb/Fact_Received.xlsx), and [stock_level](https://github.com/Fahim-Hossain-Data/SQL-Supply-Chain-Analytics--Product-Performance-Brand-Value-Supplier-Trends/blob/b0288433ebd1392fcda7940455cbdfd884627fbb/Fact_Stock.xlsx) had been previously uploaded. A SQL script was used to create the datetime table by creating dates between 1/1/25 and 12/31/25.

*The following figure depicts the database tables name along with the data generation plan used to populate them.*
<p align="center">
  <img src="https://github.com/Fahim0729/Supply-Chain-Analytics-Using-SQL-Inventory-Sales-Supplier-Insights/blob/9926429eb37e25222dc4a0924a6475671eb8c358/Data_Generation_Plan.png" alt="Histogram" width="600"/>
  <br>
  <em>Figure: Database Tables and Data Generation Plan</em>
</p>


### 🔗 Database Diagram
Each fact table is connected to the three dimension tables, establishing relationships that support analysis and reporting.

*The database diagram in the following figure depicts the relationship between the fact and dimension table along with the primary keys of both table.*
<p align="center">
  <img src="https://github.com/Fahim0729/Supply-Chain-Analytics-Using-SQL-Inventory-Sales-Supplier-Insights/blob/29b2e9fcb6568ae46ca4417bcb80b131f7e53269/Database_Diagram.png" alt="Histogram" width="600"/>
  <br>
  <em>Figure: Database Diagram Showing Relationships between Fact and Dimension Tables.</em>
</p>

---

## 📋 Business Questions & [SQL Functions](https://github.com/Fahim-Hossain-Data/SQL-Supply-Chain-Analytics--Product-Performance-Brand-Value-Supplier-Trends/blob/21721845e0c951d62deb50fdbf61d5d42f37f039/2.%20SQL_Qustion%26Answer.sql)

The following section presents the answers to the questions along with the SQL queries used, and lists the SQL functions applied to solve each question.

### 📌 Q1. Brand Inventory Value Analysis
**Identify brands with significant restocking activity (>50 units) in the second half of 2025 (July-December) and analyze their average shelf inventory value to optimize supply chain planning for next year.**

🔹 SQL Functions: SUM(), AVG(), JOIN, BETWEEN, WHERE, GROUP BY, HAVING

📝 The brands with restocking of more than 50 units in June and December 2025 were JVC, MSCS, Sennheiser, Sony, and Toshiba. The electronics company received the highest number of units (543) from MSCS, followed by Toshiba with 202 units. Sennheiser, JVC, and Sony ranked 3rd, 4th, and 5th respectively in terms of total received units.
However, Sony had the highest average stock value despite being in 5th position based on total received units. In contrast, Toshiba recorded the lowest average stock value among the five brands.

*The results of the stock analysis are presented in the figure below, where the overall received units and the average stock value by brand during the period of July-December 2025 are shown.*
<p align="center">
  <img src="https://github.com/Fahim0729/Supply-Chain-Analytics-Using-SQL-Inventory-Sales-Supplier-Insights/blob/28f41ad3b6e538d1e7a947c404e91475f4f7f43f/Q1.png" alt="Histogram" width="600"/>
  <br>
  <em>Figure: Stock Analysis by Brand (July–December 2025)</em>
</p>

---

### 📌 Q2. Product Sales Velocity
**Identify the top 5 products by total quantity sold and categorize them as High (more than 90 units) Medium (60 to 90 units), or 
Low velocity (less than 60 units) to understand sales performance trends.**

🔹 SQL Functions: CTEs, JOIN, RANK(), ORDER BY, CASE

📝 The products were categorized into High velocity (over 90 units) and Medium velocity (60 to 90 units) and low velocity (less than 60 units) based on the total quantity sold. The five most sold products were ranked in terms of the volume of sales. The 1st to 3rd positions were occupied by the Manfrotto MN1004BAC Master Light Stand, Manfrotto MT057C3 Carbon Fibre 3 Section Geared, and Rycote 37705 Portable Recorder Suspension, which were all categorized as High Velocity. 4th and 5th were the Hoya 37S-HOY 37mm Skylight Filter and HOYA 40.5mm CP Filter -Slim, both of which were of the Medium Velocity category.

*The figure illustrates these rankings and classifications of products.*
<p align="center">
  <img src="https://github.com/Fahim0729/Supply-Chain-Analytics-Using-SQL-Inventory-Sales-Supplier-Insights/blob/28f41ad3b6e538d1e7a947c404e91475f4f7f43f/Q2.png" alt="Histogram" width="600"/>
  <br>
  <em>Figure: Product Rankings and Classifications</em>
</p>

---

### 📌 Q3. Supplier Restocking Trend Analysis
**Identify the top 3 suppliers with the largest positive change in received quantity by comparing their most recent delivery to their previous delivery, to understand suppliers with significant restocking trends.**

🔹 SQL Functions: Subquery, JOIN, LAG, ROW_NUMBER, RANK, ROUND, Filtering Logic

📝 The analysis identifies the top three suppliers with the largest positive change in received quantity by comparing their most recent delivery to the previous one. Samsung recorded the highest increase, receiving 90 units on 20 December 2025, which was 20 units more than its previous delivery. ENE was at the third position with a delivery of 77 units on 2 December 2025, which was 15 units more than what Toshiba had received previously. These findings identify suppliers with considerable tendencies of restocking over the period.


*The figure below presents the most recent deliveries of suppliers with the largest positive changes in received quantity.*
<p align="center">
  <img src="https://github.com/Fahim0729/Supply-Chain-Analytics-Using-SQL-Inventory-Sales-Supplier-Insights/blob/28f41ad3b6e538d1e7a947c404e91475f4f7f43f/Q3.png" alt="Histogram" width="600"/>
  <br>
  <em>Figure: Suppliers with the Highest Increases in Received Quantity – Latest Delivery Data</em>
</p>

---

### ⚙️ Data Cleaning / Preprocessing
A number of data cleaning procedures were researched in the project to guarantee data quality. Cost_Price and Retail_Price had to be checked to contain any zero values and transformed to NULL or default values using COALESCE and the price columns changed to DECIMAL(10,2) in consistency. Also the text fields like Product_Type were standardized by capitalizing the first letter and changing the remaining to lowercase. These steps were performed as part of the data preparation process to verify that price and product data were in the correct format.


---

## 🚀 Key Insights

| Analysis | Business Impact |
|----------|-----------------|
| **Brand Value Analysis** | Optimize inventory planning for 2026 |
| **Product Performance** | Identify sales velocity trends for top products |
| **Supplier Trends** | Recognize improving supplier relationships |

---

## 🌐 I’d Love to Connect!

- **LinkedIn:** [Md Fahim Hossain](https://www.linkedin.com/in/md-fahim-hossain-b51258227/)  
- **Email:** [fahimhossain0729@gmail.com](mailto:fahimhossain0729@gmail.com)

<div align="center">
  
**[⬆ Back to Top](#top)**

</div>
