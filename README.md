# Deployment of an .Net Core Application running on Azure App Service and using Azure SQL Service 

<a href="https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Fflecoqui%2FTestWebSqlApp%2Fmaster%2Fazuredeploy.json" target="_blank">
    <img src="http://azuredeploy.net/deploybutton.png"/>
</a>
<a href="http://armviz.io/#/?load=https%3A%2F%2Fraw.githubusercontent.com%2Fflecoqui%2FTestWebSqlApp%2Fmaster%2Fazuredeploy.json" target="_blank">
    <img src="http://armviz.io/visualizebutton.png"/>
</a>

This template allows you to deploy a .Net Core Application on Azure App Service and using Azure SQL Service.  For this deployment the source code of the .Net Core application will be stored on github and automatically deployed on Azure App Service.


![](https://raw.githubusercontent.com/flecoqui/TestWebSqlApp/master/Docs/1-architecture.png)



## CREATE RESOURCE GROUP:

**Azure CLI:** azure group create "ResourceGroupName" "RegionName"

**Azure CLI 2.0:** az group create �n "ResourceGroupName" -l "RegionName"

For instance:

    azure group create testwebsqlappg eastus2

    az group create -n testwebsqlapprg -l eastus2

## DEPLOY THE SERVICES:

**Azure CLI:** azure group deployment create "ResourceGroupName" "DeploymentName"  -f azuredeploy.json -e azuredeploy.parameters.json*

**Azure CLI 2.0:** az group deployment create -g "ResourceGroupName" -n "DeploymentName" --template-file "templatefile.json" --parameters @"templatefile.parameter..json"  --verbose -o json

For instance:

    azure group deployment create testwebsqlapprg testwebsqlappdep -f azuredeploy.json -e azuredeploy.parameters.json -vv

    az group deployment create -g testwebsqlapprg -n testwebsqlappdep --template-file azuredeploy.json --parameter @azuredeploy.parameters.json --verbose -o json


When you deploy the service you can define the following parameters:</p>
**webSiteName:**                    The name of the web site (must be unique) </p>
**hostingPlanName:**                The name of the hosting Plan (must be unique)</p>
**skuName:**                        The Sku Name, by defualt "F1"</p>
**skuCapacity:**                    The Sku Capacity, by defualt 1</p>
**sqlServerName:**                  The SQL Server Name (must be unique)</p>
**databaseName:**                   The database Name (must be unique)</p>
**sqlAdministratorLogin:**          The SQL Administrator Login</p>
**sqlAdministratorLoginPassword:**  The SQL Administrator Password (Complexe password required)</p>
**repoURL:**                        The github repository url</p>
**branch:**                         The branch name in the repository</p>

## TEST THE SERVICES:
Once the services are deployed, you can open the Web page hosted on the Azure App Service.
For instance :

     http://<websitename>.azurewebsites.net/
 
</p>


## DELETE THE RESOURCE GROUP:

**Azure CLI:** azure group delete "ResourceGroupName" "RegionName"

**Azure CLI 2.0:** az group delete -n "ResourceGroupName" "RegionName"

For instance:

    azure group delete testwebsqlapprg eastus2

    az group delete -n testwebsqlapprg 

