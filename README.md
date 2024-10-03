# Real-Time Stock Market Analytics Project on GCP

## Description
This project implements a real-time and batch data pipeline for stock market data using Google Cloud Platform (GCP) services. The pipeline fetches stock data from the Yahoo Finance API and processes it using Apache Kafka, PySpark, and BigQuery. The project aims to provide data for both high-frequency traders and value investors, with live updates and daily reports.

## Architecture Overview
The pipeline is built using the following components:
- **Airflow**: Orchestrates the daily and real-time data ingestion processes.
- **Kafka**: Used for real-time streaming of stock data every 5 minutes.
- **Zookeeper**: Manages the Kafka cluster.
- **PySpark on GCP Dataproc**: Consumes real-time data from Kafka, processes it, and writes it to BigQuery.
- **BigQuery**: Stores both real-time and daily data for analysis and visualization.
- **Elasticsearch & Kibana**: Monitors system performance and logs, visualized via Kibana.
- **Power BI**: Used to visualize the data, with DirectQuery for live updates.

## Setup Instructions
To set up the project:
1. **Airflow**: Configure Airflow to run a DAG that triggers Python scripts for fetching data from Yahoo Finance.
2. **Kafka Cluster**: Set up a Kafka cluster (3 VMs) and ensure Zookeeper is configured to manage the cluster.
3. **PySpark and Dataproc**: Configure a PySpark consumer to read from the Kafka topic, process the data, and write to BigQuery.
4. **BigQuery**: Create partitioned and clustered tables to store processed data.
5. **Elasticsearch & Kibana**: Set up Filebeat and Metricbeat to monitor Kafka logs and visualize them in Kibana.
6. **Power BI**: Connect Power BI to BigQuery using DirectQuery mode for real-time data updates.

## Usage
- **Real-Time Data**: Data is ingested into Kafka every 5 minutes for high-frequency traders. The PySpark consumer processes this data and sends it to BigQuery for real-time analysis.
- **Daily Data**: After the trading day ends, daily stock data (from 2020 to present) is fetched and processed for value investors. This is automated using Cloud Composer.

## Technologies Used
- **Google Cloud Platform**: Dataproc, BigQuery, Cloud Composer
- **Apache Kafka**: Real-time data ingestion
- **PySpark**: Data processing
- **Apache Airflow**: Workflow orchestration
- **Elasticsearch & Kibana**: Monitoring and log visualization
- **Power BI**: Data visualization

