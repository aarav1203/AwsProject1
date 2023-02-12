# AWS Pipeline 
## Problem Statement
##### 1.This project show that how the data flow into pipeline with the help of cloud service(AWS).
##### 2.Download data from Api and store into the Cloud Database

## 👨‍💻 Tech Stack Used
##### 1.AWS
##### 2.MongoDB
##### 3.Python
##### 4.Pyspark

## 🌐 Infrastructure Used
##### 1.API
##### 2.AWS Glue
##### 3.Aws S3 Bucket
##### 4.Aws Lambda
##### 5.Aws DynamoDb

## Project Architecture
![image](https://user-images.githubusercontent.com/62836744/218323041-5d3a1f48-3bcd-4601-9e0a-ad08059934ee.png)

## Requirement of Application for AWS Lambda
Web API<--- From Date and To Date
---> Json data -->s3 bucket

From_date="2011-01-01"
Current_Date="2023-01-20"

After One Month Current_Date="2023-02-20"
From_Date="2023-01-20"
Current_Date="2023-02-20"

After Next Month Current_Date="2023-03-20"
From_Date="2023-02-20"
Current_Date="2023-03-20"
And Follow The same further

Store the Current date into some database,i am using mongo-db database to store the current date and when download the data next time then it update from date and current date according to that.
 
## How to Run ?
Before we run the project, make sure that you are having MongoDB in your local system, with Compass since we are using MongoDB for data storage. You also need AWS account to access the service like S3, Glue,DynamoDb,Lambda.

## Step 1: Clone the Repository
```
git clone https://github.com/aarav1203/AwsProject1.git
cd AwsProject1
```
## Step 2: Create a conda environment after opening the repository
```
conda create -n venv python=3.7.6 -y
```
```
conda activate venv/
```
Make sure to ensure install Python Extension in VS code and select the python interpreter installed in virtual environment

## Install the Requirements
```
pip install -r requirements.txt
```
