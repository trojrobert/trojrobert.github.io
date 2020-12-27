---
date: 2020-12-26 10:38:36
layout: post
title: "Azure and Amazon Data Stream Analytics and Processing: Amazon Kinesis, Azure Stream Analytics and  Azure Event Hub"
subtitle:
description: This article gives a brief description and use cases of the data stream analytics services in AWS and Azure. It also contains resources about their prices, components, hands-on examples, code samples, and comparison.
image: https://res.cloudinary.com/dbzzslryr/image/upload/v1608985915/stream%20analytics/data_streams.png
optimized_image: https://res.cloudinary.com/dbzzslryr/image/upload/v1608985915/stream%20analytics/data_streams.png
category: Cloud
tags:
author: John Robert
paginate: false
---

Data Stream Analytics also called event stream processing or real-time analytics is the processing and analysis of real-time data.These [streaming data](https://aws.amazon.com/streaming-data/#:~:text=Streaming%20data%20includes%20a%20wide,devices%20or%20instrumentation%20in%20data) could be transaction data from an e-commerce website, financial trading floors, telemetry from IoT devices and social media data.   

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


### Hand-On Tutorials 
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

["AWS Kinesis Tutorial for Beginners /| Introduction to Amazon Kinesis  AWS Training | Edureka(video)"](https://www.youtube.com/watch?v=rYbS5ihk_xg&ab_channel=edureka%21)

## Azure Event Hub
Event Hub is a real time ingestion service. The streamed data can be store in Blob storage, Data Lake and other storage. It can be connected to Azure Stream Analytics to analyze the data.Data can be sent to Event Hub, analysed with Azure Stream Analytics at real time, then visualized with Power BI. 

![Azure Event Hub](https://res.cloudinary.com/dbzzslryr/image/upload/v1608997849/stream%20analytics/event-hub-architecture.png "Azure Event Hub ")
Source - https://docs.microsoft.com/en-us/azure-stack/user/event-hubs-overview?view=azs-2008


**Other Azure services commonly used with Azure Event Hub** :- Azure Stream Analytics, Power BI, Azure blob storage, Azure event grid, Azure Function, Azure Synapse Analytics, Azure Event Gird

### Pricing
[Azure Event Hub Pricing](https://azure.microsoft.com/en-us/pricing/details/event-hubs/) is based on throughput unit, ingress events and capture. 

### Hands on Tutorials 
[Migrate captured Event Hubs data to Azure Synapse Analytics using Event Grid and Azure Functions](https://docs.microsoft.com/en-us/azure/event-hubs/store-captured-data-data-warehouse)
* Data sent to an Azure event hub is captured in an Azure blob storage.
* When the data capture is complete, an event is generated and sent to an Azure event grid.
* The event grid forwards this event data to an Azure function app.
* The function app uses the blob URL in the event data to retrieve the blob from the storage.
* The function app migrates the blob data to an Azure Synapse Analytics.

[Visualize data anomalies in real-time events sent to Azure Event Hubs](https://docs.microsoft.com/en-us/azure/event-hubs/event-hubs-tutorial-visualize-anomalies)

[Stream Twitter data into Azure Databricks using Event Hubs](https://docs.microsoft.com/en-us/azure/databricks/scenarios/databricks-stream-from-eventhubs)


### Code Samples 
[Azure Event Hubs samples](https://github.com/Azure/azure-event-hubs/tree/master/samples)

### Official Resources
[Event Hubs](https://azure.microsoft.com/en-us/services/event-hubs/)

[Azure Event Hubs documentation](https://docs.microsoft.com/en-us/azure/event-hubs/)

### Other Resources
[Azure Event Hub Tutorial | Big data message streaming service(video)](https://www.youtube.com/watch?v=Dc3P27BsK3E&t=537s&ab_channel=AdamMarczak-AzureforEveryone)

[Azure Event Hubs for Apache Kafka | Azure Friday(video)](https://www.youtube.com/watch?v=m3UEDhVYc-Q&t=509s&ab_channel=MicrosoftDeveloper)

[How to perform data ingestion with Azure Event Hubs | Azure Makers Series(video)](https://www.youtube.com/watch?v=45wgY-VSk9I&ab_channel=MicrosoftAzure)

[https://www.youtube.com/watch?v=DDDjFQSQyF4&ab_channel=dotNET(video)](https://www.youtube.com/watch?v=DDDjFQSQyF4&ab_channel=dotNET)


## Azure Stream Analytics 
Azure Stream Analytics is a serverless real time analytics service. It uses SQL which can be extensible with custom code and built in machine learning capabilities.

![Azure Stream Analytics](https://res.cloudinary.com/dbzzslryr/image/upload/v1608999419/stream%20analytics/stream-analytics-pipeline.png "Azure Stream Analytics ")
Source - https://docs.microsoft.com/en-us/azure/stream-analytics/stream-analytics-introduction

**Other Azure services commonly used with Azure Stream Analytics** :- Azure Event Hub, Power BI, Azure blob storage, Azure event grid, Azure Function, Azure Synapse Analytics

### Pricing 
[Azure Stream Anakytics Pricing](https://azure.microsoft.com/en-us/pricing/details/stream-analytics/) is based on the number of streaming Units Provisioned. A Streaming Unit represents the amount of memory and compute allocated to your resources.

### Hands on Tutorials 
[Analyze fraudulent call data with Stream Analytics and visualize results in Power BI dashboard](https://docs.microsoft.com/en-us/azure/stream-analytics/stream-analytics-real-time-fraud-detection)
* Create event hubs. 
* Start event generator application.
* Create Stream Analytics Job and configure job input using event Hub. 
* Visualize transformed data on Power BI. 

[Monitor GeoFences in real-time using Azure SQL and Stream Analytics](https://docs.microsoft.com/en-us/samples/azure-samples/azure-sql-db-serverless-geospatial-stream-analytics/azure-sql-db-serverless-geospatial-stream-analytics/)

### Code examples 
[Real-Time Serverless GeoSpatial Public Transportation GeoFencing Solution](https://github.com/Azure-Samples/azure-sql-db-serverless-geospatial)

### Official Resources
[Azure Stream Analytics documentation](https://docs.microsoft.com/en-us/azure/stream-analytics/)

[Azure Stream Analytics](https://azure.microsoft.com/en-us/services/stream-analytics/)


### Other Resources
[Azure Stream Analytics Tutorial \| Processing stream data with SQL(video)](https://www.youtube.com/watch?v=NbGmyjgY0pU&t=582s)

[Anomaly detection using machine learning in Azure Stream Analytics "|" Azure Friday(video)](https://www.youtube.com/watch?v=Ra8HhBLdzHE)

[Azure Stream Analytics(video)](https://www.youtube.com/watch?v=rrODKaB7XSY)

## Comparing Amazon Kinesis, Azure Event Hub and Azure Stream Analytics 
[Comparing Apache Kafka, Amazon Kinesis, Microsoft Event Hubs and Google Pub/Sub](https://blog.scottlogic.com/2018/04/17/comparing-big-data-messaging)

[A closer look at data streaming capabilities of Amazon Kinesis and Azure Event Hubs](https://christofer.lof.io/2018/03/17/aws-kinesis-and-azure-eventhubs.html)

[An Introduction to stream processing systems: Kafka, AWS Kinesis and Azure Event Hubs](https://blog.container-solutions.com/introduction-stream-processing-systems-kafka-aws-kinesis-azure-event-hubs)

[Apache Kafka VS AWS Kinesis](https://medium.com/faun/apache-kafka-vs-apache-kinesis-57a3d585ef78)


I hope you have been able to get an insight to stream analytics and services provided by AWS and Azure for processing stream data. 


