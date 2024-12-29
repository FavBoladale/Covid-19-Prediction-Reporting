# Covid-19-Prediction-Reporting
A comprehensive data engineering project designed to streamline the collection, transformation, analysis, and visualization of Covid-19 data for predictive analytics and real-time reporting. 

## Data Sources
### ECDC Website
-- Confirmed cases
-- Mortality
-- Hospitalization/ICU Cases
-- Testing Numbers
### Eurostat website
-- Country's population by age population
## Overview
This project demonstrates an Azure Data Factory (ADF) pipeline that ingests data from the following websites:
-- ECDC (European Centre for Disease Prevention and Control)
-- Eurostat

The data is ingested into an Azure Data Lake Storage Gen2, and further transformations are performed using Azure Data Factory.

## Prerequisites

Azure Resources:

Azure Data Factory

Azure Data Lake Storage Gen2

Azure Key Vault (optional, for storing credentials securely)

## Data Source Access:

URLs for the ECDC and Eurostat data sources.

## Development Environment:

Azure Portal

Azure Storage Explorer (optional)

## Project Structure

Data Flow

Source Data: ECDC and Eurostat provide datasets in CSV or JSON formats via HTTP/HTTPS endpoints.

Destination: Data is stored in raw form in Azure Data Lake Storage Gen2 under specific containers (e.g., /raw/ecdc and /raw/eurostat).

Transformation: Data Factory applies transformations to clean and standardize the data, storing processed data in /processed/.

Azure Data Factory Pipeline

Pipeline 1: Data Ingestion

Downloads data from ECDC and Eurostat using HTTP connectors.

Saves raw data to Azure Data Lake Gen2.

Pipeline 2: Data Transformation

Reads raw data from ADLS Gen2.

Applies mapping, filtering, and formatting transformations.

Saves transformed data to /processed/ in ADLS Gen2.

## Deployment Steps

1. Set Up Azure Data Lake Storage Gen2

Create an Azure Data Lake Gen2 account if not already available.

Create the following containers:

/raw/ecdc

/raw/eurostat

/processed

2. Configure Azure Data Factory

Create Linked Services

HTTP Linked Services:

For ECDC and Eurostat, create HTTP linked services.

Specify the base URL of the data source.

Azure Data Lake Storage Gen2 Linked Service:

Configure access to your Azure Data Lake Gen2.

Create Datasets

Source Datasets:

HTTP datasets for ECDC and Eurostat.

Sink Datasets:

Azure Data Lake Gen2 datasets for /raw/ and /processed/ containers.

Create Pipelines

Pipeline: Data Ingestion

Use an HTTP connector to download data from the ECDC and Eurostat endpoints.

Store data in the respective /raw/ container.

Add metadata (e.g., timestamp, source details) as needed.

Pipeline: Data Transformation

Use Data Flow or Mapping Data Flow to process the raw data.

Apply transformations (e.g., schema mapping, deduplication, and enrichment).

Store the output in the /processed/ container.

Monitoring and Logging

Pipeline Monitoring:

Use the Monitoring tab in Azure Data Factory to track pipeline runs and debug failures.

Error Handling:

Configure retry policies and failure alerts.

Logging:

Enable diagnostic logging to monitor activities.

Automation

CI/CD Integration

Use Azure DevOps or GitHub Actions to manage deployment.

Store ADF pipeline JSON templates in the repository.

Use az datafactory pipeline CLI commands or ARM templates for deployment automation.
