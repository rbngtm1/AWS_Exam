#### A consulting firm repeatedly builds large architecture for their customers using AWS resources from several AWS services including IAM, Amazon EC2, Amazon RDS, DynamoDB and Amazon VPC. The consultants have architecture diagrams for each of their architectures, and are frustrated that they cannot automatically create their resources. Service that will immediately benefit to the organization is:
  * AWS Cloudformation. 
    * Cloudformation enables consultants to user their architecture diagrams to construct CloudFormation templates. 
    * Cloudformation is a service that helps you model and set up your Amazon Web Service resources so that you can spend less time managing those resources and more time focusing on your application that run on AWS. You can create a template that describes all the AWS resources that you want (like Amazon EC2 instance or Amazon RDS DB instances), and AWS CloudFormation takes care of provisioning and configuring those resources for you. 
    
#### An organization hosts a multi-language website on AWS, which is served using CloudFront. Language is specified in the HTTP request as shown below:
  * http://d11111f8.cloudfront.net/main.html?language=de
  * http://d11111f8.cloudfront.net/main.html?language=en
  * http://d11111f8.cloudfront.net/main.html?language=es
  
  **How should AWS Cloudfront be configured to deliver cache data in the correct language?**
   * Based on query string parameter
#### A Solution Architect is designing a shared service for hosting containers from several customers on Amazon ECS. These containers will use several AWS service. A container from one customer should not be able to access data from another customer. Which of the below solutions should the architect use to meet these requirements?
  * IAM roles for tasks
    * With IAM roles for Amazon ECS tasks, you can specify an IAM role to be used by the containers in a task. Applications are required to sign their AWS API requests with AWS credentials, and this feature provides a strategy to manage credentials for your application's use. This is similar to how Amazon EC2 instance profiles provide credentials to EC2 instances. 
  
#### There is a requirement to host a database on a EC2 Instance. It is also required that the EBS volume should support 12,000 IOPS. Which Amazon EBS volume type meets the performance requirement.
  * EBS Provisioned IOPS SSD
     * For high performance and high requirement as in this case, the ideal choice would be EBS Provisioned IOPS SSD. Suitable for large database workloads, such as MongoDB, Cassandra, Microsoft SQL Server, MySQL, PostgreSQL, Oracle.-- Volumesize (4GiB - 16TiB), Max IOPS/Volume = 32,000, Processing data = 500MiB/s
     * Genereal purpose SSD(gp2), on the other hand, is recommended for most wide variety of workloads, system boot volumes, virtual desktops, low-latency interactive apps, development and test environment.-- VolumeSize (1GiB - 16TiB), Max IOPS/Volume= 10,000, Processing data = 160MiB/s

#### Development teams in your organization use S3 buckets to store log files for various applications hosted in AWS development environments. The developers intend to keep the logs for a month for troubleshooting purposes, and subsequently purge the logs. What feature will enable this requirement?
  * Configuring lifecycle rules on the S3 buckets. 
#### A legacy application need a proprietary file system. Which of the following can be used to store data accessibile by an EC2 instance?
  * AWS EFS
    * Amazon Elastic file system(EFS) provides simple, scalable file storage for use with Amazon EC2 instances in the AWS Cloud. Amazon EFS is easy to use and offers a simple interface that allows you to create and configure file systems quickly and easily. With Amazon EFS, storage capacity is elastic, growing and shrinking automatically as you add and remove files, so your application have the storarge they need, when they need it. 
    * When mounted on Amazon EC2 instances, an Amazon EFS file system provides a standard file system interface and file system access semantics, allowing you to seamlessly integrated EFS with your existing application and tools. Multiple Amazon EC2 instances can access an Amazon EFS file system at the same time.
#### What options can be used to host an application that uses NGINX and is scalable at any point in time?
  * AWS EC2
  * AWS Elastic Beanstalk
    * NGINX is an open source software for web serving, reverse proxying, caching, load balancing, etc. NGINX can be hosted in EC2 instance through a series of clear steps--Launch an EC2 instance through the console. SSH into the instance and use the command yum install -y nginx to install nginx. Also, make sure that it is configured to restart automatically after a reboot. 
    * It can also be installed with an ELastic Beanstalk service. To enable NGINX proxy server with your Tomcat application, you must add a configuration file to .ebeextentions in the application source bundle that you upload to Elastic Beanstalk. 
#### A million images are required to be uploaded to S3. What option ensures optimal performance in this case?
  * Use a hexadecimal hash for the prefix
    * One way to introduce randomeness to key names is to add a hash string as prefix to the key name. 
#### There is a requirement to get the IP addresses for resources accessed in a private subnet. Which of the following can be used  to fulfill this purporse?
  * VPC flow logs
    * VPC flow logs is a feature that enables you to capture your information about the IP traffic going to and from network interfaces in your VPC. 
#### A database is required for a Two-Tier application. The data would go through multiple schema changes. The database needs to be durable, and changes to the database should not result in database downtime. Which of the following is best option for downtime?
  * AWS Aurora
#### A Redshift cluster currently contains 60TB of data. There is a requirement that a disaster recovery site is put in place in a region located 600km away. Which of the following solutions would help ensure that this requirement is fulfilled?
  * Enable cross-region snapshots for the redshift cluster.
#### A company is using a Redshift cluster to store their data warehouse. There is a requirement from the internal IT Security team to encrypt data for the Redshift database. How can this be achieved?
  * Use AWS KMS Customer Default master key. 
    * Amazon Redshift uses a hierarchy of encryption keys to encrypt the database. You can use either AWS Key Service Management Service(KMS) or a hardware security  module(HSM) to manage the top-level encryption keys in this hierarchy. 
#### There is a requirement for Block-level storage to store 500GB of data. Data Encryption is also required. Which of the following can be used in such a case?
  * AWS EBS Volumes. 
    * AWS EBS is a Block-level storage Service.
#### An application requires an EC2 instances for continuous batch processing activities requiring a minimum throughput of 500MiB/s. Which of the following is the best option for this?
  * EBS Throughput Optimized
    * EBS Throughput Optimized HDD(st1) is low cost HDD volume designed for frequently accessed, throughput intensive workloads. Used for streaming, big data, data warehouses, log processes. Volumesize (500GiB - 16TiB), Max IOPS/Volume = 500, Processing data = 500MiB/s
    * Cold HDD(sc1), on the other hand, is lowest cost HDD volume designed for less frequently accessed workloads. Volumesize (500GiB - 16TiB), Max IOPS/Volume = 250, Processing data = 250MiB/s
    
#### An application needs to access data in another AWS account in the same region. Which of the following can be used to ensure that the data can be accessed as required?
  * Use VPC Peering between both accounts.
    * A VPC Peering connection is the networking connection between two VPCs that enables you to route traffic between them privately. Instances in either VPC can communicate with each other as if they are within the same network.
    * You can create a VPC Peering connection between your own VPCs, with a VPC in another AWS account, or with a VPC in different AWS Region. 
#### An application consists of following architecture:
  * a. An EC2 instances in multiple AZ's behind an ELB.
  * b. The EC2 instances are launched via an AutoScaling Group. 
  * c. There is a NAT instance which is used so that instances can download updates from the internet. 
  **
  Which of the following is a bottleneck in the architecture?
  * NAT Instance
    * Since there is only one NAT instance, this is a bottleneck for the architecture. For high availability, launch NAT instances in multiple Availability Zones and make it as part of an Auto Scaling Group.
#### There is a requirement to host a database application having a lot of resource-intensive reads and writes. Which of the following is the best storage option to ensure that the data is persistent?
  * EBS Provisioned IOPS
#### An application send images to S3. The metadata for these images needs to be saved in persistent storage and is required to be indexed. Which of the following can be used for the underlying metadata storage?
  * AWS DynamoDB
    * The most efficient storage mechanism for just storing metadata is DynamoDB. DynamoDB is normally used in conjunction with the S3. So, after storing images in S3, you can store their metadata in DynamoDB. You can also create secondary indexes for DynamoDB Tables. 
#### An application hosted on EC2 Instances has its promotional campaign due to start in 2 weeks. There is a mandate from the management to ensure that no performance problems are encountered due to traffic growth during this time. Which of the following must be done to the Auto Scaling Group to ensure this requirement is fulfilled?
  * Configure Dynamic Scaling and use Target tracking scaling Policy. 
    * If scaling is based on a metric, which is an utilization metric that increases or decreases proportionally to the number of instances in the Auto Scaling group, it's recommeded to use target tracking policy instead. 
    * Scheduled Scaling is not a suitable option in here because you cannot predict the load changes and how long you need to run. In this scenario question, we are not sure about actual traffic, we only know there will be heavy traffic and we don't have any history to predict it either. 
#### Currently a company makes use of EBS snapshots to back up their EBS Volumes. As a part of the business continuity requirement, these snapshots need to be made available in another region. How can this be achieved?
  * Create Snapshot and copy the snapshot to new region. 
#### A company has an application hosted in AWS. This application consists of EC2 instances which sit behind an ELB with EC2 instances. The following are the requirements from an administrative perspective:
  * a. Ensure notifications are sent when the read requests go beyond 1000 requests per minute.
  * b. Ensure notifications are sent when the latency goes beyond 10 seconds. 
  * c. Any API activity which calls for sensitive data should be monitored 
**Which of the following can be used to satisfy these requirements?**
  * Use CloudTrial to monitor the API Activity
  * Use CloudWatch metrics for the metrics that needs to be monitored as per the requirement and set up an alarm activity to send out notifications when the metric reaches the set threshold limit. 
#### There is a requirement for an iSCSI device and the legacy application needs local storage. Which of the following can be used to meet the demands of the application?
  * Configure Storage Gateway Stored Volume
    * In cached mode, your primary data is written to S3, while retaining your frequently accessed data locally in a cache for low-latency access. 
    * In the stored mode, your primary data is stored locally and your entire database is available for low-latency access while asychronously backed up to AWS.
#### There is a requirement for EC2 Instances in a private subnet to access an S3 bucket. It is required that the traffic doesnot traverse to the Internet. Which of the following can be used to fulfill the requirement?
  * VPC Endpoint
    * A VPC Endpoint enables you to privately connect your VPC to supported AWS services and VPC endpoint services powered by PrivateLink without requiring an internet gateway, NAT device, VPN connection, or AWS Direct Connect connection. Instances in your VPC do not require public IP addresses to communicate with resources in the service. 
#### There is a website hosted in AWS that might get a lot of traffic over the next couple of weeks. If the application faces the disaster, which of the following can be used to reduce potential disruption to users in case of issues?
  * Use Route53 to route to static website. 
    * In a disaster recovery scenario, the best choice out of all given options is to divert the traffic to a static website. 
#### A database hosted using the AWS RDS service is getting a lot of database queries and has now become a bottleneck for the associating application. What action will ensure that the database is not a performance bottleneck?
  * Setup ElastiCache in front of the database. 
    * ElastiCache is an in-memory solution which can be used in front of a database to cache the common queries issued against the database. This can reduce the overall load on the database. 
#### You require the ability to analyze a customer's clickstream data on a website so they can do behavioral analysis. Your customer needs to know what sequence of pages and ads their customer clicked on. This data will be used in real time to modify the page layouts as customer click through the site to increase stickiness and advertising click-through. Which option meets the requirements for captioning and analyzing this data?
  * Push web clicks by session to Amazon Kinesis and analyze behaviour usin Kinesis workers. 
    * Kinesis Data Streams can continuously capture and store terabytes of data per hour from hundreds of thousands of sources such as website clickstream, financial transactions, social media feeds, IT logs, and location-tracking events. 
#### A company has an infrastructure that consists of machines which keep sending log information every 5 minutes. The number of these machines can run into thousands and it is required to ensure that the data can be analyzed at a later stage. Which of the following would help in fulfilling this requirement?
  * Use Kinesis Firehose with S3 to take the logs and store them in S3 for further processing.
    * Kinesis Firehose helps capture, transform, and load streaming data into Amazon S3, Redshift, ElastiSearch Service, and Splunk.
#### A company is planning to use Docker containers and necessary container orchestration tools for their batch processing requirements. There is a requirement for batch processing for both critical and non-critical data. Which of the following is the best implementation step for this requirement, to ensure that cost is effectively managed?
  * Use ECS for container orchestration and a combination of Spot and Reserved Instances for the underlying Instances.
    * The Elastic Container Service from AWS can be used for container orchestration. Since there are both critical and non-critical loads, one can use Spot instances for the non-critical workloads for ensuring cost is kept at minimum. 
#### A company hosts 5 web servers in AWS. They want to ensure that Route53 can be used to route user traffic to random web servers when they request for the underlying web application. Which routing policy should be used to fulfill this requirement?
  * Multivalue Answer
    * If you want to route traffic appropriately randomly to multiple resources such as web servers, you can create one multivalue answer record for each resource and, optionally, associate an Amazon Route 53 health check with each record. 
#### A customer wants to create a stream of EBS Volumes in AWS. The data on the volume is required to be encrypted at a rest. How can this be achieved?
  * Use KMS to generate encryption keys which can be used to encrypt the volume. 
#### A company has a requirement to store 100TB of data to AWS. The data will be exported using AWS Snowball and needs to then reside in a database layer. The database should have the faculty to be queried from a business intelligence application. Each item is roughly 500KB in size. Which of the following is an ideal storage mechanism for the underlying data layer?
  * AWS RedShift
    * Amazon Redshift is a fully managed, petabyte scale datawarehouse service in the cloud. You can start with just a few hundred GB of data and scale to a petabyte or more. This enables you to use the data to acquire new insights for your business and customers. 
    * The first step is to create a data warehouse is to launch a set of nodes, called an Amazon Redshift Cluster. After you provision your cluster, you can upload your data set and then perform data analysis queries. Regardless of the size of the datasets, Amazon Redshift offers fast query performance using the same SQL-based and business intelligence application that you use today. 
    * **DynamoDB** is not a better option for above scenario because the maximum item size in DynamoDB is **400KB**.
    * **AWS RDS** is not a better option because, with RDS we can create MySQL, MariaDB, SQL Server, PostgreSQL, and Oracle RDS DB instance with up to **16 TiB of storage**
    * **AWS Aurora** is not a better option because Aurora supports **64TB of data**.
#### Your company currently has a set of EC2 instances hosted in AWS. The states of these instances need to be monitored and each stage needs to be recorded. Which of the following can help fulfill this requirement. 
  * Use CloudWatch Events to monitor the stage change of the events.
  * Use AWS Lambda to store a change record in a DynamoDB table. 
#### A company has setup an application in AWS that interacts with DynamoDB. It is required that when an item is modified in a DynamoDB table, an immediate entry is made to the associating application. How can this be accomplished?
  * Use DynamoDB streams to monitor the changes to the DynamoDB table.
  * Trigger a Lambda function to make an associated entry in an application as soon as the DynamoDB streams are modified.
    * A DynamoDB stream is an ordered flow of information about changes to items in an Amazon DynamoDB table. When you enable stream on table, DynamoDB captures information about every modification to data items in the table. 
    * **Forex:** Consider a mobile gaming app that writes to a Score table. Whenever the top score of the Score table is updated, a corresponding stream record is written to the table's stream. This event could then trigger a Lambda function that posts a Congratulation message on a Social media network handle.
    

  
