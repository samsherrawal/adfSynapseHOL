# Module 04: Create self-hosted integration runtime within ADF

[< Previous Module](../modules/module03.md) - **[Home](../README.md)** - [Next Module >](../modules/module05.md)

## :loudspeaker: Introduction

In this lab, we will be provisioning Azure VM with self-hosted integration runtime pre-installed to run data factory tasks
and interact with on-prem environment. For the purpose of simulation, we are going to use existing virtual network that you previously created in the "adflab" resource group, i.e. virtual network with the name like adflab-{******}-vnet

## :thinking: Prerequisites

* An [Azure account](https://azure.microsoft.com/free/) with an active subscription.

* Data Factory. The integration runtime is created in the data factory(previosly created). If you don't have a data factory, see the [Create Data Factory](https://learn.microsoft.com/en-us/azure/data-factory/v1/data-factory-move-data-between-onprem-and-cloud#create-data-factory) for steps to create one.

* Virtual Network. The virtual machine will join this VNET. If you don't have one, use this tutorial, see [Create virtual network](https://learn.microsoft.com/en-us/azure/virtual-network/quick-create-portal#create-a-virtual-network) to create one.

## Creating and configuring a Self-hosted integration Runtime on Azure VMs

Handshake of self-hosted integration runtime in your machine is achieved by copying the key provided during the 'Self-Hosted' Integration runtime setup from Azure Data Factory and then adding it to the Authentication Key field during registration of Self-Hosted IR in your local machine, please follow the instructions provided below.

Use the following steps to create a self-hosted IR using the Azure Data Factory


1. On the home page of the Azure Data Factory UI, select the Manage tab from the leftmost pane.

2. Select Integration runtimes on the left pane, and then select +New.

    ![manage-integration-runtime](../images/module04/04-03-createIR.png)

3. On the Integration runtime setup page, select Azure, Self-Hosted, and then select Continue.

4. On the following page, select Self-Hosted to create a Self-Hosted IR, and then select Continue. 

    ![self-hostedIR](../images/module04/04-04-selfhostedIR.png)

## Configure a self-hosted IR via UI

1. Enter a name for your IR, and select Create.

2. On the Integration runtime setup page, select the link under Option 1 to open the express setup on your computer. Or follow the steps under Option 2 to set up manually. The following instructions are based on manual setup:

    ![integration-runtime-setup](../images/module04/04-05-integration-runtime-setup.png)

	(a) Copy and paste the authentication key. Select Download and install integration runtime.

	(b) Download the self-hosted integration runtime on a local Windows machine. Run the installer.

	(c) On the Register Integration Runtime (Self-hosted) page, paste the key you saved earlier, and select Register.

        ![register IR](../images/module04/04-06-registerIR.PNG)

    (d) On the New Integration Runtime (Self-hosted) Node page, select Finish.

After the self-hosted integration runtime is registered successfully, you see the following window:

    ![successful registration](../images/module04/04-07-successful-registration.PNG)



## OPTIONAL

## :test_tube: Lab Environment Setup for provisioning an Azure VM with Self-hosted integration runtime 

1. Right-click or `Ctrl + click` the button below to open the Azure Portal in a new window.

    [![Deploy to Azure](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Fsamsherrawal%2FadfSynapseHOL%2Fmain%2Ftemplate%2FselfhostIRdeploy.json)

   
 

2. Beneath the **Resource group** field, click **Create new** and provide the existing resource name (e.g. `adflab-rg`), select a [valid location](https://azure.microsoft.com/global-infrastructure/services/?products=ADF&regions=all) (e.g. `Central US`), and then click **Review + create**.

    ![Deploy Template](../images/module04/04-01-selfhostedIR.png)

3. Once the validation has passed, click **Create**.

    ![Create Resources](../images/module04/04-02-review-create.png)

4. The deployment should take approximately 3 minutes to complete. Once you see the message **Your deployment is complete**, click **Go to resource group**.


When you deploy this Azure Resource Template, you will create a logical selfhost IR in your data factory and the following resources

* Azure Virtual Machine
* Azure Storage (for VM system image and boot diagnostic)
* Public IP Address
* Network Interface
* Network Security Group
* This template can help you create self-hosted IR and make it workable in azure VMs. The VM must join in an existing VNET.

## Using the Self Hosted Runtime Integration 

Self hosted runtime integration is used to copy data from on-prem environment to azure cloud. You could use your local machine or the host computer(ADPDesktop) for these labs.

On this lab section we will perform the below three tasks: 

a) Read data from on-prem SQL table and push to azure blob storage

b) Copy files from on-prem to azure blob storage

c) running stored procedure on the onp-rem sql using self hosted IR as alternate way of performing complex ETL

[Continue >](../modules/module05.md)
