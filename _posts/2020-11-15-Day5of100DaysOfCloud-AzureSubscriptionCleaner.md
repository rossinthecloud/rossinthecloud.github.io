---
layout: post
tags: [azure,powershell,100daysofcloud]
title: Azure Subscription Cleaner [100DaysOfCloud Day 5/100] 
excerpt_separator: <!--more-->
---
If like me, you are spinning up demo or test Azure subscriptions. You will often want to quickly clear your subscription and delete everything within it.

<a href="https://github.com/rossinthecloud/AzureSubscriptionCleaner" target="_blank">This PowerShell script</a> will allow you to select which Azure subscription you want to clear and will then delete EVERYTHING inside that subscription allowing you to start from scratch.

USE THIS WITH CAUTION!

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

![]({{ site.baseurl }}/assets/img/blog/2020-11-15-Day5of100DaysOfCloud-AzureSubscriptionCleaner/1.png)
![]({{ site.baseurl }}/assets/img/blog/2020-11-15-Day5of100DaysOfCloud-AzureSubscriptionCleaner/2.png)


--

I am taking part in the <a href="https://100daysofcloud.com/" target="_blank">#100DaysOfCloud Challenge</a>. Please do have a look at my <a href="https://github.com/rossinthecloud/100DaysOfCloud" target="_blank">Github journey tracker</a> to find out more, track my progress or get involved.

If you have any questions please also do reach out to me via a comment or on Twitter<a href="https://www.twitter.com/rossinthecloud" target="_blank"> @rossinthecloud</a>.

<a href="https://github.com/rossinthecloud/100DaysOfCloud" target="_blank">![]({{ site.baseurl }}/assets/img/100dayslogo.png)</a>

