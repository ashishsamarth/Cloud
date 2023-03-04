AWS-EFS: Elastic File System
-----------------------------------------------------------------------------------------------------------------------------------------------------------

Q01: What is EFS?
-----------------------------------------------------------------------------------------------------------------------------------------------------------
    EFS is Elastic File System.
        a.  Its a Managed NFS (Network File System) that can be mounted to many EC2 instances in the same region.
        b.  EFS works with EC2 instances in multi-AZ.
        c.  Highly available, scalable, expensive (3 times of a gp2)
        d.  Works with 'Pay-per-use' model

        Suppose you have one EFS and three EC2 instances spread across different AZs in the same region.
        All 3 EC2 instances can connect to this EFS via the security group.

        USECASES:
            1.  Can be used in ContentManagement, Web-Serving, Data-Sharing, WordPress
            2.  Uses NFSv4.1 protocol
            3.  Uses security group to control access to EFS
            4.  Compatible only with Linux based AMI {Does not work with Windows}
            5.  Filesystem is encrypted at rest using KMS
        
        Special Note:
            1.  File system scales automatically, pay-per-use, no-capacity-planning.

        EFS - Performance & Storage Classes:
            EFS Scale:
                1.  1000s of concurrent NFS clients, 10GB+ /s throughput
                2.  Grow to petabyte-scale network file system, automatically
            Performance Mode (set at EFS creation time)
                1.  General Purpose (default): Latency Sensitive use cases (Web Server, CMS etc)
                2.  Max I/O - Higher Latency, throughput highly parallel (Big Data, Media Processing)
            Throughput Mode
                1.  Bursting (1TB=50MBPS + Burst of up to 100 MBPS)
                2.  Provisioned: Set your throughput regardless of the storage size, e.g. (1 GBPS for 1 TB Storage)
        
        Related Question:
        Q: If you want to increase the throughput of a very small filesystem then which mode of EFS should be used?
        A: Provisioned Throughput mode.

        Storage Tiers:
            This is a lifecycle management feature for the files, to move the file after 'N' days.
            a.  Standard: For frequently accessed file
            b.  Infrequent Access (EFS-IA): This has a lower price to store, but has a Cost to retrieve the file.
    
-----------------------------------------------------------------------------------------------------------------------------------------------------------
Q02: What is the minimum IAM permission policy that must me attached either to the group or the user to be able to create an EFS?
-----------------------------------------------------------------------------------------------------------------------------------------------------------
The mininum IAM policy required to be able to create an EFS is :- AmazonElasticFileSystemClientFullAccess.

-----------------------------------------------------------------------------------------------------------------------------------------------------------
Q03: What is the minimum IAM permission policy that must be attached either to the group or the user to be able to read data from EFS?
-----------------------------------------------------------------------------------------------------------------------------------------------------------
The mininum policy required to be able to read data from EFS is :- AmazonElasticFileSystemReadOnlyAccess.

-----------------------------------------------------------------------------------------------------------------------------------------------------------
Q04: How to create an EFS (Elastic File System)?
-----------------------------------------------------------------------------------------------------------------------------------------------------------
    Following are the steps:
        a.  On the AWS management console, search for EFS
        b.  Once navigated to the EFS console, click on 'Create File System'
        c.  On the 'Create File System' dialog, Click 'Customize'
            1.  The name is optional
            2.  And the Default VPS is pre-selected
            3.  Their is a button to 'Create' to use default settings and another one to 'Customize'
        d.  On the new page 'File System Settings'
            1.  The name is optional
            2.  Automatic Backups is 'Checked':
                {Automatically Backs up your file system data. Additional pricing is applied}
            3.  Lifecycle Management
                This is a drop down value with multiple options to move files based on how frequently they are accessed.
                If you select '30 days since last access' then any file which has not been accessed in last 30 days will be moved 
                to EFS-IA (Elastic File System - Infrequent Access Data storage class to save some cost)
            4.  Performance Mode
                i.  General Purpose: Ideal for latency sensitive use-cases like web serving and content management systems.
                ii. Max I/O: Scale to higher levels of aggregate throughput and operations per second.
            5.  Throughput Mode
                i.  Bursting: Throughput scales with file system size
                ii. Provisioned: Throughput fixed at a specified amount. {This is configurable}
            6.  Encryption:
                Enable encryption of data at rest is enabled by default.
        e.  On the new page 'Network Access Settings'
            1.  Virtual Private Cloud (VPC) : Default VPC is pre-selected
            2.  Mount Targets
                Since EFS can work across all AZs in a region, multiple AZs options are available in this section.
                The subnets are pre-selected.
                The default security groups are also selected, and can be MODIFIED. However a security group must be defined for each AZ
                where this particular EFS will be available and accessed.

        f.  File system policy is optional
        g.  Next page is 'Review and Create'
        h.  Click on Create and the EFS file system will be created.

-----------------------------------------------------------------------------------------------------------------------------------------------------------
Q05: How to attach an EFS to multiple EC2 instance in the same region but in different AZs?
-----------------------------------------------------------------------------------------------------------------------------------------------------------
    Following are the steps:
        a.  On the AWS management console, search for EC2.
        b.  Once navigated to EC2 dashboard, on the left vertical menu, click on security groups under Network Security
        c.  Create a new security group 'EC2-to-EFS'
            1.  Add a new Inbound rule with 
                TYPE=NFS
                SOURCE=Select the Security Group which has SSH Access at port 22 for EC2.
                        If you dont want to use the existing security grousp with SSH Access, create a new one with specific name
                        and then select that Security Group Here.

                        Special Note: Even though the protocol and port number are same in different security groups. They are still 
                        treated as unique. So, selection of correct security group is very important.
                Click on 'Add Rule' and then click on 'Create Security Group'.
                
        d.  Now go back to your EC2 instances on the EC2 Dashboard and under 'Security' check the 'Security Groups'
        e.  Whatever be the name of this security group (it must be same for all instances which you plan to connect to EFS)
        f.  This should be the same security group, which you will 'Select' as 'SOURCE' for 'EC2-to-EFS' security group.
        g.  Now on the AWS management console, look for EFS and navigate to EFS console.
        h.  You should have an EFS file system created.
        i.  Click on the EFS filesystem and navigate to 'Network'
        j.  Under 'Network' you MUST have 'Mount targets' 'CREATED'. Unless the status created, its not going to work
        k.  if the 'Mount Targets' are not created, check if you have done the correct selection of 'Security Groups' (i.e. 'EC2-to-EFS' SG)
        l.  Once the Mount Targets are created, go ahead and connect to your EC2 instances using the pem/ppk file via SSH
        m.  On each of the instances, create a directory 'efs' this is the directory which we will use as the mount point of EFS.
        n.  Before, we can mount the EFS to 'efs' directory, we need to install the NFS utils packaged
        o.  As root (sudo) - execute: yum install -y amazon-efs-utils
        p.  Once package is installed on the EC2 instances, come back to EFS dashboard and click on the File System that was created
        q.  On the top right you will see an option to 'Attach'
        r.  Use the 'Mount via DNS' option and run the command indicated as - 'sudo mount -t efs -o tls fs-0c621fafa80c68ea6:/ efs'
        s.  In the above command, 'tls' is for encryption and 'fs-0c621fafa80c68ea6' is the filesystem ID. and efs at the end is the mount point name.
        t.  If everything was done correctly, the EFS will be mounted on 'efs' directory as the mount point on EC2 instances.

-----------------------------------------------------------------------------------------------------------------------------------------------------------