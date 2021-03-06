---
layout: post
tags: [azure,powershell]
title: Azure Subscription Cleaner
excerpt_separator: <!--more-->
---
If like me, you are spinning up demo or test Azure subscriptions. You will often want to quickly clear your subscription and delete everything within it.

<a href="https://github.com/rossinthecloud/AzureSubscriptionCleaner" target="_blank">This PowerShell script</a> will allow you to select which Azure subscription you want to clear and will then delete EVERYTHING inside that subscription allowing you to start from scratch.

USE THIS WITH CAUTION!

<!--more-->

```powershell
# Login
Login-AzAccount 

# Get a list of all Azure subscriptions that the user can access and allow them to select one to be cleared
$SubscriptionId = (Get-AzSubscription | select Name, State, SubscriptionId, TenantId | Out-GridView -Title "Select Azure Subscription To Clear" -PassThru).SubscriptionId
Get-AzSubscription -SubscriptionId $SubscriptionId | Select-AzSubscription

# Warning confirmation
Write-Warning "Are you sure you want to DELETE EVERYTHING in Azure Subscription with ID $SubscriptionId" -WarningAction Inquire

# Get all resources and delete them
Get-AzResource | ForEach { Remove-AzResource -ResourceId $_.ResourceId -Force -Confirm:$False }
```

![]({{ site.baseurl }}/assets/img/blog/2020-07-15-AzureSubscriptionCleaner/1.png)
![]({{ site.baseurl }}/assets/img/blog/2020-07-15-AzureSubscriptionCleaner/2.png)

