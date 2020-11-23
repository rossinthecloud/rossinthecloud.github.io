---
layout: post
tags: [azure,storage,100daysofcloud]
title: Azure Storage - Prevent accidental deletion with Soft Delete [100DaysOfCloud Day 10/100] 
excerpt_separator: <!--more-->
---
#### Introduction 

Microsoft offer a feature called 'soft delete' for both Azure Blob Storage and Azure Files (this is a fairly recent addition to Azure Files!)

This feature allows you an easier recovery path if data is deleted accidentally by a service or user.
Microsoft do not currently enable this setting by default but they do recommend that you enable it, and it is a recommendation in <a href="https://azure.microsoft.com/en-us/services/advisor/" target="_blank">Azure Advisor</a> as a best practice.

#### Enabling soft delete - Azure Files
Sign into the Azure portal.

Navigate to your storage account and select Soft delete under File service.

Select Enabled for file share soft delete.

Select File share retention period in days and enter a number of your choosing.

Select Save to confirm your data retention settings.

![]({{ site.baseurl }}/assets/img/blog/2020-11-20-Day10of100DaysOfCloud-AzureStorageSoftDelete/1.png)

#### Enabling Soft Delete - Azure Blob

Navigate to your storage account in the Azure Portal.

Locate the Data Protection option under Blob service.

Set the Blob soft delete property to Enabled.

Under Retention policies, specify how long soft-deleted blobs are retained by Azure Storage.

Save your changes.

![]({{ site.baseurl }}/assets/img/blog/2020-11-20-Day10of100DaysOfCloud-AzureStorageSoftDelete/4.png)

#### More Information

You can find more info around this functionality in these Microsoft docs - 

<a href="https://docs.microsoft.com/en-us/azure/storage/blobs/soft-delete-blob-overview" target="_blank">https://docs.microsoft.com/en-us/azure/storage/blobs/soft-delete-blob-overview</a>

<a href="https://docs.microsoft.com/en-us/azure/storage/files/storage-files-prevent-file-share-deletion" target="_blank">https://docs.microsoft.com/en-us/azure/storage/files/storage-files-prevent-file-share-deletion</a>

--

I am taking part in the <a href="https://100daysofcloud.com/" target="_blank">#100DaysOfCloud Challenge</a>. Please do have a look at my <a href="https://github.com/rossinthecloud/100DaysOfCloud" target="_blank">Github journey tracker</a> to find out more, track my progress or get involved.

If you have any questions please also do reach out to me via a comment or on Twitter<a href="https://www.twitter.com/rossinthecloud" target="_blank"> @rossinthecloud</a>.

<a href="https://github.com/rossinthecloud/100DaysOfCloud" target="_blank">![]({{ site.baseurl }}/assets/img/100dayslogo.png)</a>

