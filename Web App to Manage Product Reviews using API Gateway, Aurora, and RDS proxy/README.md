# Web App to Manage Product Reviews using API Gateway, Aurora, and RDS proxy

 Create a Database and in that create 2 tables namely Product and Review where Review table references Product.
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
