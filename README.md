# Operationalizing Machine Learning

This project uses **Microsoft Azure Machine Learning** to configure, deploy and consume a cloud-based machine learning production model.
The project will also include the creation, publishing and consuming of a machine learning pipeline.

Both the **Azure ML Studio** and the **Python SDK** are used in the project. 

### Dataset

The data used for the project is the **Bank Marketing** dataset. 
The model built as part of this project will use the data to predict if a person will subscribe to the long-term deposit with the bank or not.

The dataset used for the project contains almost 33 thousand of records with 20 features.
The snapshot of the dataset is below: 

![image](https://user-images.githubusercontent.com/60096624/109403410-5a5a9900-7955-11eb-9812-c3806b9a8ffe.png)

## **Architectural Diagram**

Below is the architectual diagram of the project showing the flow of operations from start to finish.

The project starts with authentication and then we run an Automated ML experiment to deploy the best model.
Next, we will enable Application Insight to review important information about the service when consuming the model.
And finally, we will create, publish, and interact with a pipeline. 

Once all the steps are completed, a short screencast will be created to document all the steps performed.

![image](https://user-images.githubusercontent.com/60096624/112736915-53bc4300-8f4e-11eb-8637-06e2bb16b920.png)

## **Key Steps**

The following steps will be performed as part of the project:

1.  Authentication
2.  Automated ML Experiment
3.  Deploy the best model
4.  Enable logging
5.  Swagger Documentation
6.  Consume model endpoints
7.  Create and publish a pipeline
8.  Documentation

### **Step 1 - Authentication**

I am using the Lab provided by Udacity and hence the authentication step has already been performed on my behalf. 
This step requires authorization to create a security principal.

## **Create a new AutoML run**

### **Step 2 - Automated ML Experiment**

In this step we create an experiment using Automated ML, configure a compute cluster, and use that cluster to run the experiment.

The steps are performed in Jupyter notebook and include:

    - Create an Experiment in an existing Workspace
    - Create or Attach existing AmlCompute to a workspace
    - Define data loading in a TabularDataset
    - Configure AutoML using AutoMLConfig
    - Use AutoMLStep
    - Train the model using AmlCompute
    - Explore the results

- **???Registered Datasets??? in ML Studio shows "Bankmarketing" dataset available**

    After the AutoML experiment has completed the **Bankmarketing Dataset** has been created as expected:


    ![alt text](screenshots/2.1_Bankmarketing_dataset_available_1.png)

    ![alt text](screenshots/2.1_Bankmarketing_dataset_available_2.png)

- **The experiment is shown as completed**

    The AutoML experiment shows in the Azure ML Studio as completed. The experiment run for 44.5 minutes.


    ![alt text](screenshots/2.2_Experiment_completed_1.png)
    

    The AutoML experiment identified the Best model which is **VotingEnsemble** with **0.947** AUC:

    
    ![alt text](screenshots/2.2_Experiment_completed_2.png)
    
- **Best model**

    Here are the details of the Models that were included in the AutoML run.
    The Best model **VotingEnsemble** is first on the list:

    
    ![alt text](screenshots/2.3_Best_model_1.png)


    The Best model is ready for deployment:

    
    ![alt text](screenshots/2.3_Best_model_2.png)
    

## **Deploy a model and consume a model endpoint via an HTTP API**

### **Step 3 - Deploy the best model**

  In this step the best model is deployed.

- **Deploy the best model**

  The best model is deployed using the following configuration:
    
  Name:  **model-deploy** <br/>
  Desc:  **Best model deployment** <br/>
  Compute type:  **Azure Container Instance** <br/>
  Enable authentication:   **ON**
  


    ![alt text](screenshots/3.1_Best_model_deployment_1.png)
    
    ![alt text](screenshots/3.1_Best_model_deployment_2.png)
    

    The **model-deploy** endpoint has been created:

    
    ![alt text](screenshots/3.1_Best_model_deployment_3.png)
    
    ![alt text](screenshots/3.1_Best_model_deployment_4.png)
    
    ![alt text](screenshots/3.1_Best_model_deployment_5.png)
    
### **Step 4 - Enable logging**

Once the Best model is deployed we can run Python SDK script to enable the Application Insights and retrieve logs. 

- **Logging is enabled by running the provided logs.py script**

    The **logs.py** script needs to be edited to set the deployment name to **model-deploy** and to add code to enable application insights:
    
    ```
    # Set with the deployment name
    name = "model-deploy"
    . . .
    # Enable application insightS
    service.update(enable_app_insights=True)
    ```

    ![alt text](screenshots/4.2_Script_edit_logs.py.png)
    
    We run the **logs.py** script as follows:
    
    ```
    python logs.py
    ```
    
    Below is the screenshot showing the output of the above command line. 
    
    Full output of the above command is in the **OUT.01.logs.py.txt** file attachet to the project.

    ![alt text](screenshots/4.2_Script_run_logs.py_1.png)
    
    ![alt text](screenshots/4.2_Script_run_logs.py_2.png)

- **Endpoints section in Azure ML Studio, showing that ???Application Insights enabled??? says ???true???**

    After the **logs.py** script completed we can see the Application Insights enabled in Azure ML Studio:

    ![alt text](screenshots/4.1_Endpoint_Application_Insights_enabled_1.png)
    
    Clicking on the URI gives us access to the following Application Insights page: 
    
    ![alt text](screenshots/4.1_Endpoint_Application_Insights_enabled_2.png)

    
### **Step 5 - Swagger Documentation**

In this step we consume the deployed model using Swagger using the following steps:

- Download the **swagger.json** file from Azure ML Studio **model-deploy** endpoint
- Run the **swagger.sh** and serve.py scripts
- Interact with the swagger instance running with the documentation for the HTTP API of the model.
- Display the contents of the API for the model

The **swagger.sh** script downloads the latest Swagger container and it will run it on port 85. The script is executed as follows:

```
bash swagger.sh
```

The **serve.py** script will start a Python server on port 8000. This script needs to be right next to the downloaded **swagger.json** file.
It is executed as follows:

```
python serve.py
```

- **Swagger runs on localhost showing the HTTP API methods and responses for the model**

    ![alt text](screenshots/5.1_Script_run_swagger.sh.png)
    
    Swagger runs on localhost showing the model HTTP API methods:
    
    ![alt text](screenshots/5.1_swagger_localhost_1.png)
    
    Model inputs:
    
    ![alt text](screenshots/5.1_swagger_localhost_2.png)
    
    Model responses:
    
    ![alt text](screenshots/5.1_swagger_localhost_3.png)
    
    ![alt text](screenshots/5.1_swagger_localhost_4.png)
    
### **Step 6 - Consume model endpoints**

Once the model is deployed we use the **endpoint.py** script to interact with the trained model. 
First we need to modify the script to set the scoring_uri and the key to match the key for the service and the URI that was generated after deployment.

The URI can be found in the Details tab of the  **model-deploy** endpoint above the Swagger URI.

- **The endpoint.py script runs against the API producing JSON output from the model**

    ![alt text](screenshots/6.1_Script_edit_endpoint.py.png)
    
    ![alt text](screenshots/6.1_Script_run_endpoint.py.png)
    
### **Step 6 - Benchmark the endpoint using Apache bench**

In this optional step we run the Apache Benchmark ab command against the HTTP API using following steps:

    - Make sure the Apache Benchmark command-line tool is installed and available in the path
    - Replace the key and URI in the benchmark.sh script
    - Run the benchmark.sh script

- **Apache Benchmark (ab) runs against the HTTP API using authentication keys to retrieve performance results. (optional)**

    Make sure the Apache Benchmark command-line tool is installed and available in the path:

    ![alt text](screenshots/6.2_Apache_Benchmark_ab_available.png)
    
    Replace the key and URI in the benchmark.sh script using Details tab of **model-deploy** endpoint:
    
    ![alt text](screenshots/6.2_Script_edit_benchmark.sh.png)
    
    Run the benchmark.sh script using command:
    
    ```
    python benchmark.sh
    ```
            
    Below is the screenshot showing the output of the above command line. 
    
    The full output of the above command is in the **OUT.03.benchmark.sh.txt** file attachet to the project.
    
    ![alt text](screenshots/6.2_Script_run_benchmark.sh_1.png)
    
    ![alt text](screenshots/6.2_Script_run_benchmark.sh_2.png)

## **Create and publish a pipeline**

For this part of the project we use the Jupyter Notebook. 
We are using the same keys, URI, dataset, cluster, and model names as in previous part. 

### **Step 7 - Create and publish a pipeline**

- **The pipeline section of Azure ML studio, showing that the pipeline has been created**

    ![alt text](screenshots/7.1_Azure_ML_Studio_Pipeline_created.png)
    
- **The Bankmarketing dataset with the AutoML module**

    ![alt text](screenshots/7.3_Bankmarketing_dataset_with_AutoML_module.png)

- T**he ???Published Pipeline overview???, showing a REST endpoint and a status of ACTIVE**

    ![alt text](screenshots/7.4_Published_Pipeline_overview_REST_endpoint_ACTIVE.png)

## **Configure a pipeline with the Python SDK**

- **A screenshot of the Jupyter Notebook is included in the submission showing the ???Use RunDetails Widget??? with the step runs**

    ![alt text](screenshots/7.5_Jupyter_Notebook_RunDetails_Widget.png)

## **Use a REST endpoint to interact with a Pipeline**

- **ML studio showing the pipeline endpoint as Active**

    ![alt text](screenshots/7.2_Azure_ML_Studio_Pipeline_Endpoint_Active.png)

- **ML studio showing the scheduled run**

    ![alt text](screenshots/7.6_Jupyter_Notebook_Submitted_pipeline_run.png)
    
    ![alt text](screenshots/7.6_Azure_ML_Studio_Pipeline_run_overview.png)


## **Screen Recording**

This section includes the link to the project screencast. 
The screencast shows the entire process of the working ML application, including a demonstration of:

- Working deployed ML model endpoint.
- Deployed Pipeline
- Available AutoML Model
- Successful API requests to the endpoint with a JSON payload

Video is available at the following link:  https://www.youtube.com/watch?v=aglqDK0D_nA

## **Future Suggestions**

Here are some suggestions how to improve the project in the future:

- Increase AutoML run duration which would allow more models to be included in the experiment
- Try to use a larger dataset as input to the model training making sure that data is more balanced
- Try using different parameter for the experiment such as number of folds for Cross Validation. 
