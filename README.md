# Titanic-Survivors
Demonstration Jupyter Notebooks for use in SageMaker Notebook / SageMaker Studio, and SageMaker Studio Lab

This repository contains the original "Titanic Survivors" Notebook, which was created when I was working as a Senior Technical Trainer at AWS. 

The notebook trains a Machine Learning model on real data from the sinking of the Titanic in 1912. The trained model can then be used to predict the likelihood of people suriviving the sinking, based on their age, sex, numbers of siblings etc. 

The original Notebook was designed to be run on an **Amazon SageMaker** Notebook instance. It could also be used as a Notebook in **Amazon SageMaker Studio**.

In addition, in this repository, I have created a corresponding Notebook for use in **Amazon SageMaker Studio Lab**, which is a free Service for people interested in understanding Machine Learning. However, SageMaker Studio Lab does not allow direct access to the AWS SageMaker APIs. So in this revised notebook, the actual Training is done using SKLearn, rather than using AWS API calls. 

## DataSets
These notebooks are based on the dataset in OpenML at [https://www.openml.org/d/40945](https://www.openml.org/d/40945) - This data set contains the survival status, age, gender, and class (which serves as a proxy for economic status) of passengers aboard the maiden voyage of the RMS Titanic in 1912. 

Unfortunately, I have found practical issues with trying to download this dataset from OpenML. So for ease of use, I have included a copy of the dataset here, in CSV format. Full acknowledgement is given here.

## List of artifacts
| File | Purpose |
| ---- | ------- |
| data | folder for data processing. Used by Studio Lab only. |
| model | folder for trained model artefacts. Used by Studio Lab only.  |
| .gitignore | standard 'gitignore' file |
| CODE_OF_CONDUCT.md | Standard code of conduct for contributing to this repo |
| INSTRUCTIONS.md | Instructions on how to demo Titanic-Survivors, using either SageMaker, or SageMaker Studio Lab | 
| LICENSE | Free to use license |
| README.md | this file |
| Titanic-Survivors-SMSL.ipynb | Jupyter Notebook for using in Amazon SageMaker Studio Lab only. The dataset should be loaded onto the hard drive of the SageMaker Studio Lab Jupyter Lab |
| Titanic-Survivors.ipynb | Jupyter Notebook for using in Amazon SageMaker (full version) only. The dataset should loaded onto an S3 bucket referenced in this notebook. |
| titanic-environment.yml | Conda Environment creation file. Used in Amazon SageMaker Studio Lab only. |
| titanic.csv | Original Titanic dataset copied from OpenML |
| titanic.xlsx | Excel Version of the OpenML dataset, with conditional formatting to help students understand the technical issues in data wrangling |

## How to Use
See the [INSTRUCTIONS.md](INSTRUCTIONS.md) file for detailed notes on how to use these notebooks to demonstrate in either Amazon SageMaker (the AWS paid product) or SageMaker Studio Lab (the free lab environment)

