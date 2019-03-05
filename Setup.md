Before starting, you must provision your environment as follows :

## 1. Setup your Virtual Machine and Conda Env

- Create Data Science Virtual Machine [DSVM](https://azure.microsoft.com/en-us/services/virtual-machines/data-science-virtual-machines/) on Ubuntu (which also includes Azure ML CLI) using [Azure Portal](https://portal.azure.com/)

  Here we use DSVM, but you can also build your own environment from scratch.

  You will have to run some commands after the initial install to update your DSVM application and libararies

```
# Fetches the list of available updates
sudo apt-get update
# Strictly upgrades the current packages
sudo apt-get upgrade
# Installs updates (new ones)
sudo apt-get dist-upgrade
```

or you can do it all nicely with this single script

```
sudo bash -c 'for i in update {,dist-}upgrade auto{remove,clean}; do apt-get $i -y; done'
```

- Create conda virtual environment and activate as follows.

```
conda create -n myenv -y Python=3.6
# Update Conda Environment 
conda update -n base -c defaults conda 
conda activate myenv
```

- Install required packages in your conda environment (You must run in your conda env.)
 so please ensure you have used the command conda activate myenv

## Install Azure Machine Learning SDK

In the next step we will install  ```azureml-sdk[notebooks]``` installs notebook in your conda env and ```azureml_widgets``` extension (which is used in Exercise06) this Notebook extension is enabled in Jupyter. (See installed extension using ```jupyter nbextension list```.)
```
# install AML SDK
pip install azureml-sdk[notebooks]

# install notebook integration for conda
conda install nb_conda

# install required packages for development
# (use "tensorflow-gpu" if using GPU VM)
conda install -y matplotlib tensorflow
```

## 2. Create AML Workspace

Create new "Machine Learning services workspace" using [Azure Portal](https://portal.azure.com/) see [Creating Azure ML Workspace](https://docs.microsoft.com/en-us/azure/machine-learning/studio/create-workspace)
Please make sure that **you must specify location (region) which supports NC-series (K80 GPU) virtual machines in workspace creation**, because workspace location is used when you create AML compute resources (virtual machines) in AML Python SDK. (See [here](https://azure.microsoft.com/en-us/global-infrastructure/services/?products=virtual-machines) for supported regions.)

## 3. Make Sure to Install Azure Container Instance (ACI) Provider in Your Azure Subscription

Azure Container Instances offers the fastest and simplest way to run a container in Azure, without having to provision any virtual machines and without having to adopt a higher-level service. [Learn how to create and manage container instances with our quickstarts, tutorials, and samples](https://docs.microsoft.com/en-us/azure/container-instances/)

- Remove azure-ml-admin-cli extension on VM as follows. (This extension is already installed on DSVM and prevents you from running ```az login``` command.)

```
sudo -i az extension remove --name azure-ml-admin-cli
```

- Login to Azure using CLI

```
az login
```

- Check to see if ACI provider is already registered

```
az provider show -n Microsoft.ContainerInstance -o table
```

- If ACI is not registered, run the following command. (You should be the subscription owner to run this command.)

```
az provider register -n Microsoft.ContainerInstance
```


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

## 4. Start Jupyter Notebook

- Start jupyter notebook server in your conda environment.

```
jupyter notebook
```

- Copy url for notebook in the console output, and set SSH tunnel (port forwarding) on your desktop to access notebook.
  For instance, the following picture is the SSH tunnel setting on "putty" terminal client in Windows. (You can use ```ssh -L``` option in Mac OS.)
  ![SSH Tunnel settings with putty](/assets/images/putty.png)

- Open your notebook url (http://localhost:8888/?token=...) using web browser in your desktop.
![Notebook Login](/assets/images/Notebooks.png)

Simply paste into the password or token box the token received and press login this will load the Jupyter Hub

- Create new notebook by selecting "Python 3.6" kernel (which is your current conda environment).

Now you're ready to start !

## Getting Started

- [Exercise 1 Introduction](Exercise1.ipynb)
- [Exercise 2 Creating AMLS + Compute](Exercise2.ipynb)
- [Exercise 3 Uploading Data](Exercise3.ipynb)
- [Exercise 4 Prepare Training](Exercise4.ipynb)
- [Exercise 5 Tensorboard](Exercise5.ipynb)
- [Exercise 6 Distributed Training](Exercise6.ipynb)
- [Exercise 7 Hyperparameter Tuning](Exercise7.ipynb)
- [Exercise 8 Inferencing](Exercise8.ipynb)
- [Exercise 9 Deploying Model as Web Service](Exercise9.ipynb)
- [Exercise 10 Test Web Service](Exercise10.ipynb)
- [Exercise 11 Web Service Example](Exercise11.ipynb)

## References

- All student get $100 of Azure credit via Azure for Student for more details and get registered see [Azure Dev Tools for teaching](https://azureforeducation.microsoft.com/en-US/Institutions)
- Azure Machine Learning – [Notebooks & Resources](https://github.com/Azure/MachineLearningNotebooks)
- Using Azure Machine Learning Services - [Tutorial and Documentation](https://docs.microsoft.com/en-us/azure/machine-learning/service/)
- Azure Containers [Docs and Tutorials](https://docs.microsoft.com/en-us/azure/container-instances/)
- Data Science Virtual Machine [DSVM](https://azure.microsoft.com/en-us/services/virtual-machines/data-science-virtual-machines/)
