---
date: 2021-01-03 21:31:41
layout: post
title: "Serverless in AWS and Azure: Amazon Lambda, Amazon Fargate, and Azure Function"
subtitle:
description:
image:
optimized_image:
category:
tags:
author:
paginate: false
---

Serverless is building and running applications without servers, that is without the burden of managing infrastructure.

Use cases 
* Application for continuous delivery pipeline
* Data  processing 
* Real time stream processing 
* Real time file Processing  for instance run a code when new data is received 
* Data preprocessing and model serving in machine learning 

## Amazon Lambda

Amazon Lambda runs code without servers and clusters. In other words, you don’t need to provision infrastructure. Amazon Lambda also has a code editor where you can write, test, and view execution results. Your code should be uploaded as a zip file or as a container image, the resources required are automatically allocated to it. This code could be run based on a trigger for instance change in data in S3 bucket, response to HTTP request using Amazon API Gateway.

 S3, DynamoDB, Kinesis, SNS, CloudWatch, Amazon API Gateway, AWS IoT Core, Amazon SNS, Amazon SAM

### Code Samples

[Use AWS Lambda to build serverless backend for an iOS mobile application](https://github.com/aws-samples/lambda-refarch-mobilebackend)

[Humidity sensor application to monitor humidity under a set threshold with AWS Lambda](https://github.com/aws-samples/lambda-refarch-iotbackend)

[To-Do App](https://github.com/aws-samples/lambda-refarch-webapp)

[Real-time data processing with Amazon Kinesis and AWS Lambda](https://github.com/aws-samples/lambda-refarch-streamprocessing)

[Processing Interview Markdown files](https://github.com/aws-samples/lambda-refarch-fileprocessing)


### Hands-On 
[Using AWS Lambda with the Mobile SDK for Android](https://docs.aws.amazon.com/lambda/latest/dg/with-android-example.html)

