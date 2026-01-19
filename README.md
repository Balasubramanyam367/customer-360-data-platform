# Customer 360 Data Platform

## Overview
This project builds a batch-oriented data platform that consolidates customer
data from multiple source systems into a single, analytics-ready warehouse.

## Architecture
(We will add the diagram in the next step.)

## Tech Stack
- Apache Airflow
- Apache Spark (PySpark)
- dbt
- AWS S3
- Data Warehouse (Snowflake / BigQuery)
- Python
- SQL

## Data Flow
1. Source systems (CRM, Payments, Support) generate operational data.
2. Incremental ingestion extracts new and updated records.
3. Raw data is staged in object storage.
4. Spark jobs clean, deduplicate, and join datasets.
5. dbt models create analytics-ready tables.
6. BI tools consume curated data.

## Challenges & Debugging

### Slow Full Loads
- Issue: Full table loads exceeded SLA limits.
- Debugging: Analyzed job runtime and table sizes.
- Fix: Implemented incremental ingestion.

### Inconsistent Customer Identifiers
- Issue: Customer IDs differed across systems.
- Debugging: Identified join failures.
- Fix: Introduced surrogate keys.

### Data Quality Issues
- Issue: Null and duplicate values in key fields.
- Debugging: Audited downstream reports.
- Fix: Added dbt tests for nulls and uniqueness.

## Data Quality & Reliability
- dbt schema and freshness tests
- Airflow SLA monitoring
- Incremental load checkpoints

## Learnings
- Incremental processing improves scalability.
- Data modeling is critical for analytics usability.
