---
date: 2020-06-03 23:18:10
layout: post
title: "From Competition to Production: Deploying a Machine Learning Model on Azure"
subtitle:
description:
image: /assets/img/uploads/air-quality-workflow.PNG
optimized_image: /assets/img/uploads/air-quality-workflow.PNG
category:
tags:
author:
paginate: false
---


A lot of attention has been put into getting the best accuracy while building Machine Learning models, these supposed accurate models are not valuable until they are deployed into reality to solve problems. [Kaggle]( https://www.kaggle.com/) and [Zindi]( https://zindi.africa/) platforms have also focused on competing to get the best accuracy. I competed in [AirQo Ugandan Air Quality Forecast Challenge]( https://zindi.africa/competitions/airqo-ugandan-air-quality-forecast-challenge) to predict future air quality level in cities in Uganda. Though my model’s loss was +3 higher than the winning team in the competition, I spent more time deploying the model and articulating how we can move from just a competition to solving the real-life problem.
This article describes all the steps involved in the lifecycle of a ML project using the competition as a use case. I used [Microsoft Azure](https://azure.microsoft.com/en-gb/overview/what-is-azure/) cloud services for deploying the model.You can find the detail of the implementation on [github](https://github.com/trojrobert/uganda-air-quality-challenge).

## Defining Project Goals
The goal of the [AirQo Ugandan Air Quality Forecast Challenge]( https://zindi.africa/competitions/airqo-ugandan-air-quality-forecast-challenge/data) on [Zindi](https://zindi.africa/) is to predict the air quality level of cities in [Uganda](https://en.wikipedia.org/wiki/Uganda) a country in Africa at exactly 24 hours after a 5 day series of hourly weather data readings . To measure the air quality level, we need to know the mass of PM2.5(particulate matter smaller than 2.5 micrometers in diameter or around 1/30th the thickness of a human hair strand) in a volume of air given by micrograms per cubic meters(m/m3). These particles are not visible to human eye because they are exceedingly small; they are generated from vehicle exhaust, machines in industries, burning of fossil fuels, and others. Bad air quality causes respiratory diseases, heart diseases, and stroke.

## Choose the project task 
From the goal of the project, I can formulate the project for different tasks.
* **Classification**: If the level of air quality has been divided into different classes for instance good, moderate, unhealthy for sensitive groups, unhealthy, very unhealthy, and hazardous. The task could be to predict the class of a place. 
* **Regression**: If the task is to predict the PM2.5 a continuous variable.
* **Clustering**: If the task is to cluster cities with similar air quality levels.
* **Anomaly detection**: If the task is to monitor sudden changes in the air quality level.
* **Forecasting**: If the task is to predict the air quality level for the future.
In this challenge/project, the best choice is a forecasting task since we are asked to predict the air quality level at exactly 24 hours after a 5-day series of hourly weather data readings.

## Data Collection 
Measuring PM2.5 which affects the air quality level of place require gathering data from several sensors. For the Ugandan Air Quality challenge, they used 5 sensors to get the following data every hour:
1.	**Temperature(temp)**: mean temperature recorded at the site over an hour, measured in degrees Celsius.
2.	**Precipitation(precip)**: total rainfall recorded over an hour, measured in millimeter.
3.	**Wind Direction(wind_dir)**: mean direction of wind over an hour, measured in degrees.
4.	**Wind Speed(wind-spd)**: mean of the speed of wind over an hour, measured in meters per second.
5.	**Atmospheric Pressure(atmos_press)**: mean of Atmospheric pressure over an hour, measured in atm.

For each of these 5 sensors used for gathering the data, they collected the features(location, height above sea level...) of the sensor, these could be called the Metadata, you can find the details [here]( zindi.africa/competitions/airqo-ugandan-air-quality-forecast-challenge/data).

## Data Ingest
Data ingestion is a process of moving data from one or more sources to a destination for instance a database where it can be stored and further analyzed. In this use case, we need to collect the data from the sensors and stored them in a data storage. We will be using Azure data storage container to store the data. 
To understand this section very well, we need to understand some terms in Azure
* [Azure IoT Edge](https://docs.microsoft.com/en-us/azure/iot-edge/about-iot-edge) this is used to move cloud analytics and custom business logic to devices so that you can focus on business insights instead of data management. It consists of IoT Edge modules, IoT Edge runtime, and cloud-based interface.
* IoT Edge modules are containers that run Azure services, third-party services, or our own code. Modules are deployed to IoT Edge devices and execute locally on those devices.
* IoT Edge runtime runs on each IoT Edge device and manages the modules deployed to each device. It also performs management and communication operations. 
* Cloud-based interface enables you to remotely monitor and manage IoT Edge devices.
* [IoT Hub](https://docs.microsoft.com/en-us/azure/iot-hub/about-iot-hub) is a managed service hosted in the cloud that acts as a central message hub for bi-directional communication between our IoT application and the devices it manages. 
* [Time Series Insight(preview)](https://docs.microsoft.com/en-us/azure/time-series-insights/time-series-insights-update-overview)  is used to collect, process, store, analyze, and query data from Internet of Things (IoT), scale data that's highly contextualized and optimized for time series.
* [Azure gateway](https://docs.microsoft.com/en-us/azure/iot-edge/how-to-create-transparent-gateway) - we use a transparent gateway configuration that allows devices to connect to Azure IoT Hub through the gateway without knowing that the gateway exists. A gateway is used for sending encrypted traffic.
* [Azure Container Registry](https://docs.microsoft.com/en-us/azure/container-registry/container-registry-intro) is used to store and manage your Docker container images and related artifacts.
In the diagram, the data ingestion part involves the section in the red dotted box. For the project, we will connect our sensors to the IoT edge device through a gateway. Azure IoT runtime in the IoT Edge also manage a secure connection to our sensors, installs and updates workloads on the sensors, remotely monitoring the sensors and other communication to our sensors. We also register each sensor on the IoT hub to identify each sensor. Then we get an image that triggers some computation on the data
from the azure container registry and deploy it in an IoT edge module. This is just a high-level view of the workflow between a sensor, an Azure IoT edge device, and an Azure IoT Hub. We could also deploy [Azure Functions](https://docs.microsoft.com/en-us/azure/azure-functions/functions-overview) or [Azure Stream Analytics](https://docs.microsoft.com/en-us/azure/stream-analytics/stream-analytics-introduction) and Azure Machine Learning as a module to the Azure IoT edge device.

The data in Azure IoT Hub is routed to Azure storage. Azure has several storage types depending on our use case. In our case, we will use a [blob storage container]( https://docs.microsoft.com/en-us/azure/storage/blobs/storage-blobs-introduction) for storing massive unstructured data coming from our sensor. There is also Azure Cosmos DB use for multi-model database services like Mongo DB and Cassandra, etc.

![Life cycle of ML project]( /assets/img/uploads/ml-project-lifecycle.PNG "source - https://mlinproduction.com/what-does-it-mean-to-deploy-a-machine-learning-model-deployment-series-01/")
ml-project-lifecycle.png

## Labeling
In the section, we add labels to the data we will use in training our model. Most time this is done manually, the quality and accuracy of the label affect the accuracy of our model so we need to pay a lot of attention to it.  

## Building and Training Model  
At this point, we have our data stored in our storage account blob container, and they are well labeled. We need to query the storage account to provide 5-day series of the hourly data sent from the sensors. We are to follow the following steps, most of which are common in data science life cycle, I also added other steps specific to Azure Machine Learning lifecycle
* Create a workspace
* Download data from storage account
* Load and explore data
* Create Azure compute target
* Create feature engineering script
* Build model
* Create an environment and train a model   
* Build and train a model
* Register the model
To perform the above steps, you need to understand the following Azure terms used in Machine learning

**[Azure ML Workspace]( https://docs.microsoft.com/en-us/azure/machine-learning/studio/what-is-ml-studio)** is a dedicated platform for data scientist to managing data science workflow, it coordinates all resources and steps in building, testing and deploying a machine learning model.

**[Compute target](https://docs.microsoft.com/en-us/azure/machine-learning/concept-compute-target)** – is a computing resource used for training machine learning models, it helps in creating environments for training your model. It could be your local machine or a cloud-based resource.

**Estimator** – it is used for managing a machine leaning experiment, it contains all the package dependencies required to run an experiment. 

### Create a workspace
There are several ways of creating a workspace on Azure, we can use the command line, Azure SDK or the Azure Portal. In my case I used Azure SDK, the code snippet is written below
```python
from azureml.core import Workspace
    
ws = Workspace.create(name=workspace_name,
                      subscription_id=subscription_id,
                      resource_group=resource_group,
                      create_resource_group=True,
                      location=location)
```

### Download data from storage account
In the case of the competition, the dataset was already provided, all we needed to do was to create a storage account then upload the train and test data to the storage account container. In reality, our data will already be in the storage container which was routed from the IoT hub. We used the code below to retrieve the data from the storage account and download it into our workspace for easy access to the model.

```python
from azureml.core import Datastore

ds = Datastore.register_azure_blob_container(workspace=ws,
                                             datastore_name='airquality',
                                             container_name=STORAGE_ACCOUNT_CONTAINER,
                                             account_name=STORAGE_ACCOUNT_NAME,
                                             account_key=STORAGE_ACCOUNT_KEY,
                                             create_if_not_exists=False)
```

### Load and explore data
As we know in machine learning, raw data are always very messy.  We need to understand the correlation between features in the dataset, visualize the data to get some insight from the data, and understand the distribution of the data. I will not go in-depth into that since it is a popular concept in Machine learning and there are lots of [resources](https://www.analyticsvidhya.com/blog/2016/01/guide-data-exploration/) that have done a comprehensive explanation.

```python
from azureml.core.compute import ComputeTarget, AmlCompute
from azureml.core.compute_target import ComputeTargetException

cluster_name = "air-quality-comp"

try:
    # Check for existing compute target
    compute_target = ComputeTarget(workspace=ws, name=cluster_name)
    print('Found existing cluster, use it.')
except ComputeTargetException:
    # If it doesn't already exist, create it
    print('creating a new compute target ...')
    compute_config = AmlCompute.provisioning_configuration(vm_size='STANDARD_D2_V2', max_nodes=3)
    compute_target = ComputeTarget.create(ws, cluster_name, compute_config)
    
    # can poll for a minimum number of nodes and for a specific timeout. 
    # if no min node count is provided it will use the scale settings for the cluster
    compute_target.wait_for_completion(show_output=True, min_node_count=None, timeout_in_minutes=20)
    
    # For a more detailed view of current BatchAI cluster status, use the 'status' property    
    compute_target.status.serialize()
```

### Create feature engineering script 
This is also a common process in machine learning, I created a script to handle the nan values, remove features, and other features. We will import this script while building the model, also this script will be used for cleaning and transforming the raw data and doing inferencing so the model can interpret the data.  

### Build model 
In this project we will use the CatBooostRegressor model, the training data was divided into training and validation set using 20 folds, using 2500 estimators, learning rate of 0.3, and root mean square error as a metric to evaluate the model.  

### Create an environment and train a model in it  
We create an environment using the estimator class then we install some packages like catboost, joblib, and scikit-learn. These packages are important to run our models. Thereafter we run our training script in the environment. We can make some changes in our model and do hyperparameter tuning then run the experiment again. We can have several runs in an experiment, we will register the best model which will be deployed later. We can also register several models then decide the version of the registered model to deploy.

## Testing and deploying
At this point, we have a trained model. We need to test the model with the test set to check how accurate our model is, then deploy the model to test on real-life data. We will go through the following steps;

*	Make predictions with register model
*	Create a scoring script
*	Create an inference environment
*	Create a docker image 
*	Deploy the model

### Make predictions with register model
We make predictions with our saved model using the predict method. But we need to remember to run the feature engineering script to clean the data before calling the predict method to test our test data..

### Create a scoring script
The scoring script is used for inferencing, after deploying the model as a service, the script loads the model and returns the predictions for the submitted data.  The script contains two major methods. First, is the init() method which is called when the service is initialized. The second method is the run(raw_data) which takes the data we want to predict as an argument. This script can be run inside a container which can then be deployed as a web service or Azure IoT Edge module. 


```python

def init():
    global model
    model_path = Model.get_model_path(model_name = '<<modelname>>')
    # deserialize the model file back into a sklearn model
    model = joblib.load(model_path)
def run(raw_data):
    log_for_debug("raw_data", raw_data)
    
    message_data = unpack_message(raw_data)
    log_for_debug("message_data", message_data)
    
    X_data = extract_features(message_data)
    log_for_debug("X_data", X_data)
   
    # make prediction
    y_hat = model.predict(X_data)
    
    response_data = append_predict_data(message_data, y_hat)
    return response_data
    
```


### Create inference environment
Previously we created an environment to train the model, we also need to create an environment to deploy the model. This environment will be created as a YAML file, it contains all the dependencies required to run the model at production.

### Create a docker image
Create a docker image using the azure core image class, this image contains the scoring script and the inference environment YAML file. While creating the image, we also include the model in the image.

### Deploy the model
This involves the green dotted section in the diagram, we have three modules in the Azure IoT device
* **Air quality model module** – This IoT edge module contains the image of the model, it received a clean / processed data from the Router module and output prediction from the model. The output prediction is sent to the router module.
* **Router Module** – This module receives the raw data from the device, processes the data using the feature engineering scripts, the processed data is sent to the Air quality to get predictions. It also receives the prediction from the air quality model module. The prediction and the raw data are sent to the writer module.
**Writer Module** – This module stores the prediction and the raw data gotten from the router module in the azure storage.

## Conclusion
Deploying a machine learning model is a critical aspect of a machine learning model that has always been overlooked. From this article, we went through each step in building an ML project using the Air quality challenge on Zindi and we were able to deploy our model on an IoT device for real-life prediction.
