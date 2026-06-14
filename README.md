# Electronic-Hub
# Electronic-Hub-End-to-End-Sales-and-Performance-Analytics

### Dashboard Link : https://powerbi.com

## 📑 Project Overview & Problem Statement
Electronic Hub is a multi-channel retail operation managing a diverse portfolio of high-value consumer electronics alongside low-margin daily consumer commodities. Without a centralized data monitoring system, management struggled to align inventory procurement with actual cash-flow returns, evaluate promotion efficiency, and isolate season-over-season revenue variances.

This comprehensive business intelligence dashboard solves these operational blind spots. By engineering a star-schema data model across transactional ledgers, parallel timelines, and master campaign dimensions, this multi-page report delivers:
1. **Product Performance Auditing**: Instant visibility into high-value revenue anchors vs. low-margin volume sinks.
2. **Promotional Effectiveness Tracking**: Deep analysis into how aggressive discount strategies (e.g., 20% to 50% write-downs) impact row-level margins.
3. **Time-Period Comparison Analytics**: Disconnected timeline analysis to track precise sales and profit velocity deltas over custom intervals.

---

## 🛠️ Step-by-Step Engineering Process

### Phase 1: Data Acquisition & Power Query Transformation
* **Step 1**: Loaded raw retail, customer, and transactional tables into Power BI Desktop from relational tracking ledgers.
* **Step 2**: Opened the **Power Query Editor** and enabled **Column Distribution**, **Column Quality**, and **Column Profile** under the View tab to identify data anomalies.
* **Step 3**: Modified default profiling parameters to **"Column profiling based on entire dataset"** to thoroughly evaluate every row in the multi-year schema.
* **Step 4**: Standardized key dimensional indices (`CustomerID`, `OrderID`, `ProductID`, `PromotionID`) as text data types to protect data integrity and prevent accidental mathematical aggregation.
* **Step 5**: Cleaned and validated currency formats for financial performance attributes including `Net Sales`, `Price Per Unit`, `Profit`, and `Discount`.

### Phase 2: Advanced DAX Data Modeling & Time Calculations
* **Step 6**: Built two completely independent, disconnected calendar dimension tables to handle advanced parallel time-period comparisons.
* **Step 7**: Developed isolated DAX measures utilizing `CALCULATE` and evaluation context overrides (`TREATAS` / `FILTER`) to dynamically map independent dates to side-by-side reporting blocks.
* **Step 8**: Engineered a custom customer lifestyle grouping by creating a new calculated column in the customer dimension model:
  ```dax
  Age Group = 
  IF(Electronic_Hub[Age] <= 25, "Young Adult",
  IF(Electronic_Hub[Age] <= 50, "Adult", "Elder"))
  ```

### Phase 3: Visual Interface & Layout Architecture
* **Step 9: Product Rankings (Page 1)**: Constructed paired horizontal bar charts to explicitly separate the Top 5 products from the Bottom 5 products across Sales, Quantities, and Profitability.
* **Step 10: Financial Trend Analytics (Page 2)**: Embedded an interactive Map visual tracking *Net Sales by City*, paired with a high-capacity time-series Line chart mapping *Sales Trends over Time (2020-2024)*.
* **Step 11: Dynamic Period Comparison (Page 3)**: Designed a split-column reporting layout featuring dedicated dual Date Range Slicers. This allows users to view independent timeline performance indicators side-by-side using high-contrast corporate palettes (Coral for Period 1, Purple for Period 2).
* **Step 12: Granular Transaction Audit Ledger (Page 4)**: Constructed a detailed, row-by-row matrix data grid mapping 12 fields simultaneously to allow financial teams to run itemized line-level discount audits.
* **Step 13: Master Slicer Navigation (Page 5)**: Implemented high-capacity, multi-select checkbox list slicers for `Customer Name` and `Promotion Name` to allow smooth, global cross-filtering across the report pages.
* **Step 14: Cloud Deployment**: Published the validated analytics report from Power BI Desktop to the designated Power BI Service secure corporate cloud environment.

---

## 📸 Dashboard Architectural Snapshots

### 1. Product Performance Rankings (Top 5 vs. Bottom 5)
![Product Performance Rankings](top_bottom_sales.png)

### 2. Retail Sales Trends & Promotional Insights
![Retail Sales Trends](sales_trends_promotions.png)

### 3. Parallel Time-Period Comparative Analytics
![Parallel Comparison](period_comparison.png)

### 4. Row-Level Transaction Auditing Ledger
![Transaction Audit Ledger](transaction_ledger.png)

### 5. Master Data Dimension Filters
![Master Filters](master_filters.png)

---

## 📈 Strategic Business Insights & Inferences

### [1] High-Value Product Anchors vs. Low-Margin Commodities
* **Top Revenue Drivers**: High-value personal electronics dominate the sales ecosystem. The **Apple iPhone 14** generates the highest store revenue at **$21.4M** (281 units sold), with the **Apple MacBook Air** following closely at **$19.6M**.
* **Profitability Champions**: These exact electronic sectors pull in nearly 100% of net margin streams, anchored by the Apple iPhone 14 yielding **$2.14M in net profit**.
* **Commodity Vulnerabilities**: Daily consumer staples present negligible financial returns despite high relative movement. **Colgate Toothpaste** sits at the absolute bottom, yielding a minor **$0.02M ($20K) in total sales** and only **$2K in profit**, highlighting a product line that requires pricing adjustments.

### [2] Promotion Campaign Financial Dissection
* **Baseline Returns**: Standard customer purchases made without active marketing codes (`PromotionID = 0`) generate a reliable, baseline **10% net profit margin** across the board.
* **Campaign PR001 Impact (20% Discount)**: This model scales top-line sales volume rapidly but requires massive profit trade-offs. For example, an order under this campaign triggered an immediate **$13,999.80 discount** write-down on a single high-value unit, squeezing net profits down to **$5,599.92**.
* **Campaign Allocation Velocities**: **Weekend Flash Sales** consume the highest promotional volume with a massive average allocation of **23K**, while specialized holiday events like **Festive Diwali** run highly efficiently at a **0K discount average**, proving strong organic demand.

### [3] Micro-Timeline Velocity Adjustments
* **Multi-Year Macro Peak**: Long-term revenue tracking highlights severe cyclical demand volatility, culminating in a historic single-day performance peak of **$0.65M in sales** in late 2022.
* **Granular Year-End Acceleration**: Parallel comparison modeling isolates micro-movements during the high-demand holiday season. Extending the date parameter by a two-week window reveals that while top-line revenue ($122M) and profit margins ($12.2M) held perfectly steady, inventory throughput accelerated by **100 units (7.0K to 7.1K items sold)**, exposing a clear year-end consumer fulfillment wave.
