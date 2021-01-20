---
date: 2021-01-18 16:07:17
layout: post
title: "Selecting the right database in Amazon Web Service(AWS)"
subtitle:
description: This article is a documentation of what I learned and the resources I used in understanding the various databases in AWS and how to decide when to use them. 
image: https://res.cloudinary.com/dbzzslryr/image/upload/v1611072337/aws_databases/aws_databases.png
optimized_image: https://res.cloudinary.com/dbzzslryr/image/upload/v1611072337/aws_databases/aws_databases.png
category: cloud
tags:
author:
paginate: false
---

Deciding on the database to use for our application or workload can be very tricky. Since I join AWS Community Builder, I spend a least 1 hour every day exploring AWS services based on use case. Amazon Web Service(AWS) provides several options for Databases, we can be confused on the right one to choose.  This article is a documentation of what I learned and the resources I used in understanding the various databases in AWS and how to decide when to use them. I hope it will be of value to you. I will like to have feedback on what you think I should add or remove or improve on as I continue exploring AWS and other cloud services.

There are a lot of criteria the could help us in selecting the right database in AWS, to make it easier for us, we summarize it into the following 4 criteria 
1. **Type** of Data
2. **Size** of Data
3. **Structure or Shape** of Data
4. **Activities** that will be done on the Data

Now that we have an idea of the criteria required in selecting the database, let us dive into each of these databases. All databases in AWS are known to have the following properties 
* fully managed by AWS
* scalable that is increase and decrease based on demand 
* highly available that is the databases are guaranteed to be always up


# Relation Databases 

## Amazon Relational Database Service(RDS)

![Amazon RDS](https://res.cloudinary.com/dbzzslryr/image/upload/v1610989754/aws_databases/amazon_rds.png "Amazon RDS")

[source](https://www.drilling-aws.de/amazon-rds-preise/)

Amazon RDS is not a database itself instead it is used to set up, operate, and scale relational databases in the cloud. It enables us to provisioning  Amazon Aurora, PostgreSQL, MySQL, MariaDB, Oracle Database, and SQL Server. It is like an administrator for these databases. It automates failover, backups, restore, disaster recovery, access management, encryption, security, monitoring, and performance optimization.  It has two major backup solutions which are automated backups and manual snapshots. It has a maximum of 5 replicas. Its replicas can be multi-availability zone replica, cross-region replicas, and read replica. But the resources aren't replicated across AWS Regions by default expect you set it specifically.


#### When to use Amazon Relational Database Service(RDS)
If we need to use any of these six databases Amazon Aurora, PostgreSQL, MySQL, MariaDB, Oracle Database, and SQL Server.

### Pricing 
[Amazon Relational Database Services(RDS) pricing](https://aws.amazon.com/rds/pricing/) depends on either we are using it On-Demand or Reserved Instances.

### Official Resources 
[Amazon Relational Database Services(RDS)](https://aws.amazon.com/rds/)

[Amazon RDS Documentation](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/Welcome.html) 

[Amazon RDS Blog](https://aws.amazon.com/blogs/database/category/database/amazon-rds/)


### Other Resources 

[AWS Certified Solutions Architect - Associate 2020 (6:23:16 - 7:00:11)](https://www.youtube.com/watch?v=Ia-UEYYR44s)


[Amazon Relational Database Service (Amazon RDS)](https://www.youtube.com/watch?v=igRfulrrYCo) by Vlad Vlasceanu 


[Amazon Relational Database Service (RDS) (DAT302)](https://www.youtube.com/watch?v=TJxC-B9Q9tQ) by Brain Welcker


[Amazon RDS](https://docs.datadoghq.com/integrations/amazon_rds/?tab=standard)


## Amazon Aurora

Amazon Aurora has  MySQL and PostgreSQL compatibility, it is five times faster than standard MySQL and three times faster than standard PostgreSQL database. Amazon Aurora is 90% cheaper than standard MySQL and PostgreSQL databases.  It has a maximum size of 128 TB. Amazon Aurora defines a scaling policy of a maximum of 15 Aurora Replicas.  Aurora Backup and Failover are automatic. Amazon Aurora supports cross-region replication. Aurora MySQL DB Cluster and PostgreSQL are created using the Amazon Relation Database Service console.
Aurora Serverless gives Amazon Aurora the ability to automatically scale up, scale down, start-up, and shut down(auto-scaling). Aurora Serverless is best used when building an application that is not frequently used, building a new application, building an application with varying and unpredictable workloads.


![Parallel Query for Amazon Aurora](https://res.cloudinary.com/dbzzslryr/image/upload/v1611030224/aws_databases/aurora_model.png " Parallel Query for Amazon Aurora")

[Parallel Query for Amazon Aurora - source](https://aws.amazon.com/blogs/aws/new-parallel-query-for-amazon-aurora/)

### Pricing
[Amazon Aurora Pricing](https://aws.amazon.com/rds/aurora/pricing/) is based on either we select the MySQL edition or the PostgreSQL edition. 
Aurora Serverless is charged based on Aurora Capacity Unit(ACU)

### Official Resources 
[Amazon Aurora](https://aws.amazon.com/rds/aurora/) 

[Amazon Aurora Documentation](https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/)

[Amazon Aurora Blog](https://aws.amazon.com/blogs/database/category/database/amazon-aurora/)

### Other Resources 
[Amazon Aurora Introduction](https://www.youtube.com/watch?v=ZCt3ctVfGIk)

[AWS re:Invent 2019: [REPEAT] Amazon Aurora storage demystified: How it all works (DAT309-R)](https://www.youtube.com/watch?v=uaQEGLKtw54) by Murali Brahmadesa  and Tobias Ternström

[Amazon Aurora Global Database Deep Dive](https://www.youtube.com/watch?v=1vFg1z-2E7Y) by Aditya Samant

[AWS Certified Solutions Architect - Associate 2020 (7:02:14 - 7:06:56)](https://www.youtube.com/watch?v=Ia-UEYYR44s) 

[Amazon Aurora ascendant: How we designed a cloud-native relational database](https://www.allthingsdistributed.com/2019/03/Amazon-Aurora-design-cloud-native-relational-database.html)

# Data Warehousing 
## Amazon Redshift  

Amazon Redshift is columnar storage used for data warehousing, it is used to analyze and get insight from large data quickly by executing complex queries on them.  These data are usually at rest and historical data. It contains a cluster of nodes, it could be in single-node mode or multi-node mode. There are two types of nodes in Amazon Redshift, namely leader node and compute node. The leader node stores SQL endpoints, metadata, and coordinates parallel SQL processing. Compute nodes stores the data, and execute the queries. Amazon Redshift stores data on a single Availability Zone. Amazon Redshift spectrum is used to query Amazon Simple Storage Service(Amazon S3) directly. [Amazon Redshift federated queries](https://docs.aws.amazon.com/redshift/latest/dg/federated-overview.html) enables us to query and analyze live data across databases, data warehouses, and data lakes. 

![Amazon Redshift Architecture](https://res.cloudinary.com/dbzzslryr/image/upload/v1611030754/aws_databases/amazon_redshift_model.png "Amazon Redshift Architecture")

[Amazon Redshift Architecture - source](https://docs.aws.amazon.com/redshift/latest/dg/c_high_level_system_architecture.html)

### When to use Amazon Redshift
for Online Analytical Processing

if we need to run queries across multiple data sources. For instance, we can copy data from different storages like Amazon EMR and Amazon S3 into Amazon Redshift. 

Amazon Redshift is suitable for generating reports for business intelligence

### Pricing 
[Amazon Redshiftp pricing](https://aws.amazon.com/redshift/pricing/) - the basic price for Amazon Redshift starts from $0.25 per hour. There are several other features that can influence the price such as Amazon Redshift Spectrum pricing, Concurrency Scaling pricing, Redshift managed pricing, and Redshift ML pricing.

![Amazon Redshift Architecture](https://res.cloudinary.com/dbzzslryr/image/upload/v1611033488/aws_databases/Product-Page-Diagram_Redshift.png "Amazon Redshift Architecture")

[source](https://aws.amazon.com/de/redshift/?whats-new-cards.sort-by=item.additionalFields.postDateTime&whats-new-cards.sort-order=desc)

### Official Resources 
[Amazon Redshift](https://aws.amazon.com/redshift/)

[Amazon Redshift Documentation](https://docs.aws.amazon.com/redshift/latest/dg/welcome.html) 

[Amazon Redshift Blog](https://aws.amazon.com/blogs/big-data/category/database/amazon-redshift/)

### Other Resources 

[AWS re:Invent 2017: Best Practices for Data Warehousing with Amazon Redshift & Redsh (ABD304)](https://www.youtube.com/watch?v=Q_K3qH5OYaM) by Tony Gibbs

[Getting Started with Amazon Redshift - AWS Online Tech Talks](https://www.youtube.com/watch?v=dfo4J5ZhlKI) by Greg Khairallah  and Harshida Patel

[Amazon Redshift Tutorial \| Amazon Redshift Architecture \| AWS Tutorial For Beginners \| Simplilearn](https://www.youtube.com/watch?v=7bfOllAyxlg)

[Amazon Redshift Tutorial \| AWS Tutorial for Beginners \| AWS Certification Training \| Edureka](https://www.youtube.com/watch?v=fc5WPKnbam8)

[AWS Certified Solutions Architect - Associate 2020 (7:07:58)](https://www.youtube.com/watch?v=Ia-UEYYR44s)

[What is Amazon Redshift?](https://www.sumologic.com/blog/what-is-amazon-redshift/) By Kevin Goldberg

# NoSQL - Key/Value
## DynamoDB

DynamoDB is a NoSQL database, key/value, and document database. That is it support document and key/value structures. DynamoDB's major components are tables, items, attributes, keys, and values. A table is a collection of items and an item is a collection of attributes. Items are similar to rows while attributes are similar to columns in a traditional database. A key is used to identify attributes and value is the data itself. The Major API components in DynamoDB are control plane, data plane, DynamoDB streams, and transactions. On-Demand and Provisioned Mode are the read/write capacity modes in DynamoDB. Amazon DynamoDB provides us the ability to specific our Provisioned capacity based on Read Capacity Units(RCU) and Write Capacity Units(WCU). Amazon DynamoDB creates partitions based on size, Read Capacity Units and Write Capacity Units. The criteria required for partitioning are size of 10GB, RCU of 3000, and WCU of 1000.   Encrypt data at rest (that is inactive data), data that is not moving from one device to another or from one network to another.  DynamoDB has a Point in time recovery feature that is we can restore your data to any point in time. Amazon DynamoDB Accelerator(DAX) enables us to manage write through cache on DynamoDB, it reduces response time from milliseconds to microseconds. Amazon DynamoDB uses SSD storage and stores its data across 3 different availability zone. 

![Amazon DynamoDB Key/Value](https://res.cloudinary.com/dbzzslryr/image/upload/v1611062740/aws_databases/dynamoDB_key_value.png "Amazon DynamoDB Key/Value")

[source](https://www.infoq.com/articles/mars-rover-application-DynamoDB/)

### When to use Amazon DynamoDB

for Online Transaction Processing(OTP).

to store real-time data from an IoT device.

to store activities and events on a web application such as clicks. 

to store items in a Web application like user profile, user events used by advertising, gaming, retail, finance, and media companies.

for Data that requires high request rate(millions of requests per seconds).

it is best used in situations that require high consistency.

### Pricing
[Amazon DynamoDB pricing](https://aws.amazon.com/dynamodb/pricing/) depends on on-demand capacity mode and provisioned capacity mode.

### Hands-On 
[Creating Tables and Loading Data](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/SampleData.html)

### Sample Code

[Create a ToDo Web App Storing your data in  Amazon DynamoDB](https://github.com/aws-samples/lambda-refarch-webapp)

### Official Resources 

[Amazon DynamoDB](https://aws.amazon.com/dynamodb/)

[Amazon DynamoDB Documentation](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/Introduction.html)

[Amazon DynamoDB Blog](https://aws.amazon.com/blogs/database/category/database/amazon-dynamodb/)

### Other Resources 
[AWS DynamoDB Tutorial \| AWS Services \| AWS Tutorial For Beginners \| AWS Training Video \| Simplilearn](https://www.youtube.com/watch?v=2mVR_Qgx_RU&t=372s)

[AWS Certified Developer - Associate 2020 (5:05:21) ](https://www.youtube.com/watch?v=RrKRN9zRBWs&t=18321s)

[AWS re:Invent 2018: Amazon DynamoDB Under the Hood: How We Built a Hyper-Scale Database](https://www.youtube.com/watch?v=yvBR71D0nAQ) by Jaso Sorenson

[AWS re:Invent 2018: Amazon DynamoDB Deep Dive: Advanced Design Patterns for DynamoDB (DAT401)](https://www.youtube.com/watch?v=HaEPXoXVf2k&t=5s) by Rick Houlihan

[Building a Mars Rover Application with DynamoDB](https://www.infoq.com/articles/mars-rover-application-DynamoDB/)

# Document Database
## Amazon DocumentDB
This is a document database that supports MongoDB. It has the capability to easily store, query, and index JSON data. It has about 15 read replicas and scales vertically with very low impact. It has flexible schema and Ad hoc query capability. It is easy to index and can be used for operational and analytics workloads.

![Amazon DocumentDB](https://res.cloudinary.com/dbzzslryr/image/upload/v1611068153/aws_databases/amazon_documentDB.png "Amazon DocumentDB")

### Pricing
[Amazon DocumentDB pricing](https://aws.amazon.com/documentdb/pricing/) is based on On-demand instances, database I/O, database storage and backup storage.

### When to use Amazon DocumentDB

it is Amazon version of MongoDB, it is used when you need to run MongoDB at scale

best  for Profile management, Content, and catalog management.

### Official Resources

[Amazon DocumentDB](https://aws.amazon.com/documentdb/)

[Amazon DocumentDB Documentation](https://docs.aws.amazon.com/documentdb/latest/developerguide/what-is.html)

[Amazon DocumentDB Blog](https://aws.amazon.com/blogs/database/category/database/amazon-document-db/)

### Other Resources 

[AWS re:Invent 2019: Amazon DocumentDB deep dive (DAT326)](https://www.youtube.com/watch?v=D3_hWN9C9iE) by Joseph Idziorek and Antra Grover

[Building with Amazon DocumentDB (with MongoDB compatibility) - AWS Virtual Workshop](https://www.youtube.com/watch?v=Ild9ay9U_vY) by 
Meet Bhagdev

## DynamoDB vs AWS DocumentDB vs MongoDB
[MongoDB vs. DocumentDB: Which Is Right for You?](https://getstream.io/blog/mongodb-vs-documentdb-which-is-right-for-you/)

[Difference between AWS DynamoDB vs AWS DocumentDB vs MongoDB?](https://medium.com/@caseygibson_42696/difference-between-aws-dynamodb-vs-aws-documentdb-vs-mongodb-9cb026a94767)

# Graph Database
## Amazon Neptune 
Amazon Neptune is a graph database, it works with highly connected datasets. It checks for relations or similarity in data. For instance similarity between the movies a user watches on Netflix. It components are node(data entities), edges(relationships) and properties. Amazon Neptune support property graph like open-source Apache TinkerPop Germlin and Resource Description Framework(RDF)  SPARQL. Amazon Neptune replicates data 6 times across 3 Availability Zones. Amazon Neptune Streams can be used to capture changes in a graph.

![Knowledge Graph](https://res.cloudinary.com/dbzzslryr/image/upload/v1611070119/aws_databases/knowledge-graph.png "Knowledge Graph")

### Pricing
[Amazon Neptune pricing](https://aws.amazon.com/neptune/pricing/) is influenced by On-demand instances, database I/O, database storage, backup storage and data transfer.

### When to use Amazon Neptune 
Amazon Neptune is best used when we have relationships in the data.

for recommendation engines, fraud detection, and drug discovery.

for knowledge base applications such as Wikidata.

for identity graphs to show unified view of customers and prospects based on their interactions with a product or a website.

for social Networking applications to store user profiles and interactions.


![Recommendation Relationships](https://res.cloudinary.com/dbzzslryr/image/upload/v1611070132/aws_databases/recommendation-relationships.png "Recommendation Relationships")


### Official Resources 
[Amazon Neptune](https://aws.amazon.com/neptune/)

[Amazon Neptune Documentation](https://docs.aws.amazon.com/neptune/latest/userguide/intro.html)

[Amazon Neptune Blog](https://aws.amazon.com/blogs/database/category/database/amazon-neptune/)

### Other Resources 
[AWS re:Invent 2019: Deep dive on Amazon Neptune (DAT361)](https://www.youtube.com/watch?v=dSqNAlYAAoQ) by Bradley Bebee, Karthik Bharathy, and Ora Lassila

[Nike: A Social Graph at Scale with Amazon Neptune](https://www.youtube.com/watch?v=ZCj2wuKBBu4)

[Homesite: Event-Driven Data Analytics Platform Using Amazon Neptune](https://www.youtube.com/watch?v=j9OZ-7aCAyA)

[AWS on Air 2020: AWS What’s Next ft. Amazon Neptune ML](https://www.youtube.com/watch?v=K5Dr_Jdculg)


# In memory 
## Amazon ElastiCache 

Amazon ElastiCache use to manage in-memory caching. Caching is storing data in a temporary storage area. This data is stored on the RAM which is volatile, that is the data can get lost easily and can be accessed fast. It stores frequently accessed data to improve performance, this helps to avoid application latency and throughput. It caches data from the database which is different from CloudFront(Content Delivery Network). Amazon ElastiCache stores important data in memory. Amazon Cloudfront stores static files, for example, HTML, audio, video, media files required by a web app. Amazon ElastiCache access only resources in the same VPC. 

![ElatiCache Redis vs Memcached](https://res.cloudinary.com/dbzzslryr/image/upload/v1611073857/aws_databases/elasticache_redis_memcached.png "ElatiCache Redis vs Memcached")
[source](https://www.youtube.com/watch?v=v0GfpL5jfns)

Amazon ElastiCache has two engines
1. Amazon ElastiCache for Redis
2. Amazon ElastiCache for Memcached. 

### Pricing 
[Amazon ElastiCache pricing](https://aws.amazon.com/elasticache/pricing/) is based on the node types, backup storage, and data transfer.

### When to use Amazon ElastiCache
it is best used when you need microseconds latency, key-based queries, and specialized data structures.

for situations like leader boards and real-time caching

if the data is on every page load or every request. 

### Official Resources 
[Amazon ElastiCache](https://aws.amazon.com/elasticache/)

[Amazon ElastiCache for Redis Documentation](https://docs.aws.amazon.com/AmazonElastiCache/latest/red-ug/WhatIs.html)

[Amazon ElastiCache for Memcached Documentation](https://docs.aws.amazon.com/AmazonElastiCache/latest/mem-ug/WhatIs.html)

[Amazon ElastiCacke Blog](https://aws.amazon.com/blogs/database/category/database/amazon-elasticache/)

### Other Resources 

[AWS re:Invent 2019: Supercharge your real-time apps with Amazon ElastiCache (DAT208)](https://www.youtube.com/watch?v=v0GfpL5jfns) by Pratibha Suryadevara

[AWS re:Invent 2018: ElastiCache Deep Dive: Design Patterns for In-Memory Data Stores (DAT302-R1)](https://www.youtube.com/watch?v=QxcB53mL_oA) byMichael Labib

[AWS Certified Solutions Architect - Associate 2020(8:38:40)](https://www.youtube.com/watch?v=Ia-UEYYR44s&t=26691s) 



# Time series 
## Amazon Timestream 
Amazon Timestream is a serverless time-series database for IoT and operational applications. Time series data are recorded over a period of time such as stock data and temperatures of a device. Amazon Timestream can be used to store and analyze trillions of events per day up to 1,000 times faster and at as little as 1/10th the cost of relational databases. One major advantage of  Amazon Timestream database is its capability to move historical data to low-cost storage(magnetic store) but retain recent data(hot data) in-memory(SSD store). Queries can be run on both historical data and recent data. In addition, Amazon Timestream has a built-in time-series analytics function such as smoothing, approximation, and interpolation which helps in detecting patterns in data. Major concepts on Amazon Timestream are record, dimension, measure, timestamp, table, and Database. Records cannot be deleted or updated.

![Amazon Timestream](https://res.cloudinary.com/dbzzslryr/image/upload/v1611088320/aws_databases/Amazon-Timestream_IoT.png "Amazon Timestream")

### Pricing 
[Amazon Timestream pricing](https://aws.amazon.com/timestream/pricing/) is based on writes, SSD store, magnetic store, data transfer and queries.

### When to use Amazon Timestream 
for time series data from IoT devices 

collecting and analysing operational metrics 

analytical application 

### Sample code 
[Getting started with Amazon Timestream with Python](https://github.com/awslabs/amazon-timestream-tools/blob/master/sample_apps/python/README.md)

### Official Resources 

[Amazon TImestream](https://aws.amazon.com/timestream/)

[Amazon Timestream Documentation](https://docs.aws.amazon.com/timestream/latest/developerguide/what-is-timestream.html)

[Amazon Timestream Blog](https://aws.amazon.com/blogs/database/category/database/amazon-timestream/)


### Other Resources 
[Getting Started with Amazon Timestream](https://www.youtube.com/watch?v=8RHFPNReylI) by Tony Gibbs

[Deep Dive on Amazon Timestream](https://www.youtube.com/watch?v=39ijv_pfWSQ) by Tony Gibbs


# Ledger Database

## Amazon Quantum Ledger Database(QLDB)

Amazon QLDB is a fully managed ledger database that provides a transparent, immutable, and cryptographically verifiable transaction log owned by a central trusted authority.  It is used to track data changes in applications. It can be used for storing audit logs. It uses a SQL like language called PartiQL. It is immutable, transparent, cryptographically verifiable, and serverless. 

![Amazon QLDB](https://res.cloudinary.com/dbzzslryr/image/upload/v1611092933/aws_databases/AWS-Quantum.png "Amazon QLDB")

### Pricing 
[Amazon Quantum Ledger Database(QLDB) pricing](https://aws.amazon.com/qldb/pricing/) is based on the data transfer, data storage and I/O.

### When to use Amazon QLDB
best suited for economic and financial record

for application data

used in finance for tracking credit and debit transactions 

for HR systems to track employee payroll, bonus, benefits and other details 

for manufacturing to track product manufacturing history 


### Official Resources 
[Amazon Quantum Ledger Database(QLDB)](https://aws.amazon.com/qldb/)

[Amazon Quantum Ledger Database Documentation](https://docs.aws.amazon.com/qldb/latest/developerguide/what-is.html)

[Amazon Quantum Ledger Database Blog](https://aws.amazon.com/blogs/database/tag/amazon-qldb/) 


### Other Resources 
[AWS re:Invent 2019: Amazon QLDB: An engineer’s deep dive on why this is a game changer (DAT380)](https://www.youtube.com/watch?v=ZfYDl4kaVCo) by Andrew Certain 

[Building System of Record Applications with Amazon QLDB - AWS Online Tech Talks](https://www.youtube.com/watch?v=XGeCNr8eOiA) by Philip Simko and Michael Labib

# Other resources on selecting the right database

[AWS re:Invent 2017: [REPEAT] Which Database to Use When? (DAT310-R)](https://www.youtube.com/watch?v=KWOSGVtHWqA) by Tony Petrossian and Ian Meyers

[Selecting the Right Database for Your Application](https://www.youtube.com/watch?v=6K0Sds9Y2N0) by Joseph Idziorek

[Choosing The Right Database](https://www.youtube.com/watch?v=Rk0h7Jd1WGQ) by Randall Hunt


Whoa, so many databases and terminologies. I am sure you need a break. I hope you were able to understand the different databases in AWS, when to use them, and resources that will give you a deep dive. 


