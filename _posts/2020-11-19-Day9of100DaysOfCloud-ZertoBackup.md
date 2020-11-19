---
layout: post
tags: [azure,zerto,backup,100daysofcloud]
title: Zerto 8.5 and Zerto Backup [100DaysOfCloud Day 9/100] 
excerpt_separator: <!--more-->
---
#### Introduction 
On a recent project with a customer we deployed Zerto as the solution for DR replication to Azure. This was my first introduction to Zerto and traditionally I normally favour Microsoft native solutions rather than 3rd party products "unless there is a good reason not to".

So why Zerto and not Azure Site Recovery here?

Well for a few reasons..  
- This customer wanted to remain open to the possibility of multi-cloud and multi-site replication. Zerto can handle replication between Hyper-V, VMWare, AWS, Azure and others seamlessly. Either on a one to one relationship or one to many! 
- The customer also had a requirement to easily migrate their remaining VMWare estate to Hyper-V which Zerto can help with as they can replicate the VMs and pretty much convert on the fly. The cutover is not much more than a reboot!
- Finally, Zerto also us to overcome some sizing and change rate restrictions for certain workloads which were beyond the limits for Azure Site Recovery.

Overall Zerto is working well so far for DR replication from on-prem to Azure, and also in assisting with the migration from VMWare to Hyper-V. The majority of issues I have seen have been with vendor appliances but this was more down to differences in driver set within the appliance images between Hyper-V and VMWare, or licensing restriction rather than a Zerto issue.

#### Zerto Backup 
This is where it gets a little more interesting.. Zerto has traditionally been a disaster recovery product, and you would normally require a seperate backup solution for your backup requirements. 

However Zerto have been trying for a while to make inroads into the backup space and are now terming themselves as your 'data protection' solution of choice.

I attended Zerto's 'VBeers with Engineers' event this evening where they covered some of the improved backup functionality in their new 8.5 release. This release looks to have vastly improved Zerto's capabilities.

Caveat I am yet to try this new backup capability nor do I yet understand the full pros and cons in comparison to other solutions but it looks like an option worth considering.

Zerto's old view of the world - 
![]({{ site.baseurl }}/assets/img/blog/2020-11-19-Day9of100DaysOfCloud-ZertoBackup/1.png)

Zerto's new "data protection" view of the world -
![]({{ site.baseurl }}/assets/img/blog/2020-11-19-Day9of100DaysOfCloud-ZertoBackup/2.png)

In terms of benefits, what this means is you could have one single solution to cover your DR and backup - single interface/management and only one set of licensing to pay for rather than licensing DR and backup products seperately. Of course on the flip side of this, you are "putting all your eggs in one basket" so this is a factor to consider.

For backups, Zerto are doing something a little different here. They are taking continous replication of your data, sometimes as low as 5 seconds RPO using their replication and journal technology. So this could allow you to retrieve a backup from seconds ago rather than many of the traditional solutions whereby you are running a snapshot based backup every X minutes, hours, days, weeks, etc.

![]({{ site.baseurl }}/assets/img/blog/2020-11-19-Day9of100DaysOfCloud-ZertoBackup/5.png)

The 8.5 release opens up the possibility to send your long term backups to either AWS or Azure (Google is also coming soon).

![]({{ site.baseurl }}/assets/img/blog/2020-11-19-Day9of100DaysOfCloud-ZertoBackup/3.png)
![]({{ site.baseurl }}/assets/img/blog/2020-11-19-Day9of100DaysOfCloud-ZertoBackup/4.png)

It also opens up new functionality to recover right down to file and folder level.

![]({{ site.baseurl }}/assets/img/blog/2020-11-19-Day9of100DaysOfCloud-ZertoBackup/6.png)

#### VMWare on Public Cloud

There has been a number of announcements around this recently, with Microsoft also placing VMWare on Azure into GA as a first party solution. 

Zerto have joined the party as a VMWare Cloud verified solution, now fully supporting their product when used on VMWare in the public cloud. 


#### Try It Out

If you want to give this a go you have 2 options to get playing.

<a href="https://www.zerto.com/page/free-trial-zerto/" target="_blank">Download and deploy a trial license.</a>

OR

<a href="https://www.zerto.com/page/free-on-demand-labs/" target="_blank">Try it out in Zerto's online/on-demand labs </a>


--

I am taking part in the <a href="https://100daysofcloud.com/" target="_blank">#100DaysOfCloud Challenge</a>. Please do have a look at my <a href="https://github.com/rossinthecloud/100DaysOfCloud" target="_blank">Github journey tracker</a> to find out more, track my progress or get involved.

If you have any questions please also do reach out to me via a comment or on Twitter<a href="https://www.twitter.com/rossinthecloud" target="_blank"> @rossinthecloud</a>.

<a href="https://github.com/rossinthecloud/100DaysOfCloud" target="_blank">![]({{ site.baseurl }}/assets/img/100dayslogo.png)</a>

