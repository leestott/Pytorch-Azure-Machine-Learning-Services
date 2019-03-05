# Setup

## Install Conda/Miniconda
Download and install Miniconda. Select the Python 3.7 version or later. Don't select the Python 2.x version.

## AzureML Python SDK
Install the Python SDK: make sure to install notebook, and contrib
```
conda create -n azureml -y Python=3.6 ipywidgets nb_conda
conda activate azureml
pip install --upgrade azureml-sdk[notebooks,contrib] scikit-image tensorflow tensorboardX matplotlib --user 
jupyter nbextension install --py --user azureml.widgets
jupyter nbextension enable azureml.widgets --user --py
```

## Install PyTorch:
On MacOS:

```
conda install pytorch torchvision -c pytorch
```

On Windows

```
conda install pytorch -c pytorch
pip install torchvision
```
On Linux

```
conda install pytorch-cpu torchvision-cpu -c pytorch
```

You will need to restart jupyter after this Detailed instructions are [here](https://docs.microsoft.com/en-us/azure/machine-learning/service/quickstart-create-workspace-with-python)

## Install Tensorboard

```
pip install tensorboard
pip install tensorboardX

```

## Install VS Code and the VS Code extension

Download and install Visual Studio Code then the Azure Machine Learning Extension Make sure it has a recent version of the Python SDK -- remove the folder ~/.azureml/envs if there are issues. A current SDK will be installed when you first use AML from VSCode.

## Clone this repository

```
git clone https://github.com/leestott/Pytorch-Azure-Machine-Learning-Services
jupyter notebook
```

## Getting Started

Open the [StatHere.ipynb](StartHere.ipynb) Notebooks within Jupyter.