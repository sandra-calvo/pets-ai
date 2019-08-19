# pets-ai
Mimmitkoodaa 2019 Pets &amp; AI workshop

## Gather and prepare data 

- Clone the animal sounds repository:

git clone https://github.com/ibm-early-programs/animal-sounds

- Change to the new animal sounds directory:

cd animal-sounds


- Sign in to Kaggle and download the cats_dogs.zip file. Extract the files and copy them to the audio directory. The zip file contains the test and train subfolders.

- Change to the src directory inside the animal-sounds directory:

/app/animal-sounds/src

- Run the pip install command to install the application requirements, which are the converter and the service application that you'll use in a subsequent lab:

pip install -r requirements.txt

PIP NEEDS TO BE INSTALLED!!! 

 - https://www.shellhacks.com/python-install-pip-mac-ubuntu-centos/
 
 MAC 
 $ sudo easy_install pip
 $ sudo pip install --upgrade pip
 
- Run the converter application that finds the audio files and generates a sound.csv file in the outputs folder:

python ospconverter.py

The file soundmac.csv is the same file that is opened and saved as a Mac CSV file by using a spreadsheet tool.

Files on Windows and Macs have different coding for line endings. When you upload the documents to Watson Studio, the line endings are converted to a Linux variant, which might be incorrect if you use the wrong file.

If you have a spreadsheet application, you can open the file and save it as a .csv file with the appropriate line endings for your operating system.


- Review the generated file.

Column 1 is the cat and dog classifier, and the remaining columns are the signal processing representation of the related audio tracks.

You now have the audio files in a representation that can be used to generate a machine learning model.


## Build a machine learning model 

In this section, you create a machine learning project and use it as the container for your data assets and the machine models that you generate.

To complete this lab you will need an instance of Watson Machine Learning that allows you to create and deploy machine learning models, and an instance of Watson Studio which provides a user interface and wizards that guide you through the process of creating machine learning models.

If you created Watson Studio projects before, you might see different images than what is shown here.

Go to the IBM Watson page and click Log In to log in to IBM Watson Studio with your IBM ID and password. Then, scroll down to the Watson Services section.

- Click Add service and then Add to select Machine Learning.

- Verify that you have Watson Studio properly configured by opening your Studio profile.

- Click the Apps tab. Then, check whether you have a Watson Studio application listed. If this is your first machine learning project, you will not see Watson Studio listed. If you don't have an application in the list, click Add other apps to add Watson Studio.

- Go back to the Studio home page and click New Project. Select Data Science and give the project a name and description.

- Make sure that the Storage field is populated with cloud-object-storage credentials. You might need to create IBM Cloud Object Storage and set your region appropriately for the credentials to appear on the Watson Studio project creation page.

You must use IBM Cloud Object Storage for reading input (such as training data) and for storing results, such as log files.

If your Storage field is showing as unpopulated, click Cloud Object Storage.


Click Add to add Cloud Object Storage for Watson Studio.

You might need to go back to the previous step to associate the cloud object storage with your data science project.

- When you're done creating the project, click Create.


