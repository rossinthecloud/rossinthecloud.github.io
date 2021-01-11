---
layout: post
tags: [azure,cloudadoptionframework,enterprisescale]
title: Azure Enterprise Scale - Deployment Errors 
excerpt_separator: <!--more-->
---
A short post on some common errors I have seen in environments when trying to deploy <a href="https://docs.microsoft.com/en-us/azure/cloud-adoption-framework/ready/enterprise-scale/implementation" target="_blank">Enterprise Scale Landing Zones</a> and how to resolve them.

#### Validation or Authorization Errors
I have seen cases of validation errors **before** any resources are attempted to be deployed.

![]({{ site.baseurl }}/assets/img/blog/2020-11-14-EnterpriseScaleDeploymentErrors/1.png)

```plaintext
The client 'x' with object id 'x' does not have authorization to perform action 'Microsoft.Resources/deployments/validate/action' over scope '/providers/Microsoft.Resources/deployments/' or the scope is invalid. If access was recently granted, please refresh your credentials.
```

This is typically due to missing permissions in your environment. Ensure that you have followed <a href="https://github.com/Azure/Enterprise-Scale/blob/main/docs/EnterpriseScale-Setup-azure.md#1-elevate-access-to-manage-azure-resources-in-the-directory" target="_blank">these steps </a>and wait 30 minutes or so before retrying your deployment.


#### The subscription is not registered to Microsoft.insights resource provider

This can often happen with a new subscription whereby the provider has never been registered.

You can fix this with PowerShell:

```powershell
Register-AzureRmResourceProvider –ProviderNamespace Microsoft.Insights
```

After a few minutes you can check that the provider is registered with the command: 
```powershell
Get-AzureRmResourceProvider –ProviderNamespace Microsoft.Insights
```
Once the resource provider is successfully registered you can retry your deployment.

