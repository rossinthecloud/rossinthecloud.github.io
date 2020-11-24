---
layout: post
tags: [azure,patching,windowsupdate,windows,100daysofcloud]
title: Automatic VM Patching in Azure [100DaysOfCloud Day 13/100] 
excerpt_separator: <!--more-->
---

Server patching is a pain that many IT admins have to suffer (or at least manage!) 

There are a whole plethora of options available out there these days to manage and automate your server or VM patching. Over the years, I have seen patching done both very well and badly, the principals are nearly always the same.. You want to keep as up to date as you can whilst minimising the risk and disruption to your organisation at the same time.

![]({{ site.baseurl }}/assets/img/blog/2020-11-24-Day13of100DaysOfCloud-AzureAutomaticVMPatching/1.png)

*The worst I have personally seen was an organisation with Windows Updates force disabled at GPO level across the entire domain - and servers running RTM - so never patched! (inc some Server 2003).* 

Microsoft are working on a feature in Azure which will automatically manage your VM guest OS patching. Currently in preview but I will walk through an overview below.

*Note as this feature is still in preview it does not have an SLA and it is not recommended to rely upon it for production workloads.*

#### How does this work?

When you have the service enabled, the VM will be assessed periodically for new available 'Critical' or 'Security' operating system patches. When Microsoft release new patches every month, the process will kick off for your VMs and patches will then be installed within 30 days of their monthly Windows Update release.

If new patches are identified, they are automatically downloaded and then installed during the VM's off peak hours (determined by the timezone of the VM).

The platform will automatically monitor your virtual machine health when applying patches to determine if any failures have occured.

Patches are also applied on "availability first principles" as per these examples provided by Microsoft.

For a group of virtual machines undergoing an update, the Azure platform will orchestrate updates:

**Across regions:**
- A monthly update is orchestrated across Azure globally in a phased manner to prevent global deployment failures.
- A phase can have one or more regions, and an update moves to the next phases only if eligible VMs in a phase update successfully.
- Geo-paired regions are not updated concurrently and can't be in the same regional phase.
- The success of an update is measured by tracking the VM’s health post update. VM Health is tracked through platform health indicators for the VM.

**Within a region:**
- VMs in different Availability Zones are not updated concurrently.
- VMs not part of an availability set are batched on a best effort basis to avoid concurrent updates for all VMs in a subscription.

**Within an availability set:**
- All VMs in a common availability set are not updated concurrently.
- VMs in a common availability set are updated within Update Domain boundaries and VMs across multiple 
- Update Domains are not updated concurrently.
 
#### What OS are supported?

Currently Microsoft are supporting Server 2012 R2, 2016 and 2019 Datacenter for this functionality. 

#### How do I enable the service?

As this is a preview service, I would recommend going direct to the Microsoft documentation to check the latest requirements and steps to get started - as things can change!

The Microsoft documentation can be found here - <a href="https://docs.microsoft.com/en-us/azure/virtual-machines/windows/automatic-vm-guest-patching#requirements-for-enabling-automatic-vm-guest-patching" target="_blank">https://docs.microsoft.com/en-us/azure/virtual-machines/windows/automatic-vm-guest-patching#requirements-for-enabling-automatic-vm-guest-patching</a>


--

I am taking part in the <a href="https://100daysofcloud.com/" target="_blank">#100DaysOfCloud Challenge</a>. Please do have a look at my <a href="https://github.com/rossinthecloud/100DaysOfCloud" target="_blank">Github journey tracker</a> to find out more, track my progress or get involved.

If you have any questions please also do reach out to me via a comment or on Twitter<a href="https://www.twitter.com/rossinthecloud" target="_blank"> @rossinthecloud</a>.

<a href="https://github.com/rossinthecloud/100DaysOfCloud" target="_blank">![]({{ site.baseurl }}/assets/img/100dayslogo.png)</a>

