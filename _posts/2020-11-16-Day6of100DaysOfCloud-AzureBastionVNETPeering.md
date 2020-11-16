---
layout: post
tags: [azure,bastion,100daysofcloud]
title: Azure Bastion and VNet Peering [100DaysOfCloud Day 6/100] 
excerpt_separator: <!--more-->
---
The concept of having a bastion or "jump" host is not a new one. But it was once the case whereby to manage Azure VMs you would have to setup a VPN into your Azure environment or god forbid, punch some holes in your firewall or NSGs to allow SSH or RDP from the internet (or at least particular external IPs).

Azure Bastion can help you avoid all of these things, it is a platform as a service offering in Azure which allows you to securely RDP or SSH to your virtual machines straight from the Azure portal in your web browser. No more VPN for management or open ports on the internet to your VMs required!

![]({{ site.baseurl }}/assets/img/blog/2020-11-16-Day6of100DaysOfCloud-AzureBastionVNETPeering/1.png)

<!--more-->

This has been around for a while now but one challenge I saw out in the wild was the service cost if you had multiple virtual networks. Despite having them connected together through VNet peering, you had to purchase the Bastion service for each virtual network.

However! Microsoft have now released into preview the ability to use Azure Bastion with VNet peering.
This includes these VNet peering scenarios - 
- Virtual network peering: Connected virtual networks within the same Azure region.
- Global virtual network peering: Connected virtual networks across Azure regions.
- Between Azure subscriptions (aslong as the subscriptions are in the same tenant)

This is a very welcome addition which means you can have one Bastion service in one of your virtual networks but access VMs in your peered VNETs. Your architecture can now look more like this -

![]({{ site.baseurl }}/assets/img/blog/2020-11-16-Day6of100DaysOfCloud-AzureBastionVNETPeering/2.png)

If you are interested in finding out more about Azure Bastion - be sure to check out these documents - <a href="https://docs.microsoft.com/en-us/azure/bastion/" target="_blank">https://docs.microsoft.com/en-us/azure/bastion/</a>

--

I am taking part in the <a href="https://100daysofcloud.com/" target="_blank">#100DaysOfCloud Challenge</a>. Please do have a look at my <a href="https://github.com/rossinthecloud/100DaysOfCloud" target="_blank">Github journey tracker</a> to find out more, track my progress or get involved.

If you have any questions please also do reach out to me via a comment or on Twitter<a href="https://www.twitter.com/rossinthecloud" target="_blank"> @rossinthecloud</a>.

<a href="https://github.com/rossinthecloud/100DaysOfCloud" target="_blank">![]({{ site.baseurl }}/assets/img/100dayslogo.png)</a>

