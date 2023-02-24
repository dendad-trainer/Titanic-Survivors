# Instructions for using the Titanic Survivors Jupyter Notebooks

This repository contains two sets of artifacts, dependent upon whether you want to use an Amazon SageMaker (Or Amazon SageMaker Studio) Notebook instance, 
or whether you would prefer to use the Free Amazon SageMaker Studio Lab.

The latter is a free resource, but has several restrictions, including the fact that it is more difficult to call the AWS APIs. 
(If you do call these APIs, then they are chargeable to your AWS account.)
So in the spirit of 'keep it free', the notebook for SageMaker Studio Lab makes use of SKLearn APIs rather than AWS APIs.

This document consists of the following sections:

1. [Background Scenario](#1.0-background-scenario) - sets the background and tells the story which you will demonstrate. This applies whichever of the two demo approaches you wish to use.
2. [Demo Notes: using Amazon SageMaker or SageMaker Studio](#2.0-demo-notes-using-amazon-sagemaker-or-sagemaker-studio) - this requires a full AWS account and Jupyter notebook instance. This makes full use of AWS Managed Services, and would be chargeable. This would be more relevant for commercial customers of AWS.
3. [Demo Notes: using Amazon SageMaker Studio Lab](#3.0-demo-notes-using-amazon-sagemaker-studio-lab) - this just requires a free Amazon SageMaker Studio Lab account. You do not need an AWS account. The Amazon SageMaker Studio Lab service is entirely free, although it does have some technical limitations compared with the full SageMaker, above. This would be more relevant to people interested in Machine Learnging from an academic or hobby perspective.

## 1.0 Background Scenario

These notebooks are based on the dataset in OpenML at https://www.openml.org/d/40945 - This data set contains the survival status, age, gender, and class (which serves as a proxy for economic status) of passengers aboard the maiden voyage of the RMS Titanic in 1912. this dataset is not included here. You need to download this dataset yourself.

When demonstrating Machine Learning, it is very easy to introduce academically interesting data sets, without relating the results back to anything that the ordinary student can identify with. That is the reason for using this 'Titanic Survivors' dataset and presenting it in this way. 

The reason for choosing this dataset is as follows:
- The story of the Titanic is reasonably well known, and there is real data about the survivors. This means we could train a machine learning model to learn how to predict which passengers would survive the disaster. 
- We can test this model by passing it data on real-world people who were actually on the Titanic, and see what the model predicts. This is more engaging than just using data, since we can find out about the actual biography of a person, before passing their details to the model to create a prediction.
- In order to make this even more engaging, we have added two other individuals from the 1997 film "Titanic". This is a fictional story. However, since we have biographical backgrounds to these fictional characters, we can pass their data to the model, to see if the result of the fictional film would align with the real events.

I hope you will enjoy using this resource to teach basic Machine Learning concepts to your students.

The Notebook combines python code and extensive comments and markdown cells, so that a student can follow the activities required for doing data preparation and training and evaluating a Machine Learning model. The sections of the Notebook are based on the phases of a typical Machine Learning project:

- Business Problem: define what we are trying to achieve in business terms.
- Problem Formulation: specify what the ML model should do in order to address the business problem.
- Setup: Define locations for the data, and import necessary python libraries
- Data Collection and Integration: Load the CSV file and review it's contents 
- Data pre-Processing and visualisation: This is the largest part of the notebook. As well as dropping some columns we do not need, and shuffling the order around, each of the columns needs some processing in order to make them suitable for machine learning. So the following columns are processed in order: pclass, sex, age, sibsp, parch, fare, embarked. The column "embarked" is then converted to numeric values by applying one-hot-encoding. Finally, we display the relationships between the features, and then save the fully processed data. Note: if you have already done this section in advance, then the next time you load the notebook, you can jump from the end of "Setup" directly to the next section.
- Model Training and Tuning: This is where we load the processed data and train a model on the data.
- Model Evaluation: Making use of the Test data set, we then evaluate how "good" the model is. We also chose some representative test data to see how the model performs.
- Evaluation of Business Goal: This is where we try out the actual data from the Titanic Film, and see what results we get.
- Conclusion: Assess the success or failure of this model, and think about what other work could be done to improve it. For example, this notebook does not include any Hyperparameter Tuning of the model.
- Tidy Up: Delete any AWS infrastructure that may have been created.


## 2.0 Demo Notes: using Amazon SageMaker or SageMaker Studio

### 2.1 Setup

You need to have an Amazon AWS Account, with an IAM user with the necessary IAM permissions to read & write to your S3 bucket, to call Amazon SageMaker APIs and Amazon SageMaker Runtime APIs. All data will be stored on S3. If you are just launching an Amazon SageMaker Notebook Instance, you can choose the interface as either Jupyter or Jupyter Lab.

Create an S3 bucket to store the artifacts. Create a folder 'Titanic', and upload the 'titanic.csv' file from the OpenML link (above), or the copy I have taken in this repository, into this folder.

Launch an Amazon SageMaker Notebook instance. A 'T3.Micro' instance type should suffice. Give this instance an IAM Role which will enable it to make API calls to 'sagemaker' and to 'sagemaker-runtime',  and to access the S3 bucket. 

When the Amazon SageMaker Notebook instance is running, click on 'Open Jupyter'. This will bring up the Jupyter page showing the instance file system.

Upload the file named Titanic-Survivors.ipynb from this GitHub repository.

Double-click on **Titanic-Survivors.ipynb** to launch it. 

### 2.2 Demo

Follow the instructions on the Jupyter Notebook, and talk through the process. 

### 2.3 Cleanup

The "Tidy Up" section of the notebook deletes the following:
- The SageMaker Endpoint API, which is hosted by a managed EC2 instance. Note that this will incur costs until it is shut down.
- The Endpoint Configuration file used to build the above.
- The Model definition which is referenced by the the configuration file.

After you have completed the notebook, go back to the Amazon SageMaker console and Shutdown the Notebook Instance. You can then Delete the Notebook instance. If you are using Amazon SageMaker Studio, you will need to delete all Studio artefacts; these will continue running unless you explicitely delete them.
Remember to delete all data from your S3 bucket.


## 3.0 Demo Notes: using Amazon SageMaker Studio Lab

### 3.1 Setup

You need to have a free account in Amazon SageMaker Studio Lab.  There are no permissions / IAM restrictions. All data is stored on the hard drive of the Jupyter Notebook instance itself. The interface is Jupyter Lab.

Launch a 'Project'. This can be type 'CPU', not 'GPU'. 

This will start up Jupyter Lab.
Click on the "GIT" icon <img width="33" alt="Screenshot 2023-02-24 at 09 31 49" src="https://user-images.githubusercontent.com/121753610/221143412-5b116e00-93d0-4b4c-8249-64dc2bb528de.png"> and enter https://github.com/dendad-trainer/Titanic-Survivors to Clone the git repository. This should create a folder called 'Titanic-Survivors', with the folders 'data' and 'model', and following files at the top level: titanic-environment.yml, Titanic-Survivors-SMSL.ipynb, Titanic-Survivors.ipynb. You can delete the last file, since it only applies to the full SageMaker service.

Copy the 'titanic.csv' file into the 'data' folder.

In Jupyter Lab, Right click on titanic-environment.yml and "Create Conda Environment". This will start a terminal session and install the necessary requirements, including sklearn, pandas, numpy.

Double-click on **Titanic-Survivors-SMSL.ipynb** to launch it. 

You will be asked to Select the Kernel. Choose the kernel called. **Titanic-env:Python** which was created using the yml file above.

### 3.2 Demo

Follow the instructions on the Jupyter Notebook, and talk through the process. 

### 3.3 Cleanup

After you have finished the demo, you can go into the "Kernel" section of the Jupyter Lab browser (<img width="24" alt="Screenshot 2023-01-06 at 14 01 17" src="https://user-images.githubusercontent.com/121753610/211027274-e6ec0fe2-32c5-4fd9-b7d4-7560d7bf82d2.png">) and Stop the Kernel.

You also need to Delete the conda environment by launching a terminal in "Launcher", and entering the following command: `conda env remove -n Titanic-env`

Delete all data from the hard drive from the 'Titanic-Survivors' folder downwards.
