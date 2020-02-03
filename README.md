# Automated Deployment of APIM, Application Gateway and Azure Traffic Manager using ARM Templates

## High level of deployment
Deploying the azuredeploy.json template file provisions the following Azure resources along with their required dependencies:
1. APIM
2. App Gateway
   - Virtual Network - VNet required for App Gateway deployment within its specified namespace
     - Subnet - App Gateway will be deployed within this subnet
       - Public IP - entry point for App Gateway
3. Traffic Manager

