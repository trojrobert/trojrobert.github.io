---
date: 2021-01-03 21:31:41
layout: post
title: "Serverless in AWS and Azure: Amazon Lambda, Amazon Fargate, and Azure Function"
subtitle:
description: This covers a brief description and use cases of the serverless services in AWS and Azure. It also provide resources on their prices, components, hands-on examples, code examples, and comparison.
image:
optimized_image:
category: Cloud
tags:
author:
paginate: false
---

I spend 1 hour every day exploring cloud services in AWS and Azure. I explore based on use case or functionality. Each week I document the resources I used during my exploration. This week I explored serverless services in AWS and Azure. The major serverless services in AWS are Amazon Lambda and Amazon Fargate, while for Azure we have Azure Function. Amazon Lambda is similar to Azure Functions.

This covers a brief description and use cases of the serverless services in AWS and Azure. It also provide resources on their prices, components, hands-on examples, code examples, and comparison.

Serverless is building and running applications without servers, that is without the burden of managing infrastructure. It does not mean we don't use a server, it just meant we don't need to manage the required server or infrastructure ourselves. The cloud service provider manages all the infrastructure for us.

### Use cases for Serverless
* Application for continuous delivery pipeline
* Data  processing 
* Real time stream processing 
* Real time file Processing  for instance run a code when new data is received 
* Data preprocessing and model serving in machine learning 

## Amazon Lambda

Amazon Lambda runs code without servers and clusters. In other words, you don’t need to provision infrastructure. Amazon Lambda also has a code editor where you can write, test, and view execution results. Your code should be uploaded as a zip file or as a container image, the resources required are automatically allocated to it. This code could be run based on a trigger for instance change in data in S3 bucket, response to HTTP request using Amazon API Gateway.

 Major Amazon Web Services(AWS) used with Amazon Lambda: Amazon S3, Amazon DynamoDB, Amazon Kinesis, Amazon SNS, Amazon CloudWatch, Amazon API Gateway, AWS IoT Core, Amazon SNS, Amazon SAM, Amazon EventBridge, Amazon Step Functions, SQS, Amazon Aurora Serverless.
 
### Pricing 

Amazon Lambda free usage tier includes 1M free requests per month and 400,000 GB-seconds of compute time per month.[Amazon Lambda pricing](https://aws.amazon.com/lambda/pricing/) is based on the number of requests for your functions and the duration, the time it takes for your code to execute.
 
### Hands-On Tutorials

[Using AWS Lambda with the Mobile SDK for Android](https://docs.aws.amazon.com/lambda/latest/dg/with-android-example.html)

[Using AWS Lambda with Amazon S3](https://docs.aws.amazon.com/lambda/latest/dg/with-s3-example.html)

[Web application to request unicorn rides ride](https://aws.amazon.com/getting-started/hands-on/build-serverless-web-app-lambda-apigateway-s3-dynamodb-cognito/)

[Building Lambda functions with Python](https://docs.aws.amazon.com/lambda/latest/dg/lambda-python.html)

[Create a Lambda function with the console](https://docs.aws.amazon.com/lambda/latest/dg/getting-started-create-function.html#gettingstarted-images)


### Code Examples

[Use AWS Lambda to build serverless backend for an iOS mobile application](https://github.com/aws-samples/lambda-refarch-mobilebackend)

[Humidity sensor application to monitor humidity under a set threshold with AWS Lambda](https://github.com/aws-samples/lambda-refarch-iotbackend)

[To-Do App](https://github.com/aws-samples/lambda-refarch-webapp)

[Real-time data processing with Amazon Kinesis and AWS Lambda](https://github.com/aws-samples/lambda-refarch-streamprocessing)

[Processing Interview Markdown files](https://github.com/aws-samples/lambda-refarch-fileprocessing)


### Official Resources 

[Amazon Lambda](https://aws.amazon.com/lambda/)

[Amazon Lambda Documentation](https://docs.aws.amazon.com/lambda/latest/dg/welcome.html)

[Amazon Lambda Blog](https://aws.amazon.com/blogs/compute/category/compute/aws-lambda/)


### Other Resources 
[AWS Lambda - The Ultimate Guide](https://www.serverless.com/aws-lambda)

[AWS Lambda with Python: A Complete Getting Started Guide](https://stackify.com/aws-lambda-with-python-a-complete-getting-started-guide/)

[AWS Lambda Tutorial For Beginners \| What is AWS Lambda? \| AWS Tutorial For Beginners \| Simplilearn(video)](https://www.youtube.com/watch?v=97q30JjEq9Y)

[AWS Lambda Tutorial \| AWS Tutorial for Beginners \| AWS Cloud \| AWS Lambda \| AWS Training \| Edureka](https://www.youtube.com/watch?v=XZggsCITQdY)

[AWS Lambda Introduction](https://www.youtube.com/watch?v=d6lrokAELO0)


## Amazon Farget

Amazon Farget runs containers without provisioning any infrastructure. It works majorly with Amazon ECS and Amazon EKS.
Task Definition is the blueprint to run application, it contain the description of containers used in the application. It is always in JSON format.

### Pricing

[AWS Fargate pricing](https://aws.amazon.com/fargate/pricing/) is based on the amount of vCPU and memory resources consumed by your containerized applications.

### Hands-On Tutorials
[Getting Started with Amazon ECS on AWS Fargate](https://docs.aws.amazon.com/AmazonECS/latest/userguide/fargate-getting-started.html)

[Creating a Cluster with a Fargate Task Using the AWS CLI](https://docs.aws.amazon.com/AmazonECS/latest/userguide/ECS_AWSCLI_Fargate.html)

[Deep dive into Fargate Spot to run your ECS Tasks for up to 70% less](https://aws.amazon.com/blogs/compute/deep-dive-into-fargate-spot-to-run-your-ecs-tasks-for-up-to-70-less/)


### Code Examples

[Application Tracing on Fargate with AWS X-Ray](https://github.com/aws-samples/aws-xray-fargate)


### Official Resources 

[AWS Fargate](https://aws.amazon.com/fargate/)

[AWS Fargate Documentation](https://docs.aws.amazon.com/AmazonECS/latest/userguide/what-is-fargate.html)

[AWS Fargate Blog](https://aws.amazon.com/blogs/compute/category/compute/aws-fargate/)



### Other Resources

[AWS Fargate Tutorial \| AWS Tutorial For Beginners \| AWS Certification Training \| Edureka](https://www.youtube.com/watch?v=fmFlAWtKnGA)

[Deep Dive into AWS Fargate](https://www.youtube.com/watch?v=xBgiArJHv7E)

[Deep Dive into AWS Fargate 2](https://www.youtube.com/watch?v=IEvLkwdFgnU)


## Azure Functions 

Azure Functions is a serverless compute service that runs event triggered code without provisioning infrastructures like compute. “Compute on demand”.

### Pricing

Azure Functions provides a monthly free grant of 1 million requests and 400,000 GBs of resource consumption per month per subscription in pay-as-you-go pricing across all function apps in that subscription. [Azure Function Pricing](https://azure.microsoft.com/en-us/pricing/details/functions/) is based on per-second resource consumption and executions.


### Hands-On Tutorials

[Filtering sensor data simulated on IoT  Edge with Azure Functions](https://docs.microsoft.com/en-us/azure/iot-edge/tutorial-deploy-function?toc=%2Fazure%2Fazure-functions%2Ftoc.json&view=iotedge-2018-06)

[Detect poor sentiment on Tweets and send email using Azure Functions and Logic App](https://docs.microsoft.com/en-us/azure/azure-functions/functions-twitter-email)

[Thumbnail generation with Azure Event Grid and Azure Functions](https://docs.microsoft.com/en-us/azure/event-grid/resize-images-on-storage-blob-upload-event?toc=%2Fazure%2Fazure-functions%2Ftoc.json&tabs=dotnet)

[Update web application using Azure Functions](https://docs.microsoft.com/en-us/learn/modules/automatic-update-of-a-webapp-using-azure-functions-and-signalr/1-introduction)



### Code Examples

[Trigger HTTP API endpoint with Azure Function to classify images](https://github.com/Azure-Samples/functions-python-pytorch-tutorial)


### Official Resources 

[Azure Functions](https://azure.microsoft.com/en-us/services/functions/)

[Azure Functions Documentation](https://docs.microsoft.com/en-us/azure/azure-functions/)

[Azure Functions Blogs](https://azure.microsoft.com/en-us/blog/tag/azure-functions/)


### Other Resources

[Azure Function Apps Tutorial \| Introduction for serverless programming](https://www.youtube.com/watch?v=Vxf-rOEO1q4&t=875s)
