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
#### An application currently uses AWS RDS MySQL as its data layer. Due to recent performance issues on the database, it has been decided to seperate the querying part of application by setting up a seperate reporting layer. Which of the following additional steps could also potentially assist in improving the performance of the underlying database?
  * Make use of Read Replicas to setup a secondary read-only database.
    * Amazon RDS read replicas provide enhanced performance and durability for database(DB) instances. This feature makes it easy to elastically scale out beyond the capacity constrants of a single DB instance for read-heavy database workloads. You can create one or more replicas of a given source DB instance and serve high-volume application read traffic from multiple copies of your data, thereby increasing aggregate read throughput
#### A company is asking its developers to store application logs in an S3 bucket. These logs are only required for a temporary period of time after which, they can be deleted. Which of the following steps can be used to effectively manage this?
  * Use S3 Lifecycle Policies to manage the deletion
#### An application running on EC2 instances processes sensitive information stored in Amazon S3. This information is accessed over the Internet. The security team is concerned that the Internet connectivity to Amazon S3 could be a security risk. Which solution with resolve the security concern?
  * Access the data through a VPC endpoint for Amazon S3
    * A VPC endpoint enables you to privately connect your VPC to supported AWS services and VPC endpoints services powered by PrivateLink without requiring an internet gateway, NAT device, VPN connection, or AWS Direct Connect connection. Instances in your VPC do not require public IP addresses to communicate with resources in the service. 
#### You have set up a Redshift cluster in AWS and are trying to access it, but are unable to do so. What should be done so that you can access the Redshift Cluster?
  * Change the security group of the cluster
    * When you provision an Amazon Redshift cluster, it is locked down by default so nobody has access to it. To grand other users inbound access to an Amazon Redshift cluster, you associate the cluster with a security group.
#### You have a web application hosted on a EC2 instances in AWS which is being accessed by users across the globe. The Operations team has been receiving support requests about extreme slowness from users in some regions. What can be done to the architecture to improve the response time of these users?
  * Place the EC2 Instance behind CloudFront
    * Amazon CloudFront is a web service that speeds up distribution of your static and dynamic web content, such as .html, .css, .js, and images files, to your users. CloudFront delivers your content through a worldwide network of data centers called edge locations. 
#### Currently, you have a NAT Gateway defined for your private instances. You need to make the NAT Gateway highly available. How can this be accomplished?
  * Create a NAT Gateway in Another Availability Zone
#### A company wants to have a fully managed data store in AWS. It should be a compatible MySQL database, which is an application requirement. Which of the following database can be used for this purpose?
  * Amazon Aurora
    * is a fully managed, MySQL and PostgreSQL compatible, relational database engine
#### A Solution Architect is designing an online shopping application running in a VPC on EC2 instances behind an ELB Application. The instances run in a Auto Scaling group across multiple Availability Zones. The application tier must read and write data to a customer database cluster. There should be no access to the database from the Internet, but the cluster must be able to obtain software patches from the Internet. Which VPC design meets these requirements?
  * Public subnets for the application tier and NAT Gateway, and private subnets for the database cluster.
#### A company has an application that stores images and thumbnails for images on S3. While the thumbnail images need to be available for download immediately, the images themselves are not accessed that frequently. Which is the most cost-efficient storage option to store images that meets these requirements?
  * Amazon S3 standard Infrequent Access 
#### You have an application hosted on AWS consisting of EC2 Instances launched via an AutoScaling Group. You notice that the EC2 Instances are not scaling up on demand. What checks can be done to ensure that the scaling occurs as expected?
  * Ensure that the right metrics are being used to trigger the scale out.
    * If your scaling events are not based on the right metrics and donot have the right threshold defined, then the scaling will not occur as you want it to happen.
#### You have an application hosted in AWS that writes images to an S3 bucket. The concurrent number of users on the application is expected to reach around 10,000 with approximately 500 reads and writes expected per second. How should the architecture maximize Amazon S3 performance?
  * Prefix each object name with a random string
    * If the request rate is high, you can use hash keys or random string to prefix the object name. 
#### A company has a set of EBS Volumes that need to be catered to in case of a disaster. How can one achieve this in an efficient manner using the existing AWS services?
  * Use EBS Snapshots to create the volume in another region.
#### Your company currently has a web distribution hosted using the AWS CloudFront service. The IT Security department has confirmed that the application using the web distribution now falls under the scope of PCI compliance. Which of the following steps needs to be carried out to ensure that the compliance objectives are met? 
  * Ensure CloudFront access logs
  * Capture requests that are sent to the CloudFront API
    * If you run PCI or HIPPA compliant workloads on AWS shared responsibility model, it is recommended that you log your CLoudFront usage data for the last 365 days for future audition process. To log usage data, follow above 2 options.
#### Your company has a set of EC2 instances hosted in AWS. There is a mandate to prepare for disaster and come up with the necessary disaster recovery procedures. Which of the following would help in mitigating the effects of a disaster for the EC2 Instances?
  * Use AMIs to recreate the EC2 Instances in another region.
    * You can create an AMI from the EC2 instances and then copy them to another region. In case of a disaster, an EC2 instance can be created from the AMI. 
#### A company currently hosts a Redshift cluster in AWS. For security regions, it should be ensured that all traffic from and to the Redshift cluster doesn't go through the Internet. Which of the following features can be used to fulfill this requirement in an efficient manner?
  * Enable Amazon Redshift Enhanced VPC Routing.
    * When you use Amazon Redshift Enhanced VPC Routing, Amazon Redshift forces all **Copy** and **Unload** traffic between your cluster and your data repositories throught your Amazon VPC.
    * If Enhanced VPC is not enabled, Amazon Redshift routes traffic through the internet, including traffic to other services within the AWS network. 
#### A company has a set of Hyper-V machines and VMware virtual machine. They are now planning on migrating these instances to the AWS cloud. Which of the following can be used to move this resources to AWS Cloud?
  * Use the VM Import Tools
    * You can import Windows and Linux VMs that use VMware ESX or Workstation, Microsoft Hyper-V, and Citrix Xen virtualization formats.
#### An architecture consists of following:
  * a. primary and secondary infrastructure hosted in AWS.
  * b. Both infrastructure comprise ELB, AutoScaling and EC2 resources.
  **

  How should Route 53 be configured to ensure proper failover in case the primary infrastructure were to go down?
  * Configure a failover routing policy.
    * You can create an active-passive failover configuration by using failover records. Create a primary and a secondary failover record that have the same name and type, and associate a health check with each. 
#### A company requires to provision test environment in a short duration. Also required is an ability to tear them down easily for cost optimization. How can this be achieved.
  * Use CloudFormation templates to provision the resources accordingly. 
    * AWS CLoudFormation provides templates that you can use to create AWS resources and provision them in an orderly and predictable fashion. This can be useful for creating short-lived environments, such as test environments.
#### A company stores its log data in S3 bucket. There is current need to have search capabilities available for the data in S3. How can this be achieved in an efficient and ongoing manner?
  * Use an AWS Lambda function which gets triggered whenever the data is added to the S3 bucket.
  * Load the data into Amazon ElasticSearch.
    * AWS ELasticSearch provides full search capabilities and can be used to log files stored in S3 buckets. 
#### A company wants to self-manage a database environment. Which of the following should be adopted to fulfill this requirement?
  * Create an EC2 Instance and install the database service accordingly. 
#### A company wants to have a 50Mbps dedicated connection to its AWS resources. Which of the below services can help fulfill this requirement?
  * Direct Connect
    * AWS Direct Connect makes it easy to establish a dedicated network connection from your premises to AWS. Using AWS DirectConnect, you can establish private connectivity between AWS and your datacenter, office, or colocation environment, which in many cases can reduce your network costs, increase bandwidth throughput, and provide a more consistent network experience than Internet-based connections.
#### A company is building a Two-Tier web application to serve dynamic transaction-based content. The Data Tier uses an Online Transactional Processing (OLTP) database. What should you leverage to enable an elastic and scalable Web Tier?
  * ELastic Load Balancing, Amazon EC2, and AutoScaling
#### A customer planning on hosting an AWS RDS instance, needs to ensure that the underlying data is encrypted. How can this be achieved? 
  * Ensure that the right instance class is chosen for the underlying instance. 
  * Encrypt the database during creation 
    * Encryption for the database can be done during the creation of the database. Also, you need to ensure that the underlying instance type supports DB encryption.
#### Your Operations department is using an incident based application hosted on a set of EC2 instances. These instances are placed behind an Auto Scaling Group to ensure the right number of instances are in place to support the application. The operations department has expressed dissatisfaction with regard to poor application performance at 9:00 AM each day. However, it is also noticed that the system performance returns to optimal at 9:45 AM. What can be done to ensure that this issue gets fixed?
  * Add a Scheduled Scaling Policy at 8:30 AM.
    * Scaling based on a schedule allows you to scale your application in response to predictable load changes. 
#### Your company currently has data hosted in an Amazon Aurora MySQL DB. Since this data is critical, there is a need to ensure that it can be made available in another region in case of a disaster. How can this be achieved?
  * Create a Read Replica for the database.
    * You can create an Amazon Aurora MySQL DB cluster as a Read Replica in a different AWS Region than the source DB cluster. Taking this approach can improve your disaster recovery capabilities, let you scale read operations into a region that is closer to your users, and make it easier to migrate from one region to another. 
#### A company has a set of EC2 Linux based instances hosted in AWS. There is a need to have a standard file interface for files to be used across all Linux based instances. Which of the following can be used for this purpose?
  * Consider using AWS EFS
#### Your company is planning on using Route 53 as the DNS provider. There is a need to ensure that the company's domain name points to an existing CloudFront distribution. How can this be achieved?
  * Create an Alias record which points to the CloudFront distribution.
#### A company needs to extend their storage infrastructure to the AWS Cloud. The storage needs to be available as iSCSI devices for on-premises application servers. Which of the following would be able to fulfill this requirement?
  * Use the AWS Storage Gateway-cached volumes service.
    * By using cached volumes, you can use Amazon S3 as your primary data storage, while retaining frequently accessed data locally in your storage gateway. 
#### Your company has a set of application that make use of Docker containers used by the Development team. There is a need to move these containers to AWS. Which of the following methods could be used to set up these Docker containers in a seperate environment in AWS?
  * Create an Elastic Beanstalk environment with the necessary Docker containers. 
    * Elastic Beanstalk supports the deployment of web applications from Docker containers. 
#### A company currently hosts their architecture in the US region. They now need to duplicate this architecture to the Europe region and extend the application hosted on this architecture to the new region. In order to ensure that users across the globe get the same seamless experience from either setups, what among the following needs to be done?
  * Create a Geolocation Route 53 Policy to route the policy based on the location.
    * Geolocation routing lets you choose the resources that serve your traffic based on the geographic location of your users, meaning the location that DNS queries originate from. 
#### A customer has an instance hosted in the AWS Public Cloud. The VPC and subnet used to host the instance have been created with the default settings for the Network Access Control Lists. An IT Administrator needs to be provided secure access to the underlying instance. How can this be accomplished?
  * Ensure that the security group allows Inbound SSH traffic from the IT Administrator's Workstation
    * Since, security group are stateful, we do not have to configure outbound traffic. What enters the inbound traffic is allowed in the outbound traffic too. 
    * The default network ACL is configured to allow all traffic to flow in and out of the subnets to which it is associated. Since the question does not mention that it is a custom VPC we would assume it be the default one. 
#### A company has an on-premises infrastructure which they want to extend to the AWS Cloud. There is a need to ensure that communication across both environments is possible over the Internet. What would you create in this case to fulfill this requirement?
  * Create a VPN connection between the on-premises and the AWS Environment
    * AWS Direct connection between the on-premises and AWS Environment is not a better option because the question says **"Over the internet"** Direct connect does not involve the Internet.
    * VPN connection can be configured in minutes and are good solution if you have an immediate need, have low to modest bandwidth requirement, and can tolerate the inherent variability in Internet-based connectivity. 
#### A company wants to build a brand new application on the AWS Cloud. They want to ensure that this application follows the Microservices architecture. Which of the following services can be used to build this sort of architecture?
  * AWS Lambda
  * AWS ECS (Elastic Container Service)
  * AWS API Gateway: Serverless component for managing access to APIs.
#### A CloudFront distribution is being used to distribute content from an S3 bucket. It is required that only a particular set of users get access to certain content. How can this be accomplished?
  * Create CloudFront signed URLs and then distribute these URLs to these users. 
#### Your Development team wants to start making use of EC2 Instances to host their Application and Web servers. In the space of automation, they want the Instances to always download the latest version of the Web and Application servers when they are launched. As an architect, what would you recommend for this scenario?
  * Ask the Development team to create scripts which can be added to the Users Data section when the instance is launched. 
#### Your company has an application that takes care of uploading, processing and publishing videos posted by users. The current architecture for this application includes the following:
* a. A set of EC2 instances to transfer user uploaded videos to S3 buckets
* b. A set of EC2 worker processes to process and publish the videos.
* c. An Auto Scaling Group for the EC2 worker processes.
Which of the following can be added to the architecture to make it more reliable?
  * Amazon SQS
    * is used to decouple systems. It can store requests to process videos to be picked up by the worker processes.
#### You have a business-critical two-tier web application currently deployed in 2 Availability Zones in a single region, using Elastic Load Balancing and Auto Scaling. The app depends on synchronous replication at the database layer. The application needs to remain fully available even if one application AZ goes offline and if Auto Scaling cannot launch new instances in the remaining AZ. How can the current architecture be enhanced to ensure this?
  * Deploy in 3 AZ with Auto Scaling minimum set to handle 50 per cent peak load per zone. 
    * Bcoz, we need to maintain 100% availability. 
#### You have the following architecture deployed in AWS:
* a. A set of EC2 instances which sit behind an ELB
* b. A database hosted in AWS RDS.
**** 
Of late, the performance on the database has been slacking due to a high number of read requests. Which of the following can be added to the architecture to alleviate the performance issue?
  * Use ElastiCache in front of the database.
    * ElastiCache is an in-memory-cache which can be used to cache common read requests.
#### An application is currently hosted on an EC2 Instances which has attached EBS Volumes. The data on these volumes is frequently accessed. But after a duration of a week, the documents needs to be moved to infrequent access storage. Which of the following EBS volume type provides cost efficiency for the moved documents?
  * EBS Cold HDD(sc1)
    * Most cost efficient
#### A company is running three production web server reserved EC2 instances with EBS-backed root volumes. These instances have a consistent CPU load of 80%. Traffic is being distributed to these instances by an Elastic Load Balancer. They also have production and development Multi-AZ RDS MySQL databases. What recommendation would you make to reduce cost in this environment without affecting availabilty of mission-critical systems?
  * Consider not using a Multi-AZ RDS deployment for the development database. 
    * Multi-AZ databases are better for production environments rather than for development environments, so you can reduce costs by not using these for development environments.
#### An application consists of a couple of EC2 Instances. One EC2 Instance hosts a web application and the other Instance hosts the database server. Which of the following changes can be made to ensure high availability of the database layer?
  * Have another EC2 instances in the another Availability Zone with replication configured.
    * To ensure high availability, have the EC2 instances in another Availability Zone, so even if one goes down, the other one will still be available. 
#### You are designing an architecture on AWS with disaster recovery in mind. Currently the architecture consists of an ELB and underlying EC2 Instances in a primary and secondary region. How can you establish a switchover in case of failure in the primary region?
  * Use Route 53 Health Checks and then do a failover.
    * If you have multiple resources that perform the same function, you can configure DNS failover so that Route 53 will route your traffic from an unhealthy resources to a healthy resource. 
#### Your company currently has an infrastructure hosted On-premises. You have been requested to devise an architecture on AWS for migrating some of the On-premise components. A current concern is the data storage layer. Minimum administrative overheads are also required for the underlying infrastructure in AWS. Which of the following would be included in your proposed architecture?
  * Use DynamoDB to store data in tables
  * Use the Simple Storage Service to store data
#### Currently, you're helping design and architect a highly available application. After building the initial environment, you discover that a part of your application doesnot work correctly until port 443 is added to the security group. After adding port 443 to the appropriate security group, how much time will it take before the changes are applied and the application begins working correctly?
  * Changes apply instantly to the security group, and the application should be able to respond to 443 requests.
    * Some systems for setting up firewalls let you filter on source ports. Security groups let you filter only on destination ports.
    * When you add or remove rules, they are automatically applied to all instances associated with the security group.
#### A customer has a single 3-TB volume on-premise that is used to hold a large repository of images and print layout files. This repository is growing at 500GB a year and must be presented as a single logical volume. The customer is becoming increasingly constrained with their local storage capacity and wants an offsite backup of this data, while maintaining low-latency access to their frequently accessed data. Which AWS Storage Gateway configuration meets the customer requirements?
  * Gateway-Cached Volumes with snapshots scheduled to Amazon S3
    * Gateway-cached volumes let you use Amazon S3 as your primary data storage while retaining frequently accessed data locally in your storage gateway. 
  
 
