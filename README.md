# Streaming Finance Data with AWS Lambda
### Introduction
For this project, we are tasked with provisioning a few Lambda functions to generate near real time finance data records 
for downstream processing and interactive querying.

### Infrastructure
This project consists of three major infrastructure elements that work in tandem:
1. A lambda function that collects our data (DataCollector)
1. A lambda function that transforms and places data into S3 (DataTransformer)
1. A serverless process that allows us to query our s3 data (DataAnalyzer)

### Process Break Down
##### AWS Firehose -> AWS Lambda Functions -> Docker Deployment Package -> AWS Glue -> AWS Athena -> Jupyter Notebook Analysis
1. Setup **Kinesis Firehose Delivery Stream with Lambda Function**. It will transform our record and streams it into an S3 bucket. (DataTransformer)
2. Setup Another **Lambda Function**, triggered from a simple URL call. On trigger, it will grab stock price data and place it into the delivery defined in the DataTransformer. (DataCollector)
3. Configure **AWS Glue**, pointing it to the **AWS S3 Bucket** we created in our DataTransformer.
4. Using **AWS Athena** to interactively query the S3 files generated by the DataTransformer to gain insight into our streamed data. (DataAnaylzer) 

### Lambda Function Link and Configuration Page
Data Collector Lambda Function URL:

https://eb9iumoz0b.execute-api.us-east-2.amazonaws.com/default/STA9760-project3-data-collector

Configuration Page
![image](https://raw.githubusercontent.com/hailin-du/Streaming-Finance-Data-with-AWS-Lambda/master/Images/Data%20Collector%20Lambda%20%20Function.png)


### Lambda Deployment Package
We can use docker to install necessary packges where we don't have to install the yfinance module via subprocess. We can actually create our dependency package via docker. 

In order to run lambda functions that also manage dependencies, we must leverage a "deployment package", basically a zip file containing our lambda code and all the dependencies it needs all packaged into a single artifact. For more details we can find it here. 

[STA9760 Simple_Deployment Package By Professor Taq](https://github.com/mottaquikarim/STA9760_simple_deployment_package)


### Kinesis Data Firehose Delivery Stream Monitoring

Stream Monitoring
![image](https://raw.githubusercontent.com/hailin-du/Streaming-Finance-Data-with-AWS-Lambda/master/Images/Data%20Monitoring.png)

### AWS Glue and Athena

We will then configure AWS Glue, pointing it to the S3 Bucket we created in our DataTransformer. This will allow us to now interactively query the S3 files generated by the DataTransformer using AWS Athena to gain insight into our streamed data. This process is also known as DataAnalyzer.

### Jupyter Notebook Analysis
After we have generated our output, we can download the CSV file. Then, we can upload the file to Jupyter Notebook, using Python packages to create data visualizations. 
