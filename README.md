# Welcome to this Azure Machine Learning Workshop!

## Azure access for Students & Educators

 All student get $100 of Azure credit via Azure for Student for more details and get registered see [Azure Dev Tools for teaching] (https://azureforeducation.microsoft.com/en-US/Institutions)

## Data Resources

The model is trained to classify dog breeds using the [Stanford Dog dataset](http://vision.stanford.edu/aditya86/ImageNetDogs/) and it is based on a pretrained ResNet18 model. This ResNet18 model has been built using images and annotation from ImageNet. The Stanford Dog dataset contains 120 classes (i.e. dog breeds), however, for most of the tutorial, we will only use a subset of this dataset which includes only 10 dog breeds.

You can view the subset of the data used [here](https://github.com/heatherbshapiro/pycon-canada/tree/master/breeds-10).
Please refer to the [dog-breed-classifier.ipynb](dog-breed-classifier.ipynb) notebook for instructions.

Microsoft Research Open Data Beta - Is a collection of free datasets from Microsoft Research to advance state-of-the-art research in areas such as natural language processing, computer vision, and domain specific sciences. Download or copy directly to a cloud-based Data Science Virtual Machine for a seamless development experience. see [https://msropendata.com/](https://msropendata.com/)

## Getting Started with PyTorch

In this tutorial, you will learn how to train a Pytorch image classification model using transfer learning with the Azure Machine Learning service. The Azure Machine Learning python SDK's [PyTorch estimator](https://docs.microsoft.com/en-us/azure/machine-learning/service/how-to-train-pytorch) enables you to easily submit PyTorch training jobs for both single-node and distributed runs on Azure compute.

## Not sure where to start

If your new to PyTorch and Azure there is an excellent course at [Microsoft learn](https://docs.microsoft.com/en-us/learn/modules/interactive-deep-learning/) which provides a sandbox azure environment.

## PyTorch tutorials

[Getting Started with Pytorch](https://pytorch.org/tutorials/beginner/blitz/cifar10_tutorial.html)

In this tutorial, you will learn how to train a Pytorch image classification model using transfer learning with the Azure Machine Learning service. The Azure Machine Learning python SDK's PyTorch estimator enables you to easily submit PyTorch training jobs for both single-node and distributed runs on Azure compute. The model is trained to classify dog breeds using the Stanford Dog dataset and it is based on a pretrained ResNet18 model. This ResNet18 model has been built using images and annotation from ImageNet. The Stanford Dog dataset contains 120 classes (i.e. dog breeds), to save time however, for most of the tutorial, we will only use a subset of this dataset which includes only 10 dog breeds.

## What is Azure Machine Learning service?

![Azure Machine Learning](/assets/images/aml-overview.png)

Azure Machine Learning service is a cloud service that you can use to develop and deploy machine learning models. Using Azure Machine Learning service, you can track your models as you build, train, deploy, and manage them, all at the broad scale that the cloud provides. 

## How can we use it for training image classification models?

Training machine learning models, particularly deep neural networks, is often a time- and compute-intensive task. Once you've finished writing your training script and running on a small subset of data on your local machine, you will likely want to scale up your workload.

To facilitate training, the Azure Machine Learning Python SDK provides a high-level abstraction, the estimator class, which allows users to easily train their models in the Azure ecosystem. You can create and use an Estimator object to submit any training code you want to run on remote compute, whether it's a single-node run or distributed training across a GPU cluster. For PyTorch and TensorFlow jobs, Azure Machine Learning also provides respective PyTorch and TensorFlow estimators to simplify using these frameworks.

## Steps to train with a Pytorch Estimator:

![AzureMachineLearingProcess](/assets/images/aml-run.png)

- In this tutorial, we will:
- Connect to an Azure Machine Learning service Workspace 
- Create a remote compute target
- Upload your training data (Optional)
- Create your training script
- Create an Estimator object
- Submit your training job

## Getting Stated

To get started on this project start with dog-breed-classifier.ipynb