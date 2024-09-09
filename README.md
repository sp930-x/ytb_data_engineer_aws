# Youtube Data Engineering Project Using AWS

This project is inspired by Darshil Parmar's guided project [here](https://www.youtube.com/watch?v=yZKJFKu49Dk&ab_channel=DarshilParmar), focusing on leveraging AWS' Big Data technologies for data processing and analysis.

## Motivation

The goal of this project is to learn and apply various AWS tools for handling large datasets, build data pipeline, and transforming raw data into actionable insights.

## Amazon Web Services and Technologies Used

- Amazon S3
- AWS IAM
- AWS Lambda
- AWS Athena
- AWS Glue Crawler, AWS Glue Catalog
- Python
- QuickSight

## Project Overview

1. **Data Acquisition**
Downloaded CSV files from [Kaggle](https://www.kaggle.com/datasets/datasnaek/youtube-new) and uploaded to Amazon S3 bucket (raw data). In this project only three regions that use English are selected for simplicity.
2. **ETL**:
   - Schema Inference: AWS Glue Crawler was used to infer the schema and store it in the AWS Glue Catalog.
   - Data Cleaning: A custom AWS Lambda function to preprocess the incoming new data and store them into the Amazon S3 bucket (cleaned data). In this project, the function to convert json file to parquet was involved. Trigger event is when the new object is created in the S3 bucket.
   - Data Transformation: ETL jobs extracted the data from Amazon S3, transformed it, and loaded the cleaned data back into S3 for analysis.
   - Transformation:
     ![ETL](https://github.com/user-attachments/assets/f9a31d06-2bd7-4080-bca6-72d3d8664790)

5. **Data Visualization & Analysis**: Analyzed transformed data using SQL and Python within Azure Synapse Analytics.   

## My QuickSight Visualization
The visualization with QuickSight
![QuickSight](https://github.com/user-attachments/assets/b10350d6-8cd9-480a-965f-27e684950c93)


Observations:
1. We can observe that actions such as pressing likes, dislikes and leaving comments are way lower compared to the count of views in total. Hence higher views does not lead to proactive actions such as likes and comments
2. In the perspective of the region, count of records does not necessarily match the number of comments in the order. Count of records were in order of Canada - Great Britain - USA but the comments were left in the order of Great Britain - USA - Canada. This supports the first theory as well.
3. From the bar charts in the third row, we can observe that, although the ordering of the channels are not necessarily exactly same as the number of likes and comments, half of them are in the rank of top 10. The channels marked as red implies both the order of rank in comments and likes are the same, yellow are not in same rank but included in top 10. For example, 'zefrank1' is in the rank of 5 in terms of the number of likes but ranked in 7 in terms of the number of comments. Lastly, the channel remarked as blue represents channels that has discrepancy between the comments and likes.
4. From the last row of the visualization, we can see that users tend to comment as they have energy to click the 'like' button. Interestingly, this also applies for the 'dislike' button as well. However unlike 'like' button, 'dislike' tend to have less comments even if it's very disliked by users. This could be due to the fact that users are being careful for not leaving hate comments. Although this specific scatter plots are generated from 2,500 data points only due to the limitation of QuickSight, it will be interesting to deep dive for further analysis such as sentiment analysis with like and dislikes.

Feel free to reach out with any questions or feedback!
