# LAB 2 - Use the ML model from a web application 

Create a Node-RED application (web page) where you can run predictions against audio files and see the results.

- [Create a Node-RED application](#create-a-node-red-application)
- [Create your first flow](#create-your-first-flow)
- [Add new nodes](#add-new-nodes)
- [Import the application flow](#import-the-application-flow)
- [Configure your application](#configure-your-application)
- [Test the application](#test-the-application)
- [Summary](#summary)


## Create a Node-RED application

**Node-RED** is a visual tool for wiring the internet of things - connecting hardware devices, APIs and online services in a new and interesting way. Node-RED provides a browser-based flow editor that makes it easy to wire together flows using the wide range nodes in the palette. Flows can be then deployed to the runtime in a single click.

1. In a browser navigate to https://cloud.ibm.com/

Select '_LOG IN_' with your IBM id (your email). After login you should see your IBM Cloud dashboard. 

2. Click the _**Create Resource**_ button at the top right 

<img src="/images/create-resource.png" width="90%" height="90%">

3. Locate the **Node-RED starter** service, under Starter Kits, and click on it. This starter kit contains a Cloudant dabatase and SDK for Node.js. 

<img src="/images/nodered.png" width="40%" height="40%">

4. Enter a name for your application, for example: *dogsandcats* (host will automatically be completed). The hostname must be unique on IBM Cloud, so please if you use the example name add your initials or a number. 
Be creative and try to make a unique name then click '_CREATE_'. 

<img src="/images/appname.png" width="90%" height="90%">
 
Your application is now staging and will be up and running in a short while. Click 'OVERVIEW' to see information about your application. 

The application will be ready in a couple of minutes. If you want to check the progress click on the _LOGS_  icon on the left side menu. Go back to _Overview_ tab to see your app dashboard.

<img src="/images/logs.png" width="20%" height="20%">

5. When fully staged, click on the _Visit app URL_, next to the green or half green circle, this launches the Node-RED main page.

<img src="/images/app-overview.png" width="90%" height="90%">

*Note: If you are using Lite accounts your application will be in an awake mode. That means that if after 10 days your application has not been used IBM will stop it.*

6. Now you will set up a username and password to protect your flow. Click **Next** in the first window.

<img src="/images/node-red-next.png" width="60%" height="60%">

7. We are working in the public cloud that means that anyone can access your application through a web browser, set a username and password to protect your code. 

<img src="/images/node-red-username.png" width="60%" height="60%">

Write an username and a password of your choice and click 'Next'. Remember that it does not have to be related to your IBM Cloud ID. Let the browser remember the password if you are using your own laptop, it will come in handy later. 

<img src="/images/node-red-config.png" width="50%" height="50%">

<img src="/images/node-red-finnish.png" width="50%" height="50%">
 
**Your Node-RED flow is all set!**
 
8. Now click Go to your Node-RED flow editor to open the flow editor. Enter your credentials to access the editor.

<img src="/images/node-red-editor.png" width="80%" height="80%">

When using Node-RED we build our apps using this graphical editor interface to wire together the blocks we need. We can simply drag and drop the blocks from the left menu into the workspace in the center of the screen and connect them to create a new flow. 

## Create your first flow

Before we jump into the lab flow, let's get familiar with the Node-RED canvas. 

The **main pane** is the flow creation workspace in the middle. This is where you drag and drop nodes and connect them with wires. Along the top of the workspace pane is a set of tabs. Each tab opens a previously created workspace and shows any flows created using that workspace.

On the **left** is the node pane that contains all the built-in nodes that your instance of Node-RED supports. As you can see, nodes are grouped into categories. Opening up a category shows the individual nodes.

On the **right-hand** side is the output pane that can be toggled between the info and debug tabs. When info is selected, documentation for the selected node is shown there.  When debug is selected, it will display the output of debug nodes, errors and warnings.

The **Deploy button** is used when a flow has been constructed and causes the flow to be deployed onto the Node-RED system and executed. 

1. Drag and drop the following nodes to the canvas:

- **Inject**: The inject node is used to generate input into a flow and is one of the first nodes in the node palette under input.

<img src="/images/inject.png" width="20%" height="20%">

Double click on the inject node, select string and write a message then click **Done**.

<img src="/images/inject-edit.png" width="50%" height="50%">

- Debug
<img src="/images/debug.png" width="20%" height="20%">

2. Connect the nodes and click the deploy button in the Node-RED window (top right). You’ll see a pop-up saying the flow has been successfully deployed. You will also notice that the blue dots on the nodes disappear, indicating there are no un-deployed changes.

Now, before you try the flow, make sure the the debug tab is selected on the right pane. Then click on the left tab on the inject node and look at what appears in the debug pane. This will send the message and you will see it in the debug window on the right side. 

<img src="/images/testflow.png" width="80%" height="80%">


## Add new nodes

We are going to add new nodes to the Node-RED palette directly from the Node-RED window. For this lab we need the following nodes:

      - node-red-base64
      - node-red-contrib-browser-utils

1. In the Node-RED window click on the three lines on the top right corner and in the menu, click on the "Manage palette". This will open the node menu where you can add new nodes to your application. 

<img src="/images/manage-palette.png" width="30%" height="30%">

You will see the nodes that are installed by default and if you go to the 'install' tab you can search for any node package and add it directly to your app.

<img src="/images/install-nodes.png" width="80%" height="80%">
             
2. Search for the base64 nodes by writing 'base64'. This will return one node package, you need to install the package 'node-red-base64'. Click on install. 

<img src="/images/base64.png" width="90%" height="90%">
 
This will prompt a window to confirm the installation. Click on install and wait few minutes. Click "Done" to close the left side menu. 

<img src="/images/base64-installed.png" width="50%" height="50%">

After few seconds you will see the base64 node in your Node-RED palette.

3. Repeat the process for the **node-red-contrib-browser-utils** package. 


## Import the application flow

In this section we will build a simple flow to test our model sending cat and dog sounds using the microphone or via audio files. 

1. Copy the content of the **dog-car-flow.json** file. Open the file URL. [Dog-car-flow code](https://raw.githubusercontent.com/sandra-calvo/pets-ai/master/node-red-flows/dog-cat-flow.json?token=AI24OL2ZJJKOWJHL7F5WILK5PDKNG) 

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

This flow reads data from audio files or audio coming through the microphone on your computer, then the audio files are sent to a OSP converter application that converts the audio file into a buffer readable to our machine learning model. The input buffer is sent to out Machine Learning model created in the previous lab and we see the results in the debug tab of the Node-RED window. 

Your flow should look like this:

<img src="/images/node-red-flow.png" width="90%" height="90%">


## Configure your application

In order to connect your model with your application you need to edit few nodes. First, let's get the Machine Learning service API key. 

1. Go to IBM Cloud. If you closed it you can always access by opening https://cloud.ibm.com/ in a new tab.

2. Click on the hamburger menu on the left top corner. 

<img src="/images/hamburger-menu.png" width="20%" height="20%">

Then select **Resource List** to access all your services.

<img src="/images/resource-list.png" width="40%" height="40%">

3. Find the machine learning service under **Services**. Note that the name of your service will be different to the one in the picture. 

<img src="/images/ml-list.png" width="100%" height="100%">

Click on the name to access the service's details. 

4. In the left side menu go to **Service Credentials**. 

<img src="/images/service-credentials.png" width="20%" height="20%">

5. Click on **View credentials** and copy the API key. You can save the API key in a notepad. 

<img src="/images/view-credentials.png" width="100%" height="100%">

Let's go back to your Node-red application.
If you closed the Node-RED tab you can always find it in the IBM Cloud resource list. 

6. Double click the **Get token parameters** node and add your API key and click Done.

<img src="/images/edit-apikey.png" width="80%" height="80%">

7. Doble click on the **Model REST call** and add your machine learning endpoint. You saved this during lab 2. Click Done.

<img src="/images/edit-rest-call.png" width="80%" height="80%">

8. Deploy your application changes from the **Deploy** button on the top right side of the screen to save the changes. 

## Test the application

Let's try using a file!

1. Click on the left side of the file node to open your local's machine menu. 

<img src="/images/file-inject.png" width="20%" height="20%">

2. Select an audio file from the audio folder you downloaded as a part of this repository. Click open. 

<img src="/images/select-file.png" width="60%" height="60%">

This will initiate the flow. Send the file to the OSP converter, get the buffer and send it to the machine learning model. 

3. You will see the results in the debug tab on the right side of your screen. 

<img src="/images/file-inject-results.png" width="70%" height="70%">

Now test the microphone!

1. Click on the left side of the microphone node to start recording. 

<img src="/images/microphone.png" width="20%" height="20%">

2. Make cat or dog noices. :cat: :dog:

3. Click again on the microphone node to stop recording and send the audio to be processed. 

4. Check the results in the debug tab on the left side of your screen. 

## Summary
