# Automated Deployment of APIM, Application Gateway and Azure Traffic Manager using ARM Templates

## High level of deployment
Deploying the azuredeploy.json template file provisions the following Azure resources along with their required dependencies:
1. **APIM**
2. **App Gateway**
   - *Virtual Network* - VNet required for App Gateway deployment within its specified namespace
   - *Subnet* - App Gateway will be deployed within this subnet
   - *Public IP* - entry point for App Gateway
3. **Traffic Manager**

## Steps to deploy
1. Open your command prompt/bash shell and connect to Azure:
```
az login
```
2. Create a Resource Group in your Azure subscription (if you don't already have one):
```
az group create --name <YOUR-RESOURCE-GROUP-NAME> --location <CHOOSE-RESOURCE-GROUP-LOCATION>
```
3. Make sure you are in the working directory that holds your template and paramter files
4. Simply run the following command to deploy all the resources defined in both the template and parameter files:
```
az group deployment create --resource-group <YOUR-RESOURCE-GROUP-NAME> --template-file azuredeploy.json --parameters azuredeploy.parameters.json
```
   - **Note:** if you don't specify the **--parameters** option, the template will still deploy successfully. This is because the template file defines default values for the required user input.

## Considerations
* Be mindful of the public IP's SKU and its compatibility with App Gateway's SKU
  - Deploying public IP with type *Basic* and allocation method *Dynamic* along with App Gateway's SKU *Standard_v2* throws a compatibility error during deployment
