---
layout: post
tags: [azure]
title: Server Core Quick Domain Deployment
excerpt_separator: <!--more-->
---
I am rebuilding my home lab (for the millionith time - but that's the point right!)

Quick post around deploying a new Active Directory forest/domain and domain controller using Server Core... This is not new but I still speak with a lot of people who have never deployed or used Server Core!

1.. Deploy your VM using your chosen Windows Server OS image - I am deploying Windows Server, version 20H2 which only comes as Core.

2.. Once you have installed you will be prompted on first boot to set a local administrator password. Set your local admin password.

3.. Run sconfig at the command prompt.

![]({{ site.baseurl }}/assets/img/blog/2020-03-09-ServerCoreDomainControllers/1.png)

4.. Using sconfig, configure your static IP address and network settings that you will need for your domain controller. Also set your chosen name for the server and reboot.

5.. Once you've rebooted, login and run powershell at the command prompt.

6.. First install Active Directory Domain services 

```powershell
Install-WindowsFeature AD-Domain-Services
```

7.. New configure a brand new Active Directory forest - 

```powershell
Install-ADDSForest -DomainName NAMEOFYOURCHOSENDOMAIN
```

8.. When prompted, enter the safe mode administrator password  - this is also known as the Directory Services Restore Mode (DSRM) password.

9.. Once the install process completes, you’ll be prompted for a restart, and after restarting you’ll have the first Domain Controller for a new forest.

To manage your domain controller you can use a <a href="https://www.microsoft.com/en-us/download/details.aspx?id=45520" target="_blank">Windows 10 desktop with the RSAT tools.</a>

