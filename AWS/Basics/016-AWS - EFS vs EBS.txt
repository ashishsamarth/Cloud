-----------------------------------------------------------------------------------------------------------------------------------------------------------
EBS vs EFS
-----------------------------------------------------------------------------------------------------------------------------------------------------------
EBS Volumes:
    Characteristics
        a.  Can be attached to only ONE instance at a time
        b.  Are locked at the Availability Zone (AZ) level
        c.  For gp2 SSD volumes: IO increases if the disk size increases
        d.  io1: Can increase IO independently
    
    To Migrate an EBS volume across AZ
        a.  Take a Snapshot
        b.  Restore the snapshot to another AZ
        c.  EBS backups use IO and you shouldn't run them while your application is handling a lot of traffic
    
    Root EBS volumes of instances gets terminated by default (Due to Delete on Termination Attribute), if the EC2 instance is terminated


EFS
    Characteristics
        a.  Can be attached to multiple instances at a time
        b.  Are NOT locked at the Availability Zone (AZ) level and can be used across different AZs in a region
        c.  Only supports LINUX instances (POSIX File system)
        d.  EFS has a HIGHER price point than EBS
        e.  You can leverage (EFS-IA: In-frequent Access) for Cost Savings