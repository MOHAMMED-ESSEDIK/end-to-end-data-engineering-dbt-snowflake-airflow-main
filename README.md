# End-to-End Data Engineering Pipeline

> **Raw Data → Snowflake → dbt Transformation → Airflow Orchestration**
> 
> A production-grade Modern Data Stack pipeline with modular SQL modeling, incremental loads, SCD snapshots, and automated orchestration.

---

## Tech Stack

| Component | Technology | Purpose |
|---|---|---|
| Data Warehouse | Snowflake | Scalable storage for raw and transformed data |
| Transformation | dbt Core | Modular SQL modeling — Staging, Marts, Snapshots |
| Orchestration | Apache Airflow | Automated scheduling and pipeline monitoring |
| Language | Python / SQL | DAG scripting and transformation logic |
| Data Quality | dbt Tests | Schema validation and integrity checks |

---

## Architecture

```
  Local / External Data
           │
           ▼
┌──────────────────────────┐      ┌─────────────────────────┐
│     Snowflake (RAW)      │◀─────│     Apache Airflow      │
│  CSV Seeds / Raw Tables  │      │  DAG Scheduling         │
└────────────┬─────────────┘      │  Task Monitoring        │
             │                    └────────────┬────────────┘
             ▼                                 │
┌──────────────────────────┐                  │
│        dbt Core          │◀─────────────────┘
│  Staging  (Cleaning)     │     dbt run / dbt test
│  Marts    (Business)     │
│  Snapshots (SCD Type-2)  │
└────────────┬─────────────┘
             │
             ▼
┌──────────────────────────┐
│  Snowflake (ANALYTICS)   │
│  fct_orders (incremental)│
│  dim_customers           │
│  Data Quality Reports    │
└──────────────────────────┘
```

---

## Data Flow

| Step | Layer | Description |
|---|---|---|
| 01 | **Ingest** | Raw data lands in Snowflake `RAW` schema via CSV seeds |
| 02 | **Stage** | dbt cleans, casts, and standardizes raw fields |
| 03 | **Model** | Business logic builds `fct_orders` (incremental) and `dim_customers` |
| 04 | **Snapshot** | `customer_snapshot` tracks Type-2 Slowly Changing Dimensions |
| 05 | **Validate** | dbt tests assert nulls, uniqueness, and relationship integrity |
| 06 | **Orchestrate** | Airflow triggers the full end-to-end run on a daily schedule |

---

## Quick Start

### 1. Clone & Environment Setup

```bash
git clone https://github.com/MOHAMMED-ESSEDIK/end-to-end-data-engineering-dbt-snowflake-airflow-main.git
cd snowflake_data_project

python -m venv venv
source venv/bin/activate       # Windows: venv\Scripts\activate
pip install -r requirements.txt
```

### 2. Configure Snowflake Connection

Create or update `~/.dbt/profiles.yml`:

```yaml
snowflake_project:
  outputs:
    dev:
      type: snowflake
      account: your_account_id
      user: dbt_user
      password: your_password
      role: ACCOUNTADMIN
      database: finance_db
      warehouse: finance_wh
      schema: raw
  target: dev
```

### 3. Load Data & Run Transformations

```bash
dbt seed     # Load CSVs from /seeds into Snowflake
dbt run      # Build all models: Staging → Marts
dbt test     # Run data quality tests
```

### 4. Launch Airflow

```bash
export AIRFLOW_HOME=$(pwd)
airflow standalone
```

Access the UI at `http://localhost:8080` and trigger the dbt DAG to run the full pipeline.

---


---

## Key Concepts

**Modular SQL** — Complex queries are broken into small, reusable, and independently testable dbt models.

**Incremental Loads** — `fct_orders` only processes new or updated records on each run, minimizing warehouse compute costs.

**SCD Type-2 Snapshots** — `customer_snapshot` preserves full historical records of customer attribute changes using dbt's built-in snapshot strategy.

**Data Quality** — dbt generic tests (`not_null`, `unique`, `relationships`) run automatically after every model build, catching issues before they reach consumers.

**DAG Orchestration** — Airflow manages task dependencies, retries, and execution order, ensuring ingestion always precedes transformation.

---

## Troubleshooting

| Error | Cause | Fix |
|---|---|---|
| `Database Error` | Incorrect Snowflake credentials | Check `profiles.yml` for correct `account` and `role` |
| `dbt: command not found` | Virtual environment not activated | Run `source venv/bin/activate` |
| `Airflow port conflict` | Port 8080 already in use | Run `airflow webserver -p 8081` |
| `Incremental model failure` | Schema mismatch on existing model | Run `dbt run --full-refresh --select <model_name>` |

---

## Requirements

- Python 3.8+
- dbt-snowflake
- Apache Airflow 2.x
- Snowflake account with `ACCOUNTADMIN` or equivalent role

---

<div align="center">

Built with ❤️ for the Modern Data Stack community

</div>
