---
layout: post
tags: [azure,management groups,100daysofcloud]
title: Azure Management Groups - Day [1/100] #100DaysOfCloud
excerpt_separator: <!--more-->
---
A quick look into Azure Management Groups as I recently reorganised my own personal subscriptions and had a few questions from colleagues on these recently.

If you or your organisation have multiple Azure subscriptions and aren't using management groups, you probably should be :smiley:.

#### What is an Azure Management Group?

Azure Management Groups are a level above Azure Subscriptions. They are logical containers that allow you to centrally manage things like access, policy, and compliance across multiple Azure Subscriptions.

A good use case might be if you want to centrally restrict the Azure regions or virtual machine sizes available in your Azure subscriptions for compliance or cost reasons. Using Azure Management Groups you can set this once using a policy at the Management Group level.

<!--more-->



#### Quick Start Example

It's pretty quick to get going with a simple management group. In this example we will create a single management group and add a couple of Azure subscriptions into it.

Let's jump straight into the Azure portal and look for the Management group service.

![](../assets/img/blog/2020-11-11-Day1of100DaysOfCloud-AzureManagementGroups/1.png)

Press Start using management groups

![](../assets/img/blog/2020-11-11-Day1of100DaysOfCloud-AzureManagementGroups/2.png)

Enter an ID and name for your management group.

(You may want to prefix your management group with mg- as recommended by the naming conventions as part of the <a href="https://docs.microsoft.com/en-us/azure/cloud-adoption-framework/ready/azure-best-practices/naming-and-tagging" target="_blank">Cloud Adoption Framework Best Practices</a>)

![](../assets/img/blog/2020-11-11-Day1of100DaysOfCloud-AzureManagementGroups/3.png)

This next part can sometimes take a while so you might want to grab a drink of your choice!

![](../assets/img/blog/2020-11-11-Day1of100DaysOfCloud-AzureManagementGroups/4.png)

Once your management group has been created - to move a subscription into it, click on the three dots and select Move

![](../assets/img/blog/2020-11-11-Day1of100DaysOfCloud-AzureManagementGroups/5.png)
![](../assets/img/blog/2020-11-11-Day1of100DaysOfCloud-AzureManagementGroups/6.png)

Follow the wizard to add the subscription to your management group, then repeat this to add another.

You should end up with something which looks like this -

![](../assets/img/blog/2020-11-11-Day1of100DaysOfCloud-AzureManagementGroups/7.png)

--

I am taking part in the <a href="https://100daysofcloud.com/" target="_blank">#100DaysOfCloud Challenge</a>. Please do have a look at my <a href="https://github.com/rossinthecloud/100DaysOfCloud" target="_blank">Github journey tracker</a> to find out more, track my progress or get involved.

If you have any questions please also do reach out to me via a comment or on Twitter<a href="https://www.twitter.com/rossinthecloud" target="_blank"> @rossinthecloud</a>.

<a href="https://github.com/rossinthecloud/100DaysOfCloud" target="_blank">![](../assets/img/100dayslogo.png)</a>

