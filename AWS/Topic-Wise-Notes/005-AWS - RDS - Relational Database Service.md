Amazon RDS (Relational Database Service)
-----------------------------------------------------------------------------------------------------------------------------------------------------------

-----------------------------------------------------------------------------------------------------------------------------------------------------------
    RDS stands for Relational Database Service.
    Its a managed DB service for DB and uses SQL as a query Language.
    It allows you to create databases in the cloud that are managed by AWS, following DBs are supported:
        a.  Postgres
        b.  MySQL
        c.  MariaDB
        d.  Oracle
        e.  Microsoft SQL Server
        f.  Aurora (AWS Proprietry Database)

-----------------------------------------------------------------------------------------------------------------------------------------------------------

Advantage of using RDS versus deploying DB on EC2
-----------------------------------------------------------------------------------------------------------------------------------------------------------
    RDS is a managed service
        a.  Automated Provisioning, OS patching
        b.  Continuous backup and restore to specific timestamp (Point in time restore)
        c.  Monitoring Dashboards
        d.  Read Replicas for improved read performance
        e.  Multi AZ setup for DR (Disasater Recovery)
        f.  Maintenance windows for upgrades
        g.  Scaling Capability (vertical and horizontal)
        h.  Storage backed by Elastic Block Store (gp2 or io1)

    But, you cannot SSH into your RDS instances, since its a Managed Service.

-----------------------------------------------------------------------------------------------------------------------------------------------------------

RDS Backups:
-----------------------------------------------------------------------------------------------------------------------------------------------------------
    a.  Backups are automatically enabled in RDS.
    b.  Automated Backups:
        1.  Daily Full backup of the database (during the maintenance window)
        2.  Transaction Logs are backed-up by RDS every 5 minutes
        3.  Ability to restore at any point in time (from oldest backup to 5 mins ago)
        4.  7 Day retention (can be increased to 35 days)
    c.  DB Snapshots.
        1.  DB snapshots are manually triggered by the user
        2.  Retention of backup for as long as you want

-----------------------------------------------------------------------------------------------------------------------------------------------------------

RDS: Storage Auto Scaling
-----------------------------------------------------------------------------------------------------------------------------------------------------------
    a.  Helps you increase storage on your RDS DB instance dynamically
    b.  When RDS detects you are running out of free database storage, it scales automatically
    c.  This helps you avoid manually scaling your database storage
    d.  You have to set "Maximum Storage Threshold" [maximum limit of DB storage]
    e.  It helps you automatically modify storage if:
        1.  Free storage is less than 10% of allocated storage
        2.  Low-Storage lasts at least 5 minutes (depending on transaction writes)
        3.  6 hours have passed since last modification
    f.  Useful for applications with un-predicable workloads
    g.  Supports all RDS Database Engines [Postgres, MySQL, MariaDB, Oracle, Microsoft SQL Server]

-----------------------------------------------------------------------------------------------------------------------------------------------------------

Q01: What is RDS Read Replication?
-----------------------------------------------------------------------------------------------------------------------------------------------------------
Replication means a continuous copy of the data from one Database (master/publisher) to another Database (slave/subscriber). The slave/subscriber Databases can be on the same server or different servers and contain the replica of the master database. The main aim of replication is to provide fault-tolerant access to data in case of failure of the master. Also, load balancing and routing some of the queries to the subscriber database to reduce the load on the primary Database.

Amazon RDS Read Replication is a feature on Amazon RDS that allows you to create one or more read copies (up to 5) of the primary Database within the same or different AWS region. The data from the master database is asynchronously copied to these slave or secondary databases.

-----------------------------------------------------------------------------------------------------------------------------------------------------------
        a.  Up to 5 Read Replicas
        b.  Read Replicas can be created - Within AZ, or Across AZs or Across Regions.
        c.  Replication is ASYNC, so reads are eventually consistent
        d.  Replicas CAN be promoted to their own Database, and then they will follow their own lifecycle.
        e.  Applications must update the connection string to leverage read replicas.

        USECASE:
            Suppose you have a production database, that is operating under normal load. Now for some analytics or 
            reporting tasks, you need access the production database.
            a.  If both the application and the reporting tasks are accessing the production database simultaneously, 
                then it may increase the load on the database.
            b.  To avoid this, as a solution architect, you can create a "READ REPLICA" , so that only the application 
                is working on the production DB, while the reporting tasks are working through the 'READ REPLICA'
            c.  This way the production database is not overloaded and the application remains un-affected.

        Special Note:
            Read replicas are used for 'SELECT' only statements (not Insert, Update or Delete)

-----------------------------------------------------------------------------------------------------------------------------------------------------------
    
Q02: Explain associated costs for RDS Read Replicas - Across the network?
-----------------------------------------------------------------------------------------------------------------------------------------------------------
    Usually for AWS managed services, there is no network cost when data travels from One AZ to another, however there are exceptions.
        a.  For RDS Read Replicas: If your RDS DB and RDS Read Replica are in the same region 
            (may or may not be in different AZ), then no replication charges will be incurred.
        b.  For RDS Read Replicas: If you RDS DB and RDS Read Replica are in different regions, 
            then replication charges will be incurred.

-----------------------------------------------------------------------------------------------------------------------------------------------------------
    
Q03: What is RDS Multi AZ?
-----------------------------------------------------------------------------------------------------------------------------------------------------------
    RDS multi AZ is used for disastor Recovery
        a.  Unlike READ REPLICAS (which are A-SYNC replication), Multi AZ is SYNC Replication.
        b.  RDS Multi AZ is one DNS name : And supports automatic Failover from the Master DB to the Standby DB
        c.  RDS Multi AZ increases the application availability, due to automatic Failover
        d.  Failover Will trigger:
            1.  Due to Loss of AZ
            2.  Due to Loss of network
            3.  Due to Instance failure
            4.  Due to storage failure
        e.  Their are no manual interventions needed in applications to move the connection from Master DB to 
            Standby DB, since the failover happens, beneath the DNS layer.
        f.  The STANDBY DB cannot be used for SCALING, no body can directly read from or write to 'STANDBY' DB 
            unless it becomes Master.

        Special Note:
        Common Exam Question: Can Read Replicas be setup as 'Multi-AZ' for Disaster Recovery (DR) purposes?
        Answer              : YES

-----------------------------------------------------------------------------------------------------------------------------------------------------------
    
Q04: How to convert a RDS-Single AZ to RDS-Multi AZ?
-----------------------------------------------------------------------------------------------------------------------------------------------------------
    To convert a RDS-Single AZ to RDS-Multi AZ, we just need to modify the database and convert it.
        a.  Their is no downtime to convert RDS from single-AZ to multi-AZ, since we dont need to stop the DB.
        b.  When you convert a single-AZ to multi-AZ:
            1.  A snapshot is taken from the Master DB
            2.  A new standby DB is created.
            3.  The snapshot is written to the standby DB
            4.  After the snapshot is written, SYNC replication happens between master and standby, until Standy 
                catches up completely.

-----------------------------------------------------------------------------------------------------------------------------------------------------------

Q05: What is Data at rest?
-----------------------------------------------------------------------------------------------------------------------------------------------------------
Data at rest refers to data residing in computer storage in any digital form. This data type is currently inactive and is not moving between devices or two network points. No app, service, tool, third-party, or employee is actively using this type of info.

At rest is not a permanent data state. As soon as someone requests a file, that data moves across a network and becomes in-transit data. Once someone (or something) starts processing a file, the data enters the in-use state

-----------------------------------------------------------------------------------------------------------------------------------------------------------
    Data at rest includes both structured and unstructured data. Some examples of where a company can store data at rest are:

        a.  Hard and SSD drives on PCs and laptops.
        b.  Database servers.
        c.  The cloud.
        d.  At a third-party colocation facility.
        e.  Edge-point devices and portable storage (mobile phones, USBs, tablets, portable hard drives, etc.).
        f.  Network-attached storage (NAS).

        Static data storage typically has a logical structure and meaningful file names, unlike individual in-motion 
        packets moving through a network. 
        
        Data at rest also typically contains the company's most valuable and private info, such as:

        a.  Financial documents (past transactions, bank accounts, credit card numbers, etc.).
        b.  Intellectual property (product information, business plans, schematics, code, etc.).
        c.  Contacts.
        d.  Marketing data (user interactions, strategies, directions, leads, etc.).
        e.  Employee and customer personal info.
        f.  Healthcare data.
        g.  Contracts.
        h.  Supply chain info.

-----------------------------------------------------------------------------------------------------------------------------------------------------------

Q06: What is Data at Rest Encryption?
-----------------------------------------------------------------------------------------------------------------------------------------------------------
Data at rest encryption is a cybersecurity practice of encrypting stored data to prevent unauthorized access. Encryption scrambles data into ciphertext, and the only way to return files into the initial state is to use the decryption key.

-----------------------------------------------------------------------------------------------------------------------------------------------------------
        Plain-Text Message                           Cipher-Text                             Plain-Text Message
        --------------------      Encryption      --------------------      Decryption      -------------------
        |  Data Storage 1a |  ------------------> | sdgsde7%^--4489-0|  ------------------> | Data Storage 1a | 
        --------------------                      --------------------                      -------------------

-----------------------------------------------------------------------------------------------------------------------------------------------------------

If an un-authorized person accesses encrypted data but does not have the decryption key, the intruder must defeat the encryption to decipher the data. This process is significantly more complex and resource-consuming than accessing the unencrypted data on a HDD.

In most cases, at rest encryption relies on symmetric cryptography. The same key encrypts and decrypts the data, unlike with assymetric encryption in which one key scrambles data (public key) and the other deciphers file (private-key). Security teams typically choose symmetric cryptography when speed and responsiveness are the priority.

-----------------------------------------------------------------------------------------------------------------------------------------------------------
Q07: Explain RDS Security - Encryption?
-----------------------------------------------------------------------------------------------------------------------------------------------------------
    RDS Security - Encryption provides
        a.  At rest encryption:
            1.  Possibility to encrypt the master and read replicas with AWS-KMS-AES-256 encryption
            2.  Encryption HAS TO BE defined at RDS launch time.
            3.  if the master is not encrypted, the read replicas CANNOT be encrypted
            4.  Transparent Data Encryption (TDE) can be applied and is available for Oracle and SQL Server.
        
        b.  In-Flight Encryption:
            1.  SSL Certificates to encrypt data to RDS in flight
            2.  Provide SSL options with trust certificates when connecting to database.
            3.  To enforce SSL:
                i.  PostgreSQL: rds.force_ssl=1 in the AWS RDS console (Parameter Groups)
                ii. MySQL: Within the DB:
                    GRANT USAGE ON *.* TO 'mysqluser'@'%' REQUIRE SSL;

-----------------------------------------------------------------------------------------------------------------------------------------------------------
    
Q08: Explain RDS Encryption Operations?
-----------------------------------------------------------------------------------------------------------------------------------------------------------
    Following are important details about RDS encryption operations.
        a.  If you take a snapshot of an un-encrypted RDS Database, the snapshot will be 'Un-Encrypted' by default.
        b.  If you take a snapshot of an encrypted RDS Database, the snapshot will be 'Encrypted' by default.
        c.  TO Encrypt an un-encrypted RDS Database:
            1.  Create a snapshot of the un-encrypted database.
            2.  Copy the snapshot and enable encryption for the snapshot
            3.  Restore the database from the encrypted snapshot
            4.  Migrate applications to the new database, and delete the old database.

-----------------------------------------------------------------------------------------------------------------------------------------------------------
    
Q09: Explain RDS-Security at Network & IAM Levels?
-----------------------------------------------------------------------------------------------------------------------------------------------------------
    Network Security:
        a.  RDS Database are usually deployed within a private subnet, not in a public one
        b.  RDS Security works by leveraging security groups (Same as EC2 instances), it controls 
            which IP / SG can COMMUNICATE with RDS.

    Access Management:
        a.  IAM policies help control who can manage AWS RDS (Through the RDS API)
        b.  Traditional Username and Password can be used to login into the Database.
        c.  IAM-Based authentication can be used to login into RDS MySQL & PostgreSQL.

-----------------------------------------------------------------------------------------------------------------------------------------------------------

Q10: Explain RDS-IAM Authentication?
-----------------------------------------------------------------------------------------------------------------------------------------------------------
    a.  IAM database authentication works only with MySQL and PostgreSQL
    b.  No password is needed, rather an Authentication Token is obtained through IAM and RDS API Calls
    c.  Auth Token has a lifetime of 15 minutes

    Benefits:
        a.  Network In/Out is encrypted using SSL
        b.  IAM to centrally manage users instead of DB
        c.  Can Leverage IAM Roles and EC2 profiles for easy integration.

-----------------------------------------------------------------------------------------------------------------------------------------------------------