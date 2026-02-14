# GlobalMart
## Project Background

GlobalMart, established in 2010, is a global retail company selling Technology, Furniture, and Office Supplies products across 165 countries via its e-commerce platform.

The company has significant amounts of data on its sales, operational efficiency, product offerings, and regional performance that has been previously underutilized. This project thoroughly analyzes and synthesizes this data in order to uncover critical insights that will improve GlobalMart's commercial success.

Insights and recommendations are provided on the following key areas:

- **Sales Trends Analysis:** Evaluation of historical sales patterns from 2012-2015, focusing on revenue growth, order volume, and seasonal patterns.

- **Product Category Performance:** Analysis of Technology, Furniture, and Office Supplies categories, comparing revenue contribution and profitability.

- **Regional Market Performance:** Assessment of five global markets (Asia Pacific, Europe, USCA, LATAM, Africa) to guide expansion strategy.

An interactive Tableau dashboard can be downloaded [here](https://public.tableau.com/app/profile/nicolas.siebler/viz/SalesPerformanceDashboard_17689124400200/Dashboard1).

The Python code utilized to clean, organize, and prepare data for the dashboards can be found [here](https://github.com/Nicolas-Sieb/GlobalMart/blob/main/GlobalMart_Data_Cleaning.ipynb).

Targeted SQL queries regarding various business questions can be found [here](https://github.com/Nicolas-Sieb/GlobalMart/blob/main/GlobalMart_SQL.ipynb).

## Data Structure & Initial Checks

The data for this analysis comes from GlobalMart's transactional database, covering four years of e-commerce sales (2012-2015). The raw dataset contained 49,366 order records with 32 fields including customer information, product details, geographic data, and financial metrics.

### Data Preparation Process

## Data Structure & Initial Checks

The data for this analysis comes from GlobalMart's transactional database, covering four years of e-commerce sales (2012-2015). The raw dataset contained 49,366 order records across 165 countries.

### Why a Database?

As GlobalMart's operations scaled globally, the company's data infrastructure needed to evolve beyond spreadsheet-based analysis. With nearly 50,000 transactions generating over 1.6 million data points, a relational database became essential for:

* **Data Integrity:** Ensuring customer, product, and geographic data remains consistent across all transactions
* **Query Performance:** Enabling sub-second analysis of complex business questions across multiple dimensions
* **Scalability:** Supporting continued business growth without requiring infrastructure redesign
* **Concurrent Access:** Allowing multiple analysts and dashboards to access data simultaneously
* **Historical Tracking:** Maintaining complete audit trail as new data arrives

A **star schema** was implemented using **SQLite**, consisting of six dimension tables and one fact table:

![Database Layout](images/Database%20Layout-1.png)


*Database Entity Relationship Diagram*

### Database Tables

| Table | Rows | Description |
|-------|------|-------------|
| **fact_orders** | 49,366 | Sales transactions with revenue, profit, quantity, discount |
| **dim_products** | 3,784 | Unique products across 3 categories |
| **dim_customers** | 17,995 | Unique customers with segment classification |
| **dim_geography** | 5,047 | Locations across 165 countries and 5 markets |
| **dim_ship_mode** | 4 | Shipping method options |
| **dim_order_date** | 1,430 | Date dimension for order analysis |
| **dim_ship_date** | 1,464 | Date dimension for shipping analysis |

Prior to beginning the analysis, a variety of checks were conducted for quality control and familiarization with the datasets. The Python data cleaning notebook can be found [here](https://github.com/Nicolas-Sieb/GlobalMart/blob/main/GlobalMart_Data_Cleaning.ipynb). The SQL database creation and analytical queries can be found [here](https://github.com/Nicolas-Sieb/GlobalMart/blob/main/GlobalMart_SQL.ipynb).

---

## Executive Summary

### Overview of Findings

GlobalMart generated **$12.15M in revenue** with **$1.41M in profit** (11.62% margin) across 49,366 orders from 2012-2015. Revenue shows strong year-over-year growth with pronounced Q4 seasonality.

Technology leads profitability at **14.05% margin**, while Furniture underperforms at only **6.77%** despite generating 32% of revenue. This margin gap represents the highest-value improvement opportunity—bringing Furniture to company average would generate **$190K in additional annual profit**.

Asia Pacific represents the largest market (32% of revenue), while all five regions demonstrate growth trajectories with varying profit acceleration.

### Additional Technical Findings (SQL Deep-Dive)

SQL analysis uncovered critical transaction-level issues:
- **24.5% of orders operate at a loss**, significantly above the 10-15% industry benchmark
- Root cause: excessive discounting and pricing inconsistencies across product categories
- Regional margin analysis shows Europe at 13.76% vs. Asia Pacific at 9.99%, indicating replicable best practices

**Recovery Opportunity:** Addressing unprofitable orders and closing regional margin gaps could recover **$150K+ in annual profit** without increasing sales volume.

## Dashboard Deliverables

Two interactive Tableau dashboards were developed to serve different stakeholder needs: This dual-dashboard approach ensures each stakeholder receives relevant insights at the appropriate level of detail—strategic overview for executives, operational depth for product teams.

**Product Performance Dashboard** - Designed for Product Managers
- Granular product-level sales trends and category mix evolution
- Detailed product tables for inventory planning and SKU rationalization
- Operational insights to support day-to-day category management

![Product Analysis Dashboard](images/GlobalMart%20-%20Product%20Analysis%20Dashboard.png)


**Executive Dashboard** - Designed for C-suite leadership (CEO, CFO)
- High-level KPIs with YoY trends: sales, profit, margins, order volume
- Strategic view of profit performance across all five global regions
- Category-level profitability to guide portfolio decisions

![Executive Dashboard](images/GlobalMart%20-%20Executive%20Dashboard-1.png)
---

## Insights Deep Dive

### Sales Trends Analysis

GlobalMart's sales demonstrate consistent year-over-year growth from 2012-2015, with pronounced **Q4 seasonality** driving peak performance.

**Key Findings:**
- Q4 (Nov-Dec) consistently generates 15-20% higher revenue than average months due to holiday purchasing behavior
- Revenue growth accelerated in 2014-2015, with several quarters showing double-digit sequential growth
- Q1 (Jan-Mar) consistently underperforms, creating cash flow challenges and inventory management issues
- Total order volume grew from 8,307 orders in 2012 to 16,692 orders in 2015, demonstrating strong customer acquisition

**Business Impact:** Targeted Q1 promotional campaigns could smooth revenue distribution and improve working capital efficiency by reducing seasonal variance.

---

### Product Category Performance

GlobalMart's three product categories demonstrate vastly different profitability profiles, with Technology leading and Furniture significantly underperforming.

| Category | Revenue | % of Total | Profit Margin | Orders | Assessment |
|----------|---------|------------|---------------|--------|------------|
| **Technology** | $4.56M | 37.5% | **14.05%** | 33,946 | Strongest performer |
| **Office Supplies** | $3.65M | 30.0% | 13.80% | 104,183 | Solid margins, high frequency |
| **Furniture** | $3.94M | 32.4% | **6.77%** | 33,534 | Critical underperformer |

**Key Insights:**

**Technology Excellence:** 14.05% margin with $4.56M revenue validates category strategy. This category shows consistent margin discipline and strong customer willingness to pay premium prices for quality products.

**Furniture Crisis:** Despite generating 32% of total revenue, Furniture's 6.77% margin is **half the company average** (11.62%). This represents the single largest margin improvement opportunity in the portfolio and suggests excessive discounting, unfavorable supplier terms, or competitive pricing pressure.

**Office Supplies Consistency:** Highest order frequency (104,183 orders) with 13.80% margins indicates strong repeat purchase behavior and effective pricing discipline. This category demonstrates the value of high-volume, steady-margin business.

**Product-Level Variance (SQL Analysis):**  
Deep-dive analysis reveals significant margin inconsistency even within high-performing categories. Top revenue-generating products show margins ranging from 40.91% (Canon imageCLASS Copier) to -0.41% (Samsung Smart Phone), indicating pricing optimization opportunities within the Technology portfolio.

**Business Impact:** Bringing Furniture margins from 6.77% to company average (11.62%) would generate **$190K in additional annual profit** without increasing sales volume.

---

### Regional Market Performance

GlobalMart operates across five global markets with significantly different performance and growth characteristics.

| Market | Revenue | % of Total | Orders | Customers | Revenue/Customer |
|--------|---------|------------|--------|-----------|------------------|
| **Asia Pacific** | $3.89M | 32.03% | 13,750 | 5,083 | $765.74 |
| **Europe** | $3.17M | 26.08% | 11,320 | 4,196 | $755.32 |
| **USCA** | $2.27M | 18.66% | 9,970 | 2,851 | **$795.39** |
| **LATAM** | $2.07M | 17.07% | 9,916 | 3,790 | $547.40 |
| **Africa** | $0.75M | 6.16% | 4,410 | 2,075 | $360.56 |

**Key Findings:**

**Asia Pacific - Volume Leader:** Represents the largest market at 32% of revenue with broad customer base (5,083 customers), indicating successful market penetration. Profit trends show steady growth, though margin optimization opportunities exist.

**Europe - Strong Performer:** Demonstrates accelerating profit growth with consistent performance across all product categories. Revenue per customer ($755.32) similar to APAC suggests comparable customer profiles, yet profit performance indicates superior operational efficiency.

**USCA - Premium Market:** Highest revenue per customer ($795.39) suggests more affluent customer base or higher average order values. Despite moderate market size (18.66% of revenue), profit trends show strong acceleration in recent quarters.

**LATAM & Africa - Growth Markets:** Combined represent 23% of revenue with developing customer bases. Lower revenue per customer indicates price-sensitive markets requiring localized strategy.

**Business Impact:** All five markets demonstrate positive growth trajectories. Continued investment in high-performing regions (Europe, USCA) while implementing margin improvement initiatives in high-volume markets (APAC, LATAM) can drive sustainable profit growth.
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
## License

This project is available under the MIT License. GlobalMart is a fictional company created for portfolio demonstration purposes.

---
