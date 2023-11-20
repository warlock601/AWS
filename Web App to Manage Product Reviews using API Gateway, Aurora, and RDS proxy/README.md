# Web App to Manage Product Reviews using API Gateway, Aurora, and RDS proxy

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
  
  
