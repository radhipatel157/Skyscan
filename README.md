# ✈️ SkyScan: Serverless Airline Data Processing Pipeline

## Overview

SkyScan is a fully automated, serverless data pipeline built using AWS to process and clean airline flight data efficiently. It leverages multiple AWS services to detect anomalies, transform data, and orchestrate the entire workflow without the need for manual intervention.

## 🔍 Features

- **Data Ingestion & Storage**: Raw airline data is uploaded and stored in Amazon S3.
- **Anomaly Detection**: AWS Lambda filters anomalous flights with excessive delays.
- **Data Transformation**: AWS Glue processes and transforms the cleaned data.
- **Workflow Orchestration**: AWS Step Functions automate the ETL process.
- **Event Triggering**: AWS EventBridge initiates the pipeline on new uploads.
- **Failure Notifications**: AWS SNS alerts upon processing failures.

## 🧰 AWS Services Used

- Amazon S3 – Data storage and folder structuring
- AWS Lambda – Python-based anomaly detection
- AWS Glue – Data crawling and ETL job orchestration
- AWS Step Functions – Workflow automation
- AWS EventBridge – Event-driven triggers
- AWS SNS – Email notifications for errors

## 🧱 Folder Structure in S3
/raw/ → Incoming airline data
/anomalies/ → Flights with delays > 500 minutes
/processed/ → Cleaned and transformed data
/logs/ → Logs from Glue and Step Functions

## 🗂 Workflow Summary

1. Upload raw CSV to `/raw/` in S3.
2. Lambda detects anomalies and segregates clean data.
3. Glue Crawler updates schema catalog from `/raw/`.
4. Glue Job transforms and saves data to `/processed/`.
5. Step Function manages the entire process.
6. EventBridge triggers the pipeline automatically on file upload.

## 📣 Failure Handling

- On any failure, a message is published to an SNS Topic (subscribed via email).
- Logs are stored for debugging in S3 `/logs/`.

## 📦 Technologies

- Python (AWS Lambda)
- AWS Management Console
- Glue Studio (Visual ETL)
- IAM Roles and Permissions
- Parquet/CSV for storage formats

## 🚀 Getting Started

1. Upload your dataset to `s3://airline-data-bucket/raw/`.
2. Ensure Lambda and Glue jobs are configured as per the implementation guide.
3. Monitor pipeline via AWS Step Functions and SNS alerts.

## 🧑‍💻 Contributors
- Radhi Patel (Developer & Architect)
- Shiv Dixit (Developer & Architect)

## 📝 License

This project is licensed under the MIT License.
