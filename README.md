# Amazon Product Review Analysis with BigData and AWS

Apache Hadoop (Hadoop) is one of the most popular open source frameworks, with numerous technologies for big data. Google developed Hadoop to process large amounts of data by splitting data across a distributed file system. With the growing interest in big data and the ease of access to cloud technology, Hadoop is no longer required. New technologies allow more flexibility in data processing. One of these technologies is Spark. 

PySpark is the Python API written in Python to support Spark. One traditional way to handle Big Data is to use a distributed framework like Hadoop but these frameworks require a lot of read-write operations on a hard disk which makes it very expensive in terms of time and speed. We'll use Google Colaboratory (Colab), which are Google-hosted notebooks to write our PySpark.

Also, we will use cloud services to store our Database and also to access input data. Amazon Web Services (AWS) is the largest cloud provider in the market today. It's not the only one—many companies, such as Google and Microsoft, also have their own cloud platforms. We'll focus on AWS, but the services offered will be similar across all solutions.

## Overview

In this project we will analyze Amazon reviews written by members of the paid Amazon Vine program. The Amazon Vine program is a service that allows manufacturers and publishers to receive reviews for their products. Companies like SellBy pay a small fee to Amazon and provide products to Amazon Vine members, who are then required to publish a review.

We will pick one of the AWS S3 dataset and use PySpark to perform the ETL process to extract the dataset, transform the data, connect to an AWS RDS instance, and load the transformed data into pgAdmin. Next, we will use PySpark (we can also use Pandas, or SQL) to determine if there is any bias toward favorable reviews from Vine members in your dataset. Then, we’ll write a summary of the analysis to the SellBy stakeholders. Below are the list of Deliverables:

  * Deliverable 1: Perform ETL on Amazon Product Reviews
  * Deliverable 2: Determine Bias of Vine Reviews
  * Deliverable 3: A Written Report on the Analysis (README.md)

## Analysis

We will use Colab notebook with PySpark, AWS, pgAdmin for our Analysis. Colab notebook functionality is very similar to using Jupyter Notebook, except now everything is hosted online. Just like we do with our local environment, we need to install packages for libraries we want to use. PySpark does not come native to Google Colab and needs to be installed. We'll do so by running the set of code in the first cell and then need to create a Spark session by importing the library and setting the spark variable.

![image](https://user-images.githubusercontent.com/85472349/135903089-2186a55a-1a19-4a91-b3eb-5b8083b3ebb1.png)


![image](https://user-images.githubusercontent.com/85472349/135903121-5509454f-7363-4117-901f-a4b697160d6a.png)


![image](https://user-images.githubusercontent.com/85472349/135903175-54a3ab44-36b6-4f6f-a299-9bbd224e26c2.png)

### Deliverable 1: Perform ETL on Amazon Product Reviews

With our knowledge of the cloud ETL process, we'll create an AWS RDS database with tables in pgAdmin. We are going to use a Toy dataset from the Amazon Review datasets and extract the dataset into a DataFrame. Then we'll transform the DataFrame into four separate DataFrames that match the table schema in pgAdmin. Then, you'll upload the transformed data into the appropriate tables and run queries in pgAdmin to confirm that the data has been uploaded.

![image](https://user-images.githubusercontent.com/85472349/135903600-b089e634-9729-4c64-8bc1-f215b0f2a1d9.png)


![image](https://user-images.githubusercontent.com/85472349/135903624-5d6acfc2-2769-4ceb-824a-173fb5cb1dcd.png)


![image](https://user-images.githubusercontent.com/85472349/135903668-b022ea28-5f06-48f3-88c4-a72ed3f4bff8.png)


![image](https://user-images.githubusercontent.com/85472349/135903709-41d17ba3-26a7-4d94-8c29-082b25c410dc.png)

### Table load and verification


![Table_Load](https://github.com/saranyadurairaju/Module16-BigData-Analysis/blob/main/Challenge/Table_Verification/AWS_Table_Load.jpg)


**pgAdmin customers_table**


![customers_table](https://github.com/saranyadurairaju/Module16-BigData-Analysis/blob/main/Challenge/Table_Verification/Customers_table.PNG)

**products_table**


![products_table](https://github.com/saranyadurairaju/Module16-BigData-Analysis/blob/main/Challenge/Table_Verification/Products_table.PNG)

**review_id_table**


![review_id_table](https://github.com/saranyadurairaju/Module16-BigData-Analysis/blob/main/Challenge/Table_Verification/Review_id_table.PNG)

**vine_table**


![vine_table](https://github.com/saranyadurairaju/Module16-BigData-Analysis/blob/main/Challenge/Table_Verification/Vine_table.PNG)


## Deliverable 2: Determine Bias of Vine Reviews

In this we’ll determine if there is any bias towards reviews that were written as part of the Vine program. For this analysis, we'll determine if having a paid Vine review makes a difference in the percentage of 5-star reviews. For this we will do the below items:

**DataFrame for the vine_table data**

![image](https://user-images.githubusercontent.com/85472349/135905039-c5198bb0-b1d0-46df-a6b4-770a45993176.png)

**DataFrame where there are 20 or more total votes**

![image](https://user-images.githubusercontent.com/85472349/135905170-1a326902-d8a3-4bc6-b335-fcbe56e471d7.png)

**DataFrame where the percentage of helpful_votes is equal to or greater than 50%**

![image](https://user-images.githubusercontent.com/85472349/135905284-f8fafb0e-07c8-40cd-b8b0-acddf2dfb868.png)

**DataFrame where there is a Vine review**

![image](https://user-images.githubusercontent.com/85472349/135905436-643a9440-e0f2-4697-a67d-7e1af742a2bc.png)

**DataFrame where there isn’t a Vine review**

![image](https://user-images.githubusercontent.com/85472349/135905476-70737cd6-ac88-4a07-9600-495d814bce5e.png)

## Results

So, from our Vine Review analysis we got the dataframe with Vine and non-Vine set of reviews. With that dataframe we are finding the number of records/ percentage on each criteria for a better understanding. Below is the set of code for the same:

![image](https://user-images.githubusercontent.com/85472349/135906121-81f153a9-ced6-4161-aa05-13335b7194b1.png)

### Count table

![image](https://user-images.githubusercontent.com/85472349/135908148-5dc070df-3946-4a79-9c06-1959b5fa04e4.png)


## Summary

From the above results and table of counts we can clearly see the Percentage of **Paid 5-star reviews is 34.12%** but the non-Vine/unpaid percentage of **5 star reviews is 48.34%**. So from this we can state that there is **no bias** for reviews in the Vine program. So small companies can really try this vine program during their initial days.

### Additional Analysis

To support our summary results, we can consider the verified purchase column. An "Amazon Verified Purchase" review means they've verified that the person writing the review purchased the product at Amazon and didn't receive the product at a deep discount.

![image](https://user-images.githubusercontent.com/85472349/135907369-4a5388ee-ec20-443c-a72e-d412ac18bdeb.png)

From the below number of records its clear that **99.99% of verified purchases are unpaid purchases.** So vine program is definitely not bias.

![image](https://user-images.githubusercontent.com/85472349/135908190-e29457ea-011b-4e24-ac16-f1c817868315.png)


**Hurry!!! Amazon vine program analysis is success and Jennifer can submit the summary of analysis to the SellBy Stakeholders**


