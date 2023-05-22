# Crypto_real-time_streaming_using_kafka_and_Databricks
In this project, we are scraping crypto-data from "https://crypto.com/price" website and working on it. By the end of this project you will learn data cleaning, data-streaming using kafka and Databricks and trending aws services like- S3, Glue, and Athena.

The Basic Architechture of the project is shown below.


![Project_architechture](https://github.com/Sarang823/Crypto_real-time_streaming_using_kafka_and_Databricks/assets/133379507/de64544d-686b-4a1a-90c9-6adbcb3124fa)



# Technologies & Tools used :
1. Scrapy Python Framework (You can also use BeautifulSoup)
2. Pandas - Python data cleaning framework
3. Kafka Producer - For producing the data
4. Kafka Broker - For storing Data
5. Kafka Consumer - For receiving the data
6. DataBricks - Leading realtime data processing framework.
7. Aws S3 - Object storage for storing the data
8. AWS Glue - An ETL tool , here used for crawling the data from S3 to query using Athena
9. AWS Athena - Run SQL queries


# Datasets Used :
Actually we, have scrapped the data from crypto.com and processed it. But for reference you can use this datasets, if you are skipping those steps.
## Scrapped Raw Dataset:


[coins.csv](https://github.com/Sarang823/Crypto_real-time_streaming_using_kafka_and_Databricks/files/11527386/coins.csv)

## Processesd Dataset:

[crypto_coins.csv](https://github.com/Sarang823/Crypto_real-time_streaming_using_kafka_and_Databricks/files/11527390/crypto_coins.csv)
 
 # STEP-BY-STEP GUIDE :
 ## Step 1  Scraping the data :
 Refer the crypto_scrapping project which I have already provided. You can directly import that in IDE like PyCharm.
 If You want the project then refer this Drive link : -
 https://drive.google.com/drive/folders/1oW3JINaB-VvBjfvixobwlyDzHAzetf5S?usp=share_link
 ## Step 2 Cleaning the Data :
 For that refer the data_cleaning.ipnyb file
 ## Step 3 Setup Kafka installation on AWS EC2:
 For that refer the setup_guide.txt
 ## Step 4 For DataBricks :
 Refer the necessary databicks file.
 ## Step 5 AWS Part : 
 create 2 AWS Buckets with globally unique name. Note that the the region you choose for both the buckets should be same and uncheck the 'Block all public access'.
 
 ![aws S3](https://github.com/Sarang823/Crypto_real-time_streaming_using_kafka_and_Databricks/assets/133379507/f07c2fcc-c388-4007-b974-fe476e48141b)

 
 You have to create IAM user to access providing AdministratorAccess (just for project). Use that aws_access_key_id and aws_secret_access_key in Databricks program to establish connection between S3 and Databricks.
 IAM >> Users >> Add User >> Add name >> Attach policies directly >> Administrator Access >> Next >> Create User
  ## DataBricks Output :-
 
 
 ![DataBricks_output](https://github.com/Sarang823/Crypto_real-time_streaming_using_kafka_and_Databricks/assets/133379507/8a995240-d9e2-4f2f-8b15-99d06a6ee62e)

  
  Go to Glue >> crawlers >> crete crawler >>Enter unique name >> Next >> Not yet >> Click Add a Datasource >> S3 path >> Browse path >> select bucket >>
  Add S3 data source >> Create new IAM Role >>select AWS service >> scrol down select glue >> select AmazonS3FullAccess next >> add name and create role >>create database and finally create crawler >> then run crawler
  Next step is go to Athena and Amazon Athena >> Query editor >> Settings and Manage >> Add that second S3 bucket path which we created in the beginning.
  
  
  Then finally run sum sample SQL queries - (Select * from db_name.Table_name limit 10 ;)
  ## Final Output :-
  
  ![Final_output](https://github.com/Sarang823/Crypto_real-time_streaming_using_kafka_and_Databricks/assets/133379507/00a42b1c-9371-4963-862e-dfd2681f481f)

 
 
 
 
 
 
