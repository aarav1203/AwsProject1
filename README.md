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

## Requirement of AWS Glue
1. Read Data from S3 Bucket
2. Read Data from Dynamo Db
3. Check how many DS1 is available in DS2
4. Discard already available record
5. Insert new records into Dynamo Db

## Folder Architecture
Whenever ETL pipeline will run then it reads file from S3 Bucket -> inbox folder and dump into Dynamo Db and after succesfully inserted it moves that file from "inbox" folder to "archive" folder which help to investigate in future.

S3 /inbox/sample.json --->DynamoDb
S3/archive/sample.json
 
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

## Step 3: Install the Requirements
```
pip install -r requirements.txt
```
## Step 4: Create Lambda_Function_code folder into zip file
###### Create Lambda_Function_Code folder into zip file which we can upload into Aws Lambda Function.
After run this command many files will get created and then select all and zipped all
```
pip install --platform manylinux2014_x86_64 --target=lamda_function_code --implementation cp --python==3.9 --only-binary=:all: --upgrade pymongo[srv] boto3 requests
```

## Step 5: Create Lambda Function
##### Upload the previous zipped file into this.
##### Add all the environment eg. MongoDb database name,collection name,S3 Bucket Name
##### Give Permission to Lamda to full access S3
##### Add Trigger to Lambda function to fetch data on regular interval of time(eg.weekly or monthly basis)

## Step 6: Configure Dynamo Db
``` 
Partition key :- "complaint_id"
Sort Key :- "product"
```
## Step 7: Configure AWS Glue
1.Give permission to glue to  access S3 bucket
2.Select Python language
3.Select type as 'Spark'
4.Then go with Default Configuration
#### Upload this script in Aws Glue Script section
###### https://github.com/aarav1203/AwsProject1/blob/main/project_steps.txt
