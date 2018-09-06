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
 ### Compute
 
 #### Instance pricing
   * On-Demand Instances
     * Good for development and test environments. When you want instances for a certain period of time. 
   * Spot Instances
     * Batch processing activities. Activities that can survive an interruption. 
   * Reserved Instances
     * When you know you need servers 24*7 and all throughout the year, you can save cost by purchasing Reserved capacity. 
   * Dedicated Instances
     * Runs on hardware that is dedicated for the customer. But if the customer has multiple AWS accounts, then instances can share the same hardware. 
   * Dedicated Hosts- You have control over the physical server. If you have a third party application wherein the licensing is based on the number of cores. Of if your security policy mandes that you cannot share infrastructure. 
#### Serverless Compute
  * AWS Lambda
    * You don't have to manage the infrastructure
    * only get billed for how much you use.
    * Easy to port existing code and save on costs.
    * Normally used in conjunction with API Gateway
    * You can create API's which can be invoked by customers.
    * The API'can then call Lambda function 
#### Elastic Container Services
    * Used for orchestration
    * Instead of you installing orchestration services like Kubernetes on EC2, let the ECS manage it for you.
    * You define type that gets the images
    * Deploys the containers on Instances
    * You can then access via a Service
    * You also have autoscaling capabilities
### Elasticity and Scalability
  * For Elasticity- Use a load balancer
  * For scalability use an AutoScaling Group 
  * You can launch instances in an AutoScaling group based on different metrics.
  * In addition to the normal metrics such as CPU utilization, you can define your custom metrics. 
#### Autoscaling Policies
  * Scheduled Scaling Policy
    * Promotional event- You need to ensure infrastructure is scaled before the event
    * Team that experiences performance issues only at a certain time- Heavy utilization early in the morning. 
  * Dynamic Scaling Policy 
    * Scale dynamically based on metrics 
    * If the CPU utilization is high
    * Based on custom metrics
  * Cool down timing period 
    * 3 servers
    * Performance starts taking a hit. You have a cloudwatch alarm that gets triggered at 9:00
    * Autoscaling spins up 2 more servers. Total of 5 servers.
    * Now new software needs to be installed. Scripts need to run to ensure the new servers can start accepting requests. This takes 10 minutes.
    * But let's say in 5 minutes, again your cloudwatch alarms have been triggered and Autoscaling again starts spinning up new servers.
    * So you have not allowed for the current infrastructure of 5 serveres to settle down. 
    * Cool down timer- Increase the timing period to allow more time for the infrastructure to settle down. The cloudwatch alarms if triggered can be ignored during this period. 
   
