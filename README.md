 # AtliQ Mart Supply Chain Analytics Project

## Table of Contents

- [Project Overview](#project-overview)
- [Data Sources](#data-sources)
- [Tools](#tools)
- [Analysis Workflow](#analysis-workflow)
- [Results and Findings](#results-and-findings)
- [Key Insights](#key-insights)
- [Recommendations](#recommendations)
- [Limitations](#limitations)
- [Visualizations](#visualizations)

## Project Overview

AtliQ Mart, a fast-growing FMCG manufacturer based in Gujarat, India, is experiencing service issues that have caused some key customers not to renew their contracts. These issues revolve around two major challenges: orders not being delivered on time and/or not delivered in full, leading to poor customer satisfaction.

The management of AtliQ Mart has requested the Supply Chain Analytics team to track delivery performance metrics such as **On-Time Delivery (OT%)**, **In-Full Delivery (IF%)**, and **On-Time In-Full Delivery (OTIF%)** for each customer daily. This project aims to identify service gaps, perform root cause analysis, and provide actionable insights to improve supply chain operations before expanding to other cities in India.

### Project Goals
1. Measure OT%, IF%, and OTIF% for each customer and product category in comparison with target service levels.
2. Analyze service level performance across Surat, Ahmedabad, and Vadodara to identify city-specific challenges or bottlenecks.
3. Pinpoint the causes of delivery delays or incomplete orders.
4. Analyze the relationship between service levels and contract renewals.
5. Identify customers consistently falling below target service levels, flagging high-risk customers (especially those with churn potential)
6. Break down OTIF% performance by product identifying high-demand products with frequent delivery issues.

---

![Atliq-mart-dashboard](https://github.com/user-attachments/assets/70704927-6fce-481b-badc-b5a23233c399)

---

## Data Sources

The project will involve the following datasets:

1. **Order Line and Aggregate Order Data**:
   - `fact_order_lines.csv` contains information on customer orders, delivery dates, promised delivery dates, and quantities ordered and delivered.
   - `fact_orders_aggregate.csv` contains information on aggregate customer orders, order placement date, OT, IF, and OTIF categorization.
2. **Customer Data**:
   - `dim_customers.csv` contains information on customer_id, customer_name, and city.
3. **Order Target Data**:
   - `dim_targets_orders.csv` contains information on customer_id, and set targets for OT, IF, and OTIF.
4. **Product Data**:
   - `dim_products.csv` contains information on  product_name, product_id, and category.
  
## Tools
- `Python` - Data Analysis
- `Power BI` - Visualization

## Analysis Workflow

### Step 1: **Data Collection & Cleaning**
   - Load datasets from raw sources.
   - Clean and preprocess the data (remove duplicates, handle missing values, standardize formats).
   - Integrate datasets into a consolidated format for analysis.

### Step 2: **Exploratory Data Analysis**
EDA involved exploring the data to answer questions such as: 
  - Which customers did not renew their contracts? What are their reasons for not renewing?
  - Are there specific patterns (e.g., delayed deliveries or incomplete orders) that are more frequent with these customers?
  - Which customers consistently fall below the target service level (OTIF%)?
  - Are there any specific product categories or SKUs that are frequently delivered late or in incomplete quantities?
  - What percentage of orders meet the OTIF% targets on a city-wise and customer-wise basis?
  - Are there specific routes, warehouses, or cities where performance is lower?
  - How do lead times and fulfilment rates differ across the three current operational cities (Surat, Ahmedabad, Vadodara)?

### Step 3: **Service Level Metrics Calculation**
   - Calculate daily OT%, IF%, and OTIF% metrics for each customer and product category.
   - Generate reports comparing current performance against target service levels.

### Step 4: **Trend Analysis**
   - Perform time-series analysis to identify trends in service performance (daily, weekly, monthly).
   - Analyze performance across different cities (Surat, Ahmedabad, Vadodara).

### Step 5: **Root Cause Analysis**
   - Investigate factors contributing to poor OTIF performance (e.g., delays in transit).
   - Identify high-risk customers and products with repeated service failures.

### Step 6: **Reporting & Visualization**
   - Build dashboards and reports for senior management to track performance.

## Results and Findings:
1. **Key Metrics Overview**:
   - **Total Order Lines**: 57K
   - **Total Orders**: 32K
   - **Total Order Quantity**: 13M
   - **LIFR%** (Line Item Fill Rate): 65.96%
   - **VOFR%** (Value Order Fill Rate): 96.59%
   - **On-Time Orders (OT)**: 19K (59.03%)
   - **In-Full Orders (IF)**: 17K (52.78%)
   - **On-Time In-Full Orders (OTIF)**: 9K (29.02%)

2. **Order Lines Insights**:
   - **Ahmedabad and Vadodara** have the same number of order lines (20K), while **Surat** has slightly fewer (18K). It looks like distribution or fulfilment issues may not be too city-dependent, given similar order volumes.
   

3. **Product Insights**:
   - LIFR and VOFR for different products show that there is a disparity between them.
   - For example, **AM Butter 250** has a **LIFR% of 68.66%** but a **VOFR% of 95.98%**. This indicates fulfilment in terms of product lines is low, but overall value fulfilment is much higher.
   - **AM Milk 100** shows both lower LIFR (65.55%) and VOFR (96.43%).

4. **Lead Time Insights**:
   - Most delayed products fall within a **1-day delay**, with a product count of **37K**. Some products have experienced **2-day** delays (around 8K), while **3-day delays** seem to affect around 5K orders.
   - **Ahmedabad** has 12K orders with a 1-day delay and a smaller amount with 2-day delays.
   - **Surat** shows 12K orders delayed by 1 day and some at 3 days.
   - **Vadodara** also has significant delays of around 12K for 1 day, and a few around 3 days.
   - Delays seem uniformly distributed across cities, but 1-day delays dominate the counts.
  
5. **Service Line Insights**:
    - **Overall OTIF% is Critically Low**:
      - At only **29.02%**, OTIF is critically low and far below target, indicating that nearly 70% of orders are not being delivered on time and in full. This is a severe issue and reflects inefficiencies across both supply chain and delivery processes.
    - **In-Full (IF%) Performance**:
      - With only **52.78%** of orders being fulfilled in full, stock availability or order picking accuracy could be major bottlenecks. It’s critical to address inventory management issues, particularly in underperforming cities like Vadodara.
    - **On-Time Delivery**:
      - While OT% is better than OTIF% and IF%, it is still underperforming at **59.03%**, which means over 40% of deliveries are late. This suggests systemic delivery or logistics issues affecting all cities, with none of the cities hitting a satisfactory OT%.

6. **Customer-Specific Issues**:
   - Some key customers with notable issues:
     - **Chiptec Stores**: OTIF% is **18.32%**, well below average. This customer struggles with on-time performance (**OT%: 38.19%**) and in-full fulfillment (**IF%: 52.09%**).
     - **Info Stores**: OTIF% is **16.40%**, with an especially low in-full fulfillment rate of **41.11%**.
     - **Soretco Mart**: OTIF% is **13.37%**, one of the worst-performing customers, with on-time performance at **24.19%**.
   - On the higher end:
     - **Vivek Stores** and **Soretco Mart** show OTIF% of around **33-34%**, but still, no customer is close to the target.
     - **Acclab Stores** has a slightly better-than-average performance at **OTIF: 33.27%** but still underperforming overall.
   - **LIFR%** (Line Item Fill Rate):
   There is a notable variation in LIFR% across different customers:
     - **Logic Stores**: High LIFR% of **75.42%**, meaning they are receiving most of the line items requested.
     - **Elite Mart**: Similarly, a LIFR of **75.49%**, but lower OTIF.
     - **Ral Fresh** has a decent LIFR% of **75.61%**, but this hasn’t translated into high OTIF due to low on-time performance.
     - **Vijay Stores** has the lowest LIFR% at **59.29%**.
     - LIFR% drops significantly for some customers like **Acclab Stores (51.53%)**, indicating lower fulfilment performance for these specific customers.

## Key Insights:

1. **Low LIFR% Across the Board**:
   - The average **LIFR%** across products and customers is around 65-66%. There’s a significant opportunity to improve fulfilment at the line-item level. The business can fulfil high-value orders (as seen with the VOFR), but there are gaps in meeting individual product line demands.

2. **Customer Fulfillment Variability**:
    - At only **29.02%**, OTIF is far below target, indicating that nearly 70% of orders are not being delivered on time and in full. This is a severe issue and reflects inefficiencies across both supply chain and delivery processes.
    - With only **52.78%** of orders being fulfilled in full, stock availability or order picking accuracy could be major bottlenecks. It’s critical to address inventory management issues, particularly in underperforming cities like Vadodara.
    - While OT% is better than OTIF and IF%, it is still underperforming at **59.03%**, which means over 40% of deliveries are late. This suggests systemic delivery or logistics issues affecting all cities, with none of the cities hitting a satisfactory OT%.

3. **Delayed Products**:
   - The majority of products have **1-day delays** across all cities. Since delays are prevalent but relatively short (mostly 1-2 days), addressing logistics or stock availability could potentially eliminate a large portion of these delays.

4. **City Distribution**:
   - Fulfillment issues and delays seem to be consistent across **Ahmedabad**, **Surat**, and **Vadodara**, with no city significantly outperforming or underperforming in terms of order lines or delays. This suggests systemic issues rather than location-specific problems.

5. **Product Line Performance**:
   - Some specific products like **AM Butter 250** and **AM Milk 100** have a significant gap between LIFR and VOFR, indicating that these might be products with inconsistent availability at the line-item level, even though their overall value is well fulfilled. This points to inventory management or stock allocation challenges.

6. **Customer-Specific Issues**:
   - Several customers, such as **Chiptec Stores**, **Info Stores**, and **Soretco Mart**, have critically low OTIF%, indicating persistent service issues. These customers should be prioritized for improving service levels.

## Recommendations:
1. **Deep-Dive Analysis**:
   - Conduct a more granular analysis of the specific reasons behind the low LIFR% for key customers and products. This will help identify whether the issue is demand forecasting, stock shortages, or logistics inefficiencies.
   
2. **Operational Efficiency**:
   - Focus on reducing the **1-day delays**, which represent the majority of delayed orders. Implementing process improvements in warehousing, picking, and transportation could yield substantial improvements.

4. **Customer-Specific Initiatives**:
   - Work with low-performing customers like **Vijay Stores** and **Acclab Stores** to understand their unique challenges and devise solutions to improve LIFR% levels.
   - Engage with customers like **Chiptec Stores** and **Info Stores** to understand their pain points and work towards improving order fulfilment for them.
   - Consider implementing dedicated service-level agreements (SLAs) for top customers to ensure higher OTIF% and greater customer satisfaction.

5. **Focus on OTIF% Improvements**:
   - Prioritize improving **OTIF%** as the primary metric. This will require better coordination between inventory availability (to improve IF%) and logistics (to improve OT%).
   - Implement real-time tracking and performance dashboards for operational teams to monitor OTIF and take corrective actions.

6. **City-Specific Action Plans**:
   - **Vadodara** shows underperformance in both OT% and IF%. Investigate regional logistics or warehouse bottlenecks that might contribute to delays and stock shortages in this area.
   - Since no city is performing exceptionally well, roll out initiatives aimed at improving both in-full fulfilment and on-time delivery across all locations.
     
7. **Balance Inventory and Demand**:
   - Products like **AM Butter 250** and **AM Milk 100** may require better inventory control, as their LIFR is lagging despite high VOFR. Matching stock availability to demand more closely will help here.

8. **Logistics and Delivery Optimization**:
   - The low OT% indicates that logistics and delivery are causing significant delays. Consider route optimization software, improved coordination with 3PL providers, or enhancing internal delivery processes to reduce late deliveries.
   - Analyze current shipping times, warehouse processing, and last-mile delivery to uncover inefficiencies.

## Limitations
- Quality data on lead times or logistics operations is unavailable. The absence of quality data on supplier performance, replenishment times, or the efficiency of inbound logistics makes it difficult to pinpoint delays and assess if poor supplier performance contributes to the low IF% and OTIF%.

## Visualizations
Explore the live Power BI dashboard for interactive visualizations:
  - [View Power BI Dashboard](https://app.powerbi.com/view?r=eyJrIjoiMjFmNmE1YmEtYTc0Ny00ODk5LWJhOWQtN2ZhYzMwMDMzMTQyIiwidCI6ImFhMjRiYzRmLWJjMTQtNDcyNS04ZDM4LTVmNjQ0NmE5OGUyYyJ9)

