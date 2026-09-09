# Microsoft Fabric Retail Lakehouse

An end-to-end data engineering project built using Microsoft Fabric, PySpark, Delta Lake, and Power BI.

The pipeline ingests Olist e-commerce data, applies Bronze/Silver/Gold medallion architecture, performs data cleansing and validation, and produces analytics-ready dimensional models.

The source of Olist e-commerce data is coming from https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce

CSV
   ↓
Fabric Pipeline
   ↓
Bronze
   ↓
PySpark
   ↓
Silver
   ↓
Gold
   ↓
Semantic Model
   ↓
Power BI

## Design Decisions
### Why medallion architecture?
To separate raw ingestion, validated data,
and analytics-ready datasets.

### Why Delta tables?
To support reliable updates, schema enforcement,
and efficient analytical processing.

### Why dimensional modelling?
To provide a simplified structure optimized
for BI and analytical workloads.

## Medallion architecture
### Bronze Layer
- Loaded raw customer, product, order and order-item files
- Preserved original source structure
- Added ingestion metadata

### Silver Layer
- Removed duplicates
- Standardized data types
- Handled null values
- Validated order relationships
- Converted timestamps

### Gold Layer
Created:
- fact_sales
- dim_customer
- dim_product
- dim_date