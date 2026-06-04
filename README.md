# 🛒 E-Commerce Sales Data Analysis — SQL Project

**Decodelabs Internship | Week 3 Project**

## SQL Analysis: Extracting Business Insights from an E-Commerce Dataset Using SQL

![Image alt](https://github.com/Annozo-data/Decodelabs-E-Commerce-SQL-Analysis/blob/62567c51f3376c14c4edf85541ab57441c4b49c3/PJ3_SQL1.JPG)

---

## 📌 Project Overview

This project represents the Week 3 milestone of my Data Analytics Internship at Decodelabs.

The project focuses on using SQL to query, filter, group, and aggregate an e-commerce sales dataset to extract actionable business intelligence. The goal was to move beyond surface-level exploration and use structured relational queries to answer specific business questions with precision.

---

## 📊 Dataset Description

The dataset contains **1,200 rows** and **14 columns** representing e-commerce order transactions.

Key fields include:

* OrderID
* Date
* CustomerID
* Product
* Quantity
* UnitPrice
* TotalPrice
* CouponCode
* PaymentMethod
* ShippingAddress
* ReferralSource
* OrderStatus

---

## 🧹 Data Cleaning Process

Data cleaning was performed in **Microsoft Excel Power Query** before importing the dataset into SQL Server.

### Steps Taken

* Confirmed there were no duplicate OrderID entries.
* Standardized date formats to **YYYY-MM-DD**.
* Formatted UnitPrice and TotalPrice as currency.
* Verified that TotalPrice = Quantity × UnitPrice for consistency.
* Filled missing values in CouponCode with **"NO COUPON"**.
* Exported the cleaned dataset as **Sales.csv**.

---

## 🗄️ Database Setup

SQL Server (via Azure Data Studio) was used for all queries.

### Step 1: Create the Database

```sql
CREATE DATABASE Decodelabs;
```

### Step 2: Import the Dataset

Import **Sales.csv** as a flat file into the **Sales** table using the SQL Server Import Flat File Wizard.

### Step 3: Verify the Import

```sql
SELECT * FROM Sales;
```

---

## 🔍 SQL Queries & Analysis

### 1. View All Records

```sql
SELECT * FROM Sales;
```

### 2. High-Value Orders (TotalPrice ≥ $1,500)

```sql
SELECT *
FROM Sales
WHERE TotalPrice >= 1500;
```

### 3. Orders Without a Coupon

```sql
SELECT *
FROM Sales
WHERE CouponCode = 'NO COUPON';
```

### 4. Delivered Orders Only

```sql
SELECT *
FROM Sales
WHERE OrderStatus = 'Delivered';
```

### 5. Total Quantity Sold by Product

```sql
SELECT Product,
       SUM(Quantity) AS TotalQuantitySold
FROM Sales
GROUP BY Product
ORDER BY TotalQuantitySold DESC;
```

### 6. Total Revenue by Product

```sql
SELECT Product,
       SUM(TotalPrice) AS TotalRevenue
FROM Sales
GROUP BY Product
ORDER BY TotalRevenue DESC;
```

### 7. Average Order Value by Payment Method

```sql
SELECT PaymentMethod,
       AVG(TotalPrice) AS AvgOrderValue
FROM Sales
GROUP BY PaymentMethod
ORDER BY AvgOrderValue DESC;
```

### 8. Order Count by Referral Source

```sql
SELECT ReferralSource,
       COUNT(*) AS OrderNumber
FROM Sales
GROUP BY ReferralSource
ORDER BY OrderNumber DESC;
```

### 9. Coupon Usage and Revenue Generated

```sql
SELECT CouponCode,
       COUNT(*) AS TimesUsed,
       SUM(TotalPrice) AS Revenue
FROM Sales
GROUP BY CouponCode
ORDER BY Revenue DESC;
```

---

## 💡 Key Insights

### 1. High-Value Orders

Orders valued at **$1,500 and above** contribute significantly to overall revenue, with premium products such as Monitors and Tablets appearing frequently in this segment.

### 2. Coupon Usage

Most orders were completed without a coupon code, suggesting that customers are willing to purchase at full price, supporting healthy profit margins.

### 3. Order Fulfillment

Delivered orders accounted for the largest share of transactions. However, the presence of returned and cancelled orders highlights areas for further operational analysis.

### 4. Referral Sources

Referral and Instagram generated the highest order volumes, indicating that word-of-mouth recommendations and social media marketing are strong customer acquisition channels.

### 5. Payment Methods

Credit Card and Debit Card were the most frequently used payment methods, while Gift Card users displayed slightly different purchasing patterns.

---

## 🛠️ Tools Used

* Microsoft Excel
* Power Query
* SQL Server
* Azure Data Studio

---

## 📚 Skills Demonstrated

* Data Cleaning
* Data Transformation
* SQL Querying
* SELECT Statements
* WHERE Clauses
* GROUP BY
* ORDER BY
* Aggregations (COUNT, SUM, AVG)
* Business Intelligence Analysis

---

## 📂 Repository Contents

* Raw Dataset
* Cleaned Dataset (CSV)
* SQL Query Scripts
* Project Screenshot(s)
* README Documentation

---

## 👤 Author

**Anastasia Ozo-Ogueji**

Data Analytics Intern — Decodelabs

