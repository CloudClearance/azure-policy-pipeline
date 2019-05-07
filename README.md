# Azure Policy Pipeline

## Overview 

[Azure Policy](https://docs.microsoft.com/en-us/azure/governance/policy/overview) is a service in Azure that you use to create, assign, and manage policies over varying scopes inside of Azure. These policies can be used to audit your subscriptions of non-compliant resources or take a more forceful approach and deny the creation or operation of non-compliant resources.

When implementing a complaint Azure environment, many policies will need to be combined to accomplish your desired level of compliance. In Azure Goverance, there is the notion of [Azure Policy Initatives](https://docs.microsoft.com/en-us/azure/governance/policy/overview#initiative-definition), which is a collection of policy tailored towards achieving a singular goverance goal.

## Deployment

Before starting, ensure you have the Azure PowerShell module installed via [this guide](https://docs.microsoft.com/en-us/powershell/azure/get-started-azureps?view=azps-2.0.0).

- Open a PowerShell window
- Login using the `Connect-AzAccount` command
- Ensure you are working under the correct subscription with the `$context = Get-AzSubscription -SubscriptionId xxxx-xxxx-xxxx` and `Set-AzContext $context` commands. If you need a list of subscriptions, use the `Get-AzSubscription` command.
- Execute the below deployment script
```powershell
.\Deploy-AzTemplate.ps1 -ResourceGroupName 'test' -Location 'westus2' -TemplateFile 'azuredeploy.json' -TemplateParametersFile 'azuredeploy.
parameters.json' -StorageAccountName '' -ArtifactStagingDirectory '.' -StorageContainerName 'azurepolicypipeline-storageaccount' -UploadArtifacts
```