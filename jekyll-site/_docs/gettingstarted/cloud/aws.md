---
title: "AWS"
layout: default
parent: "Cloud"
grand_parent: "Getting Started"
nav_order: 4
description: "Currently MIMIC-III is available on AWS but MIMIC-IV is not. MIMIC-IV will be released on AWS in the future."
---

# AWS

Recently, the MIT Laboratory of Computational Physiology (LCP) started hosting the MIMIC-III dataset on the AWS cloud through the AWS Public Dataset program. You can now use the MIMIC-III dataset via S3 without having to download, copy, or pay to store it. Instead, you can analyze the MIMIC-III dataset in the AWS Cloud using AWS services like Amazon EC2, Athena, AWS Lambda, or Amazon EMR. AWS Cloud availability enables quicker and cheaper research into the dataset.

Services like Athena also offer you new analytical approaches to the MIMIC-III dataset. Using Athena, you can execute standard SQL queries against MIMIC-III without first loading the data into a database. Because you can reference the MIMIC-III dataset hosted by MIT LCP in Amazon S3, your analyses always reference the most recent version of the MIMIC-III dataset. Live hosting reduces upfront time and effort, eliminates data synchronization issues, improves data analysis, and reduces overall study costs.

Once you have successfully requested access to MIMIC-III on AWS, you can follow the instructions linked below. These instructions initialize and execute an entire study performed on MIMIC-III using a hosted Jupyter notebook service on AWS.

https://aws.amazon.com/blogs/big-data/perform-biomedical-informatics-without-a-database-using-mimic-iii-data-and-amazon-athena/
