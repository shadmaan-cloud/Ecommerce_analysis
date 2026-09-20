# 🛒 E-Commerce Sales Analytics — SQL Project

A **MySQL-based E-Commerce Sales Analytics project** designed to analyze customer behavior, product performance, order trends, and revenue using advanced SQL techniques.

The project contains **26 progressively challenging business questions** covering:

* 🔗 Joins
* 🪟 Window Functions
* 🧩 Common Table Expressions (CTEs)
* 🔍 Subqueries
* 📊 Revenue & Sales Analysis
* 👥 Customer Analysis
* 📦 Product Analysis
* 📅 Monthly Sales Trends

---

## 📌 Project Overview

The objective of this project is to analyze an e-commerce dataset containing customers, orders, products, and order line items.

The analysis focuses on understanding:

* Customer purchasing behavior
* Customer revenue contribution
* Product and product-type performance
* Order-level revenue
* Monthly revenue trends
* Customer retention and repeat purchases
* High-value customers
* Products and orders performing above average

The project was developed using **MySQL 8.0+**.

---

## 🗂️ Dataset Structure

The database consists of four normalized tables:

### 1. `customers`

| Column           | Description                |
| ---------------- | -------------------------- |
| `customer_id`    | Unique customer identifier |
| `first_name`     | Customer first name        |
| `last_name`      | Customer last name         |
| `email`          | Customer email             |
| `address`        | Customer address           |
| `city`           | Customer city              |
| `state_province` | Customer state/province    |

### 2. `orders`

| Column        | Description                   |
| ------------- | ----------------------------- |
| `order_id`    | Unique order identifier       |
| `customer_id` | Customer who placed the order |
| `order_date`  | Date of order                 |

### 3. `product_orders`

| Column       | Description        |
| ------------ | ------------------ |
| `order_id`   | Order identifier   |
| `product_id` | Product identifier |
| `quantity`   | Quantity purchased |
| `unit_price` | Price per unit     |

### 4. `products`

| Column         | Description               |
| -------------- | ------------------------- |
| `product_id`   | Unique product identifier |
| `product_name` | Product name              |
| `product_type` | Product category/type     |

Revenue is calculated as:

```text
Revenue = Quantity × Unit Price
```

The database structure and revenue definition are documented in the SQL project.

---

## 📊 Dataset Snapshot

| Dataset Component |                 Records |
| ----------------- | ----------------------: |
| Customers         |                   1,000 |
| Products          |                      64 |
| Orders            |                     300 |
| Order Line Items  |                     985 |
| Order Date Range  | 2019-02-10 → 2020-02-06 |

The dataset snapshot is also documented in the project presentation.

---

## 🛠️ Tech Stack

* **MySQL 8.0+**
* **MySQL Workbench**
* SQL
* Window Functions
* CTEs
* Subqueries
* Aggregate Functions
* Joins
* `LOAD DATA INFILE`

---

## 🧠 SQL Concepts Covered

### 🔗 Joins

Questions **Q1–Q6** use `INNER JOIN` and `LEFT JOIN` to connect customers, orders, products, and order line items.

Examples:

```sql
INNER JOIN
LEFT JOIN
```

Applications include:

* Customer revenue analysis
* Product performance
* Customers with no orders
* Products never ordered
* Order-level revenue

---

### 🪟 Window Functions

Questions **Q7–Q14** use window functions for ranking, sequencing, cumulative calculations, and time-based comparisons.

Functions used include:

```sql
DENSE_RANK()
ROW_NUMBER()
LAG()
SUM() OVER()
FIRST_VALUE()
```

Examples:

* Ranking customers by revenue
* Finding top products within each product type
* Running monthly revenue
* Customer order sequence
* Days between customer orders
* Monthly revenue growth

---

### 🧩 Common Table Expressions (CTEs)

Questions **Q15–Q20** use CTEs to break complex analysis into smaller and more readable steps.

Examples:

```sql
WITH CUSTOMER_SUMMARY AS (...)
```

Applications include:

* Customer segmentation
* Product-type performance
* Top customers per month
* Increasing order activity
* Orders above monthly average
* Customer retention analysis

---

### 🔍 Subqueries

Questions **Q21–Q26** use subqueries to compare records against calculated averages, rankings, and other aggregated values.

Examples:

* Customers spending above average
* Products above average revenue
* Orders above customer's average
* Customers with at least 3 orders
* Customers purchasing a specific product type
* Second-highest revenue product

The presentation groups Q21–Q26 under subquery-based analysis.

---

# 📋 Business Questions Covered

## Customer Analysis

1. Customer Revenue Analysis
2. Customers With No Orders
3. Rank Customers by Revenue
4. Customer Order Sequence
5. Order Contribution to Customer Revenue
6. Highest-Value Order for Every Customer
7. Customer Purchase Segmentation
8. Top 5 Customers in Each Month
9. Customers With Increasing Order Activity
10. Customer Retention / Repeat Purchase Analysis
11. Customers Spending Above Average
12. Customers With At Least 3 Orders
13. Customers Who Bought a Specific Product Type

## Product Analysis

14. Product Performance
15. Product-Type Revenue Analysis
16. Top 3 Products Within Each Product Type
17. Product Type Performance
18. Products Above Average Revenue
19. Second-Highest Revenue Product
20. Products Never Ordered

## Order & Revenue Analysis

21. Order-Level Revenue
22. Running Monthly Revenue
23. Monthly Revenue Growth
24. Orders Above Monthly Average
25. Orders Above Customer's Average Order Value

---

# 💡 Key Business Insights

The analysis generated several notable findings from the dataset.

### 👥 Customer Insights

* **1,000 customers** are present in the dataset.
* **847 customers** have never placed an order.
* **124 customers** qualify as high-value customers under the project's `≥ 1,000` revenue threshold.
* **87 customers** are repeat-purchase customers.
* **44 customers** have placed at least three orders.

### 📦 Product Insights

* **Oven** is the highest-revenue product type with revenue of **30,697.60** in the product-type analysis.
* **Bread machine** is the highest-revenue individual product with revenue of **9,987.58**.
* **Grinder** has the lowest product-type revenue at **3,887.98**.

### 💰 Revenue Insights

* Total revenue across the analyzed orders is **465,299.45**.
* **May 2019** generated the highest monthly revenue at **57,462.69**.
* May 2019 also recorded a month-over-month revenue growth of **74.68%**.

These findings are reported in the accompanying project presentation.

---

# 🧹 Data Quality & Troubleshooting

During the data-loading process, several real-world data issues were encountered:

### Character Encoding

A city value containing a non-standard character caused problems with the GUI import process because of an encoding mismatch.

### `local_infile` Restriction

MySQL required `local_infile` to be enabled before using local bulk data loading.

### Missing Trailing Newline

The final CSV record did not contain a trailing line terminator, causing an incomplete row during loading.

### Date Format

The source data contained dates in `M/D/YYYY` format. `STR_TO_DATE()` was used to convert the values into proper MySQL `DATE` values.

### Orphaned Foreign Keys

The dataset contained **21 `product_id` values in `product_orders` that were missing from the `products` catalog**.

These data-loading and quality issues are documented in the project presentation.

---

# 📁 Project Files

```text
E-Commerce-SQL-Analytics/
│
├── mysql_ecommerce_data_analytics_answers.sql
├── ecommerce_sql_presentation.pptx
└── README.md
```

### SQL File

Contains the complete set of **26 SQL business questions and solutions**, covering joins, window functions, CTEs, and subqueries.

### Presentation

Contains the project overview, database structure, data-quality challenges, SQL approach, business questions, insights, and results.

---

# 🚀 How to Run the Project

### Step 1 — Install MySQL

Install **MySQL 8.0 or later**.

### Step 2 — Open MySQL Workbench

Create or select your database.

Example:

```sql
CREATE DATABASE ecommerce_analytics;
USE ecommerce_analytics;
```

### Step 3 — Create the Tables

Create the following tables:

```text
customers
orders
product_orders
products
```

### Step 4 — Load the Dataset

Import the CSV data into the corresponding tables.

If using `LOAD DATA INFILE`, ensure that the MySQL `local_infile` setting is configured correctly.

### Step 5 — Run the SQL Queries

Open:

```text
mysql_ecommerce_data_analytics_answers.sql
```

Execute the queries individually to reproduce the analysis.

---

# 📈 Skills Demonstrated

This project demonstrates practical knowledge of:

* SQL for Data Analytics
* Relational Database Concepts
* Data Aggregation
* `GROUP BY` and `HAVING`
* `INNER JOIN`
* `LEFT JOIN`
* Subqueries
* Correlated Subqueries
* Common Table Expressions
* Window Functions
* Ranking
* Running Totals
* Time-Series Analysis
* Customer Segmentation
* Revenue Analysis
* Data Quality Troubleshooting
* Business-oriented SQL problem solving

---

# 🎯 Project Objective

The main objective of this project was not only to write SQL queries, but to transform raw e-commerce data into **business-oriented insights** using SQL.

The project progresses from basic joins and aggregations to more advanced analytical techniques such as:

```text
JOINs
   ↓
Aggregations
   ↓
Window Functions
   ↓
CTEs
   ↓
Subqueries
   ↓
Business Analysis
```

---

# 👨‍💻 Author

**Shadmaan Ahmad**

B.Tech — Computer Science & Engineering

**Data Analytics Practice Project**

---

## ⭐ Topics

`SQL` `MySQL` `Data Analytics` `E-Commerce Analytics` `SQL Project` `Joins` `CTE` `Window Functions` `Subqueries` `Data Analysis` `MySQL Workbench`
