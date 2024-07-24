Azure-Storage
-----------------------------------------------------------------------------------------------------------------------------------------------------------

-----------------------------------------------------------------------------------------------------------------------------------------------------------
**Azure Blob Storage**: 
-----------------------------------------------------------------------------------------------------------------------------------------------------------
Blob storage is the most common storage type in Azure. It can be used to store unstructured data such as videos, audio, metadata, log files, text, and binary. It is a highly scalable and very cost-effective storage solution. It  provides support for tiered storage, so the data can be stored at different tiers based on their access pattern and usage frequency. Highly used data can be kept at hot tiers, the not-so-used data in cold tiers, and historical data can be archived. The data in Blob storage can be easily accessed via REST endpoints, as well as client libraries available in a wide set of languages, such as .NET, Java, Python, Ruby, PHP, Node.js, and more.

You can access your blob storage at: https://**storage-account**.blob.core.windows.net

**Azure Data lake Gen 2**: 
-----------------------------------------------------------------------------------------------------------------------------------------------------------
Azure Data Lake Gen2 or Azure Data Lake Storage Gen 2 (ADLS Gen2) is a superset of Blob storage that is optimized for big data analytics. ADLS Gen2 is the preferred option for data lake solutions in Azure.
It provides hierarchical namespace support on top of Blob storage which basically means that the directories are supported.
Unlike Blob storage, which provides pseudo directory operations via namespaces, ADLS Gen2 provides real support for directories with POSIX compliance and Access Control List (ACL) support. This makes operations such as renaming and deleting directories atomic and quick.

For example: if you have 100 files under a directory in Blob storage, renaming that directory would require hundreds of metadata operations. But, in ADLS Gen2, just one metadata operation will need to be performed at the directory level. ADLS Gen2 also
supports role-based access controls (RBACs), just like Blob storage does.

Another important feature of ADL Gen2 is that it is a Hadoop-compatible filesystem. So, building any open source analytics pipeline on top of ADL Gen2 is a breeze.
Gen2 also supports Locally Redundant Storage (LRS), Zone Redundant Storage (ZRD), and Geo Redundant Storage (GRS) for data redundancy and recovery, while Gen1 only supports LRS.

You can access your Gen 2 storage at: https://**storage-account**.dfs.core.windows.net

To create an ADLS Gen2 account, you need to select the "Enable hierarchical namespace" checkbox on the Create a storage account screen:

**Azure Files**: 
-----------------------------------------------------------------------------------------------------------------------------------------------------------
Azure Files provides remote file shares that can be mounted using Server Message Block (SMB) or Network File Share (NFS) protocols. These are great storage options for anyone planning to migrate on-premises workloads to the cloud with a 
lift and shift model.
For instance, without having to invest in redevelopment for the cloud-based model. Azure files can easily be mounted both from cloud servers and on-premises servers. Azure Files is particularly useful for cases that need shared data, shared configurations, shared applications, and more across multiple users, teams, or regions.

*Creating Azure file shares with the Azure CLI:*

All the following examples assume that you have already created a storage account named IACStorageAcct
• You can create a new Azure file share for IAC using the share create option.The following command will create a file share named IACFileShare under the IACStorageAcct.

    az storage share-rm create --resource-group IACRG --storage-account IACStorageAcct --name IACFileShare

• You can list the file shares using the share list option

    az storage share list --account-name IACStorageAcct

• You can put a file into our file share using the file upload option:    

    az storage file upload --share-name IACFileShare --source ./testfile.txt

• You can view the files in your file share using file list:

    az storage file list --share-name IACFileShare

• You can download the file that we previously uploaded using the file download option:    

    az storage file download --share-name IACFileShare -p testfile.txt --dest ./testfile.txt

**Azure-Queues**:
-----------------------------------------------------------------------------------------------------------------------------------------------------------
Azure queues are used to store a large number of messages that can be accessed asynchronously between the source and the destination. This helps in decoupling applications so that they can scale independently. Azure queues can be used across applications that are running in the cloud, on-premises, on mobile devices, and more
There are two types of queues: Storage queues and Service Bus.

Storage queues can be used for simple asynchronous message processing. They can store up to 500 TB of data (per storage account) and each message can be up to 64 KB in size

Service Bus can be used for pub-sub models, strict ordering of messages and blocking & non-blocking APIs. The message size can be ip to 1BM, but the overall size is capped at 80GB

You can access your Azure Queues storage at: https://**storage-account**.queue.core.windows.net/**queue**.

*Creating Azure Queues using the CLI*

• You can create a new Azure queue using the storage queue create command. The following command will create a queue named IACqueue under the IACStorageAcct.

    az storage queue create --name IACqueue --account-name IACStorageAcct

• You can easily list the queues under a storage account using the storage queue list term:

    az storage queue list --account-name IACStorageAcct

• You can add a new message to the newly created queue using the storage message put option:

    az storage message put --queue-name IACqueue --content "test"

• Finally, use the storage message peek command to view the message. This command retrieves one or more messages from the front of the queue but does not alter the visibility of the message:

    az storage message peek --queue-name IACqueue


**Azure-Tables**:
-----------------------------------------------------------------------------------------------------------------------------------------------------------
Azure tables are key-value stores provided by Azure. They are good for storing structured non-relational data. There are two solutions available in Azure for Table stores: Azure Table Storage and Cosmos DB.
Both these features provide the same table model and Create, Read, Update, and Delete (CRUD) features, but the difference lies in their scale, SLAs, and availability. Cosmos DB is the premium version of Table store and can provide more than 10 million operations per second, whereas Azure Table storage has a scaling limit of 20K operations per second.
Cosmos DB also provides several additional advantages, such as five flexible levels of consistency, up to 99.999% read availability on multi-region databases, serverless mode, global presence, and more

You can access your Azure tables at: https://**storage-account**.table.core.windows.net/**table**.

*Creating Azure Tables using the CLI*

• We can create a new Azure Table for our example company, IAC, by using the storage table create option. The following command will create a table named IACtable under the IACStorageAcct.

    az storage table create --name IACtable --account-name IACStorageAcct

 • We can easily list the Tables under a storage account using the storage table list option:

    az storage table list --account-name IACStorageAcct

• We can insert an entity into the newly created Table using the storage entity insert option

    az storage entity insert --table-name IACtable --entity PartitionKey=testPartKey RowKey=testRowKey Content=testContent
    
• We can use the storage entity show command to view the entry:

    az storage entity show --table-name IACtable --partitionkey testPartKey --row-key testRowKey

**Azure Managed disks**:
-----------------------------------------------------------------------------------------------------------------------------------------------------------
Azure managed disks are the virtual hard disks that are mounted to an Azure VM. As the name suggests, these disks are completely managed by Azure. So, you don't need to worry about OS upgrades, security patches, and so on. 
Unlike physical disks, Azure Managed Disks offer 99.999% availability. They achieve such a high availability score by storing three different replicas of the data on different servers. Managed VMs can also be allocated to availability sets and availability zones (distributed across racks and data centers) to increase their survivability in cases of server, rack (stamp), or data center outages. The managed disks also provide options for data encryption at rest and disk-level encryptions. 
There are different types of managed disks available, such as standard HDD, standard SSD, premium SSD, and ultra disks.

*Creating and attaching Managed Disks to a VM using the CLI*

• This is a simple one-line command for creating a new disk and attaching it to an existing VM.

    az vm disk attach --resource-group IACRG --vm-name sampleVM --name IACmgdisk --size-gb 64 –new
