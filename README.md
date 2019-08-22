# IBM Cloud :cloud: Pets & AI 
:robot: :heart: :dog: & :cat:
## Mimmitkoodaa workshop guide 

In this guide:
  - [Introduction](#introduction)
  - [PHASE 1](#phase-1): PHASE 1
  - [PHASE 2](#phase-2): PHASE 2
  - [PHASE 3](#phase-3): PHASE 3
  - [PHASE 4](#phase-4): PHASE 4

  #### Prerequisites
- IBM Cloud account
  - Create a free account https://cloud.ibm.com
  
# INTRODUCTION: MACHINE LEARNING WITH SOUND

During the machine learning process, data is analyzed and compared to determine correlations and patterns. Without data, you cannot generate a machine learning model, and the data needs to be comparable.

In the first three labs, you will create a prediction model that is based on the sounds of cats and dogs. During training, the model must be able to compare the audio files that form the training data to determine how to identify a dog barking and a cat purring.

This lab shows you how the data set that is used to create the Cats and Dogs Sounds prediction model is created. You can follow the instructions to create the data and see how the data was built. However, this is not mandatory for the course because the data set that is created during this lab is available on GitHub, which you can use in Lab 2.

# PHASE 1

## Set up Watson Studio 

In a browser navigate to https://cloud.ibm.com/ Select 'LOG IN' with your IBM id (your email). After login you should see your IBM Cloud dashboard. Select the 'CATALOG' view. 

IMAGE

Locate the Watson Studio service, under AI, and click on it. Note that this is a one-time setup, only one instance of Watson Studio per region needs to be created.

IMAGE

You are taken to the service creation page. It is possible to create an instance of Watson Studio in either US South or United Kingdom regions. Choose United Kingdom. You can change the service name suffix or keep the suggested name. Keep the Lite service plan and click the [Create] button.

IMAGE


### Create Watson Studio project

Now that we have put in place the infrastructure to work with Data & AI, we can start creating a project for a specific data handling project.

Select the Watson Studio service instance, and click the '[Get Started]' button 

IMAGE

The first time you start the Watson Studio UI, you will be asked to confirm some details, click the [Continue]

IMAGE

Note that you can also go directly to the service's Cloud Web UI using the URL for the region where the service has been created, either https://dataplatform.ibm.com/projects?context=analytics for 'US-South' or https://eu-gb.dataplatform.ibm.com/projects?context=analytics for 'United Kingdom' Create a new project using the New 

IMAGE

Project button tile  ->  
Then select a Complete configuration. This governs which tools are made available to the project, and can be altered later if need be Validate with the [OK] button.

Name this new project e.g. Mimmitkoodaa 2019.

Note that you will want to leave the 'Restrict who can be a collaborator' unchecked, it will make sharing the project with another account more straightforward.

Watson Studio stores its file-like artifacts into an instance of Cloud Object Storage, we will create a COS service instance at this stage.

IMAGE

Select the Lite Plan 

IMAGE

Accept the default names for resource group and Service name. Back to the Project creation page, select Refresh then the new Object Storage service instance. Finally, click Create.

IMAGE


## Build a machine learning model 

In this section, you create a machine learning project and use it as the container for your data assets and the machine models that you generate.

To complete this lab you will need an instance of Watson Machine Learning that allows you to create and deploy machine learning models, and an instance of Watson Studio which provides a user interface and wizards that guide you through the process of creating machine learning models.

If you created Watson Studio projects before, you might see different images than what is shown here.

1. Go to the IBM Watson page and click Log In to log in to IBM Watson Studio with your IBM ID and password. Then, scroll down to the Watson Services section.

<img src="/images/mach_learn_lab2_step1_2.png" width="100%" height="100%">

- Click Add service and then Add to select Machine Learning.

<img src="/images/mach_learn_lab2_step1_3.png" width="100%" height="100%">

- Verify that you have Watson Studio properly configured by opening your Studio profile.

<img src="/images/mach_learn_lab2_step1_4.png" width="100%" height="100%">

- Click the Apps tab. Then, check whether you have a Watson Studio application listed. If this is your first machine learning project, you will not see Watson Studio listed. If you don't have an application in the list, click Add other apps to add Watson Studio.

<img src="/images/mach_learn_lab2_step1_5.png" width="100%" height="100%">

- Go back to the Studio home page and click New Project. Select Data Science and give the project a name and description.

<img src="/images/mach_learn_lab2_step1_6.png" width="100%" height="100%">

- Make sure that the Storage field is populated with cloud-object-storage credentials. You might need to create IBM Cloud Object Storage and set your region appropriately for the credentials to appear on the Watson Studio project creation page.

You must use IBM Cloud Object Storage for reading input (such as training data) and for storing results, such as log files.

If your Storage field is showing as unpopulated, click Cloud Object Storage.

Click Add to add Cloud Object Storage for Watson Studio.

<img src="/images/mach_learn_lab2_step1_7.png" width="100%" height="100%">

You might need to go back to the previous step to associate the cloud object storage with your data science project.

When you're done creating the project, click Create.



## Create a machine learning model

###  Create a machine learning project

In this section, you create a machine learning project and use it as the container for your data assets and the machine models that you generate.

To complete this lab you will need an instance of Watson Machine Learning that allows you to create and deploy machine learning models, and an instance of Watson Studio which provides a user interface and wizards that guide you through the process of creating machine learning models.

If you created Watson Studio projects before, you might see different images than what is shown here.

- Go to the IBM Watson page and click Log In to log in to IBM Watson Studio with your IBM ID and password. Then, scroll down to the Watson Services section.

Click Add service and then Add to select Machine Learning.

If your Storage field is showing as unpopulated, click Cloud Object Storage.


- Click Add to add Cloud Object Storage for Watson Studio.

You might need to go back to the previous step to associate the cloud object storage with your data science project.

- When you're done creating the project, click Create.

Verify that you have Watson Studio properly configured by opening your Studio profile.

Click the Apps tab. Then, check whether you have a Watson Studio application listed. If this is your first machine learning project, you will not see Watson Studio listed. If you don't have an application in the list, click Add other apps to add Watson Studio.


Go back to the Studio home page and click New Project. Select Data Science and give the project a name and description.


Make sure that the Storage field is populated with cloud-object-storage credentials. You might need to create IBM Cloud Object Storage and set your region appropriately for the credentials to appear on the Watson Studio project creation page.

You must use IBM Cloud Object Storage for reading input (such as training data) and for storing results, such as log files.

If your Storage field is showing as unpopulated, click Cloud Object Storage.



Click Add to add Cloud Object Storage for Watson Studio.

You might need to go back to the previous step to associate the cloud object storage with your data science project.

When you're done creating the project, click Create.



Optional: Skip the tutorial selections after you create the project.

### Create a machine learning model

In this section, you create a machine learning model. Models are created in the machine learning service and link back to data in the machine learning project.

If you're not already logged in, log in to the IBM Watson home page. Then, scroll down to Recently updated projects and select the data science project that you created. Then, select Assets.


Click Add to project and select the Watson Machine Learning asset type. Name the model and optionally provide a description.

Select the project that you created and click Associate a Machine Learning service instance.

You can now create a new service or use an existing one.

If you do not have a service, select the appropriate plan and click Create. If you already have a service, click Existing and select it from the list.

On the Watson Studio page, click Reload.

he service should then get populated.

Select Model Builder because you want the system to do this for you.

Associate an Apache Spark instance. Similar to connecting the Machine Learning service, click Associate an IBM Analytics for Apache Spark instance.

If you have an existing service, go to the Existing tab and select the service. If you need to create a service, follow the instructions in the New tab.

Click Reload.

Select Manual so that you can prepare the data and select the models yourself.

Click Create in the bottom right corner. In the Select Data Asset page, click Add Data Assets.

Click Load and browse for the cats and dogs CSV file. On a Mac, it's the soundmac.csv file.

Select the file that you just uploaded in the main page. You might need to refresh the page to see the file. Then, click Next.

You are asked which columns you want to predict. If you open the spreadsheet, notice that the columns are all numbered COLUMN1, COLUMN2, and so on. COLUMN1 specifies whether the audio file was a cat or a dog, which is what you want to predict.

Select COLUMN1 from the Column value to predict menu. For Feature columns, you can decide which columns to use. For this project leave it as All (default) because all the remaining columns are significant.

Select Binary Classification because you are building a model that is for cats and dogs only.

Leave the validation split at 60, 20, 20. This will use 60% of the data to train the models, 20% to test the models, and 20% as a check of the better performing models to detect overfitting.

Overfitting models perform well on training and test data that is used to build and choose a model but perform poorly on holdout data.


On the right side of the page, click Add Estimators.

Select all available estimators. By selecting all of them, you can see which model gives the best results for the data set. Click Add. Then, click Next.

The models will then be trained.

Wait until all four models have run.

Analyze the Performance, Area under roc curve, and Area under pr curve columns. Select the model with the best performance and highest scoring curve columns, in this case, the Random Forest Classifier. Then, click Save.

Now you have a model that will predict a value of cat or dog from an audio file. To be able to use this in a Node-RED application (or as an API for a different application), you must deploy it.

### Deploy the machine learning model

In this section, you deploy the new machine learning model so that applications can use it to make predictions.

Click Deployments.

On the right side of the page, click Add Deployment.

Give the deployment a name (and optional description), select Web service, and then click Save.

Wait for the model to deploy. The status will show DEPLOY_SUCCESS when it is complete. If it fails to deploy, try refreshing the browser after a few minutes. Alternatively, delete that deployment and follow these steps again.

Click the name of the deployment. On this page, note the deployment ID, which you will need later to call the predictor in your Node-RED application.

The Implementation tab shows you the scoring endpoint and the sample source code.

Next, you need to find and record your machine learning credentials in IBM Cloud.

Click the navigation menu icon and select Services > Watson Service.

In the list of services, click your machine learning service and then click Service credentials.

Make a note of the service credentials because you will need them in the next lab.

# PART 3
By now, you should have created Machine Learning models for the dog and cat audio files in Watson Studio.

In this lab, you use the machine learning model that you created in Lab 2 to make predictions on audio files selected from your file system by using a Node-RED application.

Be sure that you installed the IBM Cloud command-line interface and other course prerequisites, and completed all previous labs.

The code for this lab is on https://github.com/ibm-early-programs/animal-sounds

### Predict the animal sound


In this section, you will use Node-RED and dummy data to make a dog or cat prediction against the machine learning model that you created in Lab 2.

Log in to IBM Cloud.

If you haven’t created an instance of Node-RED, create one:

In IBM Cloud, click Catalog > Starter Kits > Node-RED Starter.

Enter an application name and domain.

The application name must be unique because it will be publicly addressable. Most likely the name catsdogs is already taken. The domain for this application does not need to match the domain that you used for Watson Studio.

Click Create. It might take some time for your instance to be created and started.

After your instance of Node-RED is running, click Visit App URL.

Optional: Secure your Node-RED instance with a user name and password.

Click Next and Next again to complete the setup. Then, click Go to your Node-RED flow editor.

Log in in to your Node-RED instance by using the credentials that you previously specified.

Next, you will be importing a prebuilt flow into your Node-RED instance. This flow will allow you to upload a file and run it through the machine learning model that you created in Lab 2.

Open a new tab and go to the GitHub repository for this course and select the noderedflows folder.


Select the predictionflow.json file.

Click Raw and copy the file contents to your clipboard. By clicking Raw, you can copy the raw data without having any unnecessary data on the clipboard that will result in errors when pasting.

Back in your Node-RED instance, click the menu icon and click Import > Clipboard.

Paste your clipboard contents into the field and click Import.

You might see a number of unknown nodes that appear in the imported flow, particularly if you created your Node-RED instance for this lab. This is because the Node-RED starter kit comes preinstalled only with certain nodes. You will install the additional nodes in the next steps.


Click the menu and click Manage palette. Then, select the Install tab.

Search for watson-machine-learning.

Click Install. Then, click Install again to confirm the installation.

Install two more nodes: node-red-contrib-browser-utils, which contains a microphone, and node-red-node-base64. The flow should now show all nodes.


Click Deploy. Ignore any warnings about the new nodes. You will configure those nodes in the next few steps.

Your application is now deployed and is ready for you to test. Before experimenting with an audio file, you will start with a hardcoded test to check that the prediction is working.

The hardcoded test is the subflow near the bottom.

The hardcoded values are specified in the Build Payload Values function node. Note that the columns start from COLUMN2 because COLUMN1 is the value that the machine learning model will be predicting.

Initiate the flow by using the blue tab on the left of the Hard Coded Test node.

Click the Debug tab. Depending on your version of Node-RED, you might need to click the Debug icon to show the debug messages pane.

You should see a "No Configuration Found" error message. This occurs because the Watson Machine Learning node (Run Prediction) has not been configured.

Double-click the machine learning node (Run Prediction).

Click the Pencil icon to edit the WML Connection configuration. Then, complete the configuration by using your machine learning credentials. The Access Key can be any non-empty value.

To find your credentials, select the service from IBM Cloud and click Credentials. If your machine learning credentials don’t include an access key, then enter dummy text into that field. Then, click Update when you're done.

Refetch the Model List.

This will temporarily hide the mode and deployments fields because the node invokes Watson Machine Learning APIs to retrieve a revised list. After the new lists are retrieved, the fields will reappear. Depending on network latency, this might a while to complete. If the fields are not displayed, click Done, click Deploy, and open the node again.

Set the mode to Run Prediction. Then, select your model and deployment.

Click Done to save the configuration and deploy the updated flow.

Initiate the flow by clicking the left tab.

Check the output. In this hardcoded test, there is an 84% probability that the sound was of a cat.

You can now make predictions of sampled audio files, but you can't feed an audio file directly into the Node-RED flow. To be able to do this, you need the audio sampling functionality to be available as an API. You will do this in the next section.





