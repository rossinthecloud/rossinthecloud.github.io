---
layout: post
tags: [azure]
title: Azure Policy as Code with Github
excerpt_separator: <!--more-->
---
#### Introduction
Azure Policy helps to enforce organisational standards and to assess compliance at-scale in Azure. Common use cases for Azure Policy include implementing governance for resource consistency, regulatory compliance, security, cost, and management.

If you are using Azure Policy, as you grow and mature your policies and artefacts you may be looking for a better way to manage your policy content. 

Microsoft have introduced preview functionality to integrate your Azure Policies with Github. This can allow you to have a more structured and collaborative "as code" approach.

<!--more-->

#### Walkthrough
In the steps below I will walk through how to get started managing your Azure Policy with Github.

You will need a Github account, if you don't have one please go ahead and sign up - <a href="https://github.com/join" target="_blank">https://github.com/join</a>. If you've got one you can of course skip this step!

I recommend to create a repository to store your policies in first as the Azure portal only allows you to export to existing repos.

![]({{ site.baseurl }}/assets/img/blog/2020-11-30-AzurePolicyAsCodeGitHub/4.png)

Now open up the Azure Portal, and head for the Policy service. From the left menu choose Definitions, you should now see an option for Export definitions.

![]({{ site.baseurl }}/assets/img/blog/2020-11-30-AzurePolicyAsCodeGitHub/1.png)

Press Sign in with Github then Authorise Azure Github Actions.

![]({{ site.baseurl }}/assets/img/blog/2020-11-30-AzurePolicyAsCodeGitHub/2.png)
![]({{ site.baseurl }}/assets/img/blog/2020-11-30-AzurePolicyAsCodeGitHub/3.png)

Now select the repository, branch and directory where you want to push your policies to.

![]({{ site.baseurl }}/assets/img/blog/2020-11-30-AzurePolicyAsCodeGitHub/5.png)

In these next steps you should choose your scope for the management groups, subscriptions and definitions/assignments you wish to export.

![]({{ site.baseurl }}/assets/img/blog/2020-11-30-AzurePolicyAsCodeGitHub/6.png)

![]({{ site.baseurl }}/assets/img/blog/2020-11-30-AzurePolicyAsCodeGitHub/7.png)

Press Export.

![]({{ site.baseurl }}/assets/img/blog/2020-11-30-AzurePolicyAsCodeGitHub/8.png)

Head back over to Github and you should now see your policies begining to populate in your repo.

![]({{ site.baseurl }}/assets/img/blog/2020-11-30-AzurePolicyAsCodeGitHub/9.png)

Now you have your policies in Github, you can manage and source control them from there - then push any changes into Azure using Github Actions.

A sample Github workflow file is included with your policy export. This workflow file uses the <a href="https://github.com/marketplace/actions/manage-azure-policy" target="_blank">Manage Azure Policy action</a> to allow you to push any changes made to the exported policy resources in GitHub repository to Azure policy.

By default the workflow can be triggered manually using the Run workflow option from the actions menu.

![]({{ site.baseurl }}/assets/img/blog/2020-11-30-AzurePolicyAsCodeGitHub/10.png)

When ran the workflow will sync the changes to policy files with Azure and give you the status in the logs.

![]({{ site.baseurl }}/assets/img/blog/2020-11-30-AzurePolicyAsCodeGitHub/11.png)


