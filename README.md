# sagemaker-basketball
Learning how to use machine learning by using sagemaker to predict the outcome of basketball games.

# Welcome to the “NBA on SageMaker” workshop. 

This workshop contains everything needed to train and deploy your own machine learning endpoint for predicting the outcomes of NBA basketball games. The steps here will take you to the point of deploying a Jupyter notebook which contains the python code needed to complete the workshop. Once you finish the instructions here, you will want to follow the instructions listed in the Jupyter notebook.


**First we will want to create an S3 bucket where we can store information like our training data, as well as several artifacts created during the training and deployment stages.**


* Navigate to S3 (either by finding it in the list, or typing in S3 into the search bar)

* Select the “create bucket” button

* Name the bucket basketball-predictor-YOURNAME

* Click the create button in the bottom left (all default settings are fine)

* Create bucket basketball-predictor-YOURNAME

* Remember this bucket name, you’ll need it later


**Now that we have a place to store our SageMaker items, we need a development environment to begin training and deploying our machine learning model. Part of SageMaker is hosted Jupyter notebooks that allow us to more quickly get building. These notebooks come with certain things pre-installed that will make it easier to get started.**


* Navigate to the SageMaker console (either by finding it in the list, or typing in sagemaker into the search bar)

* Find the link for “Amazon SageMaker Studio” in the left-hand column

* Select “Quick Start”

* Choose "Create a new role"

**Now we will need to detail the IAM permissions that our SageMaker instance will have. We will need to give it access to our S3 bucket that we created earlier.**

* Choose "Specific S3 bucket" and type the bucket name you created earlier. Then select "Create role"

* Then select "submit". You'll need to wait a couple of minutes for your SageMaker Studio Control Panel to be created


**Here you have the option to select the configuration of your Jupyter notebook. This includes settings like instance size and storage amount. Note that this is the size of only the notebook itself, and the training and deployment of the model will occur on entirely different instances. In this case a t2 medium is more than enough for what we need.**


* Choose t2.medium for your instance size


**Now we will need to detail the IAM permissions that our SageMaker instance will have. We will need to give it access to our S3 bucket that we created earlier.**

* Under the section labled: Permissions and encryption, look for IAM Role

* Click on the dropdown box and choose to create a new IAM role

* Enter in the name of your S3 bucket to give access


**Let’s finish creating the SageMaker notebook instance. It will take a couple minutes to spin up.**


* Keep all other options the same and select create notebook instance

* Your notebook may take a up to five minutes to spin up

* Once your sagemaker notebook has appeared and is available, select “Open Jupyter”


**This is your very own Sagemaker Studio. The first thing we need to do is download the python code from the git repository. We can do this through the git command line interface.**


In the top left corner, choose the “new” option and select terminal


**First cd into the main directory**

**Clone the public repository into the current locations**

* Type `git clone https://github.com/stmayne/sagemaker-studio-nba.git`

**We also need to upload our data to our s3 bucket**

* Type `aws s3 cp nba_data.csv s3://YOURBUCKETNAME`


## Now we want to create our Sagemaker AutoPilot Experiment.

* Click "new" in the top left, then select "Experiment"

* Name your experiement what you want

* Use "Find S3 bucket", and enter the name of your S3 bucket name

* For S3 object key prefix type "nba_data.csv"

**Our target attribute is the value we will be trying to predict. In this case the field is named "point_diff"**

* Type "point_diff" for Target attribute name

* For output S3 bucket type the name of your S3 bucket

* For the S3 object key prefix type "output/"

**Now we need to choose the type of machine learning probem we have. Since were trying to predict a value in a range, we choose "Regression"**

* Select "Regression"

* Select "Yes" for "Do you want to run a complete experiment?"

* Select "Create Experiment"