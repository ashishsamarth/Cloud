-----------------------------------------------------------------------------------------------------------------------------------------------------------
AWS-EBS: Elastic Block Store
-----------------------------------------------------------------------------------------------------------------------------------------------------------

Q01: What's an EBS volume?
-----------------------------------------------------------------------------------------------------------------------------------------------------------
    An EBS volume is a NETWORK Drive (like a network usb stick) that you can attach to your instance while they run.
        It allows the instances to persist data, even after their termination, which means, if take a snapshot of the volume before the instance was 
        terminated. You can utilize the snapshot to retain the data and a new EBS volume can be used on a new EC2 instances with the old data.
        a.  EBS volumes can be mounted to only one instance at a time (CCP-Level), and one instance can have multiple EBS volumes to it.
            There is an 'multi-attach' functionality for EBS volumes, but that is more advanced
        b.  When an EC2 instance is created, an EBS volume is attached to it, for the boot.
        c.  EBS volumes are bound to a specific availability zone, that means once created in a specific availability zone it cannot be utilized in 
            another zone

        Free-Tier: 30 GB of free EBS storage of type (General Purpose SSD or magnetic) per month

        Special Notes:
            1.  Its a network drive, i.e. Not a Physical Drive
                a.  It uses the network to communicate with the instance, which means there might be a bit of latency.
                b.  It can be detached from an EC2 instance and attached to another one quickly
            2.  Its locked to an Availability Zone (AZ)
                a.  An EBS volume in us-east-1a cannot be attached to us-east-1b
                b.  To move a volume across, you first need to snapshot it
            3.  Have a provisioned capacity (size in GBs, and IOPS)
                a.  You get billed for all the provisioned capacity
                b.  You can increase the capacity of the drive over time
            4.  An EBS volume can be created standalone and not be attached to an EC2 instance, this is possible.

        Important: How to mount additional EBS volumes to your EC2 instance.
        https://devopscube.com/mount-ebs-volume-ec2-instance/

        EBS - Delete on Termination attribute
            1.  The volume type = Root, attached to the EC2 instance has an attribute 'Delete On Termination' which is 'Checked' by default.
                : Which means, when the instance is terminated the 'root' volume will be deleted.
                This attribute is modifiable, and if you want, you can preserve the root volume.
            2.  The volume type = EBS, attached as an EBS volume to the EC2 instance, also has the attribute 'Delete On Termination' which is NOT 
                'Checked' by default. And as mentioned earlier, this attribute is modifiable.
                : Which means, when the instance is terminated the 'EBS' volume will not be deleted.

            : This attribute can be controlled by the AWS console / AWS CLI.
        
        USECASE: How to preserve the root volume when instance is terminated.

-----------------------------------------------------------------------------------------------------------------------------------------------------------
Q02: What is EBS Snapshots?
-----------------------------------------------------------------------------------------------------------------------------------------------------------
    EBS Snapshots are used to
        a.  Make a backup (snapshot) of your EBS volume at a point in time
        b.  Not necessary to detach a volume to do snapshot, but recommended
        c.  Copy snapshots across AZ or Region.

-----------------------------------------------------------------------------------------------------------------------------------------------------------
Q03: How to create a snapshot?
-----------------------------------------------------------------------------------------------------------------------------------------------------------
    Login to the EC2 dashboard and then follow these steps:
        a.  On the left side vertical menu, look for 'Elastic Block Store'
        b.  Under 'Elastic Block Store' click on 'Volume'
        c.  On the new page that opens, you will see the EBS volumes that are created / attached to the EC2 instance.
        d.  Select the volume you wish to create a snapshot for.
        e.  Click on Actions menu on the same page (horizontal bar) and click on 'Create Snapshot'
        f.  On the next screen, provide a description for the snapshot, for identification. You can add tags as well.
        g.  And then click on 'Create Snapshot'
        h.  You will see a message on the screen - 'Create Snapshot Request Succeeded'
        i.  Now click on 'Snapshots' under 'Elastic Block Store', and you will see the newly created snapshot


        Special Note: Snapshots are created in 'Regions', so these can be copied to 'Another Region' or 
        'Another AZ in the same region'

-----------------------------------------------------------------------------------------------------------------------------------------------------------
Q04: How to copy a snapshot to another region
-----------------------------------------------------------------------------------------------------------------------------------------------------------
    Login to the EC2 dashboard and then follow these steps:
        a.  On the left side vertical menu, look for 'Elastic Block Store'
        b.  Under 'Elastic Block Store' click on 'Snapshots'
        c.  Assuming you have a snapshot created earlier (which will be listed in this window)
        d.  Click on 'Actions' menu, then click on 'Copy'
        e.  On the 'Copy Snapshot' window, select the 'Destination Region' and provide/select the description and click copy.
        f.  The snapshot will then be copied to the destination region.

-----------------------------------------------------------------------------------------------------------------------------------------------------------
Q05: How to create a volume based on a snapshot from one region to another.
-----------------------------------------------------------------------------------------------------------------------------------------------------------
    Login to the EC2 dashboard and then follow these steps:
        a.  On the left side vertical menu, look for 'Elastic Block Store'
        b.  Under 'Elastic Block Store' click on 'Snapshots'
        c.  Assuming you have a snapshot created earlier (which will be listed in this window)
        d.  Click on 'Actions' menu, then click on 'Create Volume'
        e.  One the 'Create Volume' window. provide the following
            1.  Volume Type: Its a dropdown list, you can select whatever is your Requirements
            2.  Size in GBs
            3.  Availability Zone: Its a dropdown list of AZs in your current region
            4.  Encryption: Its a checkmark
        f.  Click on create volume
        g.  Now that the EBS volume has been created, click on 'Volume' under 'Elastic Block Store'
        h.  You should be able to see the new volume in the new availability zone.

        This is how you take a snapshot and copy the data from one AZ to Another AZ in the same region.

-----------------------------------------------------------------------------------------------------------------------------------------------------------
Q06: What is an AMI?
-----------------------------------------------------------------------------------------------------------------------------------------------------------
    AMI is Amazon Machine Image
        a.  AMIs are a customization of an EC2 instance.
            1.  You add your own software, configuration, OS, monitoring etc.
            2.  Faster Boot / Configuration time because all of your software is pre-packaged
        b.  AMI are built for SPECIFIC region (And can be copied across regions)
        c.  You can launch EC2 instances from:
            1.  A public AMI: Provided by AWS
            2.  Your Own AMI: You make and maintain them yourself.
            3.  AWS Marketplace AMI: An AMI someone else made (and potentially sells)

-----------------------------------------------------------------------------------------------------------------------------------------------------------
Q07: How to create an AMI from an EC2 Instance?
-----------------------------------------------------------------------------------------------------------------------------------------------------------
Start an EC2 instance with any specific AMI, then customize it (add JDK, Tomcat, DB etc) and then stop the instance.
Then we will build the AMI from this image (This will also create EBS snapshots, since attached EBS will be a part of the AMI)
Now this modified AMI can be used to launch new instance, with the pre-packaged software.

    Following are the steps:
        a.  Assuming you have done all the required changes to the current EC2 instance
        b.  Right click on the running 'EC2' instance and then click on 'Image and Templates'
        c.  Then click on 'Create Image'
        d.  Provide a name to the image
        e.  You will notice, the image creation has automatically selected the EBS volume used to boot this current EC2 instance, with the 
            attribute (Delete on Termination) enabled.
        f.  There are two following options for tags {Radio Buttons}
            1.  Tag image and snapshots together
            2.  Tag image and snapshots separately
        g.  Click on 'Create Image' on this page.
        h.  The image will be created successfully.

-----------------------------------------------------------------------------------------------------------------------------------------------------------
Q08: How to Launch a new EC2 instance based on 'Created AMI'?
-----------------------------------------------------------------------------------------------------------------------------------------------------------
    Once you have successfully created your own modified AMI image, the image should show up under 'Images' in EC2 dashboard
        {Left Vertical Menu}
        a.  On the EC2 dashboard, click on Launch Instances.
        b.  On the next step 'Choose an Amazon Machine Image (AMI), click on 'My AMIs' on the left vertical menu
        c.  Your modified AMI should be visible here, select it.
        d.  Select the instance type
        e.  Configure the security group
        f.  Review the launch instance and then click on 'Launch Instance'
    This is how you launch an EC2 instance based on the 'Created AMI'

-----------------------------------------------------------------------------------------------------------------------------------------------------------
Q09: What is an EC2 Instance Store?
-----------------------------------------------------------------------------------------------------------------------------------------------------------
    EBS volumes are network drives with good, but 'Limited' Performance.
        If you need a 'High-Performance hardware disk' use EC2 Instance Store

        EC2 Instance Store has the following characteristics.
        a.  Better I/O Performance
        b.  EC2 Instance Store lose their storage if they are stopped (ephemeral) {More like RAM}
        c.  This is good for Buffer / Cache or temporary content.
        d.  Risk of Data Loss, if the hardware fails
        e.  Back up and Replication are Your responsibility
        f.  The instances usually start with 'i' in the naming conventions (e.g. i3.large, i3en.metal, i3.metal, i3.8xlarge)

-----------------------------------------------------------------------------------------------------------------------------------------------------------
Q10: Explain the types of EBS Volumes?
-----------------------------------------------------------------------------------------------------------------------------------------------------------
    There are total 6 types of EBS volumes for now, following are the categories.
        a.  gp2 / gp3 (SSD) : General purpose SSD volumes that balance price and performance for a variety of workloads
        b.  io1/ io2 (SSD)  : Highest performance SSD volume for mission-critical low-latency or high-throughput workloads
        c.  st1 (HDD)   : Low Cost HDD volume designed for frequently accessed, throughput-intensive workloads.
        d.  sc1 (HDD)   : Lowest cost HDD volume designed for less frequently accessed workloads.
    
    EBS volumes are characterized in Size
        a.  By Size
        b.  By throughput
        c.  By IOPS (I/O operations per second)
    When in doubt, always use AWS documentation.

    Special Note: For EC2 instance, only gp2/gp3 and io1/io2 EBS volumes can be used for boot volumes.

-----------------------------------------------------------------------------------------------------------------------------------------------------------
Q11: Explain the characteristics of General Purpose SSD EBS volume?
-----------------------------------------------------------------------------------------------------------------------------------------------------------
    General Purpose SSDs are
        a.  Cost Effective Storage, Low-latency
        b.  Used for : System boot volumes, Virtual Desktops, Development and Test environments.
        c.  Size is between: 1GB - 16TB
    
    gp3 is the higher generation of General Purpose SSDs
        gp3:
            1.  Baseline of 3000 IOPS and throughput of 125 MBPS
            2.  Can increase IOPS to 16000 and throughput to 1000 MBPS independently
        gp2:
            1.  Small gp2 volumes can burst IOPS to 3000
            2.  Size of the volume and IOPS are linked, max IOPS is 16000
            3.  IOPS per GB, means at 5334 GB we are at the max IOPS.

-----------------------------------------------------------------------------------------------------------------------------------------------------------    
Q12: Explain the characteristics of Provisioned IOPS EBS Volume?
-----------------------------------------------------------------------------------------------------------------------------------------------------------
    Provisioned IOPS SSDs are good for
        a.  Critical Business applications with sustained IOPS performance
        b.  OR Applications that need more than 16000 IOPS
        c.  Great for database workloads (sensitive to storage performance and consistency)
        d.  Supports EBS multi attach

        io1/io2: size ranges from 4GB to 16TB
            1.  Max provisioned IOPS : 64000 for Nitro EC2 instances & 32000 for other.
            2.  Can increase PIOPS independently from Storage size
            3.  io2 have more durability and more IOPS per GB (at the same price of io1)
        
        There is a new type of io volume namely io2 Block Express
            1.  Size range is 4GB to 64TB
            2.  Sub-Millisecond latency
            3.  Max PIOPS: 256000 with an IOPS:GB ratio of 1000:1

-----------------------------------------------------------------------------------------------------------------------------------------------------------
Q13: Explain the characteristics of HDD EBS volume?
-----------------------------------------------------------------------------------------------------------------------------------------------------------
    HDD EBS Volumes
        a. Cannot be a boot volume
        b. Size ranges between 125MB to 16TB
        
        There are two types of HDD EBS Volumes
        1.  st1: These are throughput optimized HDDs, good for Big Data, Data Warehouses and Log processing workloads.
        2.  sc1: These are cold HHDs, and good for infrequently (archival) accessed data, and has the lowest cost of all.

-----------------------------------------------------------------------------------------------------------------------------------------------------------    
Q14: What is EBS Multi-Attach?
-----------------------------------------------------------------------------------------------------------------------------------------------------------
    Multi-Attach is a functionality that allows you to "attach one EBS volume to multiple EC2 instances in the SAME AZ."
        This functionality is only available for EBS volumes from the io1/io2 family
        Note:
            1.  Each EC2 instance attached to such an EBS volume has full read and write permissions to the volume
        
        USECASE:
            1.  Applications using this functionality must be able to manage concurrent write operations to the same volume
            2.  Applications using this functionality muse you a filesystem that's cluster aware.
        This functionality will allow the applications to achieve higher application availability in clustered Linux applications.

 -----------------------------------------------------------------------------------------------------------------------------------------------------------