---
layout: post
tags: [azure,management groups]
title: Azure Management Groups Intro
excerpt_separator: <!--more-->
---
A look into Azure Management Groups as I recently reorganised my own personal subscriptions into a new management group and wanted to share a quick example here.

If you or your organisation have multiple Azure subscriptions and aren't using management groups, I would recommend a look into this.

<!--more-->

#### What is an Azure Management Group?

Azure Management Groups are a level above Azure Subscriptions. They are logical containers that allow you to centrally manage things like access, policy, and compliance across multiple Azure Subscriptions.

A good use case might be if you want to centrally restrict the Azure regions or virtual machine sizes available in your Azure subscriptions for compliance or cost reasons. Using Azure Management Groups you can set this once using a policy at the Management Group level.



#### Quick Start Example

It's pretty quick to get going with a simple management group. In this example we will create a single management group and add a couple of Azure subscriptions into it.

Let's jump straight into the Azure portal and look for the Management group service.

![]({{ site.baseurl }}/assets/img/blog/2020-05-11-AzureManagementGroupsIntro/1.png)

Press Start using management groups

![]({{ site.baseurl }}/assets/img/blog/2020-05-11-AzureManagementGroupsIntro/2.png)

Enter an ID and name for your management group.

(You may want to prefix your management group with mg- as recommended by the naming conventions as part of the <a href="https://docs.microsoft.com/en-us/azure/cloud-adoption-framework/ready/azure-best-practices/naming-and-tagging" target="_blank">Cloud Adoption Framework Best Practices</a>)

![]({{ site.baseurl }}/assets/img/blog/2020-05-11-AzureManagementGroupsIntro/3.png)

This next part can sometimes take a while so you might want to grab a drink of your choice!

![]({{ site.baseurl }}/assets/img/blog/2020-05-11-AzureManagementGroupsIntro/4.png)

Once your management group has been created - to move a subscription into it, click on the three dots and select Move

![]({{ site.baseurl }}/assets/img/blog/2020-05-11-AzureManagementGroupsIntro/5.png)
![]({{ site.baseurl }}/assets/img/blog/2020-05-11-AzureManagementGroupsIntro/6.png)

Follow the wizard to add the subscription to your management group, then repeat this to add another.

You should end up with something which looks like this -

![]({{ site.baseurl }}/assets/img/blog/2020-05-11-AzureManagementGroupsIntro/7.png)



