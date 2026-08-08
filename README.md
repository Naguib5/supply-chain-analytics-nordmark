# 📦 Supply Chain Analytics | Nordmark Retail Group

## 📌 Project Overview

This project is an end-to-end **Supply Chain Analytics solution** developed using **Power BI** for **Nordmark Retail Group**, a mid-sized European omnichannel retailer operating across physical stores and e-commerce channels.

The objective of the project is to transform operational supply chain data into actionable insights that help the business move from **reactive decision-making to proactive inventory planning**.

The analysis covers inventory levels, stockouts, overstock, inventory movements, sales performance, product demand, and inventory efficiency across multiple locations and SKUs.

---

## 🏢 Business Context

Nordmark Retail Group operates an omnichannel supply chain:

```text
Suppliers
    ↓
Distribution Centers (DC)
    ↓
Stores
    ↓
Customers

        ↘ E-commerce

The company manages inventory across multiple locations while serving both physical stores and its online channel.

This creates several operational challenges:

Stockouts at specific locations
Overstock and excess inventory
Inventory imbalance between locations
Replenishment challenges
Poor visibility into inventory movements
Misalignment between inventory levels and customer demand
Reactive rather than proactive supply chain decisions
🎯 Business Objectives

The analysis was designed to answer the following key business questions:

1. Where and when does inventory run low or go out of stock?

Tables used:

inventory_snapshots
location_master

The analysis identifies locations and SKUs experiencing stockout conditions and highlights where inventory availability is most critical.

2. Which SKUs and locations drive the most sales volume and revenue?

Tables used:

sales_transactions
product_master

The analysis evaluates sales performance across products, categories, brands, and locations.

3. Which SKUs consistently carry more stock than demand requires?

Tables used:

inventory_snapshots
sales_transactions

Inventory levels are compared with sales activity to identify potential overstock and inefficient inventory allocation.

4. How often does replenishment happen, and for which SKUs / locations?

Table used:

inventory_movements

Inventory movement data is analyzed to understand replenishment activity and movement patterns across locations and products.

5. Do inventory movements broadly align with sales and inventory snapshot data?

Tables used:

inventory_movements
inventory_snapshots
sales_transactions

The analysis connects inventory movement behavior with stock levels and sales demand to identify potential supply chain misalignment.

📊 Dashboard Structure

The Power BI report contains the following main sections:

Home Page
Inventory Overview
Sales Analysis
Inventory Movements
Overstock & Stockout Analysis

The report also supports both Light and Dark dashboard themes.

🖼️ Dashboard Preview
🏠 Home Page

The Home Page provides navigation across the different analytical sections of the report.

📦 Inventory Overview

The Inventory Overview dashboard provides a high-level view of inventory health across the supply chain.

Key areas include:

Total Inventory On Hand
Inventory Value
Average Inventory Level
Active SKUs
Stockout SKUs
Stockout Rate
Inventory Trend
Inventory by Category
Stockout by Location
Inventory by Location Type
SKU-level inventory details

💰 Sales Analysis

The Sales dashboard analyzes sales performance across products, categories, locations, and other business dimensions.

Key areas include:

Sales performance
Revenue analysis
Product performance
Category performance
Location performance
Sales trends
Profitability analysis

🚨 Overstock & Stockout Analysis

This dashboard focuses on inventory imbalance and identifies products and locations that require operational attention.

It helps answer questions such as:

Where are stockouts occurring?
Which products are overstocked?
Which locations carry excessive inventory?
Which inventory positions require attention?
How does inventory compare with demand?

📈 Key Performance Indicators (KPIs)

The project includes several KPIs designed around the business requirements.

Inventory KPIs
Total Inventory On Hand
Inventory Value
Average Inventory Level
Total Active SKUs
Latest Inventory Level
Inventory to Sales Ratio
Stockout KPIs
Out of Stock SKUs
Stockout Count
Stockout Rate
Stockout by Location
Out of Stock Flag
Overstock KPIs
Overstock Products
Overstock Flag
Inventory vs Demand Analysis
Inventory to Sales Ratio
Sales KPIs
Total Sales
Units Sold
Profit
Profit Margin
Average Selling Price
Inventory Movement KPIs
Movement Count
Average Movement Quantity
Net Inventory Movement
Inventory Replenishment Activity
🧹 Data Cleaning & Preparation

The raw data was prepared before analysis using Power Query and SQL-based source tables.

The project data was extracted from the provided:

supply chain.back

database backup.

The backup was restored and the required tables were loaded into the analytical environment.

Data Sources

The project uses the following main tables:

Inventory
silver__inventory_snapshots__lite
gold__fact_inventory_exposure__lite
Inventory Movements
silver__inventory_movements__lite
Products
silver__product_master__lite
Locations
silver__location_master__lite
Sales
silver__sales_transactions__lite
Date
dim_date
Data Cleaning

Several data preparation and validation steps were performed, including:

Data type validation
Date standardization
Handling missing values
Validation of SKU identifiers
Validation of location identifiers
Checking inventory quantities
Checking duplicate records
Standardizing categorical fields
Validating relationships between tables
Reviewing negative inventory values
Validating inventory movement quantities
Preparing date attributes for time-based analysis
🧱 Data Modeling

A structured analytical model was created in Power BI using relationships between fact and dimension tables.

The model includes:

                 dim_date
                    |
                    |
                    ↓
          Sales Transactions
                    |
                    |
Product Master → Fact Tables ← Location Master
                    |
                    |
             Inventory Data
                    |
                    ↓
          Inventory Movements

The model separates transactional data from descriptive dimensions to improve:

Performance
Filtering
DAX calculations
Data consistency
Dashboard usability
🧮 DAX & Measure Development

A dedicated measures table was created to organize the analytical calculations.

Key measures include:

Total Inventory On Hand
Inventory Value
Average Inventory Level
Total Active SKUs
Out of Stock SKUs
Stockout Count
Stockout Rate
Latest Snapshot Date
Latest Inventory On Hand
Inventory to Sales Ratio
Low Inventory Products
Overstock Products
Movement Count
Average Movement Quantity
Net Inventory Movement
Total Sales
Profit
Profit Margin

The measures were designed to respond dynamically to report filters and slicers.

🔎 Exploratory Data Analysis

Before building the dashboards, the data was explored to understand:

Inventory Behavior
Inventory trends over time
Inventory distribution across locations
Inventory distribution by category
SKU-level inventory levels
Latest snapshot inventory position
Stockout Behavior
Stockout frequency
Stockout locations
Stockout SKUs
Stockout rate
Inventory availability by location
Overstock Behavior
High inventory SKUs
High inventory locations
Inventory-to-sales relationships
Potential excess inventory positions
Sales Behavior
Sales by category
Sales by product
Sales by location
Sales trends
Profitability patterns
Inventory Movements
Movement frequency
Movement quantities
Replenishment activity
Net inventory movement
Movement patterns by SKU and location
📊 Visual Analytics

The dashboards use different Power BI visualizations to communicate supply chain performance.

KPI Cards

Used for high-level operational monitoring.

Line Charts

Used for:

Inventory trends
Sales trends
Time-based performance
Column Charts

Used for:

Inventory by category
Sales by category
Product comparisons
Bar Charts

Used for:

Stockout by location
Product performance
Location comparisons
Donut Charts

Used for:

Inventory distribution by location type
Channel/location composition
Matrix

Used for detailed SKU and location-level analysis.

🎨 Dashboard Design

The dashboard was designed with a clean business-oriented UI.

Light Theme

The Light theme uses:

White / light-gray background
Blue as the primary analytical color
Consistent KPI cards
Clear navigation
Minimal visual clutter
Consistent typography
Dark Theme

A Dark theme was also developed for an alternative viewing experience.

Both themes maintain the same analytical structure while providing different visual styles.

💡 Business Insights

The dashboards help supply chain stakeholders identify:

Stockout Risk

Locations and SKUs with insufficient inventory can be identified and prioritized for replenishment.

Overstock Risk

Products with inventory levels significantly above sales demand can be investigated to reduce:

Working capital tied up in inventory
Storage costs
Markdown risk
Excess stock
Inventory Imbalance

Inventory distribution across locations can be compared to identify situations where stock exists in one location while another location experiences shortages.

Replenishment Activity

Inventory movement analysis provides visibility into how frequently inventory is being replenished and moved between locations.

Demand Alignment

Comparing inventory levels with sales activity provides an indication of whether inventory is aligned with actual customer demand.

🧭 Business Question Coverage
Business Question	Dashboard / Analysis
Where and when does inventory run low or go out of stock?	Inventory Overview + Overstock & Stockout
Which SKUs and locations drive the most sales volume and revenue?	Sales Dashboard
Which SKUs carry more stock than demand requires?	Overstock & Stockout + Inventory to Sales Ratio
How often does replenishment happen?	Inventory Movements
Do inventory movements align with sales and inventory snapshots?	Inventory Movements + Inventory Overview + Sales
👥 Business Users

The dashboard is designed to support different supply chain stakeholders.

Supply Chain Manager

Focuses on:

Stock availability
Stockout rate
Inventory efficiency
Location performance
Inventory Planner

Focuses on:

Replenishment
SKU inventory levels
Overstock
Low-stock products
Retail Operations Lead

Focuses on:

Store-level performance
Recurring stockout locations
Inventory distribution
E-commerce Lead

Focuses on:

Online inventory availability
Product availability
Replenishment requirements
Finance / Commercial Analyst

Focuses on:

Inventory value
Sales
Profit
Working capital exposure
🎯 Business Impact

The analysis is designed to support Nordmark's transition from:

Reactive Decisions
       ↓
Emergency Reallocation
       ↓
Stockouts / Overstock
       ↓
Higher Operational Cost

toward:

Data Analysis
       ↓
Early Risk Detection
       ↓
Better Replenishment
       ↓
Balanced Inventory
       ↓
Proactive Supply Chain Planning
🛠️ Tools & Technologies
Power BI
Power Query
DAX
SQL Server
Data Modeling
Data Cleaning
Exploratory Data Analysis
Business Intelligence
Data Visualization
📁 Repository Structure
Supply Chain Analytics – Nordmark Retail Group
│
├── Dashboard
│   └── Nordmark_Scenario.pbix
│
├── Dataset
│   └── Supply Chain Data
│
├── Screenshots
│   ├── Home Page.png
│   ├── Inventory Overview Dark.png
│   ├── Inventory Overview Light.png
│   ├── Inventory Movements Dark.png
│   ├── Inventory Movements Light.png
│   ├── Overstock & Stockout Dark.png
│   ├── Overstock & Stockout Light.png
│   ├── Sales Dark.png
│   └── Sales Light.png
│
└── README.md
🚀 Skills Demonstrated

Through this project, I demonstrated practical experience in:

SQL
Power BI
Power Query
DAX
Data Cleaning
Data Transformation
Data Modeling
KPI Development
Exploratory Data Analysis
Inventory Analytics
Supply Chain Analytics
Business Intelligence
Dashboard Development
Data Visualization
Business Problem Solving
Analytical Thinking
📌 Project Outcome

This project demonstrates how operational supply chain data can be transformed into a centralized analytical solution that helps decision-makers:

Detect stockout risks
Identify overstock
Monitor inventory levels
Analyze sales demand
Understand replenishment activity
Compare locations
Evaluate inventory efficiency
Make more informed supply chain decisions

The final Power BI solution provides both high-level executive monitoring and detailed SKU/location-level analysis.

🔗 Connect With Me
🌐 Portfolio

https://naguib5.github.io/

💼 LinkedIn

https://www.linkedin.com/in/naguib-mousa-a9719b220/

💻 GitHub

https://github.com/Naguib5

⭐ If you found this project useful, feel free to give the repository a star.