# Lab 0 - Set up the environment

In this lab you will set up the environment and all needed components for your machine learning model. 

  - [Set up Watson Studio](#set-up-watson-studio)
  - [Create your first project](#create-your-first-project)
  - [Configure your project](#configure-your-project)
  - [Add data to your project](#add-data-to-your-project)
  - [Summary](#summary)
  
## Set up Watson Studio

To complete this lab you will need an instance of Watson Machine Learning that allows you to create and deploy machine learning models, and an instance of Watson Studio which provides a user interface and wizards that guide you through the process of creating machine learning models.

1. Log-in to you IBM Cloud account's https://cloud.ibm.com

2. Click the _**Create Resource**_ button at the top right 

<img src="/images/create-resource.png" width="90%" height="90%">

3. Find _**Watson Studio**_ under AI and click on it. 

<img src="/images/watson-studio.png" width="50%" height="50%">

4. You are taken to the service creation page. Choose _**London**_ as the region to deploy Watson Studio. You can change the service name suffix or keep the suggested name. Keep the Lite (Free) service plan and click the [Create] button.

<img src="/images/watson-studio-create.png" width="100%" height="100%">

5. Click on [Get Started] button to start Watson Studio.

<img src="/images/watson-studio-get-started.png" width="40%" height="40%">

6. Once the environment is ready you will see a pop up. Click on _Get Started_ to access Watson Studio.

<img src="/images/done.png" width="50%" height="50%">

**WATSON STUDIO OVERVIEW**

## Create your first project

1. Create a new project using the Create a project button. 

<img src="/images/new-project.png" width="40%" height="40%">

2. Then select **Create an empty project**.

<img src="/images/empty-project.png" width="80%" height="80%">

3. Give your project a name. Watson Studio stores its file-like artifacts into an instance of Cloud Object Storage, we will add a Cloud Object Storage instance by clicking the _**Add**_ button. 

<img src="/images/ws-project.png" width="100%" height="100%">

4. Step 3 will open a new tab, an IBM Cloud tab, where you can either select an existing instance or create a new one. In this case we will create a new Cloud Object Storage service with the Lite (Free) plan. 

<img src="/images/cos.png" width="100%" height="100%">

5. Confirm the creation.

<img src="/images/confirm-cos.png" width="40%" height="40%">

6. After step 5 you will be directed again to the Watson studio tab, where you were creating the project. Select _**Refresh**_ and you will see your new Cloud Object Storage instance appear. 

<img src="/images/create-project-with-cos.png" width="100%" height="100%">

## Configure your project

In this lab we will create a machine learning model and deploy it using Watson Machine Learning. Later we will use Visual Recognition to classify images. Let's create the needed services! 

1. Click on Settings. 

<img src="/images/ws-project-view.png" width="100%" height="100%">

2. Go to _**Associated Services_**, click on _**Add service**_ and select _**Watson**_.

<img src="/images/add-services.png" width="100%" height="100%">

3. You will see a list of all Watson services that can be added to your Watson Studio project. We will add _**Machine Learning**_. Click on Add. 

<img src="/images/add-wml.png" width="50%" height="50%">

4. Create a **New** Watson Machine learning servive with the Lite (Free) plan and click **Create**.

<img src="/images/new-wml.png" width="100%" height="100%">

5. Confirm the creation of the service. 

<img src="/images/confirm-wml.png" width="40%" height="40%">

6. After you confirm the creation you will be redirected to Watson Studio and under **Associated Services** you will see you Machine Learning instance. 

<img src="/images/wml-added.png" width="100%" height="100%">

## Add data to your project

1. From the top menu select **Assets**.

<img src="/images/assets.png" width="100%" height="100%">

2. You don't have any data sets in your project so click on **New data set** and select from your local machine the files **sound.csv** and **shaped_sound.csv**.

You can download the data files from here: 

https://ibm.box.com/v/data-mimmitkoodaa2019

<img src="/images/add-data.png" width="100%" height="100%">

3. After few seconds you will see both files listed as available assets under data assets.

<img src="/images/added-data.png" width="100%" height="100%">


## Summary

Great! Lab 0 is complete!

In this lab you created a Watson Studio instance and a Machine Learning service. You also created and configured your first project and added the needed data for our next lab. 

Now that Watson Studio environment is ready go to [Lab 1 - Build a machine learning model using sound files](https://github.com/sandra-calvo/pets-ai/tree/master/Lab%201%20-%20ML%20model) to create your Machine learning model. 

