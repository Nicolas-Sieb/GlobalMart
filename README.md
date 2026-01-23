# Superstore
## Project Background

GlobalMart, established in 2010, is a global retail company selling Technology, Furniture, and Office Supplies products across 165 countries via its e-commerce platform.

The company has significant amounts of data on its sales, operational efficiency, product offerings, and regional performance that has been previously underutilized. This project thoroughly analyzes and synthesizes this data in order to uncover critical insights that will improve GlobalMart's commercial success.

Insights and recommendations are provided on the following key areas:

* **Sales Trends Analysis:** Evaluation of historical sales patterns from 2012-2015, focusing on Revenue, Order Volume, and profitability trends.
* **Product Category Performance:** An analysis of Technology, Furniture, and Office Supplies categories, understanding their impact on overall profitability.
* **Market Regional Performance:** An assessment of the five global markets (Asia Pacific, Europe, USCA, LATAM, Africa) to guide expansion strategy.
* **Unprofitable Orders:** An evaluation of loss-making transactions to identify pricing and discount management issues.


An interactive Tableau dashboard can be downloaded [here](https://public.tableau.com/app/profile/nicolas.siebler/viz/SalesPerformanceDashboard_17689124400200/Dashboard1).

The Python code utilized to clean, organize, and prepare data for the dashboards can be found [here](https://github.com/Nicolas-Sieb/GlobalMart/blob/main/GlobalMart_Data_Cleaning.ipynb).

Targeted SQL queries regarding various business questions can be found [here](https://github.com/Nicolas-Sieb/GlobalMart/blob/main/GlobalMart_SQL.ipynb).

## Data Structure & Initial Checks

GlobalMart's database structure consists of a star schema with six dimension tables and one fact table, with a total row count of 49,366 order records.

![Database Schema](images/database-schema.png)

*Database Entity Relationship Diagram*

### Database Tables

| Table | Rows | Description |
|-------|------|-------------|
| **fact_orders** | 49,366 | Sales transactions with revenue, profit, quantity, discount |
| **dim_products** | 3,784 | Unique products across 3 categories |
| **dim_customers** | 17,995 | Unique customers with segment classification |
| **dim_geography** | 5,047 | Locations across 165 countries and 5 markets |
| **dim_ship_mode** | 4 | Shipping method options |
| **dim_order_date** | - | Date dimension for order analysis |
| **dim_ship_date** | - | Date dimension for shipping analysis |

Prior to beginning the analysis, a variety of checks were conducted for quality control and familiarization with the datasets. The SQL queries utilized to inspect and perform quality checks can be found [here](#).

---

## Executive Summary

### Overview of Findings

GlobalMart generated **$12.15M in revenue** with **$1.41M in profit** (11.62% margin) across 49,366 orders from 2012-2015. However, **24.5% of orders are unprofitable**, representing a significant opportunity for margin recovery. Technology leads profitability at 14.04% margin, while Furniture underperforms dramatically at only 6.77% despite generating 32% of revenue.

Asia Pacific represents the largest market (32% of revenue) but delivers below-average margins. Europe demonstrates best-in-class profitability at 13.76% margin, providing a replicable model for other regions. Revenue shows strong year-over-year growth with pronounced Q4 seasonality.

Below are the overview pages from the Power BI (Executive) and Tableau (Product Performance) dashboards. More examples are included throughout the report. The entire interactive dashboards can be downloaded [here](#) and [here](#).

![Executive Dashboard](images/executive-dashboard.png)

*Executive Dashboard Overview - C-Suite KPIs and Performance Metrics*

![Product Dashboard](images/product-dashboard.png)

*Product Performance Dashboard - Category and Product Analysis*

---

## Insights Deep Dive

### Sales Trends

GlobalMart's sales show consistent year-over-year growth from 2012-2015, with **pronounced Q4 seasonality** driving peak revenue in November and December.

* **Q4 represents the strongest sales period** due to holiday consumer behavior, with November averaging 15-20% higher revenue than typical months. Q1 (January-March) consistently underperforms, creating cash flow challenges.
* Revenue growth accelerated in 2014-2015, with several quarters showing double-digit sequential growth. This momentum indicates successful market expansion and product strategy execution.
* **Monthly patterns reveal opportunity in Q1:** Targeted promotional campaigns could smooth revenue distribution and improve working capital efficiency.

![Sales Trends](images/sales-trends.png)

*Year-over-Year Sales Trends showing growth trajectory and Q4 peaks*

---

### Product Category Performance

GlobalMart's three product categories demonstrate vastly different profitability profiles:

| Category | Revenue | % of Total | Profit Margin | Orders | Assessment |
|----------|---------|------------|---------------|--------|------------|
| **Technology** | $4.56M | 37.5% | 14.04% | 33,946 | Strongest performer |
| **Office Supplies** | $3.65M | 30.0% | 13.86% | 104,183 | Solid margins, high frequency |
| **Furniture** | $3.94M | 32.4% | 6.77% | 33,534 | Critical underperformer |

**Key Insights:**

* **Technology delivers optimal performance:** With 14.04% margins and $4.56M revenue, this category should receive increased marketing investment and inventory prioritization.
* **Furniture presents urgent concern:** Despite generating 32% of total revenue, Furniture's 6.77% margin is **half the company average**. This suggests excessive discounting, high cost of goods, or competitive pricing pressure.
* **Office Supplies demonstrates consistency:** High order frequency (104,183 orders) with solid 13.86% margins indicates strong repeat purchase behavior and pricing discipline.

**Business Impact:** Bringing Furniture margins from 6.77% to company average (11.62%) would generate an additional **$190K in annual profit** without increasing sales volume.

---

### Top Product Performance

**Critical Finding:** Top 10 products account for only 4.95% of total revenue, indicating healthy diversification and reduced concentration risk.

**Technology Dominance:** 8 of top 10 revenue-generating products are Technology items (smartphones, copiers, office equipment), validating category strategy.

**Profitability Variance:**

* Canon imageCLASS Copier achieves **40.91% margin** on $61.6K revenue
* Samsung Smart Phone (rank #8, $48.7K revenue) operates at **-0.41% margin** (losing money)

**Opportunity:** The stark margin difference between similar technology products suggests pricing inconsistency. Applying Canon Copier's pricing discipline to other high-ticket items could significantly improve profitability.

![Top Products](images/top-products.png)

*Top 10 Products by Revenue with Margin Analysis*

---

### Market Regional Performance

GlobalMart operates across five global markets with significantly different performance profiles:

| Market | Revenue | % of Total | Profit Margin | Orders | Customers | Revenue/Customer |
|--------|---------|------------|---------------|--------|-----------|------------------|
| **Asia Pacific** | $3.89M | 32.03% | 9.99% | 13,750 | 5,083 | $765.74 |
| **Europe** | $3.17M | 26.08% | **13.76%** | 11,320 | 4,196 | $755.32 |
| **USCA** | $2.27M | 18.66% | 13.04% | 9,970 | 2,851 | $795.39 |
| **LATAM** | $2.07M | 17.07% | 9.98% | 9,916 | 3,790 | $547.40 |
| **Africa** | $0.75M | 6.16% | 11.24% | 4,410 | 2,075 | $360.56 |

**Key Findings:**

* **Asia Pacific leads volume but lags profitability:** As the largest market (32% of revenue), APAC's 9.99% margin falls 1.63 points below company average. This represents the highest-value improvement opportunity given revenue scale.
* **Europe provides blueprint for success:** 13.76% margin is 3.77 points above Asia Pacific despite similar product mix. Replicating European practices (pricing strategy, operational efficiency, product mix) could unlock significant margin gains.
* **USCA shows premium positioning:** Highest revenue per customer ($795.39) suggests more affluent customer base or higher AOV, despite moderate market size.

**Business Impact:** Closing the margin gap between Europe (13.76%) and Asia Pacific (9.99%) would generate **$147K additional annual profit** on existing $3.89M APAC revenue base.

![Regional Performance](images/regional-performance.png)

*Global Market Performance showing revenue and margin by region*

---

### Unprofitable Orders Analysis

**Critical Issue:** 24.5% of all orders (12,083 transactions) operate at a loss, significantly above industry benchmark of 10-15%.

**Potential Root Causes:**

* Excessive discounting (>30% off)
* High shipping costs relative to order value
* Negative-margin products in order mix
* Pricing errors or promotional mismanagement

**Immediate Action Required:** Implement discount approval workflow for orders with >20% price reduction. Analyze shipping cost allocation methodology to ensure proper coverage.

**Recovery Potential:** Reducing unprofitable order rate from 24.5% to 15% (industry benchmark) could recover **$150K+ in annual profit**.

---

## Recommendations

Based on the uncovered insights, the following recommendations have been provided:

### Immediate Actions (0-3 Months)

**Unprofitable Order Intervention**

Analyze the 12,083 loss-making orders to identify common patterns (heavy discounts, high shipping, specific products). Implement approval controls for discounts exceeding 20%. Target: Reduce unprofitable rate from 24.5% to 15%. **Impact: $150K annual profit recovery.**

**Furniture Category Pricing Audit**

Conduct comprehensive margin analysis for Furniture products currently at 6.77% (vs Technology's 14.04%). Evaluate if low margins stem from excessive discounting, high COGS, or competitive pricing pressure. Negotiate better supplier terms leveraging $3.94M annual volume. Target: Increase Furniture margin to 10%. **Impact: $127K annual profit improvement.**

**Samsung Phone Correction**

Address the #8 top-selling product operating at -0.41% margin. Either increase price, reduce costs, or discontinue if structural profitability cannot be achieved. Replace with alternative SKU if necessary.

### Growth Initiatives (3-6 Months)

**Asia Pacific Margin Enhancement**

Study European market practices driving 13.76% margin (3.77 points above APAC). Pilot European pricing strategies and product mix adjustments in select APAC markets. Target: Increase APAC margin from 9.99% to 11.5%. **Impact: $59K annual profit improvement.**

**Technology Category Expansion**

Increase Technology SKU count by 15-20% given strongest margins (14.04%). Leverage Canon Copier success (40.91% margin) as model for other office equipment. Reallocate marketing budget to emphasize Technology products. Target: Grow Technology from 37.5% to 45% of total revenue. **Impact: $80K+ annual profit improvement.**

**Q1 Revenue Smoothing**

Develop targeted promotional campaigns for January-March to counter seasonal decline. Offer early Q2 incentives for Q1 orders. Introduce annual corporate contracts with quarterly payment terms. Target: Increase Q1 revenue by 10-15%.

### Long-Term Strategic Initiatives (6-12 Months)

**Customer Segmentation Strategy**

Leverage customer data (Consumer, Corporate, Home Office) to develop segment-specific marketing and pricing strategies. Implement tiered pricing models and loyalty programs.

**Furniture Category Transformation**

After pricing review, evaluate strategic options: (A) Reduce SKU count by 30-40%, focus on high-margin specialty items, (B) Explore private label partnerships, or (C) Exit commodity furniture, concentrate on premium segment.

**Data-Driven Culture**

Deploy Executive and Product dashboards company-wide with role-based access. Train regional managers on interpretation and action planning. Establish monthly KPI review cadence.

**Total Year 1 Profit Opportunity: $416K** (29.5% improvement vs. current $1.41M profit)

---

## Assumptions and Caveats

Throughout the analysis, multiple assumptions were made to manage challenges with the data. These assumptions and caveats are noted below:

* **Historical Data Only:** Analysis covers 2012-2015 period. Current market conditions, competition, and customer behavior may have changed since this timeframe.
* **Margin Calculations:** Profit margins calculated from sales and profit figures in database. Does not account for full cost accounting (overhead allocation, marketing spend, customer acquisition costs).
* **Unprofitable Order Analysis:** Root cause analysis for 24.5% unprofitable orders requires additional data on discount policies, shipping contracts, and order-level cost allocation not available in current dataset.
* **Market Comparisons:** Regional performance differences may reflect local economic conditions, competitive landscapes, and operational maturity not captured in transaction data alone.
* **Seasonality Patterns:** Q4 seasonality based on 4-year historical pattern. Future patterns may shift based on market evolution, competitive actions, or consumer behavior changes.

---

## Technical Approach

### Data Preparation

Raw sales data containing 49,366 orders was cleaned using **Python (Pandas)** to address missing values, duplicates, and formatting inconsistencies. Data quality checks performed to validate completeness and accuracy. Clean dataset exported for database loading.

### Database Design

**Star schema architecture** implemented using **SQLite** with 6 dimension tables and 1 fact table. Foreign keys established to ensure referential integrity. Indexes created on frequently queried fields for performance optimization. Design enables efficient analytical queries and supports future scalability.

### SQL Analysis

Seven analytical queries developed to answer five core business questions. Advanced SQL techniques utilized: window functions (year-over-year growth), CTEs (monthly aggregations), subqueries (percentage calculations). All queries documented with business context and expected outputs.

### Dashboard Development

**Power BI** used for Executive Dashboard targeting C-suite audience. **Tableau** used for Product Performance Dashboard targeting product managers and marketing teams. Interactive filters and drill-down capabilities enable self-service analytics. Dashboards connected to SQLite database for data refresh capability.

---

## Project Files

### Code & Analysis

* [Python Data Cleaning Notebook](#) - Raw data cleaning and preparation
* [SQL Analysis Notebook](#) - Database creation and analytical queries  
* [Database File (.db)](#) - SQLite database with complete dataset

### Dashboards

* [Executive Dashboard (.pbix)](#) - Power BI file for C-suite
* [Product Performance Dashboard (.twbx)](#) - Tableau file for product managers
* [Dashboard Screenshots](#) - High-resolution images of all visualizations

### Documentation

* [Database ERD](#) - Entity relationship diagram
* [Data Dictionary](#) - Complete schema documentation
* [Query Documentation](#) - Business logic for all SQL queries

---

## Contact

**Questions about this project?**

* Email: [your.email@example.com](mailto:your.email@example.com)
* LinkedIn: [linkedin.com/in/yourprofile](https://linkedin.com/in/yourprofile)
* GitHub: [@yourusername](https://github.com/yourusername)
* Portfolio: [yourportfolio.com](https://yourportfolio.com)

---

## License

This project is available under the MIT License. GlobalMart is a fictional company created for portfolio demonstration purposes.

---

**This analysis demonstrates end-to-end business intelligence capabilities:**

Data Engineering (Python, SQL) • Database Design (Star Schema) • Analytical Thinking (SQL Queries) • Executive Communication (Interactive Dashboards)
