# E-Commerce Business Intelligence & Data Analytics Case Study

## Project Overview
This project presents an end-to-end data analytics solution for an e-commerce platform operating across major Indian cities. The goal of this analysis is to evaluate transaction data from March 2023 to February 2024 to solve core operational and strategic challenges across four major business verticals: Customer Insights, Product Analysis, Sales Optimization, and Inventory Management.

The repository contains a fully structured SQL script optimized for **MySQL Workbench 8.0.40** (`E-Commerce.sql`), an executive PDF report (`E-Commerce_Report.pdf`), and complete documentation of findings and business recommendations.

---

## Data Sources
The analysis utilizes four relational tables sourced from the company's transactional database:

1. **`customers.csv`** (100 records)
   - `customer_id`: Unique identifier for each customer.
   - `name`: Full name of the customer.
   - `location`: Customer city (10 unique metropolitan hubs including Chennai, Delhi, Lucknow, Jaipur, Kolkata, Bangalore, Ahmedabad, Hyderabad, Pune, Mumbai).

2. **`products.csv`** (8 records)
   - `product_id`: Unique product catalog ID.
   - `name`: Product title (e.g., Laptop 15" Pro, Digital SLR Camera, Smartphone 6", Wireless Earbuds).
   - `category`: High-level category (Electronics, Photography, Wearable Tech).
   - `price`: Unit selling price (INR).

3. **`orders.csv`** (200 records)
   - `order_id`: Unique transaction identifier.
   - `order_date`: Date of purchase (spanning 2023-03-06 to 2024-02-24).
   - `customer_id`: Foreign key referencing `customers.csv`.
   - `total_amount`: Total invoice value for the order (INR).

4. **`orderdetails.csv`** (519 transaction line items)
   - `order_id`: Foreign key referencing `orders.csv`.
   - `product_id`: Foreign key referencing `products.csv`.
   - `quantity`: Number of units ordered.
   - `price_per_unit`: Unit price applied at checkout.

---

## Problem Statement

As a Data Analyst assigned to evaluate business performance, the task is to answer key strategic questions across four core verticals:

### 1. Customer Insights
- How is the customer base distributed geographically, and which locations contribute the most revenue?
- Who are the high-value (VIP) customers driving platform revenue?
- What is the breakdown of customer purchasing frequency (one-time vs. repeat vs. heavy buyers)?
- Which customers have zero order history (churned or un-activated accounts) requiring re-engagement?

### 2. Product Analysis
- Which products generate the highest total revenue versus volume sold?
- How do product categories perform in terms of overall revenue contribution and unit share?
- What product pairs are most frequently co-purchased in the same basket for cross-selling opportunities?

### 3. Sales Optimization
- What are the monthly and quarterly sales revenue trends, and how does Average Order Value (AOV) fluctuate over time?
- When do peak shopping periods occur, and how are order values distributed across spending tiers?
- What strategies can boost basket size and increase revenue conversion during off-peak periods?

### 4. Inventory Management
- What is the consumption rate (run-rate) and unit velocity per product?
- How can inventory be classified into Fast-Moving, Moderate-Moving, and Slow-Moving categories?
- What are the recommended quarterly restocking quantities to avoid stockouts while minimizing holding costs?

---

## Summary of Key Findings & Solutions Delivered

### Overall Platform Performance
- **Total Revenue**: ₹19,783,000 (₹1.978 Crore) across 200 orders.
- **Total Units Sold**: 1,033 units across 8 catalog products.
- **Average Order Value (AOV)**: ₹98,915 per order.
- **Active Customer Rate**: 84% active buyers (84 out of 100 registered customers placed at least 1 order; 16 customers are currently inactive).

---

### Vertical 1: Customer Insights & Geographic Breakdown
- **Top Revenue Hub**: **Chennai** leads all locations with **₹3,890,000** in revenue across 34 orders (15 active buyers), representing ~19.7% of total company revenue.
- **Top 5 Revenue Cities**:
  1. Chennai: ₹3,890,000 (34 orders)
  2. Lucknow: ₹2,206,000 (24 orders)
  3. Jaipur: ₹2,102,000 (22 orders)
  4. Delhi: ₹2,066,000 (28 orders)
  5. Kolkata: ₹1,928,000 (22 orders)
- **VIP Customer Segment**: 
  - **Romil Bora** (Customer ID 32, Chennai) is the highest spender at **₹889,000** across 6 orders.
  - **Rhea Issac** (Customer ID 17, Jaipur) is second with **₹864,000** across 4 orders.
  - Top 10 customers alone account for **₹6,151,000** (~31.1% of total revenue).
- **Inactive Accounts**: 16 customers (e.g., Ivana Chander, Advika Wable, Aarna Samra) have 0 orders. Targeted onboarding discounts (e.g., ₹500 off first order) are recommended.

---

### Vertical 2: Product Performance & Category Share
- **Top Revenue Driver**: **Laptop 15" Pro** (Product ID 2) generated **₹7,560,000** (38.2% of platform revenue) across 126 units sold.
- **Top Volume Driver**: **Digital SLR Camera** (Product ID 7) sold **151 units** generating **₹6,040,000** (30.5% of revenue). High-margin photography equipment is a core growth pillar.
- **Category Share**:
  - **Electronics** (5 products): **₹12,758,000** (64.5% share, 633 units)
  - **Photography** (1 product): **₹6,040,000** (30.5% share, 151 units)
  - **Wearable Tech** (2 products): **₹985,000** (5.0% share, 249 units)
- **Cross-Selling Synergy**:
  - The most frequent co-purchase product pair is **Wireless Earbuds + E-Book Reader** (purchased together in 31 orders), followed by **E-Book Reader + Laptop 15" Pro** (29 orders) and **Bluetooth Headphones + Wireless Earbuds** (28 orders).
  - Recommended bundled checkout offers (e.g., "Buy Laptop 15" Pro, get Wireless Earbuds at 20% off").

---

### Vertical 3: Sales Trends & Optimization
- **Peak Sales Months**:
  - **September 2023**: Highest revenue month at **₹2,927,000** (24 orders, AOV ₹121,958) driven by pre-festive stocking.
  - **December 2023**: Second peak at **₹2,774,000** (21 orders, AOV ₹132,095) due to year-end holiday sales.
  - **July 2023**: Third peak at **₹2,568,000** (26 orders).
- **Low Sales Periods**: **February 2024** dropped sharply to **₹396,000** (9 orders). Post-holiday clearance sales and flash deals are needed in Q1.
- **Basket Value Tiers**:
  - Premium Tier (> ₹200,000): 28 orders generating ₹6,807,000 (34.4% of total revenue).
  - High Tier (₹100,000 - ₹200,000): 47 orders generating ₹6,895,000 (34.8% of revenue).
  - Mid Tier (₹25,000 - ₹100,000): 79 orders generating ₹4,942,000 (25.0% of revenue).
  - Low Tier (< ₹25,000): 46 orders generating ₹1,139,000 (5.8% of revenue).

---

### Vertical 4: Inventory Management & Demand Forecasting
- **Velocity Classification**:
  - **Fast-Moving / High Stockout Risk**: **Digital SLR Camera** (151 units sold, avg 12.6 units/month), **Bluetooth Headphones** (135 units, 11.3 units/month), **Portable Bluetooth Speaker** (134 units, 11.2 units/month), **E-Book Reader** (130 units, 10.8 units/month), **Wireless Earbuds** (130 units, 10.8 units/month), **Laptop 15" Pro** (126 units, 10.5 units/month).
  - **Moderate-Moving**: **Smartwatch Fitness Tracker** (119 units, 9.9 units/month), **Smartphone 6"** (108 units, 9.0 units/month).
- **Recommended 90-Day Restock Quantities (with 20% safety buffer)**:
  - Digital SLR Camera: **45 units**
  - Bluetooth Headphones: **41 units**
  - Portable Bluetooth Speaker: **40 units**
  - E-Book Reader: **39 units**
  - Wireless Earbuds: **39 units**
  - Laptop 15" Pro: **38 units**
  - Smartwatch Fitness Tracker: **36 units**
  - Smartphone 6": **32 units**

---

## Actionable Business Value & Strategic Roadmap

1. **Targeted Regional Marketing**: Allocate 40% of digital ad budget to Chennai, Lucknow, and Jaipur. Launch region-specific campaigns and local fulfillment nodes in South and North hubs.
2. **Re-engagement Campaign**: Run SMS/Email reactivation workflows offering ₹500 discount vouchers for the 16 inactive customers to improve customer conversion from 84% to 95%+.
3. **Cross-Selling Bundles**: Implement automated "Frequently Bought Together" checkout prompts for accessories (Earbuds, Headphones) alongside high-ticket electronics (Laptops, DSLR Cameras).
4. **Demand-Driven Procurement**: Standardize quarterly purchase orders based on projected run-rates to prevent stockouts of high-demand items (DSLR Camera & Laptops) during peak months (September & December).

---

**Built By Jayesh**
**Data Analyst**
[LinkedIn](https://www.linkedin.com/in/jayesh-suthar-dev/) · [Portfolio](https://jayesh-analytics.github.io/)
