AWS-EC2: Elastic Compute Cloud
-----------------------------------------------------------------------------------------------------------------------------------------------------------

EC2 is the most popular offering of AWS's offerings.Knowing EC2 is the fundamental to understand how the cloud works
EC2 = Elastic Compute Cloud is an IaaS (Infrastructure as a Service)

-----------------------------------------------------------------------------------------------------------------------------------------------------------
    It has the following capabilities
        a.  Renting Virtual Machines (EC2 - Elastic Compute Cloud)
        b.  Storing Data on Virtual Drives (EBS - Elastic Block Storage)
        c.  Distributing Load Across Machines (ELB - Elastic Load Balancer)
        d.  Scaling the services using an auto-scaling group (ASG - Auto Scaling Group)

-----------------------------------------------------------------------------------------------------------------------------------------------------------

EC2 Sizing & Configuration options
-----------------------------------------------------------------------------------------------------------------------------------------------------------
    a.  Operating Systems Supported: Linux, Windows or MAC OS
    b.  How much compute power and cores: (CPU)
    c.  How much random access memory (RAM)
    d.  How much storage space
        1.  Network Attached (EBS [Elastic Block Storage] & EFS [Elastic File System])
        2.  Hardware (EC2 Instance Store)
    e.  Network Card: Speed of the card, Public IP Address
    f.  Firewall Rules: Security Group
    g.  Bootstrap Script (Configure at first launch): EC2 User Data

-----------------------------------------------------------------------------------------------------------------------------------------------------------

EC2 User Data
-----------------------------------------------------------------------------------------------------------------------------------------------------------
    a.  it is possible to bootstrap our instances using an EC2 User Data Script
    b.  Bootstrapping means launching commands when the machine starts
    c.  These scripts are executed only the first time the instance boots.
    d.  EC2 User Data is used to automate boot tasks such as:
        a.  Installing Updates
        b.  Installing Software
        c.  Downloading common files from internet
        d.  Any specific scripts that you may want to execute only when machine boots.
    Special Note: Anything that you run as EC2 User data will be executed as a 'root' user.

-----------------------------------------------------------------------------------------------------------------------------------------------------------

Q01: What are the different types of EC2 Instance Types?
-----------------------------------------------------------------------------------------------------------------------------------------------------------
    There are 7 different types of EC2 Instance types, namely:
        a.  General Purpose (GP)
        b.  Compute Optimized
        c.  Memory Optimized
        d.  Linux Accelerated Computing
        e.  Storage Optimized
        f.  Micro Instance

    Special Note: Site to compare all instances : https://www.ec2instances.info
    Complete List : https://www.amazonaws.cn/en/ec2/instance-types/
    
 -----------------------------------------------------------------------------------------------------------------------------------------------------------

Q02: How to read the naming convention of an EC2 instance?
-----------------------------------------------------------------------------------------------------------------------------------------------------------
    For example, the EC2 instance you are working with is m5.2xlarge, here's how to read it
        a.  m:          Instance Class
        b.  5:          Generation (AWS improves the generation over time)
        c.  2xlarge:    Size with in the instance class (more memory , more CPU)

-----------------------------------------------------------------------------------------------------------------------------------------------------------
    
Q03: Explain the characteristics of EC2 Instance type: General Purpose
-----------------------------------------------------------------------------------------------------------------------------------------------------------    
    General Purpose instance types are great for
        a.  Diversity of workloads, such as web servers or code repositories
        b.  These provide a balance between, Compute, Memory and Networking

-----------------------------------------------------------------------------------------------------------------------------------------------------------
    
Q04: Explain the characteristics of EC2 Instance type: Compute Optimized
-----------------------------------------------------------------------------------------------------------------------------------------------------------
    Compute Optimized instance types are great for
        a.  Batch processing workloads
        b.  Media Transcoding
        c.  High Performance Web servers
        d.  High Performance computing (HPC)
        e.  Scientific modeling and Machine Learning
        f.  Dedicated gaming servers.
    Special Note: The compute optimized instances starts with the alphabet 'C'
    e.g.    : C6g, C6gn, C5, C5a, C5n, C4

-----------------------------------------------------------------------------------------------------------------------------------------------------------

Q05: Explain the characteristics of EC2 Instance type: Memory Optimized
-----------------------------------------------------------------------------------------------------------------------------------------------------------
    Memory Optimized instance types are great for
        a.  High performance, relational or non-relational database
        b.  Distributed web scale cache stores
        c.  In-memory databases optimized for BI (business intelligence)
        d.  Applications performing real-time processing of big unstructured data
    Special Note: The memory optimized instances starts with 'R', 'X', 'z' and 'High Memory'. Here 'R' represents 'Ram'

-----------------------------------------------------------------------------------------------------------------------------------------------------------

Q06: Explain the characteristics of EC2 Instance type: Storage Optimized
-----------------------------------------------------------------------------------------------------------------------------------------------------------
Storage Optimized instances are great for 'storage intensive' tasks that require high, sequential read and write access to large data sets on local storage

-----------------------------------------------------------------------------------------------------------------------------------------------------------
    a.  High frequency online transaction processing (OLTP) Systems
    b.  Relational & No-SQL databases
    c.  Cache for in-memory databases (for example, Redis)
    d.  Data Warehousing applications
    e.  Distributed file Systems

-----------------------------------------------------------------------------------------------------------------------------------------------------------

Q07: What is an AWS security group?
-----------------------------------------------------------------------------------------------------------------------------------------------------------
Security groups are fundamental of network security in AWS. They control how traffic is allowed into OR out of EC2 Instances.

-----------------------------------------------------------------------------------------------------------------------------------------------------------
    a.  Security Groups only contain allow rules
    b.  Security Group rules can reference by IP Address or by security group
    c.  Security groups are acting as a 'Firewall' on EC2 instances. They regulate the following:
        1.  Access to ports
        2.  Authorized IP Ranges - IPv4 and IPv6
        3.  Control of inbound network (from other/outside to the instance)
        4.  Control of outbound network (from the instance to other/outside)

-----------------------------------------------------------------------------------------------------------------------------------------------------------

Characteristics of a Security Group
-----------------------------------------------------------------------------------------------------------------------------------------------------------
    a.  A single security group can be attached to multiple instances. Also, one instance can have many 
        security groups attached to it.
    b.  A security group is locked to a region-and-VPC combination. A security group created in VPN01ABC 
        in US-EAST-2 will not be available in a different Region-VPC combination
    c.  A security group resides 'outside' the EC2 instance, if the traffic is blocked, the EC2 instance 
        will not even see it.
    d.  It's good to maintain one separate security group for SSH Access
    e.  All inbound traffic is 'BLOCKED' by default
    f.  All outbound traffic is 'AUTHORIZED' by default

    Special Note:
        a.  If your application is not accessible (TIME OUT), then its a 'security group' issue
        b.  If your application gives a 'connection refused' error, then its an application error or its not launched.

-----------------------------------------------------------------------------------------------------------------------------------------------------------

Q08: What is security group referencing in AWS?
-----------------------------------------------------------------------------------------------------------------------------------------------------------
    Assume the following scenario:
        a.  You have an EC2 instance with Security Group A attached to it
        b.  This security group A basically authorizes inbound traffic which are part of 
            security group B and C
        c.  Now if you have another EC2 instance which has security group B attached to it, 
            then this will enable the 2nd EC2 instance to be able to connect to the first EC2 
            instance on the specific port (allowed by the inbound rule in security group A)
        d.  Now if you have a third EC2 instance which has security group C attached to it, 
            then this will enable the 3rd EC2 instance to be able to connect to the first EC2 
            instance on the specific port (allowed by the inbound rule in security group A)
        e.  This internal communication between EC2 instances is simply possible because the 
            Security Group A authorized the inbound traffic from security group B and C

-----------------------------------------------------------------------------------------------------------------------------------------------------------
    
Q09: What are the classic ports to know?
-----------------------------------------------------------------------------------------------------------------------------------------------------------
    Following are the classic port numbers
        a.  22 = SSH (secure shell): Login to the Linux instance
        b.  21 = FTP (File transfer protocol): Upload files into a file share
        c.  22 = SFTP (Secure file transfer protocol): Upload files using SSH
        d.  80 = HTTP - Access unsecured websites
        e.  443 = HTTPS - Access secured websites
        f.  3389 = RDP (Remote Desktop Protocol) - Login to windows instance.

-----------------------------------------------------------------------------------------------------------------------------------------------------------

Q10: How to change the file permissions for .ppk file in windows?
-----------------------------------------------------------------------------------------------------------------------------------------------------------
    While the chmod command works in Linux or Mac, windows does not have any such command available. 
    Here's how you change the permissions
        a.  Right click on the file and go to properties and then security.
        b.  Under security click on 'Advanced'
        c.  Click on 'Disable Inheritence' and then click on 'Convert inherited permissions 
            to explicit permissions on this object'
        d.  Then under 'Principal' click on 'System' and remove this user. Do the same for 
            'Administator' user.
        e.  Once the other users are removed, only the actual user will have access to the .ppk file.
        f.  This process is similar to chmod 400 filename in Mac or Linux.

-----------------------------------------------------------------------------------------------------------------------------------------------------------
    
Q11: What is EC2 Instance connect?
-----------------------------------------------------------------------------------------------------------------------------------------------------------
Once the EC2 instance is created, 'Instance Connect' feature allows you to connect to this instance like a putty session on a web-broswer. For an IAM user to be able to use 'Instance Connect' feature, the IAM user must have 'EC2InstanceConnect' policy attached to the user either as an 'Inline Policy' or via a group, which the IAM user is a part of.
    
-----------------------------------------------------------------------------------------------------------------------------------------------------------

Q12: Do you need to upload your .ppk file to connect to your EC2 instance when using 'Instance Connect'?
-----------------------------------------------------------------------------------------------------------------------------------------------------------
No, we do not need to upload our .ppk file to connect to our EC2 instance using 'Instance Connect' AWS, creates a temporary .ppk file to connect to your EC2 instance, when the connection is initiated via 'Instance Connect'
    
-----------------------------------------------------------------------------------------------------------------------------------------------------------

Q13: What will happen, if you remove the 'inbound rule' for port 22 and try to connect to your EC2 instance, via 'Instance Connect'?
-----------------------------------------------------------------------------------------------------------------------------------------------------------
We will not be able to connect to our EC2 instance, via any method utilized SSH (Instance Connect, Putty, Command Promprt, Powershell). Since the port 22 is removed / not added to the inbound rules in the security group.

-----------------------------------------------------------------------------------------------------------------------------------------------------------

Q14: Does the EC2 instance have 'AWS-CLI' pre-installed?
-----------------------------------------------------------------------------------------------------------------------------------------------------------
Yes, the EC2 instance have AWS-CLI preinstalled, & this can be validated by connecting to the instance via Instance Connect & execute the following 

-----------------------------------------------------------------------------------------------------------------------------------------------------------
    aws --version

    [ec2-user@ip-100-1-1-0 /]$ aws --version
    aws-cli/1.18.147 Python/2.7.18 Linux/5.10.162-141.675.amzn2.x86_64 botocore/1.18.6
    [ec2-user@ip-100-1-1-0 /]$ 

-----------------------------------------------------------------------------------------------------------------------------------------------------------
    
Q15: Can you run, AWS-CLI commands on EC2, when connected via Instance Connect?
-----------------------------------------------------------------------------------------------------------------------------------------------------------
    Yes, we can run AWS-CLI commands on EC2 instance, even when connected via Instance Connect.

    [ec2-user@ip-100-1-1-0 /]$ aws iam list-users
    Unable to locate credentials. You can configure credentials by running "aws configure".
    [ec2-user@ip-100-1-1-0 /]$

-----------------------------------------------------------------------------------------------------------------------------------------------------------

Q16: Should you perform 'aws configure' on EC2 instance?
-----------------------------------------------------------------------------------------------------------------------------------------------------------
In order to run AWS-CLI commands directly on the EC2 instance, rather than performing 'aws configure' on the instance, one should use, IAM roles. The reason to NOT configure your 'access-key' and 'secret-key' on the EC2 instance is, anybody who is connected to the EC2 instance can read the values of your 'access-key' and 'secret-key' there by compromising your security and profile.

-----------------------------------------------------------------------------------------------------------------------------------------------------------

Q17: If 'aws configure' on an EC2 instance is a NO-NO, how do you handle this situation?
-----------------------------------------------------------------------------------------------------------------------------------------------------------
    The recommended solution for this is, to use IAM roles.
        To use IAM roles for EC2 instance to run aws-cli commands, perform the following
        a.  Go to your EC2 dashboard and click on the instance name
        b.  On the bottom half section of the page, click on 'Security'
        c.  Under the 'Security Details' section, you will see 'IAM Role' but no permission policy attached to it.
        d.  Now on the top half of the page, you will see 'Actions'
        e.  Click on 'Actions' then, 'Security' then 'Modify IAM Role'
        f.  This will let you
            1.  Either create a new role for the task or action you are interested in.
            2.  If you have existing role created, which would suffice for your task, select it from the drop down menu.
                {For e.g. I created an IAM role to 'Read-IAM-Data' for 'EC2'}
        g.  Click on 'Update IAM Role'
        i.  Now, if you go back to the EC2 (via instance connect), you should be able to run the aws cli command 
        (aws iam list-users) and see the output

-----------------------------------------------------------------------------------------------------------------------------------------------------------
    
Q18: Explain EC2 Instance Purchasing options?
-----------------------------------------------------------------------------------------------------------------------------------------------------------
    Following are the EC2 instances purchasing options.
        a.  ON-DEMAND Instances : These are good for short workloads and have predictable pricing
        b.  RESERVED Instance   : Should be for a minimum of one year
            1.  Reserved Instances: These are good for longer workloads (for e.g. Database)
            2.  Convertiable Reserved Instances: Long workloads with flexible instances
            3.  Scheduled Reserved Instances: Example every Thursday between 3 and 6 PM
        c.  SPOT Instances  : Short workloads, Cheap and can lose instances (Less reliable)
        d.  Dedicated Hosts : Book an entire physical server, controlled / targetted instance placement.

-----------------------------------------------------------------------------------------------------------------------------------------------------------

Q19: Explain the characteristics of EC2 - On-demand Instances?
-----------------------------------------------------------------------------------------------------------------------------------------------------------
    EC2 On-Demand instance works on - 
        a.  Pay for what you use.
            1.  For Linux Machines:- These are charged for per second billing, after the first minute
            2.  For Other Machines:- These are charged for per hour billing
        b.  These instances have the HIGHEST cost, but have no upfront payment.
        c.  Their is no long term commitment for these type of instances.

        These are recommended for : SHORT-TERM and UN-INTERRUPTED workloads, where you cannot predict the 
        behaviour of the application

-----------------------------------------------------------------------------------------------------------------------------------------------------------

Q20: Explain the characteristics of EC2 - Reserved Instances?
-----------------------------------------------------------------------------------------------------------------------------------------------------------
    EC2 - Reserved Instances, provide up to 75% discount when compared with On-Demand instances.
        a.  The reservation period for these instances is between 1 and 3 years, bigger the duration, 
            bigger will be the discount
        b.  Purchasing options also have three options
            1.  No Upfront cost, meaning monthly payments
            2.  Partial upfront cost, will get you some discount.
            3.  All upfront cost, will get you even bigger discount.
        
        Their are 3 types of reserved instances
        a.  Reserved Instances:
            For these ones, you must reserve a specific instance type (t2.micro, c5.large etc) 
            and you cannot change the instance after selection
            These are recommended for steady state usage applications, for e.g. a Database

        b.  Convertible Reserved Intances:
            For these ones, you can change the selected instance type. For example c5.large to c5.2xlarge
            These provide upto 54% discount

        c.  Scheduled Reserved Instances: 
            These are available for the time duration (Fraction of Day/ Week/ Month) you reserved them.
            But the commitment should still be between 1-3 years.

-----------------------------------------------------------------------------------------------------------------------------------------------------------
    
Q21: Explain the characteristics of EC2 - SPOT Instances?
-----------------------------------------------------------------------------------------------------------------------------------------------------------
    These instances can
        a.  Get you a discount of upto 90% when compared with On-Demand instances.
        b.  You can lose them, at any point in time, if your max price is less than the 
            current spot price. The current spot price keeps on changing. (bidding fashion)
        c.  This is the MOST cost effective instance in AWS.
        
        These instances are recommended for, tasks which are resilient to failure
        a.  Batch Jobs
        b.  Data Analysis
        c.  Image processing
        d.  Any distributed workloads
        e.  Workloads with a flexible start and end time

        These instances are NOT recommended for :- Critical Jobs or Databases.

-----------------------------------------------------------------------------------------------------------------------------------------------------------
    
Q22: Explain the characteristics of EC2 - DEDICATED Instances?
-----------------------------------------------------------------------------------------------------------------------------------------------------------
    AWS EC2 Dedicated instances comprises of host, which is a physical server with the 
        EC2 instance capacity fully dedicated to your use.
        
        Dedicated hosts can help you adress the following
        a.  COMPLIANCE Requirements
        b.  Reduce cost by allowing you to use your existing server bound licenses.

        These are allocated for a 3 year reservation and are more expensive.
        These are useful for:
            a. Softwares that have complicated licensing model (BYOL - Bring your own license)
            b. Organizations with Strong compliance needs.

-----------------------------------------------------------------------------------------------------------------------------------------------------------
    
Q23: Explain the Similarities and difference between Dedicated Hosts and Dedicated Instances?
-----------------------------------------------------------------------------------------------------------------------------------------------------------
    Here are the Details
        a.  Similarities
            1.  Both Dedicated Instance and Dedicated hosts, Enables the use of dedicated physical server
            2.  Both Dedicated Instance and Dedicated hosts, have automatic instance placement
        b.  Differences
            1.  Dedicated Instance have Per-Instance-Billing, while Dedicated hosts have Per-Host-Billing
            2.  Dedicated Hosts have:
                i.  Visibility of Sockets, Cores and Hosts ID
                ii. Targeted Instance placement
                iii.Affinity between host and instance
                iv. Add capacity using an allocation request.

-----------------------------------------------------------------------------------------------------------------------------------------------------------