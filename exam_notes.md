## Storage
### Object level Storage
  * S3 and Glacier
    * S3 for high durability and availability
    * In case of disaster recovery, you need to enable Cross Region Replication.
    * Glaciar is used to archieve storage. Cost effective option. retrieval time is generally 3-5 hours.
      * Expedited retrieval-minutes-Pay extra.
    * How to transfer data to Glacier 
      * API
      * Lifecycle policies for S3
     
### Block Level Storage
  * Elastic Block Storage Volumes: don't have the save level of durability as S3
  * In an AZ, they are replicated to multiple devices. But if the AZ fails, the volume is not usable.
    * You can safeguard your data by:
      *Creating EBS Snapshots and copying it to another region for disaster recovery purposes
#### EBS Voulmes types:
  * General Purpose SSD
    * If you have EC2 Instance, web server and predictable workload,this option is  cost effective volume type
  * Provisioned IOPS
    * If you have EC2 instance, database server, resource intensive, high number of input and output operations
      * In database server, select statement is for (Read opearation-- search for data ) and Update, Insert and Delete statements are (Write Opeartion) 
      * As database needs to access volumes for read and write operations, I/O Controller(device)- takes a lot of strain for these operations. If the reads and writes are too much the controller just starts lagging behind. 
  * Throughput Optimized HDD
    * If you have EC2 instance, Processing server, Processing videos for files with large size, streaming videos or high throuhput.
      * Cost effective than Provisioned IOPS
      * 400 MiB/s
  * Cold HDD
    * Infrequently accessed storage
**** 
* If you have high frequency for 2 months, you can even store the videos for 2 months on Throughput Optimized HDD. After 2 months, have a script which transfers the videos to Cold HDD.

### Databases
  * AWS RDS (Oracle, Microsoft SQL Server, MySQL, PostgreSQL, MariaDB)
    * Use Multi-AZ RDS for high availability. If the primary DB fails, AWS will automatically switch your endpoint to the standby (Secondary DB). You don't have access to the standby (only AWS does). 
    * For automated backups of RDS, copy the snapshots to the another region. 
    * AWS RDS server (Read Replica) is available for MySQL, PostgreSQL and MariaDB. 
    * you have asynchronous replication from primary DB to secondary DB. You now have access to secondary DB because you are given another endpoint.
    * Use read replicas when you have performance problems on the primary DB. Use when your primary DB is getting a lot of hits. 
  * DynamoDB
    * Fully managed NoSQL database.
    * You also have indexes- global and local secondary indexes.
    * Highly available and durable
    * Infrastructure scales automatically based on demand
    * Before creation of the table you can choose autoscaling for read and write throuhputs.
  * Aurora(MySQL and PostgreSQL compatible)
    * MySQL workload. You want a faster MySQL engine. Better performance. Fully managed. Your IT management doen't have the time and resources for maintenance. High Availability. Low latency
  * Redshift
    * Columnar database: When you have aggregation for your data
    * Data warehouse/ Petabyte database
    * Data in redshift is stored column wise. SQLoriented databases-- Data is stored on disks row wise. Makes it easier to search.
    * You can use Business Intelligence tools with the data. 
    * Database recovery- You can enable cross region snapshots. You can restore the data into a new cluster with the snapshot data. 
   
