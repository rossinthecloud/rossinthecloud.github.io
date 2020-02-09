---
layout: post
tags: [azure,windows virtual desktop,microsoft teams]
title: Windows Virtual Desktop - Teams Machine Wide Install "Installation has failed"
---

When deploying Windows Virtual Desktop and Microsoft Teams, it is preferrable to install Teams into your desktop image using the machine wide installation option rather than each individual user having Teams installed within their profile.

The Teams MSI package can be downloaded from Microsoft using one of the following links: 

[32-bit version](https://teams.microsoft.com/downloads/desktopurl?env=production&plat=windows&download=true&managedInstaller=true )

[64-bit version](https://teams.microsoft.com/downloads/desktopurl?env=production&plat=windows&download=true&managedInstaller=true&arch=x64)

If you are using "vanilla" Microsoft Windows Virtual Desktop you will find that the installer fails with the error "Installation has failed". 

![Install Error]({{ site.baseurl }}/assets/img/blog/2020-02-09-WVD-Teams-Installationhasfailed/error.jpg)

This is because the the installer looks for the presence of Citrix or VMWare VDI components by looking up the following registry keys

> HKLM\Software\Citrix\PortICA

> HKLM\Software\VMware,Inc.\VMware VDM\Agent

Create one of these registry keys and then run the installation using this command.

> msiexec /i "path_to_msi" ALLUSER=1













