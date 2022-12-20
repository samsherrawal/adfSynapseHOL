# Module 00 - Lab Environment Setup

**[Home](../README.md)** - [Next Module >](../modules/module01.md)

## :loudspeaker: Introduction

In order to follow along with the Microsoft ADF lab exercises, you need to provision a set of resources.

## :thinking: Prerequisites

* An [Azure account](https://azure.microsoft.com/free/) with an active subscription.
* Owner permissions within a Resource Group to create resources and manage role assignments.
* The subscription must have the following resource providers registered.
  * Microsoft.Authorization
  * Microsoft.DataFactory
  * Microsoft.EventHub
  * Microsoft.KeyVault
  * Microsoft.Storage
  * Microsoft.Sql
  * Microsoft.Synapse
  * Microsoft.Insights

    > :warning: If you are using an **Azure Pass promo code**, the following resource providers - `Microsoft.Storage`, `Microsoft.EventHub`, and `Microsoft.Synapse` are not registered by default. Follow the instructions on [how to register a resource provider](./providers.md) before proceeding with the lab environment deployment below.

## :test_tube: Lab Environment Setup

1. Right-click or `Ctrl + click` the button below to open the Azure Portal in a new window.

    [![Deploy to Azure](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Fsamsherrawal%2FadfSynapseHOL%2Fmain%2Ftemplate%2Fazuredeploy.json)

2. Beneath the **Resource group** field, click **Create new** and provide a unique name (e.g. `adflab-rg`), select a [valid location](https://azure.microsoft.com/global-infrastructure/services/?products=ADF&regions=all) (e.g. `West Europe`), and then click **Review + create**.

    ![Deploy Template](../images/module00/00.01-deploy-lab.png)

3. Once the validation has passed, click **Create**.

    ![Create Resources](../images/module00/00.02-deploy-create.png)

4. The deployment should take approximately 10 minutes to complete. Once you see the message **Your deployment is complete**, click **Go to resource group**.

    ![Deployment Complete](../images/module00/00.03-deploy-complete.png)

5. If successful, you should see a set of 15 resources, similar to the screenshot below.

    ![Resource Group](../images/module00/00.04-deploy-resources.png)



## Creating a separate host machine to mimic On-Prem environment (On a separate resource group!)

Note: The below lab is optional and you can proceed with the instructions only if you want to create a separate host machine that will simulate your on-prem environment when following all the lab modules. You could use your local machine as well to do these labs. However, please ensure that these resources are deleted once you have completed the labs to avoid unexpected usage charges.

1. Right-click or `Ctrl + click` the button below to open the Azure Portal in a new window.

    [![Deploy to Azure](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Fsamsherrawal%2FadfSynapseHOL%2Fmain%2Ftemplate%2Fhostmachinedeploy.json)

2. Beneath the **Resource group** field, click **Create new** and provide a unique name (e.g. `HostVM-rg`), select a [valid location](https://azure.microsoft.com/global-infrastructure/services/?products=ADF&regions=all) (e.g. `West Europe`), and then click **Review + create**. This step takes around 4 minutes and your Azure Virtual machine will be created.

## :tada: Summary

By successfully deploying the Microsoft ADF lab template, you have the Azure resources needed to follow along with the learning exercises.

[Continue >](../modules/module01.md)
