# 🌍 Global Superstore Power BI Dashboard

## 📁 Project Overview

The goal of this project is to build an interactive Power BI dashboard using the **Global Superstore dataset**, focusing on analyzing **sales performance**, **customer behavior**, **product trends**, and **operational efficiency** across different regions and markets.

---

## 🎯 Business Objectives

- Track and compare **sales, profit, and revenue** by region, country, and city
- Analyze **product category performance** and **return impacts**
- Understand **customer demographics** and their buying behavior
- Compare **market trends** to identify growth opportunities
- Forecast **future sales and product demand**
- Improve **shipping cost efficiency** to enhance profitability

---

## 🧹 Data Cleaning & Transformation (Power Query)

- Loaded the CSV dataset into Power BI
- Cleaned 3 main tables:
  - Removed duplicates
  - Filled missing values
  - Changed data types
  - Used "First Row as Header" where needed
- Renamed columns for consistency and better readability
- Applied changes using "Close & Apply"

---

## 🧠 DAX Measures Created

- `Total Sales`
Total Sales = SUM('Orders'[Sales])
- `Total Profit`
Total Profit = SUM('Orders'[Profit])
- `Profit Margin %`
  Profit Margin % = 
    DIVIDE(
        SUM('Orders'[Profit]),
        SUM('Orders'[Sales]),
        0
    ) * 100

- `Customer Frequency`
Customer Frequency = 
    CALCULATE(
        COUNTROWS('Orders'),
        ALLEXCEPT('Orders', 'Orders'[Customer ID])
    )

- `Order Per Customer`
Order Per Customer = 
    CALCULATE(
        COUNT('Orders'[Order ID]),
        ALLEXCEPT('Orders', 'Orders'[Customer ID])
    )

- `Day Difference` between Order Date and Ship Date
Day Difference = DATEDIFF('Orders'[Order Date], 'Orders'[Ship Date], DAY)

- Created Date columns: `Order Month`, `Order Year`, `Order Day`
- Created table for top 10 customers demographics 
Top10Customers = 
TOPN (
    10,
    SUMMARIZE (
        'Orders',
        'Orders'[Order ID],
        'Orders'[Customer Name],
        'Orders'[Segment],
        'Orders'[Region],
        'Orders'[Order Priority],
        'Orders'[Ship Mode],
        'Orders'[Category],
        'Orders'[day difference],
        'Orders'[Sub-Category],
        'Orders'[Market],
        "TotalSales", SUM('Orders'[Sales])
    ),
    [TotalSales],
    DESC
)

---

## 🔗 Data Model

- Built relationships between 4 main tables using Model View
- Defined hierarchies:
  - `Category > Subcategory`
  - `Region > Country > City`
  - `Order Year > Order Month> Order Day`

---

## 📊 Dashboards Created

### 1️⃣ Sales Overview Dashboard
- **Card KPIs**: Total Sales, Average Sales, Discount, Customer Count, Purchase Frequency, Quantity Sold
- **Visuals**:
  - Sales by Region Hierarchy
  - Sales by Category Hierarchy
  - Sales by Market
  - Sales Trend by Month
  - Profit Margin % by Category

---

### 2️⃣ Profit & Returned Analysis
- **Card KPIs**: Total Profit, Profit Margin %, Avg Profit, Count of Returns, Sum of Returned Sales
- **Visuals**:
  - Profit by Region Hierarchy
  - Profit by Category Hierarchy
  - Profit over Time (Monthly)
  - Profit by Market
  - Table: Returned Orders with Sales Impact

---

### 3️⃣ Demographics & Forecasting
- **Visuals**:
  - Top 10 Customers Demographics
  - Sales by Segment
  - Sales by Ship Mode
  - Sales by Order Priority
  - Forecasting: Sales & Profit using Power BI Forecast Analytics

---

### 4️⃣ 📦 Shipping Cost Analysis (Added by Analyst)
#### 🛠️ Objective:
Analyze shipping cost distribution across order priority, delivery mode, product types, and region to uncover inefficiencies.

#### 📌 Key Metrics:
- `Total Shipping Cost`
- `Average Shipping Cost`
- `Shipping Cost per Product`
- `Shipping Cost % of Sale`

#### 📊 Visuals:
- Shipping Cost by:
  - Region Hierarchy
  - Category Hierarchy
  - Ship Mode
  - Order Priority
  - Market
  

## 🔀 Page Navigation

- Added **Page Navigator** buttons for seamless interactivity across all dashboards.

---


## 🚀 Tools & Skills Used

- **Power BI**
- **Power Query**
- **DAX (Calculated Columns & Measures)**
- **Data Modeling & Relationships**
- **Forecasting Analytics**
- **Interactive UX (Page Navigation)**

---

## ✅ Outcome

This project demonstrates the ability to:
- Clean and model real-world datasets
- Design multi-page business dashboards
- Perform deep business analysis
- Forecast trends and recommend optimizations
- Align data with strategic business goals

---






