---
date: 2021-01-03 21:31:41
layout: Cloud
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
 
### Hands-On 
[Using AWS Lambda with the Mobile SDK for Android](https://docs.aws.amazon.com/lambda/latest/dg/with-android-example.html)

[Using AWS Lambda with Amazon S3](https://docs.aws.amazon.com/lambda/latest/dg/with-s3-example.html)

[Web application to request unicorn rides ride](https://aws.amazon.com/getting-started/hands-on/build-serverless-web-app-lambda-apigateway-s3-dynamodb-cognito/)

[Building Lambda functions with Python](https://docs.aws.amazon.com/lambda/latest/dg/lambda-python.html)

[Create a Lambda function with the console](https://docs.aws.amazon.com/lambda/latest/dg/getting-started-create-function.html#gettingstarted-images)


### Code Samples

[Use AWS Lambda to build serverless backend for an iOS mobile application](https://github.com/aws-samples/lambda-refarch-mobilebackend)

[Humidity sensor application to monitor humidity under a set threshold with AWS Lambda](https://github.com/aws-samples/lambda-refarch-iotbackend)

[To-Do App](https://github.com/aws-samples/lambda-refarch-webapp)

[Real-time data processing with Amazon Kinesis and AWS Lambda](https://github.com/aws-samples/lambda-refarch-streamprocessing)

[Processing Interview Markdown files](https://github.com/aws-samples/lambda-refarch-fileprocessing)




## Amazon Farget

Amazon Farget runs containers without provisioning any infrastructure. It works majorly with Amazon ECS and Amazon EKS.
Task Definition is the blueprint to run application, it contain the description of containers used in the application. It is always in JSON format.

### Hands-On
[Getting Started with Amazon ECS on AWS Fargate](https://docs.aws.amazon.com/AmazonECS/latest/userguide/fargate-getting-started.html)

[Creating a Cluster with a Fargate Task Using the AWS CLI](https://docs.aws.amazon.com/AmazonECS/latest/userguide/ECS_AWSCLI_Fargate.html)

[Deep dive into Fargate Spot to run your ECS Tasks for up to 70% less](https://aws.amazon.com/blogs/compute/deep-dive-into-fargate-spot-to-run-your-ecs-tasks-for-up-to-70-less/)
