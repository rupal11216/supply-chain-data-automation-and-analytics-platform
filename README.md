# supply-chain-data-automation-and-analytics-platform

An event-driven data ingestion and analytics pipeline that automates the processing of supply chain data received through email. The workflow uses n8n to extract CSV attachments from Gmail, transforms the data into structured records, and loads it into a PostgreSQL database hosted on Supabase. The stored data is then analyzed using SQL to generate operational and business insights.

---

## Problem

Supply chain data is frequently shared as CSV files through email, requiring manual downloads, imports, and reporting. This repetitive process is time-consuming and increases the risk of errors.

This project automates the complete ingestion workflow, making newly received data immediately available for analysis.

---

## Solution

The workflow monitors a Gmail inbox for incoming CSV files. When a new file is received, n8n automatically downloads the attachment, converts the CSV into JSON, and inserts the records into a PostgreSQL database hosted on Supabase. The data is organized using a star schema to support efficient SQL queries and reporting.

---

## Architecture

```
Supplier / Customer
        │
        ▼
 Gmail (CSV Attachment)
        │
        ▼
    n8n Workflow
        │
        ▼
 CSV → JSON Transformation
        │
        ▼
Supabase PostgreSQL
        │
        ▼
 SQL Analytics
        │
        ▼
 Business Insights
```

---

## Workflow

1. Detect new emails containing CSV attachments.
2. Download the attachment automatically.
3. Parse CSV records into JSON.
4. Insert the transformed data into PostgreSQL.
5. Analyze the stored data using SQL.

---

## Technology Stack

| Category | Technology |
|----------|------------|
| Workflow Automation | n8n |
| Database | PostgreSQL |
| Cloud Platform | Supabase |
| Query Language | SQL |
| Data Format | CSV, JSON |

---

## Database Design

The database follows a star schema consisting of dimension and fact tables.

**Dimension Tables**

- Customers
- Products
- Targets

**Fact Tables**

- Order Line
- Aggregated Metrics

This structure minimizes redundancy while supporting efficient analytical queries.

---

## Business Metrics

The project enables analysis of key supply chain performance metrics, including:

- Line Fill Rate
- Volume Fill Rate (VOFR)
- On-Time Delivery
- In-Full Delivery
- OTIF (On Time In Full)
---

## Repository Structure

```
automated-supply-chain-analytics-pipeline/

├── workflow/
│   └── n8n_workflow.json
│
├── screenshots/
│
├── README.md
│
└── LICENSE
```

---

## Key Learnings

- Workflow automation using n8n
- Event-driven ETL pipeline design
- PostgreSQL database management
- Relational data modelling using a star schema
- SQL-based analytical reporting
- Supply chain performance analysis

---

## Future Improvements

- Support additional input formats such as Excel
- Implement automated data quality validation
- Add scheduled report generation
- Integrate interactive BI dashboards
- Extend the workflow with notification and monitoring capabilities

---

## Acknowledgement

This project was developed as part of hands-on learning in supply chain analytics and workflow automation. The implementation, documentation, and repository organization are my own.
