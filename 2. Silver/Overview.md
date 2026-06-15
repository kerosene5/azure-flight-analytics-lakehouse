# Silver Layer

Yeah, the current version reads like a university report. For a GitHub project, especially one you're trying to position as a standout data engineering project, you want it to sound more like something an engineer actually wrote.

---

# Silver Layer

The Silver layer contains cleaned, standardized, and enriched flight data.

Raw datasets from the Bronze layer are processed using Azure Databricks and PySpark to improve data quality and create a consistent dataset for downstream analytics.

This layer serves as the bridge between raw ingestion and business-ready data.

## Implementation

Data is read from the Bronze container, transformed using PySpark, and written back to Azure Data Lake Storage Gen2 in Parquet format.

### Storage Structure

```text
Silver Container
│
└── silver_flights/
    ├── part-00000.parquet
    ├── part-00001.parquet
    ├── part-00002.parquet
    └── ...
```

## Transformations

### Data Consolidation

* Loaded all yearly flight datasets from the Bronze layer.
* Combined them into a single unified dataset.

### Data Cleaning

* Removed duplicate records.
* Standardized column names.
* Trimmed inconsistent string values.
* Handled missing and invalid data.

### Schema Standardization

* Enforced a consistent schema across all years.
* Converted columns to appropriate data types.
* Prepared fields for analytical workloads.

### Data Enrichment

* Joined flight records with airline reference data.
* Added airline names alongside airline codes.

## Workflow

```mermaid
flowchart TB

    B["Bronze Container<br/>Raw Flight Data"]

    D["Azure Databricks<br/>PySpark"]

    T["Clean, Standardize<br/>Enrich"]

    S["Silver Container<br/>Refined Flight Data"]

    B --> D
    D --> T
    T --> S

    style B fill:#CD7F32,stroke:#E6A15C,color:#FFFFFF,stroke-width:3px

    style D fill:#7C3AED,stroke:#A78BFA,color:#FFFFFF,stroke-width:3px

    style T fill:#7C3AED,stroke:#A78BFA,color:#FFFFFF,stroke-width:3px

    style S fill:#C0C0C0,stroke:#E5E7EB,color:#111111,stroke-width:3px

    linkStyle default stroke:#A78BFA,stroke-width:2px
```

## Purpose

The Silver layer provides a reliable dataset for the Gold layer.

By resolving data quality issues early in the pipeline, downstream transformations can focus on analytics, KPI generation, dimensional modeling, and reporting instead of data preparation.

---

This style is much closer to how high-starred data engineering repositories write documentation: short paragraphs, concrete actions, minimal buzzwords, and letting the architecture speak for itself.
