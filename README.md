# Amazon Vine Analysis
## Overview of the Project

### Purpose

Analyzes Amazon reviews written by members of the paid Amazon Vine program. The Amazon Vine program is a service that allows manufacturers and publishers to receive reviews for their products. There are approxiametely 50 different Amazon Vine review datasets to choose from. This project analyzes a sporting goods review dataset. All the datasets have the same schemata, as shown in the following image:

![data-16-challenge-format-and-info-amazon-review-datasets-columns-1](https://user-images.githubusercontent.com/111299372/216786997-d95a77f7-2e91-478e-b5ad-2fbb3b8322a4.png)

An AWS RDS database is created with tables in pgAdmin. A dataset is picked from the amazon review datasets https://s3.amazonaws.com/amazon-reviews-pds/tsv/index.txt. The dataset was then extracted in a DataFrame. The original DataFram was transformed into four separate DataFrames that match the table schema in pgAdmin. Project uses PySpark to run an analysis to determine if having a paid Vine review makes a difference in the percentage of 5-star reviews. 

### Resources

#### Datasource
Amazon review dataset on sporting goods: https://s3.amazonaws.com/amazon-reviews-pds/tsv/amazon_reviews_us_Sports_v1_00.tsv.gz

#### Software
PySpark, PostgreSQL, pgAdmin, AWS, Google Colab

## Results

## Summary
