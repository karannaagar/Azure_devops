# Azure_devops

# Azure Devops

This repo will be an EXAMPLE to How to create Dockerimage using Azure Devops and deploy in AKS as well.


## Things you need before deploying the Pipeline

- Azure container registry 
- Github Repo
  - create nginx dockerfile in your github repo.


## Steps

- Under "connect" option 
  - Select "Github" . Connect to your Github Repo. It will Create a Service connection , Service connection will be visible in you Azure devops Org. Project Settings. 
  - Now, Select the repo from your Github 
  - Select "Docker(build and push image to Azure Container registry)" . Give access to you Azure Subscription by doing Sign In. 
  - Choose the Azure Container registry. Click Validate
  - Click Review 

- Azure will show Azure-Pipeline.yml . You need to change the vmpool option to self hosted agent i.e test, otherwise you will get parallelism error due to Azure restriction on free tier accout.

```
stages:
- stage: Build
  displayName: Build stage
  jobs:
  - job: Build
    displayName: Build

## change below code. set pool name to test
    pool: 
      name: test

```





## FAQ

#### How to create Self hosted agent , for example test?

check the Settings in your Azure Project . You will see Agent pools. 
Create new agent as "test". Then run shown commands on you local machine. Now your machine will act as agent to run Azure-pipelines.yml

