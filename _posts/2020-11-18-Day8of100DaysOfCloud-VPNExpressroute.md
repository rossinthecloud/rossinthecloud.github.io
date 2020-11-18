---
layout: post
tags: [azure,expressroute,100daysofcloud]
title: Azure VPN Over Expressroute Private Peering [100DaysOfCloud Day 8/100] 
excerpt_separator: <!--more-->
---
Great to see Microsoft have now made VPN over Expressroute as part of the service generally available. This means that you can now configure VPN natively across Expressroute private peering.

Having come up against this on some customer requirements, it was often a surprise to customers that traffic over Expressroute private peering is not necessarily encrypted end to end by default. 

You previously either had to be comfortable that your provider was keeping your traffic isolated to a good level and perhaps take an assumption that a lot of workloads these days are encrypted in transit so any risk was acceptable or fudge your own 3rd party VPN inside your Expressroute private peering.

With the GA release, you can now configure additional encryption native to the Expressroute service for private peering. This gives you a reference architecture like this -

![]({{ site.baseurl }}/assets/img/blog/2020-11-18-Day8of100DaysOfCloud-VPNExpressroute/1.png)

If this is something you are interested in please do have a look at <a href="https://docs.microsoft.com/en-us/azure/vpn-gateway/site-to-site-vpn-private-peering" target="_blank">this documentation</a> for more information.


--

I am taking part in the <a href="https://100daysofcloud.com/" target="_blank">#100DaysOfCloud Challenge</a>. Please do have a look at my <a href="https://github.com/rossinthecloud/100DaysOfCloud" target="_blank">Github journey tracker</a> to find out more, track my progress or get involved.

If you have any questions please also do reach out to me via a comment or on Twitter<a href="https://www.twitter.com/rossinthecloud" target="_blank"> @rossinthecloud</a>.

<a href="https://github.com/rossinthecloud/100DaysOfCloud" target="_blank">![]({{ site.baseurl }}/assets/img/100dayslogo.png)</a>

