# LAB 3 - Create an UI for your application

  - [Modify your Node-RED flow](#modify-your-node-red-flow)
  - [Configure your application](#configure-your-application)
  - [Test your application](#test-your-application)
  - [Summary](#summary)

Now that your application is working on Node-RED and you tested your machine learning model is working we will create a simple UI to interact easier with your model. 

## Import new flow

In this step we will modify the Node-RED flow created in lab 2. 

1. Add an http input node, an http output node, and three template nodes. Connect them so that they look like this:

<img src="/images/connect_nodes.png" width="90%" height="90%">

2. Double-click the http input node and add a suitable URL ending in the URL field. This creates the web page URL. Then click 'Done'.

For example, adding a URL ending of /dogs_cats creates a full URL of https://< myNodeREDinstance>.au-syd.mybluemix.net/dogs_cats.

<img src="/images/http_input_edit.png" width="90%" height="90%">

3. For the third template node, make these changes. When you're finished, click Done.

Set the Name field to HTML.

Set Syntax Highlight to HTML. The Syntax Highlight box helps to color code the tags and other items for ease of use.

Paste the following code in the Template field:

```html
<html>
  <head>
    <title>Dogs and Cats Machine Learning Audio Prediction</title>
    <style>{{{payload.css}}}</style>
  </head>
  <body>
    <div>
        <div>
            <h1>Dogs and Cats Machine Learning Audio Prediction</h1>
            <h2>Cat or Dog?</h2>
        </div>

        <div>
            <p>
              <label for="audiofile">Select Audio File:</label>
              <input id="audiofile" type=file name=file accept="audio/*">
              <button onclick="javascript:onAudioSendClick()">
                Process Audio
              </button>
            </p>
        </div>

        <div id="cats-dogs-result" class="cats-dogs-result">
            <p>Result shows here</p>
        </div>
    </div>

    <script type="text/javascript" src="https://code.jquery.com/jquery-2.1.4.min.js"></script>
    <script>{{{payload.script}}}</script>

  </body>
</html>
```

## Configure your application

## Test your application

## Summary
