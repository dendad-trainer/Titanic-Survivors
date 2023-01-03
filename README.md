# Titanic-Survivors
Demonstration Jupyter Notebooks for use in SageMaker Notebook / SageMaker Studio, and SageMaker Studio Lab

This repository contains the original "Titanic Survivors" Notebook, which was created when I was working as a Senior Technical Trainer at AWS. The Notebook was designed to be used in a SageMaker Notebook instance. It could also be used as a Notebook in SageMaker Studio.

In addition, in this repository, I am creating a corresponding Notebook for use in SageMaker Studio Lab, which is the free Service. However, SageMaker Studio Lab does not allow direct access to the AWS SageMaker APIs. So in this revised notebook, the actual Training is done using SKLearn, rather than using AWS API calls. 

NOTE: this is Work in progress. Bear with me.

## DataSets
These notebooks are based on the dataset in OpenML at [https://www.openml.org/d/40945](https://www.openml.org/d/40945) - This data set contains the survival status, age, gender, and class (which serves as a proxy for economic status) of passengers aboard the maiden voyage of the RMS Titanic in 1912. this dataset is not included here. You need to download this dataset yourself.

## How to Use

See the [INSTRUCTIONS.md](INSTRUCTIONS.md) file for detailed notes on how to use these notebooks to demonstrate in either Amazon SageMaker (the AWS paid product) or SageMaker Studio Lab (the free lab environment)
