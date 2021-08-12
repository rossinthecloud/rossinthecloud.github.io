---
layout: post
tags: [azure,firewall,rfc1918]
title: Azure Firewall and non RFC1918 on prem networks
excerpt_separator: <!--more-->
---
Every so often I come across a customer who is using non <a href="https://datatracker.ietf.org/doc/html/rfc1918">RFC1918</a> ranges inside their internal on prem network.

RFC1918 address space includes the following networks:

10.0.0.0 – 10.255.255.255  (10/8 prefix)
172.16.0.0 – 172.31.255.255  (172.16/12 prefix)
192.168.0.0 – 192.168.255.255 (192.168/16 prefix)

If you are using or planning to use Azure Firewall this can have implications as by default Azure Firewall will perform Source-NAT (NAT) for non RFC1918 addresses.

In my example scenario I have..

- Azure Virtual WAN with secured virtual hubs 
- ExpressRoute connectivity back to on-premises
- A firewall back on prem at the edge of my ExpressRoute
- A non RFC 1918 private internal address space on prem (e.g 23.0.0.0/8)

I need to allow traffic between a virtual machine inside one of my Azure virtual networks and some virtual machines on prem. To pass this traffic at the on prem side I need to present the traffic from the private IP of the virtual machine in Azure to be accepted by a specific firewall rule.

In the default configuration of Azure Firewall, the firewall will SNAT my traffic towards my non RFC 1918 address space (e.g 23.0.0.0/8) on prem. This means that the traffic will present a source address belonging to the firewall and not the private IP of my Azure virtual machine!

This setting can also have implications if you are force tunneling all traffic back on prem.

To resolve this we need to look at the Private IP ranges (SNAT) configuration and add in the non RFC 1918 address space on prem into the configuration. Remember to also include IANA ranges unless you have a reason not to!

![]({{ site.baseurl }}/assets/img/blog/2021-08-12-AzureFirewallRFC1918/1.png)

**Important note** - This will only help with traffic passing through network rules on the Azure Firewall and NOT traffic passing via application rules. Application rules always have SNAT applied!

Further information on this topic and how to perform the configuration can be found <a href="https://docs.microsoft.com/en-us/azure/firewall/snat-private-range">here</a>





