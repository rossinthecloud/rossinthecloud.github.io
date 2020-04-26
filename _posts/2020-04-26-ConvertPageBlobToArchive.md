---
layout: post
tags: [azure,blob,storage,blobporter,archive]
title: Converting page blobs to the archive tier in Azure Storage
excerpt_separator: <!--more-->
---
If you have a scenario where you have some database or virtual machine files in Azure Storage which you no longer require in your live environment but need to retain in archive, you will probably find that you are unable to place these files into the archive tier in Azure.

This is because these files are typically held in page blobs. Page blobs are optimised for Random IO (Databases, VM’s) whereas block blobs are optimised for Sequential IO (Text files, Images, Videos, Logs etc).

Most of the cost saving options like archive tier, blob level tiering etc are only available for block blobs and not for page blobs.

To work around this I started exploring whether it was possible to convert from page blob to block blob. None of the common tools such as AZCopy or Azure Storage Explorer appear to offer this functionality but we can accomplish this by using the hidden gem from Microsoft that is <a href="https://github.com/Azure/blobporter" target="_blank">Blobporter</a>. 

In this post we will look at using Blobporter to convert page blob data to block blob and placing this data in the Azure Storage archive tier.

<!--more-->

#### Virtual Machine & Storage Location

As the first step go ahead and spin up a temporary Azure Virtual Machine to assist with converting the data. I would recommend that you place this machine, your source storage account and your destination storage account in the same Azure region to minimise your Azure egress network charges.

This virtual machine can be either Windows or Linux depending on your preference as Blobporter is available for both platforms. In this example I will use a Windows virtual machine.

#### Download Blobporter

Once you have your temporary Azure VM spun up, go ahead and <a href="https://github.com/Azure/blobporter/releases" target="_blank">download Blobporter from Github</a>

#### Create a destination storage account 

(You can skip this part if you have an existing storageV2 account you wish to use as the destination.)

In the Azure portal create a new storageV2 account.

![]({{ site.baseurl }}/assets/img/blog/2020-04-26-ConvertPageBlobToArchive/createstorage1.png)

![]({{ site.baseurl }}/assets/img/blog/2020-04-26-ConvertPageBlobToArchive/createstorage2.png)

#### Access Keys

To connect with Blobporter you will need the access keys for both the source and destination storage accounts.

Go ahead and take a copy of these now.

![]({{ site.baseurl }}/assets/img/blog/2020-04-26-ConvertPageBlobToArchive/keys.png)

#### Converting from page blob to block blob

On your temporary Azure VM for running the conversion, open a Command Prompt and setup the connection to your source storage account.

set SRC_ACCOUNT_NAME=YOURSOURCESTORAGEACCONTNAME (if it is contososource.blob.core.windows.net enter only contososource)
set SRC_ACCOUNT_KEY=YOURSOURCESTORAGEACCOUNTKEY

Now set the values for your destination storage account

set ACCOUNT_NAME=YOURDESTINATIONSTORAGEACCOUNTNAME (if it is contosodestination.blob.core.windows.net enter only contosodestination)
set ACCOUNT_KEY=YOURDESTINATIONSTORAGEACCOUNTKEY

Navigate to the folder where you have extracted Blobporter and run the following command to execute the conversion and copy from source to destination. Substitute your own values where indicated. 

Blobporter.exe -f "https://YOURSOURCESTORAGEACCOUNT.blob.core.windows.net/CONTAINERWHEREYOURDATAIS" -c YOURDESTINATIONCONTAINER -t blob-blockblob -b 90MB

![]({{ site.baseurl }}/assets/img/blog/2020-04-26-ConvertPageBlobToArchive/conversion.png)

#### Move data to the archive tier

Now you have converted your data you can move it to the archive tier and benefit from the cost savings this brings.

To move to the archive tier, in the Azure portal navigate to the storage account containing the data.

Select the files you wish to archive, press the option for change tier. Select archive from the drop down and press Save.

![]({{ site.baseurl }}/assets/img/blog/2020-04-26-ConvertPageBlobToArchive/convert1.png)
![]({{ site.baseurl }}/assets/img/blog/2020-04-26-ConvertPageBlobToArchive/changetier.png)

More information on the archive tier is available from Microsoft <a href="https://docs.microsoft.com/en-us/azure/storage/blobs/storage-blob-storage-tiers?tabs=azure-portal#archive-access-tier" target="_blank">here</a> 

#### Move data from the archive tier

Follow the steps above but this time select the Hot tier.

#### Converting back from block blob to page blob

If you ever need to convert the data back from block blob to page blob, the process is very similar.

Set your values for your source and destination storage accounts.

set SRC_ACCOUNT_NAME=YOURSOURCESTORAGEACCONTNAME (if it is contososource.blob.core.windows.net enter only contososource)
set SRC_ACCOUNT_KEY=YOURSOURCESTORAGEACCOUNTKEY

set ACCOUNT_NAME=YOURDESTINATIONSTORAGEACCOUNTNAME (if it is contosodestination.blob.core.windows.net enter only contosodestination)
set ACCOUNT_KEY=YOURDESTINATIONSTORAGEACCOUNTKEY

Run the conversion and copy but this time use the -t option pageblob-blob

Blobporter.exe -f "https://blobporterdemodest.blob.core.windows.net/conversion" -c conversion -t blob-pageblob -b 90MB

![]({{ site.baseurl }}/assets/img/blog/2020-04-26-ConvertPageBlobToArchive/convertback.png)
