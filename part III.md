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
