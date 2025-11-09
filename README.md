# PowerBI-SuperStore-Sales-Analysis-Forecasting
# 📊 Power BI Project: Super Store Sales Analysis & Forecasting  

### 🚀 Overview  
This project presents a complete **Power BI dashboard solution** designed to analyze and forecast sales data for a retail Super Store.  
It focuses on key business KPIs — **Sales, Profit, Quantity, Delivery Time, and Revenue Trends** — while integrating **predictive analytics** to forecast future sales using Power BI’s built-in forecasting model.  

The goal of this project is to demonstrate how data visualization and DAX calculations can convert raw data into **actionable business insights** and **predictive intelligence**.  

---

## 🎯 Project Objectives  
- Analyze **regional, category, and segment-wise** sales performance.  
- Track financial metrics like **Total Sales, Profit, Quantity**, and **Average Delivery Time**.  
- Implement **YTD, QTD, and MTD** revenue calculations using **DAX time intelligence functions**.  
- Build **interactive dashboards** with slicers, filters, tooltips, and drill-through features.  
- Forecast **future sales trends** using Power BI’s predictive analytics.  

---

## 🧠 Data Modeling  
The dataset was modeled in **Star Schema** format:  
- **Fact Table:** Sales  
- **Dimension Tables:** Region, Category, Sub-Category, Segment, and Date  

Data was cleaned and transformed using **Power Query Editor**, including:  
- Removing duplicates and missing values  
- Extracting date components (Year, Month, Quarter)  
- Calculating **Delivery Duration** (Ship Date - Order Date)  

---

## 📊 Dashboard 1: Sales Performance Overview  

### Key Insights  
- **West Region** achieved the **highest sales**.  
- **Cash on Delivery (COD)** was the top payment mode.  
- **Consumer Segment** dominated sales share.  
- **Office Supplies** category recorded the most sales.  
- **Phones** led sub-category sales with $0.20M.  
- **Standard Class** shipping mode delivered the maximum sales volume.  
- **Top States:** California, New York, Texas  

### KPIs  
| Metric | Value |
|--------|--------|
| 💰 Total Sales | $1.6M |
| 📈 Total Profit | $175K |
| 📦 Quantity Sold | 22K |
| ⏱️ Avg. Delivery | 4 Days |

### Trend Insights  
- Sales steadily rose toward **November–December**, reflecting strong year-end demand.  
- Profit trends mirrored sales with clear Q4 spikes.  

📍 *Interactive Features:* Region and Time-based slicers, custom tooltips, and drill-down navigation.  

---

## 📈 Dashboard 2: 15-Day Sales Forecasting  

- Used **Power BI’s built-in exponential smoothing** model to predict short-term sales trends.  
- **Forecast Period:** 15 days beyond last available data (2020 → early 2021).  
- **Confidence Interval:** Grey band visualizes prediction range.  
- **Top States:**  
  - 🥇 California – $0.34M  
  - 🥈 New York – $0.19M  
  - 🥉 Texas – $0.12M  

📍 *Insight:* Forecast suggests continued sales growth at the start of 2021, driven by high-performing states.  

---

## 💰 Dashboard 3: Revenue Analysis (YTD, QTD, MTD)  

### DAX Formulas  
```DAX
Total MTD = TOTALMTD(SUM('SuperStore_Sales_Dataset for power bi'[Profit]),'SuperStore_Sales_Dataset for power bi'[Order Date])
Total QTD = TOTALQTD(sum('SuperStore_Sales_Dataset for power bi'[Profit]),'SuperStore_Sales_Dataset for power bi'[Order Date])
Total YTD = TOTALYTD(SUM('SuperStore_Sales_Dataset for power bi'[Profit]),'SuperStore_Sales_Dataset for power bi'[Order Date])
Total Revenue = SUM('SuperStore_Sales_Dataset for power bi'[Profit])
Data 2020 = FILTER('SuperStore_Sales_Dataset for power bi',YEAR('SuperStore_Sales_Dataset for power bi'[Order Date])=2020)
Data 2019 = FILTER('SuperStore_Sales_Dataset for power bi',YEAR('SuperStore_Sales_Dataset for power bi'[Order Date])=2019)
Sales Forecast = SUMMARIZE('SuperStore_Sales_Dataset for power bi','SuperStore_Sales_Dataset for power bi'[Order Date],"Total Sales",SUM('SuperStore_Sales_Dataset for power bi'[Sales]))
