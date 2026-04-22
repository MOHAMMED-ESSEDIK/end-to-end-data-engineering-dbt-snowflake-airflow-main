# 🚀 End-to-End Data Engineering Pipeline: dbt, Snowflake & Airflow

\<div align="center"\>

**Modern Data Stack Pipeline: Raw Data → Snowflake → dbt Transformation → Airflow Orchestration**

\</div\>

-----

## 📐 Architecture

```text
      Local / External Data
               │
               ▼
┌──────────────────────────────┐      ┌──────────────────────┐
│       Snowflake (RAW)        │      │    Apache Airflow    │
│  - CSV Seeds / Raw Tables    │◀─────│    (Orchestrator)    │
└──────────────┬───────────────┘      │   - DAG Scheduling   │
               │                      │   - Task Monitoring  │
               ▼                      └──────────┬───────────┘
┌──────────────────────────────┐                 │
│          dbt Core            │                 │
│  - Staging (Cleaning)        │◀────────────────┘
│  - Marts (Business Logic)    │       dbt run / dbt test
└──────────────┬───────────────┘
               │
               ▼
┌──────────────────────────────┐
│    Snowflake (ANALYTICS)     │
│  - Final Fact/Dim Tables     │
│  - Data Quality Reports      │
└──────────────────────────────┘
```

## 🛠️ Tech Stack

| Component | Technology | Purpose |
| :--- | :--- | :--- |
| **Data Warehouse** | Snowflake | Scalable storage for raw and transformed data |
| **Transformation** | dbt Core | Modular SQL modeling (Staging, Marts, Snapshots) |
| **Orchestration** | Apache Airflow | Automated scheduling and pipeline monitoring |
| **Language** | Python / SQL | DAG scripting and data transformation logic |
| **Data Quality** | dbt Tests | Ensures data integrity and schema validation |


## ⚡ Quick Start

### 1\. Clone & Environment Setup

```bash
git clone https://github.com/MOHAMMED-ESSEDIK/end-to-end-data-engineering-dbt-snowflake-airflow-main.git
cd snowflake_data_project

python -m venv venv
source venv/bin/activate  # venv\Scripts\activate on Windows
pip install -r requirements.txt
```

### 2\. Configure Snowflake Connection

Create/Update `~/.dbt/profiles.yml` with your credentials:

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

### 3\. Initialize Data & Run Transformations

```bash
dbt seed    # Load CSVs from /seeds to Snowflake
dbt run     # Build all models (Staging -> Marts)
dbt test    # Run data quality tests
```

### 4\. Launch Orchestration

```bash
export AIRFLOW_HOME=$(pwd)
airflow standalone
```

*Access the UI at `http://localhost:8080` to trigger the dbt DAG.*

## 🔄 Data Flow

1.  **Ingestion:** Raw data is landed in the `RAW` schema within **Snowflake**.
2.  **Staging:** **dbt** cleans, casts, and standardizes raw fields.
3.  **Marts:** Business logic is applied to create `fct_orders` (incremental) and `dim_customers`.
4.  **Snapshots:** `customer_snapshot` tracks Type-2 Slowly Changing Dimensions (SCD).
5.  **Validation:** **dbt tests** run automatically to check for nulls or relationship breaks.
6.  **Orchestration:** **Airflow** triggers the end-to-end run on a daily schedule.

## 🐛 Troubleshooting

| Problem | Cause | Fix |
| :--- | :--- | :--- |
| `Database Error` | Incorrect Snowflake Credentials | Check `profiles.yml` for correct account/role |
| `dbt command not found` | Venv not activated | Run `source venv/bin/activate` |
| `Airflow Port Conflict` | Port 8080 in use | Change port using `airflow webserver -p 8081` |
| `Incremental model fail` | Schema mismatch | Run `dbt run --full-refresh --select <model>` |

## 📚 Key Learnings

  * **Modular SQL:** Breaking complex queries into reusable dbt models.
  * **SCD Handling:** implementing snapshots to track historical record changes.
  * **Incremental Loads:** Optimizing performance by only processing new data.
  * **Automation:** Using Airflow to manage dependencies between ingestion and transformation.
  * **Data Governance:** Enforcing quality via automated testing and documentation.

-----

\<div align="center"\>
\<sub\>Built with ❤️ for the Modern Data Stack community\</sub\>
\</div\>
