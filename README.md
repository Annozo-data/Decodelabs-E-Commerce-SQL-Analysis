# 🛒 E-Commerce Sales Data Analysis — SQL Project

Decodelabs Internship | Week 3 Project

SQL  Analysis: Extracting Business Insights from an E-Commerce Dataset using SQL
![Image alt](https://github.com/Annozo-data/Decodelabs-E-Commerce-SQL-Analysis/blob/62567c51f3376c14c4edf85541ab57441c4b49c3/PJ3_SQL1.JPG)

📌 Project Overview

This project is the Week 3 milestone of my data analytics internship at Decodelabs. This project focuses on using SQL to query, filter, group, and aggregate an e-commerce sales dataset to extract actionable business intelligence.
The goal was to move beyond surface-level exploration and use structured relational queries to answer specific business questions with precision. 

📊 Dataset Description

The dataset contains 1,200 rows and 14 columns representing e-commerce order transactions.

🧹 Data Cleaning Process

Cleaning was performed in Microsoft Excel Power Query before importing into SQL Server.
Steps taken:

Confirmed No duplicate OrderID entries
Standardized date formats to YYYY-MM-DD
Formatted UnitPrice and TotalPrice as currency
Verified TotalPrice = Quantity × UnitPrice for consistency
Filled missing values in CouponCode with "NO COUPON"
Exported the cleaned dataset as Sales.csv

🗄️ Database Setup

SQL Server (via Azure Data Studio) was used for all queries.

Step 1: 
Create the database

CREATE DATABASE Decodelabs;

Step 2: 
Import Sales.csv as a flat file into the Sales table

(Done via SQL Server Import Flat File Wizard)

Step 3: 
Verify the import

SELECT * FROM Sales;

🔍 SQL Queries & Analysis

1. View All Records
SELECT * FROM Sales;

2. High-Value Orders (TotalPrice ≥ $1,500)
SELECT *
FROM Sales
WHERE TotalPrice >= 1500;

3. Orders Without a Coupon
SELECT *
FROM Sales
WHERE CouponCode = 'NO COUPON';

4. Delivered Orders Only
SELECT *
FROM Sales
WHERE OrderStatus = 'Delivered';

5. Total Quantity Sold by Product
SELECT Product, SUM(Quantity) AS TotalQuantitySold
FROM Sales
GROUP BY Product
ORDER BY TotalQuantitySold DESC;

6. Total Revenue by Product
sqlSELECT Product, SUM(TotalPrice) AS TotalRevenue
FROM Sales
GROUP BY Product
ORDER BY TotalRevenue DESC;

7. Average Order Value by Payment Method
SELECT PaymentMethod, AVG(TotalPrice) AS AvgOrderValue
FROM Sales
GROUP BY PaymentMethod
ORDER BY AvgOrderValue DESC;

8. Order Count by Referral Source
SELECT ReferralSource, COUNT(Quantity) AS OrderNumber
FROM Sales
GROUP BY ReferralSource
ORDER BY OrderNumber DESC;

9. Coupon Usage and Revenue Generated
SELECT CouponCode, COUNT(*) AS TimesUsed, SUM(TotalPrice) AS Revenue
FROM Sales
GROUP BY CouponCode
ORDER BY Revenue DESC;

💡 Key Insights

1. High-value orders (≥ $1,500) account for a significant portion of revenue — premium products like Monitors and Tablets appear frequently in this segment.

2. Most orders had no coupon applied, suggesting customers are willing to pay full price — a positive sign for margin health.

3. Delivered orders form the largest status group, but a notable number of Returned and Cancelled orders warrant further investigation.

4. Referral and Instagram are the top traffic sources, indicating social media and word-of-mouth are key acquisition channels.

5. Credit Card and Debit Card dominate payment methods, with Gift Card users showing slightly different purchasing patterns.

🛠️ Tools Used

Microsoft Excel + Power Query for data cleanining and transformation.
SQL Server (SSMS / Azure Data Studio) for database creation, import, and querying

Skills Demonstrated

Data Cleaning, SQL SELECT, WHERE, GROUP BY, ORDER BY, Aggregations (COUNT, SUM, AVG)

👤 Author

Anastasia Ozo-ogueji

Data Analytics Intern — Decodelabs


