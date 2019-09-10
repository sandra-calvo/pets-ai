# IBM Cloud :cloud: -  Pets & AI 
:robot: :heart: :dog: & :cat:
## Mimmitkoodaa workshop guide Fall 2019

In this guide:
  - [Introduction](#introduction)
  - [Lab 1 - Build a machine learning model using sound files](https://github.com/sandra-calvo/pets-ai/tree/master/Lab%201%20-%20ML%20model)
  - [Lab 2 - Call your model from a web application](https://github.com/sandra-calvo/pets-ai/tree/master/Lab%202%20-%20%20Web%20application)
  - [Lab 3 - Add visual recognition to your application](https://github.com/sandra-calvo/pets-ai/tree/master/Lab%203%20-%20Visual%20Recognition)
  - [Summary](#summary)


  #### Prerequisites
- IBM Cloud account
  - Create a free account https://cloud.ibm.com

- Download or clone this repository

<img src="/images/download-repo.png" width="60%" height="60%">
  
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


# SUMMARY


 
