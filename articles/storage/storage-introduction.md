---
title: Introduction to Azure Storage | Microsoft Docs
description: An overview of Azure Storage, Microsoft's online data storage in the cloud. Learn how to use the best available cloud storage solution in your applications.
services: storage
documentationcenter: ''
author: mmacy
manager: timlt
editor: tysonn

ms.assetid: a4a1bc58-ea14-4bf5-b040-f85114edc1f1
ms.service: storage
ms.workload: storage
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: get-started-article
ms.date: 07/26/2017
ms.author: marsma

---
# Introduction to Microsoft Azure Storage

## Overview
Azure Storage is the cloud storage solution for modern applications that rely on durability, availability, and scalability to meet the needs of their customers. By reading this article, developers, IT Pros, and business decision makers can learn about:

* What Azure Storage is, and how you can take advantage of it in your cloud, mobile, server, and desktop applications
* What kinds of data you can store with the Azure Storage services: blob (object) data, NoSQL table data, queue messages, and file shares.
* How access to your data in Azure Storage is managed
* How your Azure Storage data is made durable via redundancy and replication
* Where to go next to build your first Azure Storage application

<!-- after our quick starts are available, replace this link with a link to one of those. 
Had to remove this article, it refers to the VS quickstarts, and they've stopped publishing them. Robin --> 
<!-- To get up and running with Azure Storage quickly, see [Get started with Azure Storage in five minutes](storage-getting-started-guide.md). -->

For details on tools, libraries, and other resources for working with Azure Storage, see [Next Steps](#next-steps) below.

## What is Azure Storage?
Cloud computing enables new scenarios for applications requiring scalable, durable, and highly available storage for their data – which is exactly why Microsoft developed Azure Storage. In addition to making it possible for developers to build large-scale applications to support new scenarios, Azure Storage also provides the storage foundation for Azure Virtual Machines, a further testament to its robustness.

Azure Storage is massively scalable, so you can store and process hundreds of terabytes of data to support the big data scenarios required by scientific, financial analysis, and media applications. Or you can store the small amounts of data required for a small business website. Wherever your needs fall, you pay only for the data you're storing. Azure Storage currently stores tens of trillions of unique customer objects, and handles millions of requests per second on average.

Azure Storage is elastic, so you can design applications for a large global audience, and scale those applications as needed - both in terms of the amount of data stored and the number of requests made against it. You pay only for what you use, and only when you use it.

Azure Storage uses an auto-partitioning system that automatically load-balances your data based on traffic. This means that as the demands on your application grow, Azure Storage automatically allocates the appropriate resources to meet them.

Azure Storage is accessible from anywhere in the world, from any type of application, whether it's running in the cloud, on the desktop, on an on-premises server, or on a mobile or tablet device. You can use Azure Storage in mobile scenarios where the application stores a subset of data on the device and synchronizes it with a full set of data stored in the cloud.

Azure Storage supports clients using a diverse set of operating systems (including Windows and Linux) and a variety of programming languages (including .NET, Java, Node.js, Python, Ruby, PHP and C++ and mobile programming languages) for convenient development. Azure Storage also exposes data resources via simple REST APIs, which are available to any client capable of sending and receiving data via HTTP/HTTPS.

Azure Premium Storage delivers high-performance, low-latency disk support for I/O intensive workloads running on Azure Virtual Machines. With Azure Premium Storage, you can attach multiple persistent data disks to a virtual machine and configure them to meet your performance requirements. Each data disk is backed by an SSD disk in Azure Premium Storage for maximum I/O performance. See [Premium Storage: High-Performance Storage for Azure Virtual Machine Workloads](storage-premium-storage.md) for more details.

## Introducing the Azure Storage services
Azure storage provides the following four services: Blob storage, Table storage, Queue storage, and File storage.

* Blob Storage stores unstructured object data. A blob can be any type of text or binary data, such as a document, media file, or application installer. Blob storage is also referred to as Object storage.
* Table Storage stores structured datasets. Table storage is a NoSQL key-attribute data store, which allows for rapid development and fast access to large quantities of data.
* Queue Storage provides reliable messaging for workflow processing and for communication between components of cloud services.
* File Storage offers shared storage for legacy applications using the standard SMB protocol. Azure virtual machines and cloud services can share file data across application components via mounted shares, and on-premises applications can access file data in a share via the File service REST API.

An Azure storage account is a secure account that gives you access to services in Azure Storage. Your storage account provides the unique namespace for your storage resources. The image below shows the relationships between the Azure storage resources in a storage account:

![Azure Storage Resources](./media/storage-introduction/storage-concepts.png)

[!INCLUDE [storage-account-types-include](../../includes/storage-account-types-include.md)]

[!INCLUDE [storage-versions-include](../../includes/storage-versions-include.md)]

## Blob storage
For users with large amounts of unstructured object data to store in the cloud, Blob storage offers a cost-effective and scalable solution. You can use Blob storage to store content such as:

* Documents
* Social data such as photos, videos, music, and blogs
* Backups of files, computers, databases, and devices
* Images and text for web applications
* Configuration data for cloud applications
* Big data, such as logs and other large datasets

Every blob is organized into a container. Containers also provide a useful way to assign security policies to groups of objects. A storage account can contain any number of containers, and a container can contain any number of blobs, up to the 500 TB capacity limit of the storage account.

Blob storage offers three types of blobs, block blobs, append blobs, and page blobs (disks).

* Block blobs are optimized for streaming and storing cloud objects, and are a good choice for storing documents, media files, backups etc.
* Append blobs are similar to block blobs, but are optimized for append operations. An append blob can be updated only by adding a new block to the end. Append blobs are a good choice for scenarios such as logging, where new data needs to be written only to the end of the blob.
* Page blobs are optimized for representing IaaS disks and supporting random writes, and may be up to 1 TB in size. An Azure virtual machine network attached IaaS disk is a VHD stored as a page blob.

For very large datasets where network constraints make uploading or downloading data to Blob storage over the wire unrealistic, you can ship a hard drive to Microsoft to import or export data directly from the data center. See [Use the Microsoft Azure Import/Export Service to Transfer Data to Blob Storage](storage-import-export-service.md).

## Table storage

[!INCLUDE [storage-table-cosmos-db-tip-include](../../includes/storage-table-cosmos-db-tip-include.md)]

Modern applications often demand data stores with greater scalability and flexibility than previous generations of software required. Table storage offers highly available, massively scalable storage, so that your application can automatically scale to meet user demand. Table storage is Microsoft's NoSQL key/attribute store – it has a schemaless design, making it different from traditional relational databases. With a schemaless data store, it's easy to adapt your data as the needs of your application evolve. Table storage is easy to use, so developers can create applications quickly. Access to data is fast and cost-effective for all kinds of applications.  Table storage is typically significantly lower in cost than traditional SQL for similar volumes of data.

Table storage is a key-attribute store, meaning that every value in a table is stored with a typed property name. The property name can be used for filtering and specifying selection criteria. A collection of properties and their values comprise an entity. Since Table storage is schemaless, two entities in the same table can contain different collections of properties, and those properties can be of different types.

You can use Table storage to store flexible datasets, such as user data for web applications, address books, device information, and any other type of metadata that your service requires.  You can store any number of entities in a table, and a storage account may contain any number of tables, up to the capacity limit of the storage account.

Like Blobs and Queues, developers can manage and access Table storage using standard REST protocols, however Table storage also supports a subset of the OData protocol, simplifying advanced querying capabilities and enabling both JSON and AtomPub (XML based) formats.

For today's Internet-based applications, NoSQL databases like Table storage offer a popular alternative to traditional relational databases.

## Queue storage
In designing applications for scale, application components are often decoupled, so that they can scale independently. Queue storage provides a reliable messaging solution for asynchronous communication between application components, whether they are running in the cloud, on the desktop, on an on-premises server, or on a mobile device. Queue storage also supports managing asynchronous tasks and building process workflows.

A storage account can contain any number of queues. A queue can contain any number of messages, up to the capacity limit of the storage account. Individual messages may be up to 64 KB in size.

## File storage
The Azure Files service enables you to set up highly available network file shares that can be accessed by using the standard Server Message Block (SMB) protocol. That means that multiple VMs can share the same files with both read and write access. You can also read the files using the REST interface or the storage client libraries.

One thing that distinguishes Azure File storage from files on a corporate file share is that you can access the files from anywhere in the world using a URL that points to the file and includes a shared access signature (SAS) token. You can generate SAS tokens; they allow specific access to a private asset for a specific amount of time.

File shares can be used for many common scenarios:

* Many on-premises applications use file shares. This feature makes it easier to migrate those applications that share data to Azure. If you mount the file share to the same drive letter that the on-premises application uses, the part of your application that accesses the file share should work with minimal, if any, changes.

* Configuration files can be stored on a file share and accessed from multiple VMs. Tools and utilities used by multiple developers in a group can be stored on a file share, ensuring that everybody can find them, and that they use the same version.

* Diagnostic logs, metrics, and crash dumps are just three examples of data that can be written to a file share and processed or analyzed later.

At this time, Active Directory-based authentication and access control lists (ACLs) are not supported, but they will be at some time in the future. The storage account credentials are used to provide authentication for access to the file share. This means anybody with the share mounted will have full read/write access to the share.

## Access to Blob, Table, Queue, and File resources
By default, only the storage account owner can access resources in the storage account. For the security of your data, every request made against resources in your account must be authenticated. Authentication relies on a Shared Key model. Blobs can also be configured to support anonymous authentication.

Your storage account is assigned two private access keys on creation that are used for authentication. Having two keys ensures that your application remains available when you regularly regenerate the keys as a common security key management practice.

If you do need to allow users controlled access to your storage resources, then you can create a shared access signature. A shared access signature (SAS) is a token that can be appended to a URL that enables delegated access to a storage resource. Anyone who possesses the token can access the resource it points to with the permissions it specifies, for the period of time that it is valid. Beginning with version 2015-04-05, Azure Storage supports two kinds of shared access signatures: service SAS and account SAS.

The service SAS delegates access to a resource in just one of the storage services: the Blob, Queue, Table, or File service.

An account SAS delegates access to resources in one or more of the storage services. You can delegate access to service-level operations that are not available with a service SAS. You can also delegate access to read, write, and delete operations on blob containers, tables, queues, and file shares that are not permitted with a service SAS.

Finally, you can specify that a container and its blobs, or a specific blob, are available for public access. When you indicate that a container or blob is public, anyone can read it anonymously; no authentication is required.  Public containers and blobs are useful for exposing resources such as media and documents that are hosted on websites.  To decrease network latency for a global audience, you can cache blob data used by websites with the Azure CDN.

See [Using Shared Access Signatures (SAS)](storage-dotnet-shared-access-signature-part-1.md) for more information on shared access signatures. See [Manage anonymous read access to containers and blobs](storage-manage-access-to-resources.md) and [Authentication for the Azure Storage Services](https://msdn.microsoft.com/library/azure/dd179428.aspx) for more information on secure access to your storage account.

## Replication for durability and high availability
The data in your Microsoft Azure storage account is always replicated to ensure durability and high availability. Replication copies your data, either within the same data center, or to a second data center, depending on which replication option you choose. Replication protects your data and preserves your application up-time in the event of transient hardware failures. If your data is replicated to a second data center, that also protects your data against a catastrophic failure in the primary location.

Replication ensures that your storage account meets the [Service-Level Agreement (SLA) for Storage](https://azure.microsoft.com/support/legal/sla/storage/) even in the face of failures. See the SLA for information about Azure Storage guarantees for durability and availability.

When you create a storage account, you can select one of the following replication options:

* **Locally redundant storage (LRS).** Locally redundant storage maintains three copies of your data. LRS is replicated three times within a single data center in a single region. LRS protects your data from normal hardware failures, but not from the failure of a single data center.

    LRS is offered at a discount. For maximum durability, we recommend that you use geo-redundant storage, described below.
* **Zone-redundant storage (ZRS).** Zone-redundant storage maintains three copies of your data. ZRS is replicated three times across two to three facilities, either within a single region or across two regions, providing higher durability than LRS. ZRS ensures that your data is durable within a single region.

    ZRS provides a higher level of durability than LRS; however, for maximum durability, we recommend that you use geo-redundant storage, described below.

  > [!NOTE]
  > ZRS is currently available only for block blobs, and is only supported for versions 2014-02-14 and later.
  >
  > Once you have created your storage account and selected ZRS, you cannot convert it to use to any other type of replication, or vice versa.
  >
  >
* **Geo-redundant storage (GRS)**. GRS maintains six copies of your data. With GRS, your data is replicated three times within the primary region, and is also replicated three times in a secondary region hundreds of miles away from the primary region, providing the highest level of durability. In the event of a failure at the primary region, Azure Storage will failover to the secondary region. GRS ensures that your data is durable in two separate regions.

    For information about primary and secondary pairings by region, see [Azure Regions](https://azure.microsoft.com/regions/).
* **Read-access geo-redundant storage (RA-GRS)**. Read-access geo-redundant storage replicates your data to a secondary geographic location, and also provides read access to your data in the secondary location. Read-access geo-redundant storage allows you to access your data from either the primary or the secondary location, in the event that one location becomes unavailable. Read-access geo-redundant storage is the default option for your storage account by default when you create it.

  > [!IMPORTANT]
  > You can change how your data is replicated after your storage account has been created, unless you specified ZRS when you created the account. However, note that you may incur an additional one-time data transfer cost if you switch from LRS to GRS or RA-GRS.
  >
  >

See [Azure Storage replication](storage-redundancy.md) for additional details about storage replication options.

For pricing information for storage account replication, see [Azure Storage Pricing](https://azure.microsoft.com/pricing/details/storage/). See [Azure Regions](https://azure.microsoft.com/regions/#services) for more information about what services are available in each region.

For architectural details about durability with Azure Storage, see [SOSP Paper - Azure Storage: A Highly Available Cloud Storage Service with Strong Consistency](http://blogs.msdn.com/b/windowsazurestorage/archive/2011/11/20/windows-azure-storage-a-highly-available-cloud-storage-service-with-strong-consistency.aspx).

## Transferring data to and from Azure Storage
You can use the AzCopy command-line utility to copy blob, file, and table data within your storage account or across storage accounts. See [Transfer data with the AzCopy Command-Line Utility](storage-use-azcopy.md) for more information.

AzCopy is built on top of the [Azure Data Movement Library](https://www.nuget.org/packages/Microsoft.Azure.Storage.DataMovement/), which is currently available in preview.

The Azure Import/Export service provides a way to import blob data into or export blob data from your storage account via a hard drive disk mailed to the Azure data center. For more information about the Import/Export service, see [Use the Microsoft Azure Import/Export Service to Transfer Data to Blob Storage](storage-import-export-service.md).

## Pricing
[!INCLUDE [storage-account-billing-include](../../includes/storage-account-billing-include.md)]

## Storage APIs, libraries, and tools
Azure Storage resources can be accessed by any language that can make HTTP/HTTPS requests. Additionally, Azure Storage offers programming libraries for several popular languages. These libraries simplify many aspects of working with Azure Storage by handling details such as synchronous and asynchronous invocation, batching of operations, exception management, automatic retries, operational behavior and so forth. Libraries are currently available for the following languages and platforms, with others in the pipeline:

### Azure Storage data services
* [Storage Services REST API](http://msdn.microsoft.com/library/azure/dd179355.aspx)
* [Storage Client Library for .NET, Windows Phone, and Windows Runtime](https://www.nuget.org/packages/WindowsAzure.Storage/)
* [Storage Client Library for C++](https://github.com/Azure/azure-storage-cpp)
* [Storage Client Library for Java/Android](https://azure.microsoft.com/develop/java/)
* [Storage Client Library for Node.js](http://dl.windowsazure.com/nodestoragedocs/index.html)
* [Storage Client Library for PHP](https://azure.microsoft.com/develop/php/)
* [Storage Client Library for Ruby](https://azure.microsoft.com/develop/ruby/)
* [Storage Client Library for Python](https://azure.microsoft.com/develop/python/)
* [Storage Cmdlets for PowerShell 1.0](/powershell/module/azurerm.storage/#storage)

### Azure Storage management services
* [Storage Resource Provider REST API Reference](/rest/api/storagerp/)
* [Storage Resource Provider Client Library for .NET](/dotnet/api/microsoft.azure.management.storage)
* [Storage Resource Provider Cmdlets for PowerShell 1.0](/powershell/module/azure.storage)
* [Storage Service Management REST API (Classic)](https://msdn.microsoft.com/library/azure/ee460790.aspx)

### Azure Storage data movement services
* [Storage Import/Export Service REST API](storage-import-export-service.md)
* [Storage Data Movement Client Library for .NET](https://www.nuget.org/packages/Microsoft.Azure.Storage.DataMovement/)

### Tools and utilities
* [Microsoft Azure Storage Explorer](../vs-azure-tools-storage-manage-with-storage-explorer.md) is a free, standalone app from Microsoft that enables you to work visually with Azure Storage data on Windows, macOS, and Linux.
* [Azure Storage Client Tools](storage-explorers.md)
* [Azure SDKs and Tools](https://azure.microsoft.com/tools/)
* [Azure Storage Emulator](http://www.microsoft.com/download/details.aspx?id=43709)
* [Azure PowerShell](/powershell/azure/overview)
* [AzCopy Command-Line Utility](http://aka.ms/downloadazcopy)

## Next steps
To learn more about Azure Storage, explore these resources:

### Documentation
* [Azure Storage Documentation](https://azure.microsoft.com/documentation/services/storage/)
* [Create a storage account](storage-create-storage-account.md)

<!-- after our quick starts are available, replace this link with a link to one of those. 
Had to remove this article, it refers to the VS quickstarts, and they've stopped publishing them. Robin --> 
<!--* [Get started with Azure Storage in five minutes](storage-getting-started-guide.md)
-->

### For administrators
* [Using Azure PowerShell with Azure Storage](storage-powershell-guide-full.md)
* [Using Azure CLI with Azure Storage](storage-azure-cli.md)

### For .NET developers
* [Get started with Azure Blob storage using .NET](storage-dotnet-how-to-use-blobs.md)
* [Get started with Azure Table storage using .NET](storage-dotnet-how-to-use-tables.md)
* [Get started with Azure Queue storage using .NET](storage-dotnet-how-to-use-queues.md)
* [Get started with Azure File storage on Windows](storage-dotnet-how-to-use-files.md)

### For Java/Android developers
* [How to use Blob storage from Java](storage-java-how-to-use-blob-storage.md)
* [How to use Table storage from Java](storage-java-how-to-use-table-storage.md)
* [How to use Queue storage from Java](storage-java-how-to-use-queue-storage.md)
* [How to use File storage from Java](storage-java-how-to-use-file-storage.md)

### For Node.js developers
* [How to use Blob storage from Node.js](storage-nodejs-how-to-use-blob-storage.md)
* [How to use Table storage from Node.js](storage-nodejs-how-to-use-table-storage.md)
* [How to use Queue storage from Node.js](storage-nodejs-how-to-use-queues.md)

### For PHP developers
* [How to use Blob storage from PHP](storage-php-how-to-use-blobs.md)
* [How to use Table storage from PHP](storage-php-how-to-use-table-storage.md)
* [How to use Queue storage from PHP](storage-php-how-to-use-queues.md)

### For Ruby developers
* [How to use Blob storage from Ruby](storage-ruby-how-to-use-blob-storage.md)
* [How to use Table storage from Ruby](storage-ruby-how-to-use-table-storage.md)
* [How to use Queue storage from Ruby](storage-ruby-how-to-use-queue-storage.md)

### For Python developers
* [How to use Blob storage from Python](storage-python-how-to-use-blob-storage.md)
* [How to use Table storage from Python](storage-python-how-to-use-table-storage.md)
* [How to use Queue storage from Python](storage-python-how-to-use-queue-storage.md)
* [How to use File storage from Python](storage-python-how-to-use-file-storage.md)
