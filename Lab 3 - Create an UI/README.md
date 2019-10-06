# LAB 3 - Create an UI for your application

  - [Modify and configure your Node-RED flow](#modify-and-configure-your-node-red-flow)
  - [Test your application](#test-your-application)
  - [Summary](#summary)

Now that your application is working on Node-RED and you tested your machine learning model is working we will create a simple UI to interact easier with your model. 

## Modify and configure your Node-RED flow

In this step we will modify the Node-RED flow created in Lab 2. 
Make sure you start adding these nodes above your previous flow. You can select all nodes and move them lower if you need space. 

1. Add an http input node, an http output node, and three template nodes. Connect them so that they look like this:

<img src="/images/connect_nodes.png" width="90%" height="90%">

2. Double-click the **http input** node and add a suitable URL ending in the URL field. For example, **/dogs_cats**
This creates the web page URL. Then click 'Done'.

Adding a URL ending of /dogs_cats creates a full URL of https://< myNodeREDinstance>.mybluemix.net/dogs_cats.

<img src="/images/http_inputedit.png" width="70%" height="70%">

3. For the third template node, make these changes. When you're finished, click Done.

- Set the Name field to HTML.
- Set Syntax Highlight to HTML. The Syntax Highlight box helps to color code the tags and other items for ease of use.
- Paste the following code in the Template field:

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

This code creates a simple HTML page with a title, subtitle, an input field to select a file from your system, and a button to process the audio file. There is also space for the prediction result to show on the page.

The HTML page includes placeholders to the CSS and JavaScript code that you will create in the next few steps.

The node settings should look like this:

<img src="/images/html_template.png" width="90%" height="90%">

4. For the second template node, make these changes. When you're finished, click Done.

- Set the name to JavaScript. 
- Set the Syntax Highlight field to JavaScript.
- Set the property to msg.payload.script. This setting places the template contents on msg.payload.script that enables the HTML template reference to find and inject it at its placeholder. 
- Copy and paste the following code in the template field. 

```javascript
$(document).ready(function() {
  allofit();
});

function allofit() {
  javascriptCheck();
  uiHandlers();
}

function javascriptCheck() {
  $('#no-script').remove();
}

function uiHandlers() {
  var animalButton = $('#id_analyzeAnimal');
  animalButton.click(
    () => {
      runVRFor($('#id_listcatsdogs').val());
    });
}

function processNotOK() {
  console.log('Error Invoking AJAX');
  reportRESTError('Error Invoking AJAX');
}

function reportRESTError(msg) {
  $('#cats-dogs-result').append(createNewDiv(msg));
}

function onAudioSendClick() {
  var files = $('#audiofile');
  if (files && files['0'] && files['0'].files
            && files['0'].files[0]
            && files['0'].files[0]['name']) {
    var filename = files['0'].files[0]['name'];
    var audioBlob = files['0'].files[0];
	  var fd = new FormData();
    fd.append('fname', filename);
  	fd.append('audiodata', audioBlob);

    $.ajax({
  		type: 'POST',
      url: 'performAudioReco',
  		data: fd,
  		processData: false,
  		contentType: false,
      success: processAudioOK,
      error: processNotOK
  	});
  } else {
    reportRESTError('File not specified');
  }
}

function processAudioOK(response) {
  $('#cats-dogs-result').empty();
  var ok = false;
  if (response) {
    if (response.error) {
      reportRESTError(response.error);
    } else {
      ok = true;
      processAudioClassifiers(response);
    }
  }
  if (!ok) {
    reportRESTError('No Response from VR API');
  }
}

function processAudioClassifiers(response) {
  var table = $('#cats-dogs-result').append(createNewTable());
  table.append(createNewTableHeaders());
  var scoreColumn = 0;
  if ('dog' == response.results[3]) {
    scoreColumn = 1;
  }
  table.append(createNewTableRow(response.results[3], response.results[1][scoreColumn])) ;
}


function createNewDiv(message) {
  return $('<div></div>').text(message);
}

function createNewTable() {
  return $('<table border="1"></table>');
}

function createNewTableHeaders() {
  return $('<thead><tr><th>Name</th><th>Score</th></tr></thead>');
}

function createNewTableRow(classification, score) {
  return $('<tr><td><b>' + classification
                 + '</b></td><td><i>' + score
                 + '</i></td></tr>');
}
```

This code checks that the file that is uploaded by the user is an audio file, passes it to an API called performAudioReco, which you will create later in this lab, and returns the result by creating a new <div> element and inserting a table with the classification and score.

<img src="/images/javascript_template.png" width="90%" height="90%">

5. For the first template node, make these changes. When you're finished, click Done.

- Set the name to CSS.
- Set Syntax Highlight field to CSS.
- Set the property to msg.payload.css.
- Delete the text in the Template field.

<img src="/images/css_template.png" width="90%" height="90%">

The user interface used in this course is simple. Leave this file empty for now, but If you want to add your own styling to the interface, you can insert your CSS in this template node.

6. Deploy the application to save the changes. 
You should now have a small flow that looks like this:

<img src="/images/ui_flow.png" width="90%" height="90%">

7. Add another http input node, an http output node, and a function node and wire them together. Place the new nodes between the nodes that you just added and the microphone and base64 nodes.

<img src="/images/http_input_edit.png" width="90%" height="90%">

8. Edit the http input node and change the method to POST, and in the URL field, enter /performAudioReco. Select the Accept File Uploads checkbox and then click Done.

<img src="/images/http_input_edit.png" width="90%" height="90%">

9. Edit the function node and name it Locate Audio Buffer. Change the number of outputs to 2 at the bottom and paste in the following code. When you're finished, click Done.

```javascript
 if (msg.req && msg.req.files && 
       Array.isArray(msg.req.files) && 
       msg.req.files[0].buffer) {
           msg.payload = msg.req.files[0].buffer;
           return [null, msg];
} else {
  msg.payload = {'error' : 'No File Received'};
  return [msg, null];  
}
```
This code checks that a file has been passed in from the web page. If no file has been passed, it will throw an error.

The first output node should go to the http node that you just added.

10. Join the second output node to the base64 node.

<img src="/images/http_input_edit.png" width="90%" height="90%">

This part of the flow passes the audio file that was uploaded in the interface through the flow that you created in Lab 2 to run the machine learning model.

11. Wire the output node from the Just the results node to the http out node. You can also do this by using link nodes.

12. Deploy the application and switch back to your web page.
You should now be able to select an audio file from your file system and run a prediction by clicking Process Audio. The audio file should play, and the prediction will be returned in a table.

<img src="/images/http_input_edit.png" width="90%" height="90%">

The complete flow looks like this:

<img src="/images/http_input_edit.png" width="90%" height="90%">

## Test your application

Your Node-RED flow is ready. Test your application by going to your URL



## Summary

Congratulations! You created a web UI to interact with your machine learning model! Feel free too add some CSS to make it prettier. You can continue to Lab 4 and try the visual recognition service. 

