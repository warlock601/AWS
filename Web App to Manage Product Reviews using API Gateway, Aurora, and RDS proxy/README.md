# Micro-service to Manage Product Reviews using API Gateway, Aurora, and RDS proxy
## Overview:
An Organization's applications are currently hosted on on-premises servers, and the
application traffic is unpredictable. So, they often end up with idling servers or
over-utilized servers. As part of the cloud migration, the org is looking at a cloud-
native solution that can dynamically scale based on traffic. They also want to
minimize expenses when there is no application traffic. Their team is new to
AWS cloud, they want to build a proof-of-concept application and learn from it. <br/>
You will build a micro-service for managing products and reviews. You will use
API Gateway as the "front door" Lambda for the application logic, and Aurora
Relational database for data storage. For hosting the web page, you will use
Amazon S3.
The web page must use client-side JavaScript to interact with your API
Gateway. For connection-pooling, your Lambda function must use RDS Proxy to
talk to the database. You should maintain the database login credentials in AWS
Secrets Manager, and RDS Proxy must use these credentials to connect to the
database. Your Lambda function would acquire a connection from RDS Proxy
using IAM Role. In this solution, only Aurora is server-based, and the rest of the
application uses serverless technologies.

### Steps:
 1. Create a Database and in that create 2 tables namely Product and Review where Review table references Product.
   ```bash
   create table product(
    product_id INT primary key,
    product_category varchar(100),
    product_title varchar(255),
    sum_rating float,
    count_rating INT
   )
   ```
   
   ```bash
   CREATE TABLE Review(
    product_id INT,
    review_ts datetime primary key,
    review_headline VARCHAR(100),
    review_body VARCHAR(1024),
    star_rating FLOAT,
    foreign key (product_id) references product(product_id)
   )
   ```
Open RDS, create database with the following specifications:
- Engine Type: Aurora (MySQL Compatible)  
- Template: Dev/Test
- DB Cluster identifier: Demodatabase
- DB Instance classes: Bustable classes (db.t3.medium)
- Under Multi-AZ deployment, select Don't create an Aurora Read Replica
- Compute Resource: Don’t connect to an EC2 compute resource, Network Type as IPv4, Subnet group: Default, VPC Security Group: Default
- Expand Additional Configuration, Initial Database Name: productreview and then Create Database

Open Secrets Manager, click on "Store a new secret"
- Select Credentials for Amazon RDS Database.  
- Name the secret as "productreview/demo/admin" and then store it.

In RDS Console, Click on Proxies > Create Proxy
- Enter Proxy identifier as "productreviewproxy"
- Select the database which was created earlier
- In Authentication, Create IAM role, select the secret: productreview/demo/admin
- For IAM Authentication, select Required
- For Subnets, select all the default subnets
- Under Connectivity, check "Require Transport Layer Security"
- Additional Connectivity configuration > choose the default VPC security group

Create a Lambda Layer. Lambda layers are created to reduce the size of your deployment packages and to separate core function logic from dependencies.
- First save the "layer+pymsql.zip" on your local system
- Open lambda Console > Layers > Create Layer, name it as layer-pymsql
- Upload a zip file > Upload "Layer_pymsql.zip"
- Compatible Runtimes: Python 3.7 & Python 3.8, then Create Layer
- Now create an IAM role for Lambda function, Select AWS service & then select Lambda as use case
- Attach Policies > AWSLambdaBasicExecutionRole & AWSLambdaVPCAccessExecutionRole (These policies will allow Lambda to log & run inside a VPC)  

Create a Lambda Function and select the role we created as the default execution role
- Author From Scratch, Runtime- Python 3.8
- Advanced Settings, Enable VPC > choose default VPC, Subnets > Choose all available subnets, & choose default VPC Security Group 
  
  
