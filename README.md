# Sales-Data-Processing


This project simulates a real-time sales data pipeline using AWS services such as Lambda, DynamoDB, Kinesis, S3, Glue, and Athena. The project demonstrates an event-driven architecture for generating, transforming, and analyzing sales data.

## Table of Contents

- Project Overview
- Architecture
- How to Deploy
- Usage


## Project Overview

This project generates mock sales data using AWS Lambda, stores the data in DynamoDB, and processes the data in real time using DynamoDB Streams and EventBridge. Kinesis Firehose is used to batch and transform the data before storing it in S3. Finally, an AWS Glue Crawler is run to create a schema for querying the data in Amazon Athena.

## Architecture

![Architecture](https://github.com/user-attachments/assets/9e76a48d-e0db-4945-ac1d-09ee7b348ca3)

The architecture follows an event-driven pipeline:
1. Lambda: Generates mock sales data and sends it to DynamoDB.
2. DynamoDB: Stores the sales data.
3. DynamoDB Streams: Triggers an event when new data is added to DynamoDB.
4. EventBridge: Routes events to Kinesis Data Streams.
5. Kinesis Firehose: Batches and transforms data using another Lambda function.
6. S3: Stores the transformed data.
7. Glue Crawler: Automatically discovers the schema for the data in S3.
8. Athena: Allows querying of the sales data stored in S3.

## How to Deploy

1. Step 1: Clone this repository https://github.com/Rishith527/Sales-Data-Projection
   
   cd sales-data-projection

Step 2: Set up AWS resources (Lambda, DynamoDB, EventBridge, etc.) using the AWS Console or Infrastructure-as-Code (IaC) such as CloudFormation or Terraform.

Step 3: Deploy Lambda functions. Use the AWS CLI or Serverless Framework to package and deploy the generate_mock_data.py and transform_data.py Lambda functions.

Step 4: Set up the Kinesis Data Stream, Firehose, and S3 bucket.

Step 5: Configure the Glue Crawler and run it to detect the schema.

Step 6: Query the data in Athena.

## Usage

Generate Mock Data: The generate_mock_data.py Lambda function simulates sales orders and inserts them into DynamoDB.

Data Processing: Kinesis Firehose batches and processes this data using the transform_data.py Lambda.

Data Analysis: Use Athena to query the processed data stored in S3.


