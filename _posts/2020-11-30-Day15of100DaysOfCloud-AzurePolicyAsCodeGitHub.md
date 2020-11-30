---
layout: post
tags: [azure,100daysofcloud]
title: Azure Policy as Code with Github [#100DaysOfCloud Day 15/100] 
excerpt_separator: <!--more-->
date: 2020-11-30 21:50
---
#### Introduction
Azure Policy helps to enforce organisational standards and to assess compliance at-scale in Azure. Common use cases for Azure Policy include implementing governance for resource consistency, regulatory compliance, security, cost, and management.

If you are using Azure Policy, as you grow and and mature your policies and artefacts you may be looking for a better way to manage your policy content. 

Microsoft have introduced preview functionality to integrate your Azure Policies with Github. This can allow you to have a more structured and collaborative "as code" approach.

#### Walkthrough
In the steps below I will walk through how to get started managing your Azure Policy with Github.

1. You will need a Github account, if you don't have one please go ahead and sign up - <a href="https://github.com/join" target="_blank">https://github.com/join</a>. If you've got one you can of course skip this step!

2. I recommend to create a repository to store your policies in first as the Azure portal only allows you to export to existing repos.

![]({{ site.baseurl }}/assets/img/blog/2020-11-30-Day15of100DaysOfCloud-AzurePolicyAsCodeGitHub/4.png)

3. Now open up the Azure Portal, and head for the Policy service. From the left menu choose Definitions, you should now see an option for Export definitions.

![]({{ site.baseurl }}/assets/img/blog/2020-11-30-Day15of100DaysOfCloud-AzurePolicyAsCodeGitHub/1.png)

4. Press Sign in with Github then Authorise Azure Github Actions.

![]({{ site.baseurl }}/assets/img/blog/2020-11-30-Day15of100DaysOfCloud-AzurePolicyAsCodeGitHub/2.png)
![]({{ site.baseurl }}/assets/img/blog/2020-11-30-Day15of100DaysOfCloud-AzurePolicyAsCodeGitHub/3.png)

5. Now select the repository, branch and directory where you want to push your policies to.

![]({{ site.baseurl }}/assets/img/blog/2020-11-30-Day15of100DaysOfCloud-AzurePolicyAsCodeGitHub/5.png)

6. In these next steps you should choose your scope for the management groups, subscriptions and definitions/assignments you wish to export.

![]({{ site.baseurl }}/assets/img/blog/2020-11-30-Day15of100DaysOfCloud-AzurePolicyAsCodeGitHub/6.png)

![]({{ site.baseurl }}/assets/img/blog/2020-11-30-Day15of100DaysOfCloud-AzurePolicyAsCodeGitHub/7.png)

7. Press Export.

![]({{ site.baseurl }}/assets/img/blog/2020-11-30-Day15of100DaysOfCloud-AzurePolicyAsCodeGitHub/8.png)

8. Head back over to Github and you should now see your policies begining to populate in your repo.

![]({{ site.baseurl }}/assets/img/blog/2020-11-30-Day15of100DaysOfCloud-AzurePolicyAsCodeGitHub/9.png)

9. When you export your policies into Github, a sample Github workflow file is also deployed. This workflow file uses <a href="https://github.com/marketplace/actions/manage-azure-policy" target="_blank">Manage Azure Policy action</a> to allow you to push any changes made to the exported policy resources in GitHub repository to Azure policy.

10. By default the workflow can be triggered manually using the Run workflow option from the actions menu.

![]({{ site.baseurl }}/assets/img/blog/2020-11-30-Day15of100DaysOfCloud-AzurePolicyAsCodeGitHub/10.png)

11. When ran the workflow will sync the changes to policy files with Azure and give you the status in the logs.

![]({{ site.baseurl }}/assets/img/blog/2020-11-30-Day15of100DaysOfCloud-AzurePolicyAsCodeGitHub/11.png)


--

I am taking part in the <a href="https://100daysofcloud.com/" target="_blank">#100DaysOfCloud Challenge</a>. Please do have a look at my <a href="https://github.com/rossinthecloud/100DaysOfCloud" target="_blank">Github journey tracker</a> to find out more, track my progress or get involved.

If you have any questions please also do reach out to me via a comment or on Twitter<a href="https://www.twitter.com/rossinthecloud" target="_blank"> @rossinthecloud</a>.

<a href="https://github.com/rossinthecloud/100DaysOfCloud" target="_blank">![]({{ site.baseurl }}/assets/img/100dayslogo.png)</a>

