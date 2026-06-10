# Bronze Layer

The Bronze layer serves as the raw *ingestion* zone of the Flight Analytics Data Lakehouse.

Its primary responsibility is to store source data exactly as received, without applying business logic, transformations, or enrichment. This ensures that the original dataset remains available for auditing, reprocessing, and recovery purposes throughout the lifecycle of the project.

In a Medallion Architecture, the Bronze layer acts as the system of record and provides a reliable foundation for all downstream processing.


## Aim

The Bronze layer was designed to:

1. Preserve source data integrity.
2. Maintain a reproducible ingestion process.
3. Separate raw data from transformed datasets.
4. Support downstream Silver-layer transformations.
5. Enable future reprocessing without re-downloading source files.


## Azure Implementation

The Bronze layer is implemented using Azure Data Lake Storage Gen2 (ADLS Gen2).

### Storage Structure

```text
Bronze Container
│
├── Combined_Flights_2018.parquet
├── Combined_Flights_2019.parquet
├── Combined_Flights_2020.parquet
├── Combined_Flights_2021.parquet
├── Combined_Flights_2022.parquet
└── Airlines.csv
```

All files are stored in their original format and schema.

No transformations, filtering, joins, or data quality operations are performed within this layer.


## Ingestion Process

The ingestion workflow follows a simple raw-load pattern:

```text
Kaggle Dataset
        │
        ▼
Local Extract
        │
        ▼
Azure Data Lake Storage Gen2
        │
        ▼
Bronze Container
```

## Design Decisions

### Why Store Raw Data?

Keeping raw data unchanged provides several benefits:

* Full traceability to the original source
* Ability to replay transformations
* Easier debugging of downstream issues
* Protection against accidental data loss
* Consistent input for future pipeline executions

### Why ADLS Gen2?

Azure Data Lake Storage Gen2 was selected because it provides:

* Scalable cloud storage
* Native integration with Synapse Analytics
* Native integration with Databricks
* Hierarchical namespace support
* Cost-effective storage for large datasets


All Silver-layer transformations read directly from the Bronze container, where schemas are standardized, data quality issues are addressed, and tables are merged / joined.

The Bronze layer itself remains immutable and serves as the authoritative copy of the source data.

