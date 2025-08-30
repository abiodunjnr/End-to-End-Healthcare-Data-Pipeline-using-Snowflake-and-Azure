
# ❄️ Snowflake Healthcare Admissions Pipeline — Azure + Blob Storage + Snowsight

An **end-to-end data engineering and analytics pipeline** built on **Snowflake** with Azure services to transform a 2024 healthcare admissions dataset into actionable insights.
This project covers **ingestion, transformation, governance, orchestration, storage design, and dashboarding** — all focused on leveraging Snowflake’s cloud data platform. Visualized both in Snowsight dashboards and Power BI.

> **Note:** This is an educational analytics project using synthetic healthcare data. No clinical claims are made.

---

## 📌 Project Summary

* **Goal:** Deliver insights into healthcare admissions (billing costs, hospital performance, medical condition impact, and gender distribution).
* **Flow:** GitHub (CSV) → Azure Blob Storage → Snowflake Staging → Snowflake Tables → Snowsight Dashboards.
* **Outputs:** Curated Snowflake tables with applied security policies and visualized insights inside **Snowsight**.
* **Automation:** Scalable COPY INTO pipelines with file formats, stages, and RBAC-enabled access control.

---

## 🧱 Architecture Overview

* **Source:** CSV files hosted on GitHub (raw link).
* **Landing Zone:** Azure Blob Storage container.
* **Orchestration:** Azure Data Factory (initial ingestion) and Snowflake COPY INTO for bulk load.
* **Data Platform:** Snowflake (staging, transformations, schema enforcement, masking policies).
* **Governance:** Role-based access control (USER\_ROLE vs. ACCOUNTADMIN), masking of sensitive data.
* **Serving:** Snowsight dashboards for direct analytics, replacing external BI.
* **Power BI:** – Enterprise reporting connected live to Snowflake

*(Architecture and pipeline screenshots are included in this repo.)*

---

## 🔍 Business Context

Hospitals generate massive amounts of admissions and billing data. Without a structured pipeline, cost drivers and hospital performance remain hidden.
This project simulates a **hospital data workflow**:

* Standardize patient admissions data
* Apply governance (masking sensitive fields like patient names & insurance)
* Generate insights on **cost drivers, gender distribution, and hospital benchmarking**

---

## 🧠 Key Features & Highlights

### **Data Engineering**

* Ingested raw CSV data from **GitHub → Azure Blob Storage → Snowflake Staging**.
* Created **Snowflake Stages** and **File Formats** for structured ingestion.
* Built curated tables (`PATIENT_ADMISSIONS`) with typed columns (dates, numbers, strings).
* Applied **RBAC** to manage roles, warehouses, and schema access.
* Added **dynamic data masking** for sensitive columns (e.g., patient names, insurance provider).

### **Analytics & Insights**

* **Revenue by Medical Condition** – identified cost drivers (Cancer & Asthma generate highest average billing).
* **Gender Distribution** – showed females slightly more represented in admissions.
* **Hospital Performance** – benchmarked revenue across hospitals, uncovering high-revenue outliers.
* **Condition-Specific Hospital Loads** – highlighted where hospital focus & preventive care funding should go.

### **Ops & Governance**

* **Warehouse auto-suspend/resume** for cost efficiency.
* **Error handling** with `ON_ERROR = CONTINUE` in COPY INTO for resilient loads.
* **Versioned roles** (`USER_ROLE`, `ACCOUNTADMIN`) with clear separation of duties.

---

## 🔄 Pipeline Steps (End-to-End)

1. **Create Snowflake Roles & Warehouses** (`USER_ROLE`, `USER_WH`).
2. **Set up Database & Schemas** (`PATIENT_SURVIVAL_DB`, Silver & Gold layers).
3. **Provision File Format** for CSVs with delimiter, header skipping, and date parsing.
4. **Create Stage** pointing to Azure Blob (with SAS token).
5. **LIST & Preview** staged files in Snowflake.
6. **COPY INTO** curated Snowflake tables.
7. **Apply Masking Policies** for sensitive attributes.
8. **Run Analytics Queries** and visualize directly in Snowsight dashboards.

---

## 📊 Snowsight Dashboards (Sample Visuals)

📌 *Screenshots attached within repo directory 

---

## 🛠️ Technology Stack

* **Data Platform:** Snowflake (stages, file formats, COPY INTO, RBAC, masking, Snowsight)
* **Cloud Storage:** Azure Blob Storage (staging container)
* **Orchestration:** Azure Data Factory (GitHub → Blob pipeline)
* **Languages:** SQL (DDL, DML, masking policies)
* **Visualization:** Snowsight (native Snowflake dashboards)
* **Source Control:** GitHub (code + docs)

---

## ✅ Outcomes (Key Insights)

* **Cancer & Asthma** admissions drive the highest costs.
* **Females** slightly outnumber males in hospital admissions.
* **Revenue benchmarking** reveals large disparities across hospitals — some generating >2× more revenue than peers.
* Preventive programs (e.g., obesity & hypertension) could reduce long-term cost burdens.

---

## 📂 Repository Layout

* `sql/` — all Snowflake DDL & DML (roles, warehouses, stages, masking, copy commands)
* `docs/` — screenshots of Snowsight dashboards
* `README.md` — this overview

---

## 🧭 Next Steps / Enhancements

* Introduce **Bronze → Silver → Gold** medallion design natively in Snowflake.
* Add **Streams + Tasks** for automated incremental loads.
* Integrate **dbt Core** for modular transformations.
* Connect **Power BI or Tableau** for enterprise-scale dashboards.
* Add **Snowflake Native Apps / Marketplace** integration.

---

## 👤 About the Author

**Name:** Toluwani Adefisoye
**Email:** [toluenenate@gmail.com](mailto:toluenenate@gmail.com)
**GitHub:** [github.com/abiodunjnr](https://github.com/abiodunjnr)
**LinkedIn:** [https://www.linkedin.com/in/toluwani-adefisoye-766ab5221/](https://www.linkedin.com/in/toluwani-adefisoye-766ab5221/)
