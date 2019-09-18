# IBM Cloud :cloud: -  Pets & AI 
:robot: :heart: :dog: & :cat:
## Mimmitkoodaa workshop guide Fall 2019

In this workshop:
  - [Introduction](#introduction)
  - [Lab 0 - Set up the environment](https://github.com/sandra-calvo/pets-ai/tree/master/Lab%200%20-%20Set%20up%20the%20environment)
  - [Lab 1 - Build a machine learning model using sound files](https://github.com/sandra-calvo/pets-ai/tree/master/Lab%201%20-%20ML%20model)
  - [Lab 2 - Call your model from a web application](https://github.com/sandra-calvo/pets-ai/tree/master/Lab%202%20-%20%20Web%20application)
  - [Lab 3 - Create a UI for your application](https://github.com/sandra-calvo/pets-ai/tree/master/Lab%203%20-%20Create%20an%20UI)
  - [Lab 4 - Add visual recognition to your application](https://github.com/sandra-calvo/pets-ai/tree/master/Lab%204%20-%20Visual%20Recognition)
  - [Summary](#summary)


# INTRODUCTION

 - [Prerequisites](#prerequisites)
 - [Use Case](#use-case)
 - [Tools](#tools)
 - [Data](#data)
 - [Summary](#summary)

## Prerequisites
- IBM Cloud account
  - Create a free account https://cloud.ibm.com

- Download or clone this repository

<img src="/images/download-repo.png" width="60%" height="60%">
  
This lab is for developers who have little or no experience with machine learning or have never created and trained predictive models. No data science background required.
  

## Use Case

Have you ever had an annoying neighbour that complains about your dog barking when you are not at home? 
With this lab you will be able to prove to you neighbour that it's not your dog who barks! :smiley: 

In this lab, you'll learn to create basic machine learning models that you train to recognize the sounds of dogs and cats. You'll also integrate visual recognition to identify images of these animals. You'll build a basic user interface in Node-RED that shows the results of the predictions for both sound and images.

You will learn to:

- Build a binary classification model that can predict which animal (dogs and cats) is making a specific sound
- Make predictions on audio files by using a Node-RED application built as a web page
- Create an application in Node-RED that integrates the Watson Visual Recognition service with your machine learning model to recognize images of cats and dogs

## Tools 

In this lab, you'll use IBM Watson Studio to build classification models to predict (identify) animal sounds and use IBM Watson Visual Recognition to identify images of those animals. You'll learn how best to gather and prepare data, create and deploy models, deploy and test a signal processing application, create models with binary and multiclass classifications, and display the predictions on a web page that you create by using Node-RED.

- IBM Watson Studio: Watson Studio democratizes machine learning and deep learning to accelerate infusion of AI in your business to drive innovation. Watson Studio provides a suite of tools and a collaborative environment for data scientists, developers and domain experts.

- IBM Watson Machine Learning: Full-service IBM Cloud offering that makes it easy for developers and data scientists to work together to integrate predictive capabilities with their applications. The Machine Learning service is a set of REST APIs that you can call from any programming language to develop applications that make smarter decisions, solve tough problems, and improve user outcomes.

- IBM Watson Visual Recognition: Find meaning in visual content! Analyze images for scenes, objects, and other content. Choose a default model off the shelf, or create your own custom classifier. Develop smart applications that analyze the visual content of images or video frames to understand what is happening in a scene.

- Node-RED: A programming tool for wiring together hardware devices, APIs and online services in new and interesting ways.
It provides a browser-based editor that makes it easy to wire together flows using the wide range of nodes in the palette that can be deployed to its runtime in a single-click.


### Data

This lab uses the audio files located in the _**/audio_** folder. 

The source audio files were obtained from **Kaggle**. Kaggle is dedicated to data science and machine learning and hosts data sets that can be used to generate machine learning models. 

Audio files cannot be compared directly. They will be of differing lengths with varying lengths of opening silence before the start of the signature tune or noise. It is difficult to detect the start of the signature noise. It is not just the point at which there is no longer silence. You have no idea of how many bars into the tune the audio recording starts.

For audio files, you can use signal processing to create a series of numbers which represent each audio track. These numbers can be used to compare the tracks and be used as the basis of a machine learning model.

In this lab, we used a simplified digital signal processing application to convert the audio track into a table that represents a spectrogram with sound frequency and amplitude as the x and y coordinates. This makes the tracks comparable.

If you are interested in processing other files, you can check the python script **ospconverter.py**.


## Summary


 
