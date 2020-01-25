---
layout: post
title: Azure Site Recovery & VMWare - Addition of vCenter Server/vSphere ESXi server failed 
---
During a recent proof of concept deployment for Azure Site Recovery (ASR) with VMWare, I was  encountering issues adding vSphere instances and accounts into the environment via the setup process.

Despite being able to successfully connect and authenticate to the vCenter server from the ASR configuration server via VMWare PowerCLI I found that I was continually receiving this error within the configuration web front end.

![Error]({{ site.baseurl }}/posts/2020-01-25/error.jpg)

As an alternative it is possible to use the tool, cspsconfigtool which can be initiated from a command prompt on the configuration server and is located in "C:\ProgramData\ASR\home\svssystems\var"

![Error]({{ site.baseurl }}/posts/2020-01-25/configtool.jpg)

Using the configuration tool we can add authentication details for connecting to ESXi hosts/vCenter servers and also for authenticating to Windows and Linux machines for deployment of the Mobility Service which is used with ASR for VMWare.

Once you have added the authentication details for connecting to your ESXi hosts/vCenter servers you can add these servers to your ASR environment via the Azure portal.

![Error]({{ site.baseurl }}/posts/2020-01-25/azure1.jpg)

![Error]({{ site.baseurl }}/posts/2020-01-25/azure2.jpg)
