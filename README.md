
# Reddit Data Pipeline Engineering with Apache Airflow and AWS

This project demonstrates a complete data engineering pipeline that extracts data from Reddit, processes it, and loads it into AWS services for further transformations and visualization. The pipeline is orchestrated using **Apache Airflow** and leverages **AWS S3**, **AWS Glue**, **AWS Athena**, and **Amazon Redshift** for efficient data handling.

## Table of Contents
- [Overview](#overview)
- [Features](#features)
- [Technologies Used](#technologies-used)
- [Setup Instructions](#setup-instructions)
- [Project Workflow](#project-workflow)
- [License](#license)

## Overview

This project connects to a Reddit instance using Apache Airflow to manage ETL (Extract, Transform, Load) tasks, integrating with various AWS services to extract, clean, transform, and visualize Reddit data. The pipeline includes:

- Extracting posts from a specified subreddit using Reddit's API.
- Cleaning and transforming the data into a structured format.
- Uploading the data to an S3 bucket for storage.
- Utilizing AWS Glue to further process and transform the data.
- Querying the transformed data using AWS Athena and visualizing it through SQL queries.
- Loading the data into Amazon Redshift for advanced analytics.

## Features
- **Data Extraction**: Retrieves posts from Reddit using the PRAW library.
- **Data Transformation**: Cleans and structures the data using Pandas.
- **Cloud Integration**: Utilizes AWS S3 for storage, AWS Glue for data transformation, AWS Athena for querying, and Amazon Redshift for advanced data analytics.
- **Orchestration**: Manages the pipeline with Apache Airflow and Celery backend using Docker.

## Technologies Used
- **Apache Airflow**
- **Python** (with PRAW and Pandas libraries)
- **Docker**
- **PostgreSQL** (Airflow metadata backend)
- **Redis** (Celery message broker)
- **AWS S3**
- **AWS Glue**
- **AWS Athena**
- **Amazon Redshift**

## Setup Instructions

1. **Clone the repository**:
   ```bash
   git clone https://github.com/your-username/reddit-data-pipeline.git
   cd reddit-data-pipeline
   ```

2. **Install dependencies**:
   Necessary directories and files.
   ```bash
   mkdir config
   ```
   Using a python virtual environment (3.9 recommended), install dependencies using below.
   ```bash
   pip install apache-airflow numpy pandas praw
   ```
   Ensure you have Docker installed.
   Make requirements.txt that will be used by Docker to create a container with necessary dependencies.
   ```bash
   pip freeze > requirments.txt
   ```
   

4. **Create a Reddit application**:
   - Go to [Reddit's Developer Portal](https://www.reddit.com/prefs/apps) and create a new application.
   - Set the `client_id`, `client_secret`, and `user_agent` in the environment variables or your configuration file.

5. **Configure reddit and AWS credentials**:
   In the `.config` file, edi the .

6. **Run the Docker containers**:
   ```bash
   docker compose up -d --build
   ```

7. **Trigger the DAG**:
   Access Airflow via `localhost:8080` and trigger the DAG for Reddit data extraction and transformation.

## Project Workflow

1. **Reddit Data Extraction**:
   - The pipeline connects to Reddit using the PRAW library and extracts posts from a specified subreddit.
   
2. **Data Transformation**:
   - The extracted data is cleaned and transformed using Pandas to create a structured DataFrame.

3. **Data Storage**:
   - The cleaned data is uploaded to an AWS S3 bucket as CSV files.

4. **AWS Glue for ETL**:
   - AWS Glue crawls the data in S3 to generate a schema and further transforms the data.

5. **Querying with AWS Athena**:
   - SQL queries are executed on the cleansed data in AWS Athena for insights and visualization.

6. **Loading Data into Amazon Redshift**:
   - Finally, the transformed data is loaded into Amazon Redshift for further analysis and reporting.


