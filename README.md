*NOTE:* This file is a template that you can use to create the README for your project. The *TODO* comments below will highlight the information you should be sure to include.


# Operationalizing Machine Learning

*TODO:* Write an overview to your project.

## **Architectural Diagram**
*TODO*: Provide an architectual diagram of the project and give an introduction of each step. An architectural diagram is an image that helps visualize the flow of operations from start to finish. In this case, it has to be related to the completed project, with its various stages that are critical to the overall flow. For example, one stage for managing models could be "using Automated ML to determine the best model". 

## **Key Steps**
*TODO*: Write a short discription of the key steps. Remeber to include all the screenshots required to demonstrate key steps. 

As part of the project the following steps will be performed:

1.  Authentication
2.  Automated ML Experiment
3.  Deploy the best model
4.  Enable logging
5.  Swagger Documentation
6.  Consume model endpoints
7.  Create and publish a pipeline
8.  Documentation

### **I. Create a new AutoML run**

#### “Registered Datasets” in ML Studio shows "Bankmarketing" dataset available
#### The experiment is shown as completed.

### **II. Deploy a model and consume a model endpoint via an HTTP API**

#### Endpoints section in Azure ML Studio, showing that “Application Insights enabled” says “true”.
#### Logging is enabled by running the provided logs.py script
#### Swagger runs on localhost showing the HTTP API methods and responses for the model
#### endpoint.py script runs against the API producing JSON output from the model.
#### Apache Benchmark (ab) runs against the HTTP API using authentication keys to retrieve performance results. (optional)

### **III. Create and publish a pipeline**

#### The pipeline section of Azure ML studio, showing that the pipeline has been created
#### The Bankmarketing dataset with the AutoML module
#### The “Published Pipeline overview”, showing a REST endpoint and a status of ACTIVE

### **IV. Configure a pipeline with the Python SDK**

#### A screenshot of the Jupyter Notebook is included in the submission showing the “Use RunDetails Widget” with the step runs

### **V. Use a REST endpoint to interact with a Pipeline**

#### ML studio showing the pipeline endpoint as Active
#### ML studio showing the scheduled run

## **Screen Recording**
*TODO* Provide a link to a screen recording of the project in action. Remember that the screencast should demonstrate:

Video is available at the following link:  <link>


## **Standout Suggestions**
*TODO (Optional):* This is where you can provide information about any standout suggestions that you have attempted.
