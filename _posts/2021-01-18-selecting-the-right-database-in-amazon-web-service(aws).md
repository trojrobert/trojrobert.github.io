---
date: 2021-01-18 16:07:17
layout: post
title: "Selecting the right database in Amazon Web Service(AWS)"
subtitle:
description: This article is a documentation of what I learned and the resources I used in understanding the various databases in AWS and how to decide when to use them.
image: https://res.cloudinary.com/dbzzslryr/image/upload/v1610988705/aws_databases/database_characteristics.jpg
optimized_image: https://res.cloudinary.com/dbzzslryr/image/upload/v1610988705/aws_databases/database_characteristics.jpg
category:
tags:
author:
paginate: false
---


Deciding the database to use can be very tricky. If you have to select databases for your workload or application in Amazon Web Service(AWS), you can be confused about the right choice to select.  Since I join AWS Community Builder, I spend a least 1 hour exploring AWS services based on use case. This article is a documentation of what I learned and the resources I used in understanding the various databases in AWS and how to decide when to use them. I hope it will be of value to you. I will like to have feedback on what you think I should add or remove or improve on as I continue exploring AWS services.

There are a lot of criteria the could help us in selecting the right database in AWS, to make it easier for us, we summarize it into the following 4 criteria 
1. **Type** of Data
2. **Size** of Data
3. **Structure or Shape** of Data
4. **Activities** that will be done on the Data

![AWS Database Characteristics](https://res.cloudinary.com/dbzzslryr/image/upload/v1610988705/aws_databases/database_characteristics.jpg "AWS Database Characteristics")

Now that we have an idea of the criteria required in selecting the various databases, let us dive into each of these databases. All databases in AWS are known to have the following properties 
fully managed by AWS
scalable that is increase and decrease based on demand 
highly available that is the databases are guaranteed to be always up

# Relation Databases 

## Amazon Relational Database Service(RDS)

![Amazon RDS](https://res.cloudinary.com/dbzzslryr/image/upload/v1610989754/aws_databases/amazon_rds.png "Amazon RDS")

[source](https://www.drilling-aws.de/amazon-rds-preise/)

Amazon RDS is not a database itself instead it is used to set up, operate, and scale relational databases in the cloud. It helps us in provisioning  Amazon Aurora, PostgreSQL, MySQL, MariaDB, Oracle Database, and SQL Server. It is like an administrator for these databases.  It automates failover, backups, restore, disaster recovery, access management, encryption, security, monitoring, and performance optimization.  It has two major backup solutions which are automated backups and manual snapshots. It has automatic failover protection and maximum of 5 replicas. Its replicas can be multi-availability zone replica, cross-region replicas, and read replica. But the resources aren't replicated across AWS Regions by default expect you set it specifically.


#### When to use Amazon Relational Database Service(RDS)
* If you need to use any of these six databases Amazon Aurora, PostgreSQL, MySQL, MariaDB, Oracle Database, and SQL Server.

### Official Resources 
* [Amazon Relational Database Services(RDS)](https://aws.amazon.com/rds/)
* [Amazon RDS Documentation](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/Welcome.html) 
* [Amazon RDS Blog](https://aws.amazon.com/blogs/database/category/database/amazon-rds/)


### Other Resources 
* [AWS Certified Solutions Architect - Associate 2020 (6:23:16 - 7:00:11)](https://www.youtube.com/watch?v=Ia-UEYYR44s)

* [Amazon Relational Database Service (Amazon RDS)](https://www.youtube.com/watch?v=igRfulrrYCo) by Vlad Vlasceanu 

* [Amazon Relational Database Service (RDS) (DAT302)](https://www.youtube.com/watch?v=TJxC-B9Q9tQ) by Brain Welcker

* [Amazon RDS](https://docs.datadoghq.com/integrations/amazon_rds/?tab=standard)

## Amazon Aurora

Amazon Aurora has  MySQL and PostgreSQL compatibility, it is five times faster than standard MySQL and three times faster than standard PostgreSQL database. Amazon Aurora is 90% cheaper than standard MySQL and PostgreSQL databases.  It has a maximum size of 128 TB. Amazon Aurora defines a scaling policy of maximum of 15 Aurora Replicas.  Aurora Backup and Failover are automatic. Amazon Aurora supports cross-region replication. Aurora MySQL DB Cluster and PostgreSQL are created using the Amazon Relation Database Service console.
Aurora Serverless gives aurora the ability to automatically scale up, scale down, start-up, and shut down(auto-scaling). Aurora Serverless is best used when building an application that is not frequently used, building a new application, building an application with varying and unpredictable workloads.


![Parallel Query for Amazon Aurora](https://res.cloudinary.com/dbzzslryr/image/upload/v1611030224/aws_databases/aurora_model.png " Parallel Query for Amazon Aurora")

[Parallel Query for Amazon Aurora - source](https://aws.amazon.com/blogs/aws/new-parallel-query-for-amazon-aurora/)

### Pricing
[Amazon Aurora Pricing](https://aws.amazon.com/rds/aurora/pricing/) is based on either we select the MySQL edition or the PostgreSQL edition. 
Aurora Serverless is charged based on Aurora Capacity Unit(ACU)

### Official Resources 
* [Amazon Aurora](https://aws.amazon.com/rds/aurora/) 
* [Amazon Aurora Documentation](https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/)
* [Amazon Aurora Blog](https://aws.amazon.com/blogs/database/category/database/amazon-aurora/)

### Other Resources 
* [Amazon Aurora Introduction](https://www.youtube.com/watch?v=ZCt3ctVfGIk)
* [AWS re:Invent 2019: [REPEAT] Amazon Aurora storage demystified: How it all works (DAT309-R)](https://www.youtube.com/watch?v=uaQEGLKtw54) by Murali Brahmadesa  and Tobias Ternström
* [Amazon Aurora Global Database Deep Dive](https://www.youtube.com/watch?v=1vFg1z-2E7Y) by Aditya Samant
* [AWS Certified Solutions Architect - Associate 2020 (7:02:14 - 7:06:56)](https://www.youtube.com/watch?v=Ia-UEYYR44s) 
* [Amazon Aurora ascendant: How we designed a cloud-native relational database](https://www.allthingsdistributed.com/2019/03/Amazon-Aurora-design-cloud-native-relational-database.html)

# Data Warehousing 
## Amazon Redshift  

Amazon Redshift is columnar storage used for data warehousing, it is used to analyze and get insight from large data quickly by executing complex queries on them.  These data are usually at rest and historical data. It contains a cluster of nodes, it could be in a single node mode or in a multi-node mode. There are two types of nodes in Amazon Redshift, namely leader node and compute node. The leader node stores SQL endpoints, metadata, and coordinates parallel SQL processing. Compute nodes stores the data, and execute the queries. Amazon Redshift stores data on a single Availability Zone. Amazon Redshift spectrum is used to query Amazon Simple Storage Service(Amazon S3) directly. [Amazon Redshift federated queries](https://docs.aws.amazon.com/redshift/latest/dg/federated-overview.html) enables us to query and analyze live data across databases, data warehouses, and data lakes. 

### When to use Amazon Redshift
*For Online Analytical Processing
* When you need to run queries across multiple data sources. For instance, we can copy data from different storages like Amazon EMR and Amazon S3 into Amazon Redshift. 
* Amazon Redshift is suitable for generating reports for business intelligence

### Pricing 
Amazon Redshift pricing(https://aws.amazon.com/redshift/pricing/) basic price for Amazon Redshift starts from $0.25 per hour. There are several other capabilities that can influence the price like Amazon Redshift Spectrum pricing, Concurrency Scaling pricing, Redshift managed pricing, and Redshift ML pricing.

### Official Resources 
* Amazon Redshift (https://aws.amazon.com/redshift/)
* Amazon Redshift Documentation (https://docs.aws.amazon.com/redshift/latest/dg/welcome.html) 
* Amazon Redshift Blog (https://aws.amazon.com/blogs/big-data/category/database/amazon-redshift/)

### Other Resources 

* [AWS re:Invent 2017: Best Practices for Data Warehousing with Amazon Redshift & Redsh (ABD304)](https://www.youtube.com/watch?v=Q_K3qH5OYaM) by Tony Gibbs
* [Getting Started with Amazon Redshift - AWS Online Tech Talks](https://www.youtube.com/watch?v=dfo4J5ZhlKI) by Greg Khairallah  and Harshida Patel
* [Amazon Redshift Tutorial /| Amazon Redshift Architecture /| AWS Tutorial For Beginners /| Simplilearn](https://www.youtube.com/watch?v=7bfOllAyxlg)
* [Amazon Redshift Tutorial /| AWS Tutorial for Beginners /| AWS Certification Training /| Edureka](https://www.youtube.com/watch?v=fc5WPKnbam8)
* [AWS Certified Solutions Architect - Associate 2020 (7:07:58)](https://www.youtube.com/watch?v=Ia-UEYYR44s)
* [What is Amazon Redshift?](https://www.sumologic.com/blog/what-is-amazon-redshift/) By Kevin Goldberg



