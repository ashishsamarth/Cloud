AWS - VPC
-----------------------------------------------------------------------------------------------------------------------------------------------------------
VPC is private network to deploy your resources. Its a regional resource and a logical construct.
VPC can have multiple subnets. A Subnet allows you to partition your network inside your VPC (an Availability Zone resource)
When an AWS account is created for you, it will only have 'Public Subnets' it will not have any 'Private Subnets'. Also, you will have one Default VPC per 
region that is available to you, so essentially 'AZs' with in the region will have the same VPC.



                            INTERNET
                              ^
                              |
                              |
        ----------------------|-----------------------------------
        | VPC          INTERNET GATEWAY------^                   |
        |   __________________|______________|_______________    |
        |   |                 |              |               |   |
        |   |   **************|**************|***********    |   |
        |   |   |      NETWORK| ACL          |          |    |   |
        |   |   |   ~~~~~~~~~~V~~~~~~~~~~~~~~|~~~~~~    |    |   |
        |   |   |   |   EC2 Instance        NAT     |   |    |   |
        |   |   |   ~~~~~~~~~~~~~~~~~~~~~~~~~^~~~~~~~   |    |   |
        |   |   |    Public Subnet           |          |    |   |
        |   |   *****************************|***********    |   |
        |   |                                |               |   |
        |   |                                |               |   |
        |   |   *****************************|*******        |   |
        |   |   |   ~~~~~~~~~~~~~~~~~~~~     |      |        |   |
        |   |   |   |   EC2 Instance <-|------      |        |   |
        |   |   |   ~~~~~~~~~~~~~~~~~~~~            |        |   |
        |   |   |     Private Subnet                |        |   |
        |   |   *************************************        |   |
        |   |     AVAILABILITY ZONE A                        |   |
        |   |________________________________________________|   |
        |                                                        |
        |                                                        |
        ----------------------------------------------------------

-----------------------------------------------------------------------------------------------------------------------------------------------------------
Q01: What are the teo types of subnets?
-----------------------------------------------------------------------------------------------------------------------------------------------------------
    Following are the types of subnets
        a.  Public Subnet:  This is a subnet which is accesible from the internet
        b.  Private Subnet: This is a subnet which is NOT accessible from the internet

-----------------------------------------------------------------------------------------------------------------------------------------------------------
Q02: Which component is used to define access to the internet and between the subnets?
-----------------------------------------------------------------------------------------------------------------------------------------------------------
To define access to the internet and between the subnets, we use Route Tables

-----------------------------------------------------------------------------------------------------------------------------------------------------------
Q03: How does a resource deployed under the public subnet accesses the internet?
-----------------------------------------------------------------------------------------------------------------------------------------------------------
Since the 'Public Subnet' is connected to the internet via an 'Internet Gateway', the resource deployed in this subnet is able to access the Internet

-----------------------------------------------------------------------------------------------------------------------------------------------------------
Q04: How does a resource deployed under the private subnet accesses the internet?
-----------------------------------------------------------------------------------------------------------------------------------------------------------
The 'Private Subnet' does not connect to the internet or the internet gateway directly thats why its called Private due to the isoliation for security features. However resource deployed in this subnet may need occasional public internet access for software upgrades or security patches.

To handle this isolation, we deploy a 'NAT' in the public subnet, and this NAT will be able to access the internet via the 'Internet Gateway'.Once the NAT is able to connect to the Internet Gateway, we can connect this NAT (placed in public subnet) to the resources placed in the 'Private Subnet' and then these resources can access the internet, even being inthe private subnet.

Special Note: NAT Gateways are AWS-Managed, while NAT instances are SELF-Managed

-----------------------------------------------------------------------------------------------------------------------------------------------------------
Q05: Explain Network ACL & Security groups
    NACL: 
        a.  Its a firewall which controls traffic from and to the subnet
        b.  Can have ALLOW and DENY rules
        c.  Are attached at the Subnet level
        d.  Rules only include IP Address
    
        SECURITY GROUPS:
        a.  A firewall that controls traffic to and from an ENI / an EC2 instance
        b.  Can have only ALLOW rules
        c.  Rules include IP Address and other security groups

        Comparision Between NACL and Security Groups

                    NACL                                                            Security Groups
        ----------------------------------------------------------------------------------------------------------------------
        a.  Operates ath the subnet level                               Operates at the instance level
        ----------------------------------------------------------------------------------------------------------------------
        b.  Supports Allow & Deny rules                                 Supports Allow rules only
        ----------------------------------------------------------------------------------------------------------------------
        c.  Is Stateless: Return traffic must be explicity              Is Stateful: Return traffic is automatically allowed,
            allowed by rules                                            regardless of any rules
        ----------------------------------------------------------------------------------------------------------------------    
        d.  It processes rules in number order when deciding            It evaluate all rules before deciding whether
            whether to allow traffic                                    to allow traffic
        ----------------------------------------------------------------------------------------------------------------------    
        e.  Automatically applies to all instances in the               Applies to instance only if someone specifies the 
            Subnets its associated with (Therefore you dont             security group when launchign the instance, or associates
            have to re-apply on users to specifiy security group)       the security group with the instance later on

-----------------------------------------------------------------------------------------------------------------------------------------------------------
Q06: What are flow logs?
-----------------------------------------------------------------------------------------------------------------------------------------------------------
    Flow logs capture information about IP traffic going into your interfaces
        a.  VPC Flow logs
        b.  Subnet Flow logs
        c.  Elastic Network  Interface flow logs

        It helps to monitor and troubleshoot connectivity issues, for e.g.
            1.  Subnets to Internet
            2.  Subnets to Subnets
            3.  Internet to Subnets
        
        Captures Network Information from AWS managed interfaces to: ELB, ElastiCache, RDS, Aurora etc

        Special Note: VPC Flow logs data can go to S3 / CloudWatch logs

-----------------------------------------------------------------------------------------------------------------------------------------------------------
Q07: What is VPC Peering?
-----------------------------------------------------------------------------------------------------------------------------------------------------------
A virtual private cloud (VPC) is a logically isolated, virtual network within a cloud provider. A VPC peering connection is a networking connection between two VPCs that enables you to route traffic between them using private IP addresses. VPC peering allows you to deploy cloud resources in a virtual network that you have defined. Instances in either VPC can communicate with each other as if they were within the same network. Data can be transferred across these resources with more security.

    Benefits of VPC Peering:
        
    a.  Improve security:	VPC peering comes with the major benefit of improving security by enabling private connectivity between 
        two or more VPC networks, isolating traffic from public Internet. Because your traffic never leaves the cloud provider’s network, 
        you reduce a whole class of risks for your stack.

    b.  Save money on network costs:	With VPC peering, you save on network transit costs and benefit from improved network latency. Because 
        peering traffic does not leave your cloud provider’s network, that reduces public IP latency. And since peered networks use internal IPs to 
        communicate, transferring data over the cloud provider’s network is cheaper than over the public Internet.

    c.  Get more flexibility for services that don’t need to connect to the Internet:	Another reason to use VPC peering is when your instances 
        do not require a public IP address or a network address translation (NAT) configuration to the public Internet. This can be desirable for 
        backend services, where a user wants to block all egress traffic to the public Internet from their instances

    Special Note:
    a.  For each VPCs which is connecting to one another must not have overlapping CIDR (IP Ranges)
    b.  VPC Peering connection is not transitive (must be established for each VPC that need to communicate with one other). 
    Meaning, if their are three VPCs A,B and C, and you have VPC peering only between A<-->B and A<-->C, then 'B' and 'C' cannot talk to each other 

-----------------------------------------------------------------------------------------------------------------------------------------------------------    
Q08: What are VPC Endpoints?
-----------------------------------------------------------------------------------------------------------------------------------------------------------
A VPC endpoint enables customers to privately connect to supported AWS services and VPC endpoint services powered by AWS PrivateLink.Amazon VPC instances do not require public IP addresses to communicate with resources of the service. Traffic between an Amazon VPC and a service does not leave the Amazon network.

VPC endpoints are virtual devices. They are horizontally scaled, redundant, and highly available Amazon VPC components that allow communication between instances in an Amazon VPC and services without imposing availability risks or bandwidth constraints on network traffic. There are two types of VPC endpoints
    
    a.  Interface Endpoints
    b.  Gateway Endpoints

Interface Endpoints:
Interface endpoints enable connectivity to services over AWS PrivateLink. These services include some AWS managed services, services hosted by other AWS customers and partners in their own Amazon VPCs (referred to as endpoint services), and supported AWS Marketplace partner services. The owner of a service is a service provider. The principal creating the interface endpoint and using that service is a serviceconsumer.An interface endpoint is a collection of one or more elastic network interfaces with a private IP address that serves as an entry point for traffic destined to a supported service.
        
Gateway Endpoints:
A gateway endpoint targets specific IP routes in an Amazon VPC route table, in the form of a prefix-list, used for traffic destined to Amazon DynamoDB or Amazon Simple Storage Service (Amazon S3). Gateway endpoints do not enable AWS PrivateLink.Instances in an Amazon VPC do not require public IP addresses to communicate with VPC endpoints, as interface endpoints use local IP addresses within the consumer Amazon VPC. Gateway endpoints are destinations that are reachable from within an Amazon VPC through prefix-lists within the Amazon VPC’s route table

-----------------------------------------------------------------------------------------------------------------------------------------------------------
Q09: Explain the difference between Site-to-Site VPN & Direct Connect?
-----------------------------------------------------------------------------------------------------------------------------------------------------------
    Following are the key details

        Site-to-Site VPN:
            a.  Connects an On-Premise Data Center VPN to AWS
            b.  The connection is automatically encrypted
            c.  Goes over the public internet
        
        Direct Connect (DX)
            a.  Establishes a Physical Connection between on-premise and AWS
            b.  The connection is private, secure and fast
            c.  Goes over a private network
            d.  Takes atleast a month to establish
        
        Special Note:
            Site-to-Site VPN and Direct Connect : CANNOT access VPC Endpoints at all. since VPC endpoints 
            are available only with in your regional VPC

-----------------------------------------------------------------------------------------------------------------------------------------------------------