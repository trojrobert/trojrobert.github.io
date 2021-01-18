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

## Relation Databases 

### Amazon Relational Database Service(RDS)

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
