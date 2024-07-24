Azure-Storage
-----------------------------------------------------------------------------------------------------------------------------------------------------------

-----------------------------------------------------------------------------------------------------------------------------------------------------------
**Azure Blob Storage**: Blob storage is the most common storage type in Azure. It can be used to store unstructured data such as videos, audio, metadata, log files, text, and binary. It is a highly scalable and very cost-effective storage solution. It  provides support for tiered storage, so the data can be stored at different tiers based on their access pattern and usage frequency. Highly used data can be kept at hot tiers, the not-so-used data in cold tiers, and historical data can be archived. The data in Blob storage can be easily accessed via REST endpoints, as well as client libraries available in a wide set of languages, such as .NET, Java, Python, Ruby, PHP, Node.js, and more.

You can access your blob storage at: https://**storage-account**.blob.core.windows.net

**Azure Data lake Gen 2**: Azure Data Lake Gen2 or Azure Data Lake Storage Gen 2 (ADLS Gen2) is a superset of Blob storage that is optimized for big data analytics. ADLS Gen2 is the preferred option for data lake solutions in Azure.
It provides hierarchical namespace support on top of Blob storage which basically means that the directories are supported.
Unlike Blob storage, which provides pseudo directory operations via namespaces, ADLS Gen2 provides real support for directories with POSIX compliance and Access Control List (ACL) support. This makes operations such as renaming and deleting directories atomic and quick.

For example: if you have 100 files under a directory in Blob storage, renaming that directory would require hundreds of metadata operations. But, in ADLS Gen2, just one metadata operation will need to be performed at the directory level. ADLS Gen2 also
supports role-based access controls (RBACs), just like Blob storage does.

Another important feature of ADL Gen2 is that it is a Hadoop-compatible filesystem. So, building any open source analytics pipeline on top of ADL Gen2 is a breeze.
Gen2 also supports Locally Redundant Storage (LRS), Zone Redundant Storage (ZRD), and Geo Redundant Storage (GRS) for data redundancy and recovery, while Gen1 only supports LRS.

You can access your blob storage at: https://**storage-account**.dfs.core.windows.net

To create an ADLS Gen2 account, you need to select the "Enable hierarchical namespace" checkbox on the Create a storage account screen:

**Azure Files**: Azure Files provides remote file shares that can be mounted using Server Message Block (SMB) or Network File Share (NFS) protocols. These are great storage options for anyone planning to migrate on-premises workloads to the cloud with a 
lift and shift model.
For instance, without having to invest in redevelopment for the cloud-based model. Azure files can easily be mounted both from cloud servers and on-premises servers. Azure Files is particularly useful for cases that need shared data, shared configurations, shared applications, and more across multiple users, teams, or regions.

*Creating Azure file shares with the Azure CLI:*

All the following examples assume that you have already created a storage account named IACStorageAcct
• You can create a new Azure file share for IAC using the share create option.The following command will create a file share named IACFileShare under the IACStorageAcct.

-----------------------------------------------------------------------------------------------------------------------------------------------------------
    az storage share-rm create --resource-group IACRG --storage-account IACStorageAcct --name IACFileShare

• You can list the file shares using the share list option

-----------------------------------------------------------------------------------------------------------------------------------------------------------
    az storage share list --account-name IACStorageAcct

• You can put a file into our file share using the file upload option:    

-----------------------------------------------------------------------------------------------------------------------------------------------------------
    az storage file upload --share-name IACFileShare --source ./testfile.txt

• You can view the files in your file share using file list:

-----------------------------------------------------------------------------------------------------------------------------------------------------------
    az storage file list --share-name IACFileShare

• You can download the file that we previously uploaded using the file download option:    

-----------------------------------------------------------------------------------------------------------------------------------------------------------
    az storage file download --share-name IACFileShare -p testfile.txt --dest ./testfile.txt
