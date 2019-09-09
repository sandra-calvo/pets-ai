# IBM Cloud :cloud: -  Pets & AI 
:robot: :heart: :dog: & :cat:
## Mimmitkoodaa workshop guide Fall 2019

In this guide:
  - [INTRODUCTION](#introduction)
  - [PHASE 1](#phase-1): Build a machine learning model using sound files
  - [PHASE 2](#phase-2): Call your model from a web application
  - [PHASE 3](#phase-3): Add visual recognition to your application
  - [SUMMARY](#summary)
 

  #### Prerequisites
- IBM Cloud account
  - Create a free account https://cloud.ibm.com
  
This lab is for developers who have little or no experience with machine learning or have never created and trained predictive models. No data science background required.
  
# INTRODUCTION

### Use Case

Have you ever had an annoying neighbour that complains about your dog barking when you are not at home? 
With this lab you will be able to prove to you neighbour that is not your dog who barks! :smiley: 

In this lab, you'll learn to create basic machine learning models that you train to recognize the sounds of dogs and cats. You'll also integrate visual recognition to identify images of these animals. You'll build a basic user interface in Node-RED that shows the results of the predictions for both sound and images.

You will learn to:

- Build a binary classification model that can predict which animal (dogs and cats) is making a specific sound
- Make predictions on audio files by using a Node-RED application built as a web page
- Create an application in Node-RED that integrates the Watson Visual Recognition service with your machine learning model to recognize images of cats and dogs

## Tools 

In this lab, you'll use IBM Watson Studio to build classification models to predict (identify) animal sounds and use IBM Watson Visual Recognition to identify images of those animals. You'll learn how best to gather and prepare data, create and deploy models, deploy and test a signal processing application, create models with binary and multiclass classifications, and display the predictions on a web page that you create by using Node-RED.

**IBM Watson Studio**:

**IBM Watson Machine Learning**:

**IBM Watson Visual Recognition**:

**Node-RED**: 


### Data

This lab uses the audio files located in the _**/audio_** folder. Feel free to download them. 

The source audio files were obtained from **Kaggle**. Kaggle is dedicated to data science and machine learning and hosts data sets that can be used to generate machine learning models. 

Audio files cannot be compared directly. They will be of differing lengths with varying lengths of opening silence before the start of the signature tune or noise. It is difficult to detect the start of the signature noise. It is not just the point at which there is no longer silence. You have no idea of how many bars into the tune the audio recording starts.

For audio files, you can use signal processing to create a series of numbers which represent each audio track. These numbers can be used to compare the tracks and be used as the basis of a machine learning model.

In this lab, we used a simplified digital signal processing application to convert the audio track into a table that represents a spectrogram with sound frequency and amplitude as the x and y coordinates. This makes the tracks comparable.
You can see the convertion output in the file: **sound.csv**.

If you are interested in processing other files, you can check the python script **ospconverter.py**.

# PHASE 1

## Build a machine learning model with sound

Create a machine learning project in Watson Studio. Then, use a **sound.csv** file to build and deploy a binary machine learning model that can predict whether a sound is coming from a cat or a dog.

In the first lab, you will create a prediction model that is based on the sounds of cats and dogs. During training, the model must be able to compare the audio files that form the training data to determine how to identify a dog barking and a cat purring.

We will create the machine learning model using **SPSS Modeler**. With SPSS Modeler flows in Watson Studio, you can quickly develop predictive models using business expertise and deploy them into business operations to improve decision making. 

### Set up the environment

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

### Create your first project


### Build the ML model 


### Deploy the ML model


# PHASE 2

## Use the ML model from a web application 

Create a Node-RED application (web page) where you can run predictions against audio files and see the results.

### Create a Node-RED application

### Configure Node-RED application

### Test the Node-RED application

# PHASE 3

## Add visual recognition to your application

Create two simple UIs in Node-RED: one for the birdsong models and one for the cats and dogs model. Then, integrate the IBM Watson Visual Recognition service to identify images of these animals.

## Configure Visual Recognition flow

### Test your application

# SUMMARY


 
