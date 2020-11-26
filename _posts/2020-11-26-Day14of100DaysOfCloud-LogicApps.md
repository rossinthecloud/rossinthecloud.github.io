---
layout: post
tags: [azure,100daysofcloud]
title: Automatic Posting with Azure Logic Apps [#100DaysOfCloud Day 14/100] 
excerpt_separator: <!--more-->
date: 2020-11-26 22:23
---
#### Introduction
I have used Azure Logic Apps to perform various automation tasks - from helping organisations automate business processes, move data around, autoscale a VDI platform and lots of weird and wonderful things in between.

However, it has been a little while since I’ve used them and I’m kicking myself here! 

I have been manually posting updates about my blog posts across LinkedIn and Twitter. And each time I've been doing this, thinking to myself I should really automate this somehow..

#### What are Logic Apps

Azure Logic Apps is a cloud service that helps you schedule, automate, and orchestrate tasks, business processes, and workflows when you need to integrate apps, data, systems, and services across enterprises or organisations.

Similar to Azure Functions, this is serverless compute which you can design using a workflow designer or as code.

There are a wide range of prebuilt integrations out of the box so it is quick to get going!

#### Example Logic App

Here I am going to build a simple Logic App to automatically post to LinkedIn and Twitter when I publish a blog post.

Search for Logic Apps in the Azure Portal and press Add

![]({{ site.baseurl }}/assets/img/blog/2020-11-26-Day14of100DaysOfCloud-LogicApps/1.png)

Select a resource group, a name for your Logic App and your preferred region

![]({{ site.baseurl }}/assets/img/blog/2020-11-26-Day14of100DaysOfCloud-LogicApps/2.png)

Press Review + create

Once your Logic App has deployed, select Logic Apps Designer

![]({{ site.baseurl }}/assets/img/blog/2020-11-26-Day14of100DaysOfCloud-LogicApps/3.png)

You will see there are a ton of options with loads of integrations straight out the box. For now we just want to select Blank Logic App.

![]({{ site.baseurl }}/assets/img/blog/2020-11-26-Day14of100DaysOfCloud-LogicApps/4.png)

When a post is published to this blog, it is added to the RSS feed for my blog automatically. So what we want the logic app to do here is to check the RSS feed for new posts as it’s trigger to go off and do something.

Search for and select the RSS connector

![]({{ site.baseurl }}/assets/img/blog/2020-11-26-Day14of100DaysOfCloud-LogicApps/5.png)

Select the trigger

![]({{ site.baseurl }}/assets/img/blog/2020-11-26-Day14of100DaysOfCloud-LogicApps/6.png)
 
Enter in the RSS feed you want to check and how often you want the logic app to check. Here I am using the PublishDate element to check for new items in the RSS feed

![]({{ site.baseurl }}assets/img/blog/2020-11-26-Day14of100DaysOfCloud-LogicApps/7.png)

Press New Step

I want to automatically tweet when a blog post is published so search for Twitter and then select it

![]({{ site.baseurl }}/assets/img/blog/2020-11-26-Day14of100DaysOfCloud-LogicApps/8.png)

Choose Post a tweet

![]({{ site.baseurl }}/assets/img/blog/2020-11-26-Day14of100DaysOfCloud-LogicApps/9.png)

(I already have my Twitter account authenticated with my logic apps but if you don’t follow the prompts to login to Twitter and authorise Logic Apps to work here)

Now go ahead and press Add new parameter then select Tweet text

![]({{ site.baseurl }}/assets/img/blog/2020-11-26-Day14of100DaysOfCloud-LogicApps/10.png)

A handy little box will appear with common dynamic options we can use here.

I’ve selected Feed title and Primary feed link as I want the title for each blog post and a link to it to appear in my tweet. I can also add manual hashtags if I want as shown below.

![]({{ site.baseurl }}/assets/img/blog/2020-11-26-Day14of100DaysOfCloud-LogicApps/11.png)

If you only want to publish to Twitter you can go ahead and press Save to get your Logic App going. 

However, I also want to publish to LinkedIn so I’m going to add an additional step here which is very similar to the previous one.

Press New step and search for LinkedInV2

Select Share an article V2 and populate your values

![]({{ site.baseurl }}/assets/img/blog/2020-11-26-Day14of100DaysOfCloud-LogicApps/12.png)

Press Save to finish editing your Logic App

Press Run to test your Logic App. For anything to happen here you will need to publish a new blog post that the app can pick up and do something with.

Here is a working example run -

![]({{ site.baseurl }}/assets/img/blog/2020-11-26-Day14of100DaysOfCloud-LogicApps/13.png)
![]({{ site.baseurl }}/assets/img/blog/2020-11-26-Day14of100DaysOfCloud-LogicApps/14.png)

#### Next Steps

More information on Azure Logic Apps can be found in this documentation - <a href="https://docs.microsoft.com/en-us/azure/logic-apps/" target="_blank">https://docs.microsoft.com/en-us/azure/logic-apps/</a>

--

I am taking part in the <a href="https://100daysofcloud.com/" target="_blank">#100DaysOfCloud Challenge</a>. Please do have a look at my <a href="https://github.com/rossinthecloud/100DaysOfCloud" target="_blank">Github journey tracker</a> to find out more, track my progress or get involved.

If you have any questions please also do reach out to me via a comment or on Twitter<a href="https://www.twitter.com/rossinthecloud" target="_blank"> @rossinthecloud</a>.

<a href="https://github.com/rossinthecloud/100DaysOfCloud" target="_blank">![]({{ site.baseurl }}/assets/img/100dayslogo.png)</a>

