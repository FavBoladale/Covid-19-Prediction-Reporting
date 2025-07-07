# Covid-19 Data Ingestion and Transformation Pipeline
This end-to-end project leverages Azure Data Factory to efficiently orchestrate the collection, transformation, analysis, and visualization of COVID-19 data, enabling predictive analytics and real-time reporting through a fully integrated Azure-based solution.
![Covid19 data ingestion Diagram-Icons](https://github.com/user-attachments/assets/527a72bb-76df-421f-b4e6-3eff6c58458c)


# Solution Architecture
The pipeline ingests and processes datasets from ECDC and Eurostat using Azure Data Factory (ADF), stores them in both Azure Data Lake Storage Gen2 and Azure SQL Database, and exposes the results to Power BI for reporting and to Machine Learning (ML) workloads for forecasting and modeling.

## 1. Data Sources
Our solution integrates two key data sources:
- ECDC – European Centre for Disease Prevention and Control
  - Confirmed COVID-19 cases
  - Mortality statistics
  - Hospitalization / ICU cases

- Eurostat
  - Population by age group and country

## 2. Raw Storage (Landing Zone)
Raw datasets are ingested using Copy Data activities in ADF and stored in Azure Data Lake Storage Gen2 under the /raw/ container. This landing zone serves as the initial layer for all ingested files from ECDC and Eurostat.

## 3. Data Transformation
Data is transformed using Data Flows in Azure Data Factory. Key transformations include:
- Schema Standardization: Renaming columns, enforcing consistent data types
- Missing Value Handling: Cleaning and imputing incomplete records
- Conditional Split: Splits data into daily and weekly partitions
- Derived Columns: Adds calculated fields like week_start_date and week_end_date
- Join: Combines ECDC datasets with Eurostat population data by country and age group
- Aggregate: Summarizes data by ecdc_year_week and other dimensions

## 4. Processed Storage
The cleaned and enriched data is written back to Azure Data Lake Gen2 under the /processed/ zone. These processed datasets are structured for downstream consumption, including:
- Machine Learning training
- Historical trend analysis

## 5. Data Loading and Consumption
- Azure SQL Database – Used by Power BI dashboards for real-time and historical reporting
- Azure Data Lake Gen2 (ML Zone) – Used for training and deploying ML models to predict cases and healthcare resource needs


# Final Thoughts
This project demonstrates the power of Azure-native tools when orchestrated effectively. By building a fully automated, modular, and scalable pipeline, we were able to convert raw public health data into meaningful, decision-ready insights.

Whether you're working on a similar public dataset, modernizing legacy pipelines, or building cloud-based data platforms, this project highlights how Azure Data Factory, combined with Data Lake and SQL, can drive impact at scale.

Thanks for reading, and feel free to connect if you’d like to discuss or collaborate on similar data engineering initiatives!
