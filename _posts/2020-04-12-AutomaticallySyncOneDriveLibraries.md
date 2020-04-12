---
layout: post
tags: [onedrive,automation,office365]
title: Configuring SharePoint team site libraries to sync automatically with OneDrive
excerpt_separator: <!--more-->
---
Using the 'next generation' OneDrive client and Windows 10, it is possible to automatically sync SharePoint team site libraries. This can be configured either via group policy or Intune depending on which platform you are using to manage your policies.

There are a number of use cases where you may want to use this functionality, for example with document templates. If you have a central set of document templates in SharePoint these can then be automatically synced to Windows 10 devices.

In the example policy we will look at configuring a library to sync automatically using OneDrive group policies.

<!--more-->

#### Prerequisites  
- Download the latest OneDrive Group Policy templates and add to your group policy store.
- You must be using OneDrive Files On-Demand.
- Client devices must be running Windows 10 1709 build or later.

#### Limitations
- You should not use this setting for libraries with more than 5,000 files or folders. 
- Do not enable this setting for the same library to more than 1,000 devices.
- This feature is not available for on-premises SharePoint sites, only Office 365.
- Whilst the setting is enabled the user cannot choose to stop syncing the libraries.

#### Gathering your library ID(s)

The policy makes use of library ID(s) in order to know which libraries to sync. 

To find the library ID, sign in as a Global Admin or SharePoint Admin in Office 365, browse to the library, and select Sync. In the Starting sync dialog box, select the Copy library ID link.

![]({{ site.baseurl }}/assets/img/blog/2020-04-12-AutomaticallySyncOneDriveLibraries/1.png)

In order to avoid any issues with special characters in the ID, we can use PowerShell to normalise the string. Replace "Copied String" with your library ID.

```powershell
[uri]::UnescapeDataString("Copied String")
```
Take a note of the normalised string from PowerShell, we will need this below.

#### Enabling the policy (Group Policy)

Create a new group policy or edit your existing group policy where you are defining OneDrive settings.

Navigate to User Configuration > Policies > Administrative Templates > OneDrive

Double click on the setting 'Configure team site libraries to sync automatically'

![]({{ site.baseurl }}/assets/img/blog/2020-04-12-AutomaticallySyncOneDriveLibraries/2.png)

Press Enabled and then press Show

Under Value name, enter a friendly name for your library and under Value paste in the normalised string for the library ID we captured earlier.

![]({{ site.baseurl }}/assets/img/blog/2020-04-12-AutomaticallySyncOneDriveLibraries/3.png)

Press OK to apply the change to the group policy.

Once enabled, the setting applies the next time a user signs in to the OneDrive sync app (OneDrive.exe). In order to distribute network load, the change will only take affect any time within an eight hour window.

If you disable this setting, team site libraries that you've specified aren't automatically synced for new users. Existing users can choose to stop syncing the libraries, but the libraries won't stop syncing automatically.




