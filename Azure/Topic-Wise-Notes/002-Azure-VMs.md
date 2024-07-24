Azure-Virtual-Machines
-----------------------------------------------------------------------------------------------------------------------------------------------------------

-----------------------------------------------------------------------------------------------------------------------------------------------------------
Virtual machines (VMs) are software abstractions of the physical hardware. They can emulate the computer hardware for the applications running on it. We can have multiple VMs running on a single machine. Each VM will have a portion of the host machine's 
CPU, memory, and storage allocated to it.
Azure VMs are the most common resources that are spun up in Azure. You can use VMs to set up virtually any application that you want. They are like plain vanilla servers that can be used to install any software that you need, except the OS upgrades and security patches, which are taken care of by Azure.
Azure VMs provide the advantage of faster deployments, scalability, security isolation, and elasticity. Azure provides both Windows and Linux VMs. There is a huge collection of OS flavors and versions available in the Azure Marketplace that can be used to spin up the VMs.

Here's the link for VMs available in Azure: 

-----------------------------------------------------------------------------------------------------------------------------------------------------------
https://learn.microsoft.com/en-us/azure/virtual-machines/sizes/overview?tabs=breakdownseries%2Cgeneralsizelist%2Ccomputesizelist%2Cmemorysizelist%2Cstoragesizelist%2Cgpusizelist%2Cfpgasizelist%2Chpcsizelist

Following are the classifications:
-----------------------------------------------------------------------------------------------------------------------------------------------------------
    • General-purpose
    • Compute-optimized
    • Memory-optimized
    • Storage-optimized
    • GPU
    • High performance
-----------------------------------------------------------------------------------------------------------------------------------------------------------

*Their are multiple ways to create a VM*
• Via Azure Web Portal
• Via Azure CLI
• Via Azure Resource manager

Here's an example of creating a VM using the Azure CLI.

a.  First, we have to find all the Ubuntu images that are available using the vm image list option:

-----------------------------------------------------------------------------------------------------------------------------------------------------------
    az vm image list --all --offer Ubuntu --all
b. Next, we need to find the Azure regions where we want to deploy. We can use account list-locations for this. You can choose a region that is closest to you

-----------------------------------------------------------------------------------------------------------------------------------------------------------
    az account list-locations --output table

This can also be written as 

-----------------------------------------------------------------------------------------------------------------------------------------------------------
    az account list-locations -o table

c. Once we've done this, we can either create a new resource group or use an existing one to associate this VM with. Let us create a new resource group called IACRG using the group create option, as shown here:

-----------------------------------------------------------------------------------------------------------------------------------------------------------
    az group create --name 'IACRG' --location 'eastus'

This can also be written as 

-----------------------------------------------------------------------------------------------------------------------------------------------------------
    az group create -n 'IACRG' -l 'eastus'

d. Finally, lets create the VM using the information from preceeding commands

-----------------------------------------------------------------------------------------------------------------------------------------------------------
    az vm create --resource-group 'IACRG' --name 'sampleVM' --image 'UbuntuLTS' --admin-username '<your username>' --admin-password '<your password>' --location 'eastus'

This can also be written as

-----------------------------------------------------------------------------------------------------------------------------------------------------------
    az vm create --resource-group 'IACRG' --n 'sampleVM' -image 'UbuntuLTS' --admin-username '<your username>' --admin-password '<your password>' -l 'eastus'