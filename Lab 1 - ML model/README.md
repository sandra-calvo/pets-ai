# LAB 1 - Build a machine learning model with sound


In this lab you will build a machine learning model with audio files:

  - [Build the machine learning model](#build-the-machine-learning-model)
  - [Deploy the model](#deploy-the-model)
  - [Test your model](#test-your-model)
  - [Save your credentials](#save-your-credentials)
  - [Summary](#summary)

Create a machine learning project in Watson Studio. Then, use a **sound.csv** file to build and deploy a binary machine learning model that can predict whether a sound is coming from a cat or a dog.

In the first lab, you will create a prediction model that is based on the sounds of cats and dogs. During training, the model must be able to compare the audio files that form the training data to determine how to identify a dog barking and a cat purring.

We will create the machine learning model using **SPSS Modeler**. With SPSS Modeler flows in Watson Studio, you can quickly develop predictive models using business expertise and deploy them into business operations to improve decision making. 


## Build the machine learning model 

1. We will build the machine learning model using SPSS Modeler. Click on **Add to project** button on the top menu. 

<img src="/images/add-to-project.png" width="20%" height="20%">

2. Then select **Modeler flow**. 

<img src="/images/modeler.png" width="80%" height="80%">

3. Give your modeler flow a name and keep the default options selected - Modeler Flow & IBM SPSS Modeler. Then click on **Create**.

<img src="/images/modelerflow.png" width="80%" height="80%">

4. You will access an empty canvas where we will drag and drop nodes from the left menu and configure them to create our machine learning model. Note how easy it is to create a machine learning model with no code. 

<img src="/images/canvas.png" width="80%" height="80%">

5. From the left side menu find the node **Data Assets** under the Import category. Drag and drop the node to the canvas.
You can use the Data Asset import node to pull in data from remote data sources using connections. You can also pull in data from an Excel file (.xls) or a .csv file. 

<img src="/images/data-assets.png" width="15%" height="15%">

Double click on the data assets node and you will see a new menu open in the rights side of the screen. Click on the **Change data asset** button. 

<img src="/images/data-assets-menu.png" width="30%" height="30%">

Select Data Assets and file sound.csv, then click OK.

<img src="/images/select-data-set.png" width="80%" height="80%">

Now you will see your file listed as the data asset in use. Click **Save** to save the changes and go back to the canvas. 

<img src="/images/data-asset-added.png" width="40%" height="40%">

6. Find the **Partition** node under Field Operations. Drag and drop the node and connect it to the Data Asset node. 

Partition nodes are used to generate a partition field that splits the data into separate subsets or samples for the training, testing, and validation stages of model building. By using one sample to generate the model and a separate sample to test it, you can get a good indication of how well the model will generalize to larger datasets that are similar to the current data.

<img src="/images/partition-node.png" width="15%" height="15%">

Double click on the Partition node and select a training partition of 80% and a testing partition of 20%. Then click Save. 

<img src="/images/partition-menu.png" width="30%" height="30%">

7. From the node menu select **Type** under Field Operations and move it to the canvas after the partition node. Connect the partition and the type node. Type node specifies the type of the parameters in the data set. 

<img src="/images/type-node.png" width="15%" height="15%">

Double click on the Type node and click on **Read Values**, this will read the data set and detect the data type. Make sure you select COLUMN1 as the target. This is the value we want to predict. Then click Save. 

<img src="/images/type-menu.png" width="80%" height="80%">

8. From the node palette find a node called **Auto Classifier** located under Modeling. Connect the Type node to the Auto Classifier. 

The Auto Classifier node estimates and compares models for either nominal (set) or binary (yes/no) targets, using a number of different methods, enabling you to try out a variety of approaches in a single modeling run. You can select the algorithms to use, and experiment with multiple combinations of options. 

<img src="/images/autoclassifier-node.png" width="15%" height="15%">

Your flow should look like this:

<img src="/images/modeler-flow-init.png" width="80%" height="80%">

9. Run the flow by clicking the play button on the top menu. This will take few minutes. 

<img src="/images/play.png" width="60%" height="60%">

10. Running the flow created a new orange node. 

<img src="/images/modeler-flow1.png" width="80%" height="80%">

11. Now delete the line connecting the **Type** node and the orange node. Double click on the line to delete it. 

<img src="/images/delete-line.png" width="80%" height="80%">

12. Drag a **Data assets** node and put it under the **Type** node. 

Double click on the data assets node and you will see a new menu open in the rights side of the screen. Click on the **Change data asset** button. 

<img src="/images/data-assets-menu.png" width="30%" height="30%">

Select Data Assets and file shaped_sound.csv, then click OK.

Now you will see your file listed as the data asset in use. Click **Save** to save the changes and go back to the canvas. 

13. Connect the new Data assets node to the orange node. 

14. Find a **Table** node and connect it to the orange node output. 

<img src="/images/table-node.png" width="15%" height="15%">

Your modeler flow should look like this:

<img src="/images/modeler-flow2.png" width="80%" height="80%">

15. Click on the 3 dots in the Table node and from the menu select **Save branch as a model**.

<img src="/images/save-branch.png" width="40%" height="40%">

16. Give your model a name and click Save.

<img src="/images/save-model.png" width="60%" height="60%">

Close the pop-up window and you will be redirected to the SPSS canvas. 

<img src="/images/model-saved.png" width="50%" height="50%">

From the top menu click on your project name to go back to the project main page. Note that in this lab we called our project Machine Learning. 

<img src="/images/go-back-menu.png" width="50%" height="50%">


## Deploy the model

You should be back in your project window. Let's deploy our model!

When you deploy the model, you are making it available to process new data and return confidence scores about how well the new data aligns with the rules the model established during processing. 

1. Go down to Models and you will see your new model listed.

<img src="/images/models-list.png" width="100%" height="100%">

2. Click on your model. You will see a summary of your model's information. Go to deployments.

<img src="/images/model-overview.png" width="100%" height="100%">

3. Select the right side button **Add deployment**.

This will be using the Watson Machine Learning service we created in the beginning of the lab. 

<img src="/images/new-deployment.png" width="100%" height="100%">

4. Give your deployment a name and click Save. This will create a web service and you will be able to access your deployment through an API endpoint to analyze data.

<img src="/images/new-deployment-name.png" width="60%" height="60%">

Check the status of the deployment. It will go from Initializing to Deploy_Success in few minutes. Refresh the page to see the changes. 

## Test your model 

Now that you have a machine learning model deployed we can test it. 

1. Click on the deployment's name. 

<img src="/images/deployment.png" width="100%" height="100%">

2. Now you see your deployment's information. Click on **Test** to test your model 

<img src="/images/deployment-overview.png" width="80%" height="80%">

3. In this window we can write the input values of our model and see the prediction. Since our model accepts over 100 columns we will not input each value manually. 

Click on the page icon to access the payload input field. 

<img src="/images/test-model.png" width="50%" height="50%">

For a **cat** introduce the following text then click on **Predict**:

```json
{"fields" : ["COLUMN2","COLUMN3","COLUMN4","COLUMN5","COLUMN6","COLUMN7","COLUMN8","COLUMN9","COLUMN10","COLUMN11","COLUMN12","COLUMN13","COLUMN14","COLUMN15","COLUMN16","COLUMN17","COLUMN18","COLUMN19","COLUMN20","COLUMN21","COLUMN22","COLUMN23","COLUMN24","COLUMN25","COLUMN26","COLUMN27","COLUMN28","COLUMN29","COLUMN30","COLUMN31","COLUMN32","COLUMN33","COLUMN34","COLUMN35","COLUMN36","COLUMN37","COLUMN38","COLUMN39","COLUMN40","COLUMN41","COLUMN42","COLUMN43","COLUMN44","COLUMN45","COLUMN46","COLUMN47","COLUMN48","COLUMN49","COLUMN50","COLUMN51","COLUMN52","COLUMN53","COLUMN54","COLUMN55","COLUMN56","COLUMN57","COLUMN58","COLUMN59","COLUMN60","COLUMN61","COLUMN62","COLUMN63","COLUMN64","COLUMN65","COLUMN66","COLUMN67","COLUMN68","COLUMN69","COLUMN70","COLUMN71","COLUMN72","COLUMN73","COLUMN74","COLUMN75","COLUMN76","COLUMN77","COLUMN78","COLUMN79","COLUMN80","COLUMN81","COLUMN82","COLUMN83","COLUMN84","COLUMN85","COLUMN86","COLUMN87","COLUMN88","COLUMN89","COLUMN90","COLUMN91","COLUMN92","COLUMN93","COLUMN94","COLUMN95","COLUMN96","COLUMN97","COLUMN98","COLUMN99","COLUMN100","COLUMN101","COLUMN102","COLUMN103","COLUMN104","COLUMN105","COLUMN106","COLUMN107","COLUMN108","COLUMN109","COLUMN110","COLUMN111","COLUMN112","COLUMN113","COLUMN114","COLUMN115","COLUMN116","COLUMN117","COLUMN118","COLUMN119","COLUMN120","COLUMN121","COLUMN122","COLUMN123","COLUMN124","COLUMN125","COLUMN126","COLUMN127","COLUMN128","COLUMN129","COLUMN130","COLUMN131","COLUMN132","COLUMN133","COLUMN134","COLUMN135","COLUMN136","COLUMN137","COLUMN138","COLUMN139","COLUMN140","COLUMN141","COLUMN142","COLUMN143","COLUMN144","COLUMN145","COLUMN146","COLUMN147","COLUMN148","COLUMN149","COLUMN150","COLUMN151","COLUMN152"],"values" : [[2.9999136161521376,7.0642554870466014,-0.7008103994356188,8.053854718947424,-0.8779088352217362,8.323649661431926,-37.049054311662985,-22.019168313265887,105.46535172621935,5.193712062231059,14.290785613587282,-5.95665173464119,-2.4001816822475037,20.2368616998849,-100.81068469248302,161.57361716269094,-5.081254184132196,101.81288597652797,-50.18229563169662,51.72786781569367,19.808826482184962,-6.487970124503255,-1.1055003999803414,8.788123568727258,-2.531402096799536,8.345219256145398,21.43374432780269,15.134561006582803,-13.087116130593007,-12.011697276034166,-42.193679427080255,-11.121402731864368,-11.443613209229298,-0.09366210044132606,-8.330976540865725,0.3693040032039052,-3.7295857251555864,1.0054415025052583,-9.907550847054514,-8.27422634687937,-21.343661952743705,-9.728353622631701,-1.8541398696903324,11.043400039969317,6.564610233721918,5.524179269953645,0.8837344749301397,-12.667123235628509,15.125254770788757,-5.857575753394602,-7.085891594779891,0.6242868349221542,4.659399312651821,9.240263482576164,5.154938299698183,-0.9506866901810263,1.2654507262405232,0.4732565687984245,1.0532568935459872,1.0259057914183636,-0.8922574021996792,2.6613988145233485,4.183198047180496,-0.10296610679503226,-0.8962816396712906,2.57931500645791,1.0579696507468501,4.472339296353505,0.12458623523480838,-6.636733025724768,0.09634539772593698,1.075467861492609,-0.3202109315971988,-1.6822300962998602,0.22315044707861809,2.651317880316439,-2.344717998237604,0.16018176376845106,-0.70478145213041,-9.147208884865133,5.879716260852504,-0.5046210114360188,-0.1419776300088671,-0.5076896381043339,1.3208140922954028,-1.7277083070804968,-0.10552197364255478,2.3388267035839645,1.7972681091350566,-0.5488374784331664,-1.8388782013551106,-0.9106976822263597,0.3830621054190537,-0.016302595499571026,0.38101991409442215,-0.38610750974400965,-1.4890884280817134,-2.014773757188162,2.229130463721263,0.15251725240594904,0.11094064340399168,-1.2243471231153107,1.5048893997331856,1.9187678196458018,1.2217895276071644,1.5841182354296497,0.9445676330629844,0.16700513960324703,0.49303870369711245,0.15343413796233651,-2.6344867394233002,0.27164652890299945,-0.8244250155331843,-0.30602609937398206,-0.14978944543104156,-1.6066276894896696,0.7107629609749964,0.2946316695954243,-1.0588855045504915,0.6412436941035247,0.9378487968718314,0.22591012551218004,-0.7925921893765251,-0.6221053474742391,0.2574644655578524,-0.12154192498737171,0.6853759018751386,-0.7929742927205672,1.036336292266462,-0.5855675567962102,0.03646805627441618,0.273586571424822,0.05013189038289312,0.31260720249065344,0.028720307081933072,0.16017347797604664,-0.13970435763135924,-0.19927041692407155,-0.11121340051484818,0.11701648065887715,-0.1991517955528339,0.03576788358142191,-0.2728486231353835,-0.24117169898716284,0.3565073723412553,0.24951739392465289,0.11403653782295975,0.0066911841963874785,0.0552146121292898,-0.15586420132499956,0.0766671071589291]]}
```

As a result you your see in the bottom of the response Cat and the probablity of the prediction.

<img src="/images/test-results-cat.png" width="50%" height="50%">

You can try a **dog** prediction too using the following code:
```json
{"fields" : ["COLUMN2","COLUMN3","COLUMN4","COLUMN5","COLUMN6","COLUMN7","COLUMN8","COLUMN9","COLUMN10","COLUMN11","COLUMN12","COLUMN13","COLUMN14","COLUMN15","COLUMN16","COLUMN17","COLUMN18","COLUMN19","COLUMN20","COLUMN21","COLUMN22","COLUMN23","COLUMN24","COLUMN25","COLUMN26","COLUMN27","COLUMN28","COLUMN29","COLUMN30","COLUMN31","COLUMN32","COLUMN33","COLUMN34","COLUMN35","COLUMN36","COLUMN37","COLUMN38","COLUMN39","COLUMN40","COLUMN41","COLUMN42","COLUMN43","COLUMN44","COLUMN45","COLUMN46","COLUMN47","COLUMN48","COLUMN49","COLUMN50","COLUMN51","COLUMN52","COLUMN53","COLUMN54","COLUMN55","COLUMN56","COLUMN57","COLUMN58","COLUMN59","COLUMN60","COLUMN61","COLUMN62","COLUMN63","COLUMN64","COLUMN65","COLUMN66","COLUMN67","COLUMN68","COLUMN69","COLUMN70","COLUMN71","COLUMN72","COLUMN73","COLUMN74","COLUMN75","COLUMN76","COLUMN77","COLUMN78","COLUMN79","COLUMN80","COLUMN81","COLUMN82","COLUMN83","COLUMN84","COLUMN85","COLUMN86","COLUMN87","COLUMN88","COLUMN89","COLUMN90","COLUMN91","COLUMN92","COLUMN93","COLUMN94","COLUMN95","COLUMN96","COLUMN97","COLUMN98","COLUMN99","COLUMN100","COLUMN101","COLUMN102","COLUMN103","COLUMN104","COLUMN105","COLUMN106","COLUMN107","COLUMN108","COLUMN109","COLUMN110","COLUMN111","COLUMN112","COLUMN113","COLUMN114","COLUMN115","COLUMN116","COLUMN117","COLUMN118","COLUMN119","COLUMN120","COLUMN121","COLUMN122","COLUMN123","COLUMN124","COLUMN125","COLUMN126","COLUMN127","COLUMN128","COLUMN129","COLUMN130","COLUMN131","COLUMN132","COLUMN133","COLUMN134","COLUMN135","COLUMN136","COLUMN137","COLUMN138","COLUMN139","COLUMN140","COLUMN141","COLUMN142","COLUMN143","COLUMN144","COLUMN145","COLUMN146","COLUMN147","COLUMN148","COLUMN149","COLUMN150","COLUMN151","COLUMN152"],"values" : [[-14.406518813369349,1.7273610526814314,-0.09084235082153325,-0.4762979627661598,1.8542652800699948,16.937972991303532,17.835703105712554,-6.87092023558417,-20.93629821319206,-19.940461831556846,15.214167015480378,-113.36581846376268,-17.272175870128297,38.54308178172622,30.58080392894969,11.185961178051247,-21.63093818313139,-16.804415607505117,-8.990164566357453,-57.9310995585435,-34.62840863195788,3.747919712263433,-3.7441628408563044,-2.7964812485381536,-17.847052196818666,-2.5275668160720843,-25.685443394453358,15.91056394219856,-16.28494986810471,-2.2827860209795414,7.452494653548147,21.137145637554013,1.6666474157633107,-12.503898743214082,3.824402575388445,-8.370263856052809,-0.36970722982211773,-1.8840136502398814,0.8417513233030212,-0.6705451751466261,3.3001011398373183,1.136872404379091,1.3861767357150594,0.047836799151006026,-0.13335402330005053,-0.7789985507581911,-2.349870616322012,-1.457035488010247,-0.1191982590281011,-2.9037137971307985,1.8079144330030232,0.44274675254519913,0.2900134851166922,0.5170786267596625,-2.2809560490372904,-1.2738507289083962,-0.195808055312658,-0.3369449693117226,-0.8760967050113329,-0.4883173238629026,-0.15494942487099816,0.550620876335348,0.5048274180474142,0.0031494741602369203,-0.2101271797427131,-0.42874890677757627,0.2225450533037634,-0.28294485144396875,-0.12667929095224828,0.0665633806144128,-0.0688381988586011,-0.06147800466249621,0.23804849110492354,-0.04742942105943784,-0.32165062659885735,0.03297013689957207,0.3056983454363103,-1.2438096164145396,-0.050003998255113785,-0.2095357543585919,-0.6719589927387852,0.3700120002685501,-0.6430307427540366,-0.03226410848224193,0.061325181465220036,-0.02473626767050785,0.1217931534300547,0.14662032056674779,-0.0378392999359356,0.16197376041489164,-0.01408017289406982,-0.253429229974933,-0.06025561057359852,-0.04676320370202591,-0.035386204667369636,-0.036911656914083935,-0.05891895951198478,0.0014495771729619022,-0.028211527757564525,-0.04550564022848158,-0.020212074478502373,-0.06627916842980675,-0.09105397090458744,-0.09292262951526542,-0.035498056821605894,-0.030539824634874813,-0.07707522978424852,-0.07937404345623111,-0.035527005512223875,-0.0292074794915978,-0.25187430843900527,-0.14097450253604776,-0.021117115197855918,-0.17895918963842172,0.06303133604859784,0.05236241759762317,0.11382282595579607,-0.17680708998210054,-0.17976994233507426,-0.005734732159847766,-0.0063321772736628645,0.2512400088271517,-0.17109285890328296,-0.308593839465896,-0.12211314127582185,-0.09997345466011076,0.10286928746488552,0.019541964952818347,-0.2342520594393368,0.17402160204815154,0.053098266628484936,-0.1488166829676003,0.03821731379284543,0.058878398327853354,-0.11280646323788801,-0.031499383190507046,-0.056101363072805555,0.0032674406110295706,0.07605789333039326,0.0795873995072256,0.26366732465872156,0.006483065366545304,0.043980446970464104,-0.015078911754922153,0.035844843785883373,0.27622494286959365,-0.02625853454360083,-0.6244973828751231,-0.40484409840511715,-0.19668737615771675,0.13362773492742452]]}
```

## Save your credentials

In the next lab we will be creating a web application which will call the model. It will send the processed audio file and get a prediction. For this step we will need the model's credentials. 

1. Go to the Implementation tab and copy in a notepad the **Scoring End Point**. We will need it later. 

<img src="/images/score-endpoint.png" width="90%" height="90%">

## Summary

Congratulations! You completed Lab 1! :clap:

In this lab you created a machine learning model using SPSS with zero lines of code. Then you saved the model and created a deployment as a web service. In the last part you got to test your model with test data. 

Time to move to the [Lab 2 - Call your model from a web application](https://github.com/sandra-calvo/pets-ai/tree/master/Lab%202%20-%20%20Web%20application) and build your own web application that will call your model through a REST API. 
