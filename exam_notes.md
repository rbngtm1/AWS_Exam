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
  * AWS RDS, DynamoDB, Aurora and Redshift.
