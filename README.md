# Getting Started for AWS Certification

## Fundamental Key Areas to focus:
  * Object storage
  * Database Services offered
  * Networking in Cloud
  * Backups and Restore Mechanism
  * AWS Managed services
  * Compute Engines and Serverless
  * Containerized Applications hosting
  * Authorization and authentication
  * Logging and Monitoring in AWS
  * Firewalls
  * Content Delivery
  * How integrations among different native services works

## Storage
### Object level Storage
  * S3 and Glacier
    * S3 for high durability and availability
    * In case of disaster recovery, you need to enable Cross Region Replication.
    * Glacier is used to archive storage. Cost effective option. retrieval time is generally 3-5 hours.
      * Expedited retrieval-minutes-Pay extra.
    * How to transfer data to Glacier
      * API
      * Lifecycle policies for S3

### Block Level Storage
  * Elastic Block Storage Volumes: don't have the save level of durability as S3
  * In an AZ, they are replicated to multiple devices. But if the AZ fails, the volume is not usable.
    * You can safeguard your data by:
      *Creating EBS Snapshots and copying it to another region for disaster recovery purposes
#### EBS Volumes types:
  * General Purpose SSD
    * If you have EC2 Instance, web server and predictable workloads. This option is  cost effective volume type
  * Provisioned IOPS
    * If you have EC2 instance, database server, resource intensive, high number of input and output operations
      * In database server, select statement is for (Read operations-- search for data ) and Update, Insert and Delete statements are (Write Operations)
      * As database needs to access volumes for read and write operations, I/O Controller(device)- takes a lot of strain for these operations. If the reads and writes are too much the controller just starts lagging behind.
  * Throughput Optimized HDD
    * If you have EC2 instance, Processing server, Processing videos for files with large size, streaming videos or high throughput.
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
    * Before creation of the table you can choose autoscaling for read and write throughputs.
  * Aurora(MySQL and PostgreSQL compatible)
    * MySQL workload. You want a faster MySQL engine. Better performance. Fully managed. Your IT management doesn't have the time and resources for maintenance. High Availability. Low latency
  * Redshift
    * Columnar database: When you have aggregation for your data
    * Data warehouse/ Petabyte database
    * Data in redshift is stored column wise. SQL oriented databases-- Data is stored on disks row wise. Makes it easier to search.
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
   * Dedicated Hosts- You have control over the physical server. If you have a third party application wherein the licensing is based on the number of cores / if your security policy mandates that you cannot share infrastructure.
#### Serverless Compute
  * AWS Lambda
    * You don't have to manage the infrastructure
    * only get billed for how much you use.
    * Easy to port existing code and save on costs.
    * Normally used in conjunction with API Gateway
    * You can create API's which can be invoked by customers.
    * The API's can then call Lambda function
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
    * So you have not allowed for the current infrastructure of 5 servers to settle down.
    * Cool down timer- Increase the timing period to allow more time for the infrastructure to settle down. The cloudwatch alarms if triggered can be ignored during this period.
 #### SQS Queue
   * Front end server-->SQS Queue-->AutoScaling Group Instances
   * can trigger scaling based on the number of message in the queue
   * so if the number of message are going beyond a point, then do a scale up operation
 #### ELastiCache
   * Front end server-->ElastiCache-->Database Server
   * Used when you want to cache frequently used data such as queries
   * Add ElastiCache in front of Database Server
 ### Security Practices
 #### AWS CLoudTrial
   * Used to monitor all API activity in an AWS Account.
   * Its good for compliance purpose
   * Also if you suspect any malicious activity in your account, check the Cloudtrial logs to see if an irregular API activity has been fired
   * Enable Cloudtrial for all regions. All future regions also get covered.
#### IAM
  * Use access with least privilege
  * Use Multi-Factor Authentication
  * Change the password policy.
  * Disable the root access keys
  * Buckets in S3
    * Manage via Bucket Policy
    * Use Bucket policy when giving access to external accounts
    * Use Pre-signed URL's if you don't want to give public access to the bucket. And you want a selection of users to get access to the objects.
 ****
   * IAM Roles
     * Used for secure access to resources
     * If you have an application on an EC2 Instance which needs to access a service like S3 or DynamoDB, then attach an IAM Role to the EC2 Instance with that specific privilege
     * Access Keys are OK to use during development time, but not in deployment or production
     * Even when using a Lambda function, if it accesses an external resource like DynamoDB or S3, ensure an IAM Role is attached to the Lambda function.
 #### Network Security
   * Nat instance or Nat gateway is used to allow instances in a private subnet to access the Internet.
   * If you want instances in a private subnet to access public resources like DynamoDB, S3, KMS, you have to use VPC Endpoints.
   * VPC Gateway Endpoints- S3 and DynamoDB
   * VPC Interface Endpoints- KMS
   * For KMS, Create a VPC Endpoint, attach it to the VPC and make the instances in the private subnet access the resources via the endpoint.
   * For Redshift, if you want the LOAD or COPY process to be private via a VPC, then enable Redshift Enhanced VPC Routing.
   * Monitoring IP addresses of traffic into your VPC- Use VPC Flow Logs
   * Use a bastion host for administrators to administer instances in the private subnet.
### Security for you VPC
#### Security Groups
  * Used to control traffic to your EC2 Instances
  * By default all traffic is denied
#### Network ACL's
  * When you want to limit traffic for a subnet
  * Remember this will effect all instances in that subnet
  * When you have malicious traffic from a set of EC2 Instances. Deny traffic based on the IP addresses.
### NAT
  * When would you use a NAT gateway
    * When your NAT Instance is becoming a bottleneck.
    * When you want completely managed service
  * When would you want to use a NAT instance
    * If you want to use the server as a proxy server as well
  * High Availability for NAT Instance
    * Create an Autoscaling Group
    * Have Multiple NAT instances in multiple AZ
  * High Availability for NAT Gateway
    * Have Multiple NAT gateway in multiple AZ
### Encryption
#### EBS Volumes
  * You can Enable Encryption for EBS Volumes using the Customer Key defined in the KMS service.
  * This needs to be done during the Volume creation time
  * If there is already an existing volume, you can use Operating System Level tools like BitLocker for Windows for Encryption
#### AWS RDS
  * You can also enable Encryption of the AWS Relational database service, Aurora. This will automatically also encrypt all logs and snapshots.
#### DynamoDB
  * You can also enable DynamoDB tables at table creation time
#### S3
  * Server Side Encryption
    * Using AWS Managed Keys
    * Using KMS Keys
    * Using Customer Managed Keys when uploading the object.
  * Client Side Encryption

#### Key Management Service
  * Fully managed Key Service from AWS
  * You can define Customer master keys
  * You can then use the keys for encryption
#### Cloud HSM
  * This when you want complete control of your keys
  * Sometimes required from a compliance perspective
  * It's a hardware device that can get access via an IP through your VPC.

### Performance for Services
   * DynamoDB acceleration (DAX) -- In-memory cache for DynamoDB. Fully managed. Millions requests per second for DynamoDB and you want to reduce latency to access to the DynamoDB table.
   * Amazon S3
     * Recommended practice if you're workload if you have more that 100 requests per second for objects in an S3 bucket.
     * Amazon S3 uses the key name to store the objects in multiple partitions. It then creates an index based on this.
     * For better performance, it is better that the keys are distributed across multiple partitions (use a random hash prefix as part of the key during the upload process.


 #### Network
   * Better Network Throughput - Use EC2 Instances with Enhanced Networking
   * Place Instances in a placement group for low latency between the instances. But the instances must be in the same AZ
   * Use EC2 Instances with the Instance type of EBS Optimized.
   * For connections between On-premise and AWS (hybrid IT Connectivity)- Use AWS Direct Connect
   * If you want secure connections between on-premise and AWS-- Use AWS Managed VPN Connections
   * For connections between On-premise and AWS with both low latency and Encryption-- First, create a Direct Connect Connection. Then use AWS VPN over the Direct Connect Connection.

 #### Operational Excellence
   * Always looks towards ease of use and Automation
     * Microservices based application with orchestration-- Choose the Elastic Container Service
     * Quickly provisioning development environments-- Use Elastic Beanstalk --Can also create custom Docker environments.
     * If you want to automate the provisioning of infrastructure -- Use Cloudformation
     * If you have configuration tools such as Chef and you want to use AWS, use the AWS OpsWork service.
   * Use Autoscaling for managing scalability
     * Web Tier
     * Application Tier
     * Proxy Servers
     * NAT Instances
     * Put the right conditions for Scale In and Scale Out
   * Managing Deployemts
     * Blue Green Deployments--Use Route 53 for managing traffic--Use the Weighted Routing Policy
     * Working with failure in mind--Using Route 53 failover policy to direct users to a static web site in S3.
     * If you have users across the globe and you have a web application: Use Cloudfront to distribute the traffic.
   * AWS Lambda for automation
     * Use case- used along with AWS Cloudwatch events to carry out tasks. If you see an instance has been compromised, you can use the events and Lambda to terminate the instance
     * Use case- storing objects in S3. The metadata for the object needs to be stored in DynamoDB. Add an S3 event, call a Lambda function. The function will read the object metadata and insert the data into DynamoDB.
