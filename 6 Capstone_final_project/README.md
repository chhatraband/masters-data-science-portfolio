# 🏗 Enterprise Data Engineering Capstone  
## Slowly Changing Dimension Type 2 (SCD2) with Databricks & Delta Lake

**Author:** Nikhil Chhatraband  
**Program:** Master’s in Data Science  
**Focus Area:** Data Engineering  

---

## 🚀 Project Overview

This capstone project implements a **Slowly Changing Dimension Type 2 (SCD2)** pipeline using:

- Apache Spark (PySpark)
- Databricks
- Delta Lake
- Medallion Architecture (Bronze → Silver → Gold)
- Streaming + Batch processing
- SHA-256 hash change detection

The objective is to design and implement a production-style data pipeline that tracks historical changes in dimension records while ensuring scalability, reliability, and data quality.

---

## 🎯 Business Problem

Organizations must preserve historical changes in dimensional data such as:

- Customer information
- Product attributes
- Employee records
- Address updates

A simple overwrite approach destroys history.

SCD Type 2 solves this by:
- Expiring old records
- Creating new versioned rows
- Maintaining full auditability

---

## 🏛 Architecture Design

### 🔶 Medallion Architecture

The project follows the Databricks medallion pattern:

Bronze Layer:
- Raw ingested data
- Stored in Delta format
- Minimal transformation

Silver Layer:
- Cleaned & standardized data
- Deduplicated
- Data quality checks applied

Gold Layer:
- Business-ready dimension tables
- SCD Type 2 implemented
- Historical tracking enabled

---

## 🧠 SCD Type 2 Logic

Each record contains:

- surrogate_key
- business_key
- start_date
- end_date
- is_current
- hash_value

### Change Detection Strategy:
- SHA-256 hash created from non-key attributes
- Compare incoming hash vs existing hash
- If changed:
  - Expire old record (set end_date)
  - Insert new record
- If unchanged:
  - No action

---

## ⚙ Implementation Approaches

### 1️⃣ Custom PySpark SCD2 (Manual Implementation)

- Auto Loader ingestion
- Hash-based comparison
- MERGE INTO Delta Table
- Streaming checkpointing
- Identity columns for surrogate keys

Key functions:
- add_scd2_hash()
- build_latest_per_pk()
- run_scd2_merges()

---

### 2️⃣ Declarative SCD2 using Delta Live Tables (DLT)

- LakeFlow pipeline
- APPLY CHANGES INTO
- Automatically handles:
  - Versioning
  - Record expiration
  - Change tracking

Comparison:

| Feature | Custom PySpark | DLT |
|----------|----------------|------|
| Control | High | Moderate |
| Automation | Manual | Automatic |
| Maintenance | Medium | Low |
| Flexibility | High | Medium |

---

## 📊 Data Flow

Source → Bronze → Silver → Gold (SCD2 Dimension Table)

Bronze:
- Parquet ingestion
- Schema enforcement

Silver:
- Deduplication
- Data cleansing
- Validation rules

Gold:
- SCD2 logic
- Historical tracking
- Business-ready table

---

## 📈 Key Technical Features

- Delta Lake ACID transactions
- Streaming ingestion
- Hash-based change detection
- Identity column surrogate keys
- Merge operations
- Time-travel capability
- Partition optimization
- Checkpointing for fault tolerance

---

## 🛠 Tech Stack

- Databricks
- Apache Spark (PySpark)
- Delta Lake
- SQL
- Auto Loader
- Delta Live Tables (DLT)
- Parquet
- Medallion Architecture

---

## 📁 Project Structure

