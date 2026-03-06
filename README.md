# Data Quality & Drift Monitoring System

Offline, packageable data quality and drift monitoring system designed as a middleware component for machine learning pipelines. The system validates incoming datasets, detects statistical drift, and maintains historical baselines to enable reproducible monitoring across data runs.

---

## Overview

Machine learning systems rely on stable and reliable data. However, in real-world deployments data distributions often change over time due to evolving environments, user behavior, or upstream pipeline modifications. These changes can silently degrade model performance.

This project provides an **offline-first monitoring framework** that validates incoming datasets, tracks statistical profiles of features, and detects distributional drift across time. It is designed to function as a **lightweight middleware layer** between data ingestion and model training or inference pipelines.

The system focuses on:

* Data integrity validation
* Feature statistical profiling
* Baseline versioning
* Drift and anomaly detection
* Reproducible monitoring across multiple data runs

---

## Project Pipeline

The following diagram illustrates the end-to-end data validation and drift detection pipeline implemented in this project.

![Project Pipeline](/assets/images/pipeline.jpg)

## Key Features

**Data Ingestion Layer**

* Supports CSV, Parquet, database dumps, and batch inputs
* Uniform interface for batch or pipeline ingestion
* Metadata attachment for experiment tracking

**Schema & Type Validation**

* Detects column mismatches and datatype drift
* Prevents silent schema-breaking changes
* Ensures compatibility with downstream ML components

**Data Quality Checks**

* Missing value detection
* Range validation
* Cardinality explosion detection
* Identification of constant or dead features

**Feature Profiling**

* Statistical summaries (mean, std, quantiles, histograms)
* Categorical frequency distributions
* Feature-level descriptive analytics

**Baseline Statistical Store**

* Stores reference feature statistics
* Versioned by timestamp and dataset metadata
* Supports local persistence via SQLite, DuckDB, or Parquet

**Drift Detection Engine**

* Compares current dataset with stored baselines
* Statistical tests and distribution distance metrics
* Detects feature-level distribution shifts

**Anomaly Detection**

* Identifies unusual data behavior
* Highlights unexpected distribution changes

**Decision Logic**

* Evaluates drift results against predefined thresholds
* Determines severity of detected drift

**Alert Generation**

* Generates monitoring alerts and insights
* Human-readable explanations for detected issues

**Report & Artifact Generation**

* Structured output formats (HTML / JSON / PDF)
* Reproducible analysis artifacts
* Auditable results for offline environments

---

## Project Pipeline

The following diagram illustrates the end-to-end monitoring pipeline implemented in this project.

![Pipeline](docs/pipeline.png)

### System Flow

Raw Data Source
→ Data Ingestion
→ Schema Validation
→ Reference Statistical Store
→ Feature Profiling
→ Drift Detection Engine
→ Anomaly Detection
→ Decision Logic
→ Alert Generator
→ Storage & Reports

---

## Example Use Cases

* Monitoring production ML data pipelines
* Detecting distribution drift before model retraining
* Data validation in batch ETL workflows
* Offline analysis of dataset evolution
* Data quality auditing for research experiments

---

## Project Structure (planned)

```
Data-Quality-Drift-Monitoring-System
│
├── data
│   └── sample datasets
│
├── src
│   ├── ingestion
│   ├── validation
│   ├── profiling
│   ├── drift_detection
│   ├── anomaly_detection
│   └── reporting
│
├── baselines
│   └── stored statistical references
│
├── reports
│   └── generated monitoring reports
│
├── docs
│   └── pipeline diagrams
│
└── README.md
```

---

## Technology Stack

* **Python**
* **Pandas / NumPy**
* **SciPy statistical tests**
* **DuckDB / SQLite / Parquet storage**
* **Matplotlib / Plotly (optional visualization)**

---

## Roadmap

Planned improvements:

* Automated feature drift dashboards
* Streaming data monitoring
* Advanced drift metrics (PSI, KL divergence, Wasserstein distance)
* Visualization interface for dataset comparison
* Integration with experiment tracking tools

---

## License

This project is released under the **MIT License**.

