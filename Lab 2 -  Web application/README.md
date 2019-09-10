
# LAB 2 - Use the ML model from a web application 

Create a Node-RED application (web page) where you can run predictions against audio files and see the results.

- [Create a Node-RED application](#create-a-node-red-application)
- [Create your first flow](#create-your-first-flow)
- [Add new nodes](#add-new-nodes)
- [Configure your application](#configure-your-application)
- [Get machine learning API Key](#get-machine-learning-api-key)
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

<img src="/images/logs.png" width="40%" height="40%">


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

## Add new nodes
We are going to add new nodes to the Node-RED palette directly from the Node-RED window. For this lab we need the following nodes:

      - node-red-dashboard
      - node-red-node-openweathermap

In the Node-RED window click on the three lines on the top right corner and in the menu, click on the "Manage palette". This will open the node menu where you can add new nodes to your application. 

<img src="/images/App23.png" width="20%" height="20%">

You will see the nodes that are installed by default and if you go to the 'install' tab you can search for any node package and add it directly to your app.

<img src="/images/App24.png" width="30%" height="30%">
             
Search for the dashboard nodes by writing 'dashboard'. This will return multiple node packages, you need to install the package 'node-red-dashboard'. Find it in the search results and click on install. 

<img src="/images/App25.png" width="30%" height="30%">
 
This will prompt a window to confirm the installation. Click on install and wait few minutes. Click "Done" to close the left side menu. 

<img src="/images/App26.png" width="50%" height="50%">

After few seconds you will see the new nodes in your Node-RED palette.

**Remember to repeat this process to install node-red-node-openweathermap package.** :partly_sunny:

## Configure your application

## Get machine learning API Key

## Test the application

## Summary
