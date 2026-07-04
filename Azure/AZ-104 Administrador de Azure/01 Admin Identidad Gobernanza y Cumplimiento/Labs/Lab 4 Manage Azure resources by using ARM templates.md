![](media/Manage_Azure_resources_by_using_ARM_templates.mp4)




```powershwell

New-AzResourceGroupDeployment -ResourceGroupName az104-rg3 -TemplateFile template.json -TemplateParameterFile parameters.json



Comprobar la creacion del disco
Get-AzDisk | ft Name,ResourceGroupName,Location,DiskSizeGb,ProvisioningState
```


```bash

az deployment group create --resource-group az104-rg3 --template-file template.json --parameters parameters.json



Comprobar la creacion del disco
az disk list --resource-group az104-rg3 --output table
```

```bash
az deployment group create --resource-group az104-rg3 --template-file azuredeploydisk.bicep



az disk list --resource-group az104-rg3 --output table
```


## Learn more with self-paced training

- [Deploy Azure infrastructure by using JSON ARM templates](https://learn.microsoft.com/training/modules/create-azure-resource-manager-template-vs-code/). Write JSON Azure Resource Manager templates (ARM templates) by using Visual Studio Code to deploy your infrastructure to Azure consistently and reliably.
- [Review the features and tools for Azure Cloud Shell](https://learn.microsoft.com/training/modules/review-features-tools-for-azure-cloud-shell/). Cloud Shell features and tools.
- [Create Azure Resources Using Azure CLI](https://learn.microsoft.com/training/modules/create-azure-resources-by-using-azure-cli/). Learn to install Azure CLI across Windows, Linux, and macOS, execute commands interactively, create Bash automation scripts, and troubleshoot common issues.
- [Build your first Bicep template](https://learn.microsoft.com/training/modules/build-first-bicep-template/). Define Azure resources within a Bicep template. Improve the consistency and reliability of your deployments, reduce the manual effort required, and scale your deployments across environments. Your template will be flexible and reusable by using parameters, variables, expressions, and modules.