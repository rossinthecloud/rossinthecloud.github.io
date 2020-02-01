---
layout: post
tags: [azure,site recovery,vmware]
title: Azure Site Recovery & VMWare - Addition of vCenter Server/vSphere ESXi server failed 
excerpt_separator: <!--more-->
---
During a recent proof of concept deployment for Azure Site Recovery (ASR) with VMWare, I was  encountering issues adding vCenter instances and accounts into the environment via the setup process.

Despite being able to successfully connect and authenticate to the vCenter server from the ASR configuration server via VMWare PowerCLI I found that I was continually receiving this error within the configuration web front end.

![Error]({{ site.baseurl }}/assets/img/blog/2020-01-25-ASRVMwareError/error.JPG)

<!--more-->

As an alternative it is possible to use the tool, cspsconfigtool which can be initiated from a command prompt on the configuration server and is located in "C:\ProgramData\ASR\home\svssystems\var"

![Configuration Tool]({{ site.baseurl }}/assets/img/blog/2020-01-25-ASRVMwareError/configtool.JPG)

Using the configuration tool we can add authentication details for connecting to ESXi hosts/vCenter servers and also for authenticating to Windows and Linux machines for deployment of the Mobility Service which is used with ASR for VMWare.

Once you have added the authentication details for connecting to your ESXi hosts/vCenter servers you can add these servers to your ASR environment via the Azure portal. (Note it can sometimes take 15-30 minutes for these to appear)

![Azure Portal]({{ site.baseurl }}/assets/img/blog/2020-01-25-ASRVMwareError/azure1.JPG)

![Azure Portal]({{ site.baseurl }}/assets/img/blog/2020-01-25-ASRVMwareError/azure2.JPG)
