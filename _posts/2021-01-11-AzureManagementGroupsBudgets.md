---
layout: post
tags: [azure,management groups,costmanagement]
title: Azure Management Groups - Budgets 
excerpt_separator: <!--more-->
---
Getting my own "house" in order, I wanted to have a look at how I can track consumption across my Azure subscriptions. I am grateful to receive Azure credits each month from my Visual Studio subscription and as an MCT benefit, however I wanted to be able to track if my credit is burning down. 

You can perform cost analysis and create budgets at the Azure Management Group level. This is a neat way to get a consolidated view and more importantly, alerts across multiple subscriptions for usage.

By creating a budget you can be notified once spend on your Azure Management Group (based on the usage of the underlying subscriptions) reaches your defined thresholds. 

Let's dive into an example below..

<!--more-->

#### Quick Start Example

Navigate to your Azure Management Group and choose Budgets from the menu

![]({{ site.baseurl }}/assets/img/blog/2021-01-11-AzureManagementGroupsBudgets/1.png)

Press Add

![]({{ site.baseurl }}/assets/img/blog/2021-01-11-AzureManagementGroupsBudgets/2.png)

Fill in the values you want to use for your budget. Press Next

![]({{ site.baseurl }}/assets/img/blog/2021-01-11-AzureManagementGroupsBudgets/3.png)

Enter at what percentage of budget used you want to receive emails and an email address.

![]({{ site.baseurl }}/assets/img/blog/2021-01-11-AzureManagementGroupsBudgets/4.png)

Press Create. Easy as that!

Small word of caution - If you have a Pay-As-You-Go, MSDN, or Visual Studio subscription, your invoice billing period might not align to the calendar month!


