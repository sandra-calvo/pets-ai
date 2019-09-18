# LAB 4 - Add visual recognition to your application

In this lab you will set up the environment and all needed components for your machine learning model. 

  - [Create a visual recognition service](#create-a-visual-recognition-service)
  - [Get credentials](#get-credentials)
  - [Import Visual Recognition flow](#import-visual-recognition-flow)
  - [Configure Visual Recognition flow](#configure-visual-recognition-flow)
  - [Test your application](#test-your-application)
  - [Summary](#summary)
  
## Create a visual recognition service 

The Watson  Visual Recognition service allows to analyze the contents of an image and produce a series of text classifiers with a confidence index. 



## Get credentials 



## Import Visual Recognition flow

Back in Node-RED. 

1. Copy the content of the **visual_recognition_flow.json** file. Open the file URL. [visual_recognition_flow code](https://raw.githubusercontent.com/sandra-calvo/pets-ai/master/node-red-flows/dog-cat-flow.json?token=AI24OL2ZJJKOWJHL7F5WILK5PDKNG) 

Use the keyboard shortcuts to select all content and copy it.
    
  OSx
    <kbd>Cmd</kbd>+<kbd>A</kbd> -->
    <kbd>Cmd</kbd>+<kbd>C</kbd>

  Windows
    <kbd>Ctrl</kbd>+<kbd>A</kbd> -->
    <kbd>Ctrl</kbd>+<kbd>C</kbd>

2. Import the flow by simply clicking on the 3 white lines on the top right corner of the Node-RED window.  Import - Clipboard.

<img src="/images/import-flow.png" width="50%" height="50%">

3. Paste the text you copied from the file and click Import.

<img src="/images/import-code.png" width="50%" height="50%">

4. Deploy your application changes from the **Deploy** button on the top right side of the screen to save the changes.

The flow will present a simple web page with a text field of where to input the image's URL, then submit it to Watson Visual Recognition. It will output the labels that have been found on the reply Web page.

Your flow should look like this:

 <img src="/images/visual_recognition_flow.png" width="90%" height="90%"> 

## Configure Visual Recognition flow

1. Double click on the Visual Recognition node.  <img src="/images/visual_recognition_node.png" width="10%" height="10%"> 

2. Paste the API key you saved in the first part of this lab, when you created the visual recognition service. 

 <img src="/images/visual_recognition_service_credentials.png" width="90%" height="90%"> 
 
 3. Click Done and then Deploy changes. 


## Test your application

To run the web page, point your browser to:

- London region: `http://yourAppName.eu-gb.mybluemix.net/reco` 
- Frankfurt region: `http://yourAppName.eu-de.mybluemix.net/reco` 
- US region: `http://yourAppName.mybluemix.net/reco` 
- Sydney region: `http://yourAppName.au-syd.mybluemix.net/reco` 

Enter the URL of an image. The URL of the pre-selected images can be copied to clipboard and pasted into the text field.

The Watson Visual Recognition API will return an array with the recognized features, which will be formatted in a HTML table by the template:

<img src="/images/visual_recognition_web.png" width="80%" height="80%">

## Summary

Congratulations! You completed the last lab of this workshop! :+1:


