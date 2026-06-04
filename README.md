# Automated Supply Chain Analytics Platform

## Overview

This project demonstrates the development of an automated Supply Chain Analytics Platform that streamlines data ingestion, storage, transformation, and business intelligence reporting. The solution leverages workflow automation, cloud databases, and analytics tools to monitor order fulfillment performance across India and the USA.

The platform automatically extracts supply chain datasets from Gmail using n8n workflows, stores them in Supabase PostgreSQL, enriches the data with exchange rates and date dimensions, and generates business-ready analytical tables for KPI reporting and operational insights.

---

## Business Problem

Supply chain organizations need continuous visibility into order fulfillment performance to maintain customer satisfaction and operational efficiency. Manual data collection and reporting processes are time-consuming, error-prone, and difficult to scale.

This project automates the entire analytics pipeline, enabling stakeholders to monitor service-level performance metrics and identify operational improvement opportunities.

---

## Solution Architecture

```text
Gmail Inbox
     │
     ▼
n8n Workflow
(Gmail Trigger + File Extraction)
     │
     ▼
Supabase PostgreSQL
(Data Storage Layer)
     │
     ▼
Data Transformation
(Date Table + Exchange Rates + Fact Summary)
     │
     ▼
Quadratic Analytics
     │
     ▼
KPIs, Trends & Business Insights
```

---

## Workflow

### 1. Automated Data Ingestion

* Connected Gmail using n8n Gmail Trigger.
* Filtered incoming emails containing supply chain datasets.
* Extracted CSV attachments automatically.
* Loaded data into Supabase PostgreSQL.

### 2. Data Storage

Created and maintained the following tables:

#### Fact Tables

* fact_order_line_india
* fact_order_line_usa
* fact_aggregate_india
* fact_aggregate_usa

#### Dimension Tables

* dim_customers
* dim_products
* target_orders

### 3. Data Enrichment

#### Date Dimension

Generated a complete calendar table from:

* March 1, 2025
* May 31, 2025

Containing:

* Date
* Day
* Month
* Quarter
* Year
* Weekday

#### Exchange Rate Table

Generated historical USD-INR exchange rates using Open Exchange Rates API.

Fields:

* Date
* USD_INR_Rate

This enabled standardized revenue calculations across multiple currencies.

### 4. Data Transformation

Performed:

* Data cleaning and validation
* ID standardization
* Date conversion
* Customer and product data integration
* Currency conversion
* Revenue calculation

Merged:

```text
fact_order_line
      +
dim_products
      +
dim_customers
      +
exchange_rates
```

into a consolidated Fact Summary table.

---

## KPIs Developed

The following business KPIs were calculated:

| KPI                | Description                                    |
| ------------------ | ---------------------------------------------- |
| Total Order Lines  | Total number of order line records             |
| Total Orders       | Unique orders processed                        |
| Line Fill Rate     | Percentage of order lines fulfilled completely |
| Volume Fill Rate   | Percentage of ordered volume delivered         |
| On-Time Delivery % | Orders delivered on or before committed date   |
| In-Full Delivery % | Orders delivered in full quantity              |
| OTIF %             | Orders delivered On-Time and In-Full           |

---

## Analytics Performed

### Customer Analysis

* Customer-level OTIF performance
* Service level tracking against targets

### Product Analysis

* Product category performance
* Revenue contribution analysis

### Regional Analysis

* India vs USA performance comparison

### Time-Series Analysis

* Monthly On-Time Delivery trends
* City-wise delivery performance monitoring

### Performance Tracking

* Comparison of actual performance against target metrics

---

## Database Schema

```text
                    dim_customers
                          │
                          │
                    customer_id
                          │
         ┌────────────────┴───────────────┐
         │                                │
         │                                │
target_orders                    fact_order_line
                                          │
                                          │
                                     product_id
                                          │
                                          │
                                    dim_products
```

---

## Technologies Used

* n8n
* Gmail API
* PostgreSQL
* Supabase
* SQL
* Quadratic Analytics
* Open Exchange Rates API
* CSV Data Processing

---

## Key Features

✔ Automated email-based data ingestion

✔ Cloud-based PostgreSQL data warehouse

✔ Automated ETL pipeline

✔ Historical exchange rate integration

✔ Data cleaning and transformation

✔ KPI generation and reporting

✔ Supply chain performance monitoring

✔ City-wise and monthly trend analysis

---

## Key Learnings

* Workflow Automation using n8n
* ETL Pipeline Design
* PostgreSQL Database Management
* Data Modeling and Warehousing
* Supply Chain Analytics
* KPI Development
* Business Intelligence Reporting
* Cloud Data Infrastructure

---

## Future Improvements

* Interactive Power BI Dashboard
* Automated KPI Alerts
* Predictive OTIF Forecasting
* AI-powered Supply Chain Assistant
* Real-time Data Streaming Pipeline

---
