Azure-Networking
-----------------------------------------------------------------------------------------------------------------------------------------------------------

-----------------------------------------------------------------------------------------------------------------------------------------------------------
**V-Net**
-----------------------------------------------------------------------------------------------------------------------------------------------------------
A VNet ties all resources, such as VMs, stores, and databases, together securely in a private network. It is used to encapsulate the cloud or on-premises services together within a secure boundary by controlling who can access these services and from which endpoints. Azure Networking provides the following four main services:
-----------------------------------------------------------------------------------------------------------------------------------------------------------
    • Secure connectivity within Azure resources using the basic VNet, VNet Peering, and Service Endpoints
    • Networking beyond the Azure Cloud and into the internet and hybrid clouds using Express Routers, Private Endpoints, and Point-to-Site and 
        Site-to-Site VPNs..
    • Network filtering or, in other words, Firewall Rules that can be implemented either via the Network or App Security Groups. There are options to    
        implement the same using network appliances, which are ready-made VMs available for specialized networking scenarios.
    • Network routing abilities that allow you to configure network routes using Route Tables and Border Gateway Protocols.
-----------------------------------------------------------------------------------------------------------------------------------------------------------    

*Creating Azure VNet using the Azure CLI:*

•First, we need to create a VNET by specifying the necessary IP ranges and subnet prefixes. The following command creates a VNET named IACvnet under the IACRG resource group

    az network vnet create --address-prefixes 10.20.0.0/16 --name IACvnet --resource-group IACRG --subnet-name IACsubnet --subnet-prefixes 10.20.0.0/24

• Then, we need to create a public IP so that we can access our VM from the internet:

    az network public-ip create --resource-group IACRG --name IACpubip --allocation-method dynamic

• Next, we must create a network interface card (NIC), which will be the network interface between the VM and the outside world, with the previously created VNet and public IP:

    az network nic create --resource-group IACRG --vnet-name IACvnet --subnet IACsubnet --name IACnic --public-ipaddress IACpubip

• We now have all the components required to create a VM within our new VNet, IACVnet. We can reuse the UbuntuLTS image that we used in the earlier virtual machine creation example to create a new VM within the new VNet:

    az vm create --resource-group IACRG --name sampleVM --nics IACnic --image UbuntuLTS --generate-ssh-keys

More information about Azure-Networking is here:

    https://azure.microsoft.com/en-in/products/category/networking/