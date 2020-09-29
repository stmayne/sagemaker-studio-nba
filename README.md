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

* Find the link for “notebook instances” in the left-hand column

* Select “create new notebook instance”

* Name your instance sagemaker-basketball-YOURNAME


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


**This is your very own Jupyter notebook. The first thing we need to do is download the python code from the git repository. We can do this through the git command line interface.**


In the top right corner, choose the “new” option and select terminal


**First cd into the main directory**

* Type `cd SageMaker` and hit enter


**Then clone the public repository into the current locations**

* Type `git clone https://github.com/stmayne/sagemaker-basketball.git`


## Now we want to open our python code and follow the instructions in the Jupyter notebook

* Click the jupyter icon in the top left

* Click on the “sagemaker-basketball” folder

* Click nba-game-prediction.ipynb

