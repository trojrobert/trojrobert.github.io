---
date: 2020-12-26 10:38:36
layout: post
title: "Azure and Amazon Data Stream Analytics and Processing: Amazon Kinesis, Azure Stream Analytics and  Azure Event Hub"
subtitle:
description:This article gives a brief description and use cases of the data stream analytics services in AWS and Azure. It also contains resources about their prices, components, hands-on examples, code samples, and comparison.
image:https://res.cloudinary.com/dbzzslryr/image/upload/v1608985915/stream%20analytics/streams.png
optimized_image:https://res.cloudinary.com/dbzzslryr/image/upload/v1608985915/stream%20analytics/streams.png
category: Cloud
tags:
author:
paginate: false
---

Data Stream Analytics also called event stream processing or real-time analytics is the processing and analysis of real-time data. 

This article gives a brief description and use cases of the data stream analytics services in AWS and Azure. It also contains resources about their prices, components, hands-on examples, code samples, and comparison.

### Use Cases for Steam Analytics 

* Anomaly detection in credit card transactions
* Anomaly detection (fraud/outliers)
* Application logging
* Analytics pipelines, such as clickstreams
* Live dashboarding
* Archiving data
* Transaction processing
* User telemetry processing
* Device telemetry streaming
* Alert system 
* Click steam Analytics
* Analyze streaming social media data


## Amazon Kinesis 
Amazon Kinesis is an Amazon Web Service for easy and scalable collection, processing, and analysis of video and data streams in real-time. It can also be used for batch processing. It is can be used for data ingestion for machine learning, analytics, and other applications.

![Amazon Kinesis Data Stream Architecture](https://res.cloudinary.com/dbzzslryr/image/upload/v1608984421/stream%20analytics/kinesis_architecture.png "Amazon Kinesis Data Stream Architecture")
Source - https://docs.aws.amazon.com/streams/latest/dev/key-concepts.html

**Other Amazon Web Services used with Amazon Kinesis** : Kinesis Video Streams, Kinesis Data Streams, Kinesis Data Firehose, Kinesis Data Analytics, Amazon EC2, Amazon S3, Amazon Redshift, DynamoDB, Amazon EMR, Amazon Elasticsearch Service, Amazon Lambda. 

### Types of Amazon Kinesis
[Kinesis Video Streams](https://docs.aws.amazon.com/kinesisvideostreams/latest/dg/what-is-kinesis-video.html) - capture, process and store video streams.
[Kinesis Data Streams](https://docs.aws.amazon.com/streams/latest/dev/introduction.html)- capture, process and store data streams. 
[Kinesis Data Firehose](https://docs.aws.amazon.com/firehose/latest/dev/what-is-this-service.html) - capture, transform, and load data streams into AWS data stores.
[Kinesis Data Analytics](https://docs.aws.amazon.com/kinesisanalytics/latest/dev/what-is.html) - process data streams in real time with SQL or Apache Flink.   



### Pricing
[Amazon Kinesis Data Streams Pricing](https://aws.amazon.com/kinesis/data-streams/pricing/) is based on Shared Hour and PUT Payload Unit.
[Amazon Kinesis Video Streams Pricing](https://aws.amazon.com/kinesis/video-streams/pricing/) is volume of data you ingest, store, and consume in your video streams.
[Amazon Kinesis Data Firehose Pricing](https://aws.amazon.com/kinesis/data-firehose/pricing/) is based on the volume of data ingested into Kinesis Data Firehose.
[Amazon Kinesis Data Analytics Pricing](https://aws.amazon.com/kinesis/data-analytics/pricing/) is based on the average number of Kinesis Processing Units (or KPUs) used to run your stream processing application which is charged per hour.


### Hand-On Examples
[Building a log Analytics Solution](https://aws.amazon.com/getting-started/hands-on/build-log-analytics-solution/)
* Set up a kinesis Agent
* Create an end to end data delivery stream using kinesis Data Firehose 
* Process incoming data using SQL queries using Amazon Kinesis Data Analytics 
* Load processed data from Kinesis Data Analytics to Amazon Elasticsearch Service
* Analyze and visualize the processed data using Kibana.

[Real-Time Hotspot Detection in Amazon Kinesis Analytics](https://aws.amazon.com/blogs/aws/real-time-hotspot-detection-in-amazon-kinesis-analytics/)


### Code Examples 
[Generating streams of weather data](https://github.com/amazon-archives/aws-weathergen)
[Kinesis Data Generator](https://github.com/awslabs/amazon-kinesis-data-generator)

### Official Resources
[Amazon Kinesis](https://aws.amazon.com/kinesis/) 
[Amazon Kinesis Blog](https://aws.amazon.com/blogs/big-data/category/analytics/amazon-kinesis/)


### Other Resources 

[High Performance Data Streaming with Amazon Kinesis: Best Practices and Common Pitfalls(video)](https://www.youtube.com/watch?v=MELPeni0p04&ab_channel=AmazonWebServices)
[AWS Streaming Data Solution for Amazon Kinesis(article)](https://aws.amazon.com/solutions/implementations/aws-streaming-data-solution-for-amazon-kinesis/)
[Streaming Data Solutions on AWS with Amazon Kinesis(pdf)](https://d0.awsstatic.com/whitepapers/whitepaper-streaming-data-solutions-on-aws-with-amazon-kinesis.pdf)
[AWS Kinesis Tutorial for Beginners | Introduction to Amazon Kinesis | AWS Training | Edureka(video)](https://www.youtube.com/watch?v=rYbS5ihk_xg&ab_channel=edureka%21)


Good resources 
https://medium.com/faun/apache-kafka-vs-apache-kinesis-57a3d585ef78


