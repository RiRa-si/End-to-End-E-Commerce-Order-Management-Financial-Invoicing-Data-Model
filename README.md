# End-to-End E-Commerce Order Management & Financial Invoicing Data Model

## Project Overview
This repository contains a production-ready, end-to-end Power BI data modeling project built completely from scratch to integrate complex e-commerce transactional flows with downstream financial invoicing and marketing data. 

The architecture transforms raw operational silos—spanning historical order books, line-item shipments, invoicing cycles, customer contact records, and multi-currency exchange rates—into a high-performance relational analytics asset. Additionally, the model features robust data security protocols to ensure strict data governance across organizational departments.

## Data Architecture & Relational Schema
The core model transitions transactional operational data into a unified, multi-fact schema optimized for high-performance filtering, granular line-item calculations, and time-intelligence reporting.

### 📦 Transactional & Fact Layers
*   **`ORDERS_2026` & `ORDERS_2025`**: Historical and active order tables capturing high-level transactional details, order channels, priorities, and total values.
*   **`order_line_items`**: Highly granular line-item metrics computing unit quantities, unit costs, gross totals, and applied discounts per product.
*   **`shipments`**: Tracks operational logistics, milestone delivery timelines, and logistics modes (`ShipMode`).
*   **`INVOICES` & `invoice_lines`**: Governs downstream financial mapping, capturing amounts billed against corresponding order records.
*   **`payments`**: Records customer payment execution timelines, transaction dates, and clear payment identifications.
*   **`CAMPAIGN_LOG`**: Captures top-of-funnel marketing investments, clicks, impressions, and operational ad spend metrics.
*   **`sales_targets`**: Manages performance thresholds across periods to gauge strategic revenue variations.

### 🔍 Master & Dimensional Lookups
*   **`CUST_MASTER` & `customer_contacts`**: Houses centralized CRM profiles, account managers, risk segments, and contact hierarchies.
*   **`products`**: Contains master inventory data, including brand tags, descriptions, primary suppliers, and category segmentations.
*   **`Address` & `cities` & `regions`**: Establishes a clean geospatial lookup path to analyze commercial trends geographically.
*   **`exchange_rates`**: Directs multi-currency conversion mechanisms by capturing dynamic exchange value rates against transaction dates.

---

## Technical Implementations & Security Framework

### 🔒 1. Row-Level Security (RLS) Implementation
To enforce corporate data governance, security policies were built natively into the data model:
*   **Dynamic Role-Based Access Control (RBAC)**: Configured DAX filters on dimensions (such as `CUST_MASTER` or `regions`) to automatically restrict data access based on the logged-in user's corporate credentials.
*   **Account Manager Isolation**: Secured data access pathing ensures that Account Managers can only view transactional records (`ORDERS`, `INVOICES`) tied to their specifically assigned accounts, preventing unauthorized cross-department visibility.

### 2. From-Scratch Data Transformation & Modeling
*   **Granular Multi-Fact Handling**: Handled complex data joins linking high-level orders to split line-item tables (`order_line_items`, `invoice_lines`) without generating duplicate metrics or invalid cross-joins.
*   **Directional Filter Optimization**: Structured explicit 1-to-Many (`1:*`) filtering logic from dimension tables down to active fact components to maintain rapid query response times.
*   **Centralized Calculations**: Isolated all operational variables and DAX KPIs into a clean, dedicated `measures` folder to optimize workspace cleanliness.

---

## How to Explore the Model
1. Clone this repository to your local machine.
2. Ensure you have the latest version of **Power BI Desktop** installed.
3. Open the `.pbix` file.
4. Navigate to the **Model View** tab to view the relational architecture.
5. To test data security setups, go to **Modeling -> View as Roles** to preview the dashboard under different operational restrictions.
