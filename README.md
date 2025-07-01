# Covid-19 Data Ingestion and Transformation Pipeline
This is an end-to-end project designed to streamline the collection, transformation, analysis, and visualization of COVID-19 data for predictive analytics and real-time reporting.

# Solution Architecture
The pipeline performs the following stages:
## 1. Data Ingestion
- Source 1: ECDC (European Centre for Disease Prevention and Control)
-- Confirmed Cases
-- Mortality
-- Hospitalization / ICU
- Source 2: Eurostat
-- Population by age
Ingested using HTTP Linked Services and Copy Data Activities in Azure Data Factory.

2. Raw Storage (Landing Zone)
Data is initially stored in Azure Data Lake Storage Gen2 under the raw/ container for each dataset.

3. Data Transformation
Transformations include standardizing schema, handling missing values, joining population data with COVID datasets, Conditional Split to split daily and weekly data, Aggregating data by 'ecdc_year_week' producing columns 'week_start_date, week_end_date',
4. Curated Storage
Transformed data is stored back into Azure Data Lake Gen2 under the curated/ zone.

Cleaned datasets are used for:

Machine Learning training

Historical trend analysis

5. Data Loading
Final curated datasets are loaded into:

-- Azure SQL Database for consumption by Power BI dashboards

-- Azure Data Lake Gen2 (ML Zone) for Machine Learning models


