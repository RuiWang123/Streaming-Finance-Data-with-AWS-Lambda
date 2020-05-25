# Streaming Finance Data with AWS Lambda
### Introduction
For this project, we are tasked with provisioning a few Lambda functions to generate near real time finance data records 
for downstream processing and interactive querying.

### Infrastructure
This project consists of three major infrastructure elements that work in tandem:
1. A lambda function that collects our data (DataCollector)
1. A lambda function that transforms and places data into S3 (DataTransformer)
1. A serverless process that allows us to query our s3 data (DataAnalyzer)

### Lambda Function Configuration Page
Data Collector Lambda Function URL:
https://eb9iumoz0b.execute-api.us-east-2.amazonaws.com/default/STA9760-project3-data-collector


