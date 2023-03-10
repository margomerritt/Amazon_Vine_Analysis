# Amazon Vine Analysis
## Overview of the Project

### Purpose

Analyzes Amazon reviews written by members of the paid Amazon Vine program. The Amazon Vine program is a service that allows manufacturers and publishers to receive reviews for their products. There are approxiametely 50 different Amazon Vine reviews datasets to choose from. This project analyzes a sporting goods reviews dataset. All the datasets have the same schemata, as shown in the following image:

![data-16-challenge-format-and-info-amazon-review-datasets-columns-1](https://user-images.githubusercontent.com/111299372/216786997-d95a77f7-2e91-478e-b5ad-2fbb3b8322a4.png)

An AWS RDS database is created with tables in pgAdmin. A dataset is picked from the amazon reviews datasets https://s3.amazonaws.com/amazon-reviews-pds/tsv/index.txt. The dataset was then extracted in a DataFrame. The original DataFrame was transformed into four separate DataFrames that match the table schema in pgAdmin. Project uses PySpark to run an analysis to determine if having a paid Vine review makes a difference in the percentage of 5-star reviews. 

### Resources

#### Datasource
Amazon reviews dataset on sporting goods: https://s3.amazonaws.com/amazon-reviews-pds/tsv/amazon_reviews_us_Sports_v1_00.tsv.gz

#### Software
PySpark, PostgreSQL, pgAdmin, AWS, Google Colab

## Results

PySpark was utilized to run an analysis on the sporting goods reviews dataset. In this analysis we'll determine if having a paid Vine review makes a difference in the percentage of 5-star reviews. We started by filtering the vine data to retrieve all the rows where the total_votes count is equal to or greater than 20 to pick reviews that are more likely to be helpful and to avoid having division by zero errors later on. Vine reviews are the paid reviews. Non-Vine reviews are the unpaid reviews.

### Total number of Amazon Reviews

* From the PySpark analysis we see that there are 334 Vine reviews: 

![total number of paid reviews](https://user-images.githubusercontent.com/111299372/216787683-381713b8-ac3b-4ecd-82b6-1c23228288af.png)

* There are 61614 Non-Vine reviews:

![total number of unpaid reviews](https://user-images.githubusercontent.com/111299372/216787824-669d9745-a11d-47cd-89fb-720ab174f3bb.png)



Thus there are more non-paid (non-Vine) reviews than there are paid (Vine) reviews for our sporting goods review data.


### Total Number of 5-Star Reviews

* From the PySpark analysis we see that there are 139 5-star Vine reviews:

![total number of paid 5-star reviews](https://user-images.githubusercontent.com/111299372/216789679-14997e08-6513-4ef1-8e85-ea5462077937.png)

* There are 32665 5-star Non-Vine reviews:

![number of 5-star unpaid reviews](https://user-images.githubusercontent.com/111299372/216789693-df301988-2e36-4327-bd86-50f557cf50b9.png)

### Percentage of 5-star reviews

* We see that 41.62% of the paid Vine reviews were 5-star:

![percentage of 5-star paid reviews](https://user-images.githubusercontent.com/111299372/216789724-eac2e0f4-73f3-41e9-a146-7a937a15ea9a.png)

* We see that 53.02% of the non-paid reviews were 5-star:

![percentage of unpaid 5-star reviews](https://user-images.githubusercontent.com/111299372/216789739-18d70ed7-22d8-429a-a3d2-4009ba84dd86.png)

## Summary

From our PySpark analysis we found that 41.62% of the paid Vine reviews were 5-star. The unpaid Non-Vine reviews had a 5-star rating of 53.02%. Thus the non-paid reviews had a higher positivity rating than the paid reviews. Hence for this sporting goods reviews dataset we can determine that there is not a positivity bias for reviews in the paid Vine program. 

Before we ran our analysis in PySpark we filtered the Vine DataFrame to retrieve all the rows where the total_votes count is equal to or greater than 20. This allowed us to pick reviews that were more likely to be helpful and to avoid having division by zero errors later on. However, this could have introduced error into our analysis. There could be a lot more than 139 5-star reviews in our Vine reviews dataset. Those 5-star reviews might have just not received a lot of votes on the review. Customers are generally more willing to upvote a non-paid for 5-star review than they are for an obviously paid for 5-star review. 

An additional helpful analysis is to use the unfiltered Vine review dataset and run the same analysis on it. In this analysis we would have to be careful not to introduce a divide by zero error. After this additional analysis is run we can compare it to the original results to help further determine if a positivity bias exists for the paid Vine reviews. 


