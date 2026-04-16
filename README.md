# End-to-End Data Engineering Pipeline (Kafka + Snowflake + dbt + Airflow)

## Overview

This project implements an end-to-end data engineering pipeline that simulates real-time data ingestion, processing, and transformation using modern data stack tools. The system demonstrates a complete workflow from data generation to analytics-ready tables in a cloud data warehouse.

The pipeline includes streaming data ingestion using Kafka, change data capture using Debezium, storage in PostgreSQL, loading into Snowflake, transformation using dbt, and orchestration using Apache Airflow.

---

## Architecture

[Add architecture diagram here]

Data Generator → Kafka → Debezium → PostgreSQL → Snowflake → dbt → Analytics Layer  
                                             ↓  
                                     Apache Airflow Orchestration  

---

## Tech Stack

- Apache Kafka for real-time data streaming  
- Debezium for change data capture (CDC)  
- PostgreSQL as operational database  
- Snowflake as cloud data warehouse  
- dbt for data transformation and modeling  
- Apache Airflow for workflow orchestration  
- Docker for containerized deployment  
- Python for data generation and consumer logic  

---

## Project Structure

snowflake-dbt-airflow-pipeline/

- banking_dbt/ – dbt project containing models, snapshots, and tests  
  - models/staging – raw data cleaning models  
  - models/marts – dimension and fact tables  
  - snapshots – historical tracking  

- consumer/ – Kafka consumer scripts  
- data-generator/ – synthetic data generator scripts  
- kafka-debezium/ – CDC pipeline setup  
- postgres/ – PostgreSQL configuration  
- docker/ – Airflow and supporting services  
- docker-compose.yml – full environment orchestration  
- README.md – project documentation  

---

## Data Flow

1. Synthetic transactional data is generated using Python scripts  
2. Data is streamed into Kafka topics  
3. Debezium captures database changes in real time  
4. Data is loaded into PostgreSQL and then Snowflake  
5. dbt transforms raw data into structured analytical models  
6. Airflow orchestrates and schedules pipeline execution  

---

## dbt Layering

Staging Models:
- stg_accounts
- stg_customers
- stg_transactions

Mart Models:
- dim_accounts
- dim_customers
- fact_transactions

Data Quality:
- Not null constraints
- Unique key constraints
- Snapshot-based historical tracking

---

## CI/CD

GitHub Actions is used to validate and automate dbt workflows.

CI pipeline includes:
- Installing dependencies
- Running dbt compile
- Running dbt test

Workflow files:
- .github/workflows/ci.yml
- .github/workflows/cd.yml

---

## How to Run

1. Start infrastructure using Docker Compose  
   docker-compose up -d  

2. Run data generator scripts  
   python data-generator  

3. Run dbt transformations  
   cd banking_dbt  
   dbt run  
   dbt test  

4. Trigger Airflow DAGs from the UI  

---

## Key Features

- Real-time streaming data pipeline  
- CDC-based ingestion using Debezium  
- Cloud data warehouse integration with Snowflake  
- Modular dbt transformation layer  
- Automated data quality testing  
- Fully containerized architecture  
- CI/CD integration with GitHub Actions  

---

## Future Improvements

- Add data observability layer  
- Add dbt docs hosting  
- Improve CI with full dbt build pipeline  
- Add monitoring dashboards  
- Introduce incremental model optimization  

---

## Author

Varad Vaidya  
Data Engineering Project – End-to-end Modern Data Stack Implementation  
