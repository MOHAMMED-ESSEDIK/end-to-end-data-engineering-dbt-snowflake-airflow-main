
# End-to-End Data Engineering Project: dbt, Snowflake & Apache Airflow  


## Overview  
This project is a **complete data engineering pipeline** using **dbt (Data Build Tool), Snowflake (Data Warehouse), and Apache Airflow (Orchestration Tool)**. It covers **data ingestion, transformation, and scheduling** in a structured and scalable manner.  

🛠️ Tech Stack

Component

Technology

Purpose

Data Warehouse

Snowflake

Store raw and transformed data

Transformation

dbt Core

Build staging, marts, tests, snapshots

Orchestration

Apache Airflow

Schedule and automate dbt workflows

Scripting

Python

DAGs and automation

Version Control

Git

Track changes and collaboration


## Project Structure  
```bash
 snowflake_data_project/
│──  models/                 # dbt models (staging, marts)                  # Airflow DAGs (for scheduling)
│──  logs/                   # Airflow logs
│──  seeds/                  # Sample seed data for dbt
│──  macros/                 # dbt macros
│──  dbt_project.yml         # dbt project config file
│──  README.md               # Project documentation
```


## Setup & Installation  

### Clone the Repository  
```sh
git clone https://github.com/MOHAMMED-ESSEDIK/end-to-end-data-engineering-dbt-snowflake-airflow-main.git
cd your-repo-name
```

Set Up a Virtual Environment
```sh
python -m venv venv
source venv/bin/activate  # Mac/Linux
venv\Scripts\activate     # Windows

```

Configure dbt Connection to Snowflake
Update the profiles.yml file located in ~/.dbt/ with your Snowflake credentials:
```sh
snowflake_project:
  outputs:
    dev:
      account: your_snowflake_account
      database: finance_db
      user: dbt_user
      password: your_password
      warehouse: finance_wh
      role: ACCOUNTADMIN
      schema: raw
      type: snowflake
  target: dev
```
Run dbt Models
```sh
dbt run
dbt test  # To validate data integrity
```

Start Apache Airflow
```sh
airflow standalone  # Starts the UI & Scheduler
```
Data Flow

Raw data is loaded into the raw schema in Snowflake

dbt staging models clean and standardize the data

dbt mart models build business-ready tables

fct_orders is built as an incremental model

customer_snapshot tracks historical changes in customers

dbt tests validate data quality

Airflow runs the pipeline every day automatically


📚 What I Learned
Building a modern end-to-end data pipeline
Modeling raw data into business-ready marts
Using dbt incremental models to optimize performance
Tracking historical changes using snapshots
Scheduling and monitoring workflows with Airflow
Applying data quality tests and validation
Designing a scalable architecture using Snowflake


