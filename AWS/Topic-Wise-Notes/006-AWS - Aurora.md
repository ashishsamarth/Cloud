AWS - Aurora
-----------------------------------------------------------------------------------------------------------------------------------------------------------

-----------------------------------------------------------------------------------------------------------------------------------------------------------
a.  Aurora is a proprietary technology from AWS.
b.  Postgres and MySQL are both supported as Aurora DB (meaning drivers will work as if Aurora was a Postgres or MySQL DB)
c.  Aurora is 'AWS cloud optimized' and claims 5x performance improvement over MySQL on RDS, over 3x performance over Postgres on RDS.
d.  Aurora storage automatically grows in increments of 10 GB, up to 64 GB, so as a sysops, you dont have to continuously monitor it.
e.  Aurora can have 15 replicas while MySQL has 5, and the replication process is faster (10ms replication lag)
f.  Failover in Aurora is instantaneous, and its also High Availability native.
g.  Aurora costs more than RDS (20% more), but is way more efficient than MySQL or Postgres on RDS.

-----------------------------------------------------------------------------------------------------------------------------------------------------------

FEATURES OF AURORA:
-----------------------------------------------------------------------------------------------------------------------------------------------------------
    a.  Automatic Failover
    b.  Backup And Recovery
    c.  Isolation and Security
    d.  Industry Compliance
    e.  Push-Button Scaling
    f.  Automated Patching with Zero Downtime
    g.  Advanced Monitoring
    h.  Routine Maintenance
    i.  Backtrack: Restore Data at any point of time without using Backups

-----------------------------------------------------------------------------------------------------------------------------------------------------------

Q01: Explain Aurora High Availability and Read Scaling?
-----------------------------------------------------------------------------------------------------------------------------------------------------------
    Aurora saves 6 copies of your data across 3 AZs.
        a.  4 copies out of 6 are needed for writes
        b.  3 copies out of 6 are needed for reads
        c.  Self Healing with peer-to-peer replication
        d.  Storage is distributed across 100s of volumes.
    
        Aurora DB has only one master and the rest of the instances will be read replicas.
        Automated failover for master is less than 30 seconds.

        Along with the Master DB, Aurora can have 15 read replicas to serve reads, and support cross region replication.

            Availability Zone 1         |           Availability Zone 2         |       Availability Zone 3
        -----------     --------------  |   --------------      --------------  |   --------------      --------------
        |Master DB|     |Read Replica|  |   |Read Replica|      |Read Replica|  |   |Read Replica|      |Read Replica|
        -----------     --------------  |   --------------      --------------  |   --------------      --------------
        ---------------------------------------------------------------------------------------------------------------
                                                    SHARED STORAGE VOLUME
                                        REPLICATION + SELF HEALING + AUTO EXPANDING
        ---------------------------------------------------------------------------------------------------------------
        Data Block(s)   Data Block(s)   |       Data Block(s) Data Block(s)     |       Data Block(s)   Data Block(s)
        Data Block(s)   Data Block(s)   |       Data Block(s) Data Block(s)     |       Data Block(s)   Data Block(s)
        Data Block(s)   Data Block(s)   |       Data Block(s) Data Block(s)     |       Data Block(s)   Data Block(s)
    
-----------------------------------------------------------------------------------------------------------------------------------------------------------

Q02: What is a 'Writer Endpoint' in Aurora?
-----------------------------------------------------------------------------------------------------------------------------------------------------------
Writer Endpoint is a DNS based url, which is the connection point from the CLIENT to MASTER DB in AURORA DB. The reason to have this DNS based URL is, since AURORA can failover the Master DB to any of the other REPLICAS, this DNS based url automatically points to the 'CURRENT MASTER' at any given point in time, and the client does not need to scramble for a new endpoint to connect to Aurora

-----------------------------------------------------------------------------------------------------------------------------------------------------------

Q03: What is a 'Reader Endpoint' in Aurora?
-----------------------------------------------------------------------------------------------------------------------------------------------------------
'Reader Endpoint' is a DNS based url, which is the connection point from the CLIENT to READ REPLICAS in Aurora DB. The reason to have this DNS based url is:

-----------------------------------------------------------------------------------------------------------------------------------------------------------
    a.  Since there can be up to 15 Read Replicas, the reader endpoint will ensure the connection to each read replica.
    b.  It performs 'Load Balancing' at the 'Reader Endpoint' level, NOT at the QUERY level.
    c.  Also, since the Read Replicas CAN Auto Scale (based on policy), this url, can register / deregister;
        new/terminated Read Replicas.

-----------------------------------------------------------------------------------------------------------------------------------------------------------           
Q04: Explain Aurora DB Cluster?
-----------------------------------------------------------------------------------------------------------------------------------------------------------
    Following is the high level design.

                        ---------------------------------CLIENT---------------------------------
                        |                                                                       |
                        |                                                                       |
                        |                                                                       |
                        |                                                                       |
                WRITER Endpoint                                                           READER Endpoint
            [Pointing to Master DB]                                                  [Connection Load Balancing]
                        |                                                                       |
                        |                                                                       |
                        |                                                -----------------------------------------------                  
                        |                                               |       |       |       |       |       |       |
                    MASTER DB                                           RR1    RR2      RR3     RR4     RR5     RR6     RR7
                        |                                               |       |       |       |       |       |       |
                        |                                               |       |       |       |       |       |       |
                    WRITES to                                         READS   READS   READS   READS   READS   READS   READS  
        --------------------------------------------------------------------------------------------------------------------
                                                    SHARED STORAGE VOLUME
                                                AUTO EXPANDING FROM 10G to 64TB
        --------------------------------------------------------------------------------------------------------------------

-----------------------------------------------------------------------------------------------------------------------------------------------------------
    
Q05: Explain Aurora Security?
-----------------------------------------------------------------------------------------------------------------------------------------------------------
    The security in Aurora is pretty much same as in RDS, since it utilizes the same DB engines.
        a.  Encryption at rest using KMS.
        b.  Automated Backups, snapshots and replicas are also encrypted
        c.  Encryption in-flight using SSL (using same process as MySQL or Postgres)
        d.  Possibility to authenticate using IAM token (same method as RDS)
        e.  You are responsible for protecting the instance with security groups
        f.  You cannot SSH into Aurora, just like RDS, since its a managed service

-----------------------------------------------------------------------------------------------------------------------------------------------------------
    
Q06: How many modes for read and write are supported in Aurora?
-----------------------------------------------------------------------------------------------------------------------------------------------------------
    Their are 4 different modes supported in Aurora
        a.  One Writer & Multiple Readers:  
                Supports multiple reader instances connected to the same storage volume as a single writer instance.
                This is a good general-purpose option for most workloads

        b.  One Writer & Multiple Readers - Parallel Query: 
                Improves the performance of analytic queries by pushing processing down to the Aurora
                Storage layer. This is a good option for hybrid transactional / Analytic workloads.
        
        c.  Multiple Writers:   
                Supports multiple writer instances connected to the same storage volume. This is a good option, when continuous 
                Writer availability is required.
        
        d.  Serverless: 
                You specify the minimum and maximum amount of resources needed, and Aurora scales the capacity based on database load.
                This is a good option for intermittent or unpredictable workloads.

-----------------------------------------------------------------------------------------------------------------------------------------------------------