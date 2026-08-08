# Supply Chain Analytics | Nordmark Retail Group

Power BI Supply Chain Analytics Dashboard for monitoring inventory health, stockouts, overstock, sales performance, inventory movements, and supply chain efficiency.

---

## Project Overview

Nordmark Retail Group is a mid-sized European omnichannel retailer operating through physical stores and an e-commerce channel.

The company manages a multi-node supply chain where inventory flows through:

**Suppliers → Distribution Centers (DCs) → Stores → Customers**

For online orders, inventory can be fulfilled directly from Distribution Centers or stores, which increases the complexity of inventory planning and allocation.

The objective of this project is to transform operational supply chain data into actionable insights that help Nordmark move from reactive decision-making toward proactive supply chain planning.

The analysis focuses on:

- Inventory availability
- Stockout detection
- Overstock identification
- Sales performance
- Inventory movements
- Inventory value
- Product and location performance
- Supply chain efficiency
- Replenishment behavior

---

## Business Problem

Nordmark generates a large amount of operational data, but the main challenge is converting this data into timely and actionable decisions.

The key business problems identified in the scenario are:

**Stockouts**
Products can become unavailable at one location while inventory is still available elsewhere.

*Business impact:*
- Lost sales
- Lower customer satisfaction
- Reduced product availability
- Emergency inventory reallocations

**Overstock**
Some SKUs may carry significantly more inventory than the level supported by demand.

*Business impact:*
- Working capital tied up in inventory
- Higher storage costs
- Increased markdown risk
- Lower inventory efficiency

**Poor Forecasting**
Forecast errors may only become visible after inventory problems have already occurred.

**Channel Misalignment**
Store and e-commerce inventory requirements may compete for the same available stock.

**Reactive Decisions**
Supply chain teams may respond to problems after they occur instead of identifying risks early.

---

## Business Questions

The project was designed around five key business questions defined in the business scenario.

| # | Business Question | Main Data Sources |
|---|---|---|
| 1 | Where and when does inventory run low or out of stock? | Inventory Snapshots, Location Master |
| 2 | Which SKUs and locations drive the most sales volume and revenue? | Sales Transactions, Product Master |
| 3 | Which SKUs consistently carry more stock than demand requires? | Inventory Snapshots, Sales Transactions |
| 4 | How often does replenishment happen, and for which SKUs / locations? | Inventory Movements |
| 5 | Do inventory movements broadly align with sales and snapshot data? | Movements, Snapshots, Sales |

---

## Project Objectives

The analysis supports Nordmark's supply chain objectives across three time horizons.

**Short-Term (0–6 Months)**
- Reduce stockout incidents
- Stop unnecessary emergency reallocations
- Stabilize the replenishment cycle
- Improve visibility of inventory availability

**Mid-Term (6–18 Months)**
- Improve inventory efficiency
- Improve forecast accuracy
- Improve coordination between stores and online channels
- Increase inventory turnover

**Long-Term (18+ Months)**
- Build a resilient supply chain
- Absorb demand fluctuations more effectively
- Scale operations efficiently
- Reduce operational cost per unit

---

## Data Sources

The project was developed using data from the Nordmark supply chain database.

The original database was provided as a SQL Server backup: `supply_chain.bak`

The backup was restored and analyzed using SQL Server.

The Power BI model uses the following main tables:

- `silver__inventory_snapshots__lite`
- `silver__inventory_movements__lite`
- `silver__sales_transactions__lite`
- `silver__product_master__lite`
- `silver__location_master__lite`
- `gold__fact_inventory_exposure__lite`

> The SQL Server backup file is intentionally not included in the GitHub repository because the file exceeds GitHub's 100 MB file-size limit.

---

## Data Preparation & Cleaning

The data preparation process was performed using SQL Server, Power Query, and Power BI, and included:

- Data type validation
- Data consistency checks
- Handling missing and invalid values
- Standardizing date fields
- Checking duplicate records
- Validating SKU identifiers
- Validating location information
- Checking inventory quantities
- Checking inventory values
- Validating relationships between operational tables
- Reviewing negative inventory values
- Identifying stockout records
- Preparing snapshot-based inventory analysis

---

## Exploratory Data Analysis

Before building the dashboard, the data was explored to understand the operational structure of the business.

**Inventory**
- Inventory levels over time
- Inventory by category
- Inventory by location
- Inventory by location type
- Inventory value
- Stockout products
- Low inventory products
- Overstock products

**Sales**
- Sales volume
- Revenue
- Product performance
- Location performance
- Category performance
- Customer and channel behavior

**Inventory Movements**
- Movement quantities
- Movement frequency
- Movement types
- Movement behavior by SKU
- Movement behavior by location

**Supply Chain Relationships**

The analysis also compared:
- Inventory levels vs. sales
- Inventory movements vs. inventory snapshots
- Inventory availability vs. location
- Stock levels vs. demand

This exploration helped identify the KPIs and visuals required for the final dashboard.

---

## Data Model

The Power BI model was designed around the main operational supply chain entities.

**Inventory Snapshots** — tracks inventory levels at different dates and locations.

**Inventory Movements** — used to analyze replenishment and inventory movement activity.

**Sales Transactions** — used to analyze product demand, sales volume, and revenue.

**Product Master** — provides product attributes such as:
- SKU
- Category
- Brand
- Product information

**Location Master** — provides location attributes such as:
- Location
- Location type
- Store
- Distribution Center
- Online

**Date Table** — used for time-based analysis and filtering.

---

## Power BI & DAX

The dashboard was developed using:

- Power BI Desktop
- Power Query
- DAX
- Data Modeling
- Interactive Visualizations
- KPI Design

Measures were created to support inventory, sales, stockout, overstock, and movement analysis.

---

## Key Performance Indicators

The Inventory Overview dashboard includes the following KPIs:

| KPI | Description |
|---|---|
| **Total Inventory On Hand** | Total quantity of inventory currently available based on the selected snapshot |
| **Inventory Value** | Financial value of the available inventory |
| **Out of Stock SKUs** | Count of SKUs that are currently out of stock |
| **Stockout Rate** | Proportion of active SKUs affected by stockouts |
| **Selected Snapshot Date** | Latest/selected inventory snapshot date used for the current analysis |
| **Average Inventory Level** | Average inventory quantity across the selected context |
| **Total Active SKUs** | Number of active SKUs being monitored |
| **Stockout Count** | Number of stockout records/incidents within the selected context |

---

## Dashboard Structure

The Power BI report contains multiple analytical pages.

### 1. Home Page

Provides an introduction to the Nordmark Supply Chain Analytics project and acts as the main navigation page, giving access to:

- Inventory Overview
- Sales
- Inventory Movements
- Overstock & Stockout

### 2. Inventory Overview

A high-level view of the current inventory situation.

**Main Visuals**
- Inventory Trend
- Inventory by Category
- Stockout by Location
- Inventory by Location Type
- Detailed Inventory Matrix

**Main Questions Answered**
- How is inventory changing over time?
- Which categories hold the most inventory?
- Which locations experience the most stockouts?
- How is inventory distributed between stores, DCs, and online?
- Which SKUs and locations currently have inventory issues?

**Business Question Coverage**
Primarily supports **Business Question 1** — *Where and when does inventory run low or out of stock?*
Also supports **Business Question 3** — *Which SKUs consistently carry more stock than demand requires?*

### 3. Sales Dashboard

Focuses on demand and sales performance, used to understand:

- Sales volume
- Revenue
- Product performance
- Category performance
- Location performance
- Customer/channel behavior

The Sales analysis provides the demand-side perspective required to evaluate whether inventory levels are aligned with actual sales.

**Business Question Coverage**
Primarily supports **Business Question 2** — *Which SKUs and locations drive the most sales volume and revenue?*
Also supports **Business Question 3**, by providing demand information that can be compared with inventory levels.

### 4. Inventory Movements

Analyzes inventory movement activity across the supply chain, focusing on:

- Movement quantity
- Movement frequency
- Movement behavior by SKU
- Movement behavior by location
- Replenishment activity
- Inventory flow

**Business Question Coverage**
Primarily supports **Business Question 4** — *How often does replenishment happen, and for which SKUs / locations?*
Also supports **Business Question 5** — *Do inventory movements broadly align with sales and snapshot data?*

### 5. Overstock & Stockout

Focuses specifically on inventory risk, helping to identify:

- **Stockout Risk** — products that have insufficient inventory or are completely out of stock
- **Overstock Risk** — products carrying inventory levels significantly above the required level relative to demand

**Main Analysis Areas**
- Overstock products
- Stockout products
- Inventory risk by location
- Inventory risk by category
- Inventory vs. sales
- Product-level inventory status
- Location-level inventory issues

**Business Question Coverage**
Primarily supports **Business Question 3** — *Which SKUs consistently carry more stock than demand requires?*
Also supports **Business Question 1** — *Where and when does inventory run low or out of stock?*

---

## Business Question Coverage Summary

| Business Question | Dashboard Page | Main Analysis |
|---|---|---|
| Where and when does inventory run low or out of stock? | Inventory Overview + Overstock & Stockout | Stockout by Location, Stockout KPIs, Inventory Trend |
| Which SKUs and locations drive the most sales volume and revenue? | Sales | Sales, Revenue, SKU and Location Analysis |
| Which SKUs consistently carry more stock than demand requires? | Overstock & Stockout + Sales | Overstock Products, Inventory vs Sales |
| How often does replenishment happen? | Inventory Movements | Movement Count, Movement Quantity, Replenishment Analysis |
| Do inventory movements align with sales and snapshots? | Inventory Movements + Inventory Overview + Sales | Movement vs Sales vs Inventory Analysis |

---

## Interactive Features

The dashboard includes interactive filters to allow users to analyze the supply chain from different perspectives:

- Year
- Month
- Location Type
- Location Name
- Category
- Brand

Users can combine filters to investigate specific time periods, locations, product categories, brands, and supply chain nodes — allowing managers and planners to move from high-level KPIs to detailed SKU-level analysis.

---

## Dashboard Themes

The report was designed with both a **Light Theme** and a **Dark Theme**.

- The **Light Theme** uses a clean, blue-based visual identity designed for professional reporting and presentation.
- The **Dark Theme** provides an alternative visual experience while maintaining the same analytical structure.

---

## 🖼️ Dashboard Preview

### Home Page
![Home Page](Screenshots/home-page.png)

### Inventory Overview

| Light Theme | Dark Theme |
|---|---|
| ![Inventory Overview Light](Screenshots/inventory-overview-light.png) | ![Inventory Overview Dark](Screenshots/inventory-overview-dark.png) |

### Sales Dashboard

| Light Theme | Dark Theme |
|---|---|
| ![Sales Dashboard Light](Screenshots/sales-light.png) | ![Sales Dashboard Dark](Screenshots/sales-dark.png) |

### Inventory Movements

| Light Theme | Dark Theme |
|---|---|
| ![Inventory Movements Light](Screenshots/inventory-movements-light.png) | ![Inventory Movements Dark](Screenshots/inventory-movements-dark.png) |

### Overstock & Stockout

| Light Theme | Dark Theme |
|---|---|
| ![Overstock & Stockout Light](Screenshots/overstock-stockout-light.png) | ![Overstock & Stockout Dark](Screenshots/overstock-stockout-dark.png) |

---

## Key Business Insights

The dashboard is designed to help supply chain stakeholders identify:

- Locations with recurring stockout problems
- SKUs with low inventory availability
- Categories holding large amounts of inventory
- Products with potential overstock risk
- Differences in inventory distribution across supply chain nodes
- Sales and demand concentration
- Replenishment activity across locations
- Potential mismatches between inventory, sales, and movements

The purpose of these insights is not only to report what happened, but to support decisions around replenishment, inventory allocation, stockout prevention, overstock reduction, inventory planning, and channel coordination.

---

## Business Value

| Stakeholder | Can Monitor |
|---|---|
| **Supply Chain Manager** | Stockout levels, product availability, inventory distribution, inventory efficiency |
| **Inventory Planner** | Low-stock SKUs, overstock SKUs, replenishment requirements, inventory imbalances |
| **Retail Operations Lead** | Store-level stockout issues, recurring location problems, product availability |
| **E-commerce Lead** | Online inventory availability, inventory competition between channels, replenishment requirements |
| **Finance / Commercial Analyst** | Inventory value, revenue, sales performance, potential working-capital impact of excess inventory |

---

## Tools & Technologies

- Microsoft Power BI
- Power Query
- DAX
- SQL Server
- Data Modeling
- Data Cleaning
- Exploratory Data Analysis
- KPI Development
- Business Intelligence
- Data Visualization

---

## Skills Demonstrated

**Data Analytics**
- Exploratory Data Analysis
- Business Requirements Analysis
- KPI Design
- Supply Chain Analytics
- Inventory Analysis
- Sales Analysis
- Demand vs Inventory Analysis

**Data Engineering / Preparation**
- SQL Server
- Power Query
- Data Cleaning
- Data Transformation
- Data Validation
- Data Modeling

**Power BI**
- Interactive Dashboards
- DAX Measures
- KPI Cards
- Matrix Visuals
- Trend Analysis
- Category Analysis
- Location Analysis
- Drill-down Analysis
- Interactive Slicers
- Light / Dark Dashboard Themes

---

## Repository Structure

```text
Supply Chain Analytics • Nordmark Retail Group
│
├── Dashboard
│   ├── supply_chain.pbix
│   ├── supply_chain Light.pdf
│   └── supply_chain Dark.pdf
│
├── Dataset
│   └── supply_chain.bak
│
├── Screenshots
│   ├── home-page.png
│   ├── inventory-overview-light.png
│   ├── inventory-overview-dark.png
│   ├── sales-light.png
│   ├── sales-dark.png
│   ├── inventory-movements-light.png
│   ├── inventory-movements-dark.png
│   ├── overstock-stockout-light.png
│   └── overstock-stockout-dark.png
│
└── README.md
```

> **Note:** The original `supply_chain.bak` SQL Server backup is part of the project source data but is excluded from the GitHub repository because GitHub enforces a 100 MB individual file-size limit.

---

## Project Workflow

```
Business Requirements
        ↓
Data Source
        ↓
SQL Server
        ↓
Data Cleaning & Validation
        ↓
Exploratory Data Analysis
        ↓
Data Modeling
        ↓
DAX Measures & KPIs
        ↓
Dashboard Development
        ↓
Business Insights
        ↓
Decision Support
```

---

## Final Outcome

The final Power BI solution transforms raw operational supply chain data into an interactive analytical dashboard, providing visibility into:

- Inventory availability
- Stockouts
- Overstock
- Sales performance
- Inventory movements
- Product performance
- Location performance
- Inventory value
- Supply chain risk

This enables Nordmark Retail Group to move from reactive supply chain management toward a more data-driven and proactive planning approach.

---

## Author

**Naguib Mousa**
Data Analyst | Power BI Developer | SQL | Excel | Data Visualization | BI

- Portfolio: [naguib5.github.io](https://naguib5.github.io/)
- LinkedIn: [linkedin.com/in/naguib-mousa-a9719b220](https://www.linkedin.com/in/naguib-mousa-a9719b220/)
- GitHub: [github.com/Naguib5](https://github.com/Naguib5)

⭐ If you found this project useful, feel free to star the repository.