#### Currently, you're helping design and architect a highly available application. After building the initial environment, you discover that a part of your application doesnot work correctly until port 443 is added to the security group. After adding port 443 to the appropriate security group, how much time will it take before the changes are applied and the application begins working correctly?
  * Changes apply instantly to the security group, and the application should be able to respond to 443 requests.
    * Some systems for setting up firewalls let you filter on source ports. Security groups let you filter only on destination ports.
    * When you add or remove rules, they are automatically applied to all instances associated with the security group.
#### A customer has a single 3-TB volume on-premise that is used to hold a large repository of images and print layout files. This repository is growing at 500GB a year and must be presented as a single logical volume. The customer is becoming increasingly constrained with their local storage capacity and wants an offsite backup of this data, while maintaining low-latency access to their frequently accessed data. Which AWS Storage Gateway configuration meets the customer requirements?
  * Gateway-Cached Volumes with snapshots scheduled to Amazon S3
    * Gateway-cached volumes let you use Amazon S3 as your primary data storage while retaining frequently accessed data locally in your storage gateway. 
#### A company is planning to use the AWS ECS service to work with containers. There is a need for the least amount of administrative overhead while launching containers. How can this be achieved?
  * Use the Fargate launch type in AWS ECS
    * Fargate launch type allows you to run your containerized applications without the need to provision and manage the backend infrastructure. Just register your task definition and Fargate launches the container for you. 
#### You are responsible for deploying a critical application to AWS. It is required to ensure that the controls set for this application meet PCI compliance. Also, there is need to monitor web application logs to identify any malicious activity. Which of the following services can be used to fulfill this requirements.
  * Amazon CloudWatch Logs
  * Amazon CloudTrial
#### One plans on using SQS queues and AWS Lambda to leverage the serverless aspects of the AWS Cloud. Each invocation to AWS Lambda will send message to an SQS queue. In order for message to be sent, which of the following must be in place?
  * An IAM Role with the required permissions.
    * While working with AWS Lambda functions, if there is a need to access other resources, ensure that an IAM role is in place. 
#### You have enabled CloudTrial logs for your company's AWS account. In addition, the IT Security department has mentioned that the logs needs to be encrypted. How can this be achieved?
  * There is no need to do anything since the logs will already be encrypted.
    * By default, CloudTrial log files are encrypted using Amazon S3 server-side encryption (SSE). You can also choose to encrypt your log files with an AWS Key Management Service (KMS).
#### A company has set up their data layer in the S3. There are a number of requests which include read/write and updates to objects in an S3 bucket. Users sometimes complain that updates to an object are not being reflacted. The reason is:
  * Updates are being made to the same key for the objects. 
    * Updates made to objects in S3 follow an eventual consistency model. Hence, for object updates made to the same key, there can be a single delay when the updated object is provided back to the user on the next read request. 
#### You plan on hosting a web application consisting of a web server and a database server. These servers are going to be hosted on different EC2 Instances in different subnets in a VPC. Which of the following can be used to ensure that the database server only allows traffic from the web server?
  * Make use of Security Group
    * helps to control traffic into an EC2 Instance
 #### A company has a redshift cluster defined in AWS. The IT Operations team have ensured that both automated and manual snapshots are in place. Since the cluster is going to be run for a long duration of a couple of years, reserved instances have been purchased. There has been a recent concern on the cost being incurred by the cluster. Which of the following steps can be carried out to minimize the costs being incurred by the cluster?
   * Delete the manual snapshots.
     * Regardless of whether you enable automated snapshots, you can take a manual snapshot whenever you want. Amazon Redshift will never automatically delete a manual snapshot. Manual snapshots are retained even after you delete your cluster.
#### You currently have a set of Lambda functions which have business logic embedded in them. You want customers to have the ability to call these functions via HTTPS. How can this be achieved?
  * Use the API Gateway and provide integration with the AWS Lambda function
#### A company wants to deploy docker containers to the AWS Cloud. They also want a highly scalable service which can help manage the orchestration of these containers. Which of the following would be ideal for such a requirement?
  * Use the Amazon Elastic Container Service for Kubernetes (EKS)
    * Amazon EKS is a managed service that makes it easy to run Kubernetes on AWS without needing to install and operate your own Kubernetes cluster.
    
#### You create an Auto Scaling Group  which is used to spin up instances On Demand. As an architect, you need to ensure that the instance are pre-installed with a software when they are launched. What are the ways in which you can achieve this?
  * Add the scripts for the installation in the User data section
  * Create a golden image and then create a launch configuration
    * The User data section of an instance launch can be used to pre-configure software after the instance is initially booted.
    * You can create AMI or Golden Image with the already installed software, then create a launch configuration which can be used by Auto Scaling Group. 
#### You need to ensure that data stored in S3 is encrypted but do not want to manage the encryption keys. Which of the following encryption mechanism can be used in this case?
  * SSE- S3
#### You have a requirement for deploying an existing Java based application to AWS. There is a need for automatic scaling for the underlying environment. Which of the following can be used to deploy this environment in the quickes way possible?
  * Use the Elastic Beanstalk service to provision the environment. 
    * AWS ELastic Beanstalk is an easy-to-use service for deploying and scaling web applications and services developed with Java, .NET, PHP, Node.js, Python, Ruby, Go and Docker on familiar servers such as Apache, Nginx, Passenger, and IIS. 
#### You have been tasked with architecting an application in AWS. The architecture would consist of EC2, the Classic Load Balancer, Auto Scaling and Route 53. There is a directive  to ensure that BLue-Green deployments are possible in this architecture. Which routing policy could you ideally use in Route 53 for achieving Blue-Green deployment?
  * Weighted
    * Weighted routing lets you associate multiple resourcese with a single domain name(example.com) or subdomain name(hello.example.com) and choose how many traffic is routed to each resource. This can be useful for a variety of purposes, including load balancing and testing new versions of software. 
    
 #### You need to have a Data storage layer in AWS. Following are the key requirements:
   * a. Storage of JSON documents
   * b. Availability of Indexes
   * c. Automatic scaling
   * Which of the following would be an ideal storage layer for the above requirements?
     * DynamoDB.
 #### Your company is planning on hosting their development, test and production applications on EC2 Instances in AWS. They are worried about how access control would be given to relevant IT Admins for each of the above environments. As an architect, what would you suggest for managing the relevant accesses?
   * Add tags to the instances marking each environment and then segregate access using IAM Policies. 
     * You can quickly identify the resource based on tags. Tag consist of a key and an optional value. 
#### You are performing a Load Testing exercise on your application hosted on AWS. While testing your Amazon RDS MySql DB instance, you notice that your application becomes non responsive when you reach 100% CPU utilization. Your application is read-heavy. What methods will help your data-tier to meet the application's needs? 
  * Add Amazon RDS DB Read Replicas, and have your application direct read queries to them.
  * Use ElastiCache in front of AWS RDS DB to cache common queries
  * Shard your data set among multiple Amazon RDS DB Instance. 
#### You work for a large company having multiple applications which are very different from each other. These are built using different programming languages. How can you deploy these applications as quickly as possible?
  * Develop each app in a separate Docker container and deploy using Elastic Beanstalk
    * With Docker containers you can define your own runtime environment, choose your own platform, programming language. 
#### You are designing a system which needs at minimum, 8 m4.large instances operating to service traffic. While designing a system for high availability in the us-east-1 region having 6 AZ, your company needs to be able to handle the death of a full AZ. How should you distribute the servers to save as much cost as possible, assuming all of the EC2 nodes are properly linked to an ELB? Your VPC account can utilize us-east-1's AZ a through f, inclusive 
  * 2 servers in each of AZ's a through e, inclusive
    * with this soln, you can have minimum of 8 servers even if one AZ goes down. 
#### An application currently consists of an EC2 Instances hosting a Web application. The Web application connects to an AWS RDS database. Which of the following can be used to ensure that database layer is highly available?
  * Enable Multi-AZ for the AWS RDS database.
#### An application currently accepts users to upload files to an S3 bucket. You want to ensure that the file name for each uploaded file is stored in DynamoDB table. How can this be achieved? 
  * Create a AWS Lambda function to insert the required entry for each uploaded file
  * Add an event with notification send to Lambda.
#### An application allows users to upload images to an S3 bucket. Initially these images will be downloaded quite frequently, but after some time, the images might only be accessed once a week and the retrieval time should be as minimal as possible. What could be done to ensure a cost effective solution?
  * Store the objects in S3-standard storage
  * Create a Lifecycle Policy to transfer the objects to S3- Infrequent Access storage after a certain duration of time.
#### A company hosts a popular web application that connects to an Amazon RDS MySQL DB instance running in a private VPC subnet created with default ACL settings. The IT Security department has identified a DDoS attack from a suspecting IP. How can you protect the subnets from this attack?
  * Change the Inbound NACL to deny access from the suspecting IP.
#### Videos are uploaded to an S3 bucket, and you need to provide access to users to view the same. What is the best way to do so, while maintaining a good user experience for all users regardless of the region in which they are located?
  * Use CloudFront with S3 bucket as a source. 
#### An organization has a requirement to store 10TB worth of scanned files. They are required to have a search application in place to search through the scanned files. Which of below mentioned options is ideal for implementing the search facility?
  * Use S3 with standard redundancy to store and serve the scanned files. Use CloudSearch for query processing, and use Elastic Beanstalk to host the website across multiple Availability Zones.
#### A concern raised in your company is that developers could potentially delete production baseed EC2 resources. As a Cloud Admin, which of the below options would you choose to help alleviate this concern?
  * Tag the production instances with a production-identifying tag and add resource-level permissions to the developers with an explicit deny on the terminal API call to instances with the production tag
  * Create a seperate AWS account and add developers to that account
#### You are an architect for a gaming application which is in the desing phase. Which of the following services can be used to ensure optimal performance and least latency for gaming users?
  * AWS ElastiCache
    * Amazon ElastiCache offers fully managed Redis and Memcached. Seamlessly deploy, operate, and scale popular open source compatible in-memory data stores. Popular choice for Gaming, IOT apps, Ad-Tech, Financial Services and Healthcare.
#### An organization planning to use AWS for their production roll out, wants to implement automation for deployment such that it will automatically create a LAMP stack, download the latest PHP installable from S3 and setup the ELB. Which of the below metioned AWS Service meets the requirement for making an orderly deployment of the software?
  * ElastiBeanstalk
    * We can simply upload code and Elasti Beanstalk automatically handles the deployment, from capacity provisioning, load balancing, Auto-Scaling to application Health Monitoring. 
#### Your current log analysis application takes more than four hours to generate a report of a top 10 users of your web application. You have been asked to implement a system that can report this information in real time, ensure that the report is always up to date, and handle increases in the number of requests to your web application. Choose the option that is cost-effective and can fulfill the requirements.
  * Post your log data to Amazon Kinesis data stream, and subscribe your log-processing application so that is configured to process your logging data. 
#### There is a requirement to load a lot of data from your on-premise network on to AWS Redshift. Which of the below options can be used for this data transfer? 
  * Direct Connect
  * Snowball
#### As the cloud administrator of your company, you notice that one of EC2 instances is restarting frequently. There is a need to troubleshoot and analyse the system logs. What can be used in AWS to store and analyze the log files from the EC2 Instances?
  * AWS CLoudWatch Logs
#### Your company has migrated their production environment into AWS VPC 6 months ago. As a cloud architect, you are required to revise the infrastructure and ensure that it is cost-effective in the long term. There are more than 50 EC2 instances that are up and running all the time to support the business operation. What can you do to lower cost?
  * Reserved Instance
    * when you have instances that will be used continuously and throughout the year.
#### You have configured an Auto-scaling group for which the minimum running instance is 2 and maximum running instance is 10. For the past 30 minutes, all five instances have been running at 100 CPU utilization; however, the AutoScaling group has not added any more instances to the group. What is the most likely cause for this?
  * You already have 20 on-demand instances
  * The Auto Scaling group's scale up policy has not yet been reached
    * By default, you can run upto 20 on-demand EC2 instances. If you need more, you have to complete a requisition form and submit it to AWS. 
#### A company has an application hosted in AWS. This application consists of EC2 instances that sit behind ELB with EC2 instances. The following are requirements from an administrative perspective
  * a. Must be able to collect and analyze logs with regard to ELB's performance
  * b. Ensure that notifications are sent when the latency goes beyond 10 seconds.
  * Which of the following can be used to achieve this requirements?
    * Use CloudWatch for monitoring
    * Enable the logs on the ELB and then investigate the logs whenever there is an issue. 
 #### Your company would like to leverage the AWS storage option and integrate it with the current on-premise infrastructure. Besides, due to business requirements, low latency access to all the data is a must. Which of the following options would be best suited for this scenario?
  * Configure Storage Gateway Stored Volume
    If you need low-latency access to your database, first configure your on-premise gateway to store all your data locally. Then asynchronously back up point-in-time snapshots of this data to Amazon S3. This configuration provides durable and inexpensive offsite backups that you can recover to your local data center or Amazon EC2.
#### An IT company would like to secure their resources in their AWS Account. Which of the following options is able to secure data at rest and in transit in AWS?
  * Encrypt all EBS volumes attached to EC2 instances
  * Use Server-Side Encryption for S3
  * Use SSL/HTTPS when using the Elastic Load Balancer
#### Your company is hosting an appication in AWS. The application is read intensive and consists of a set of web servers and AWS RDS. It has been noticed that the response time of the application decreases due to the load on the AWS RDS instance. Which of the following measures can be taken to scale the data tier?
  * Create a Amazon DB read replica. Configure the application layer to query the Read Replicas for query needs.
  * Use ElastiCache in front of your Amazon RDS DB to cache common queries
    * RDS read replica provides enhanced performance and durability for database(DB) instances. This replication feature makes it easy to elastically scale out beyond the capacity constrants of a single DB Instance for read-heavy database workloads.

#### Your team has developed an application and now needs to deploy that application onto an EC2 Instances. This application interacts with a DynamoDB table. Which of the following is the correct and most secure way to ensure that the application interacts with the Dynamo DB table.
  * Create a role which has the necessary and can be assumed by the EC2 instance. 
    * IAM roles are designed in such a way that your application can securely make API requests from your instances, without requiring you to manage the security credentials that the applications use.
#### Your company is big on building container-based applications. Currently they use Kubernetes for their on-premise docker based orchestration. They want to move to AWS and preferably not have to manage the infrastructure for the underlying orchestration service. Which of the following could be used for this purpose.
  * AWS ECS
    * Amazon Elastic Container Service (ECS) is a highly scalable, high-performance container orchestration service that supports Docker containers and allows you to easily run and scale containerized application on AWS.
    * ECS with Kubernetics installed is not correct for this scenario because this would add maintenance overhead for the company and according to question, the company doesn't want to manage the infrastructure
#### You are creating a number of EBS Volumes for the EC2 instances hosted in your company AWS accout. The company has asked you to ensure that the EBS volumes are available even in the event of disaster. How would you accomplish this?
  * Create Snapshots of a EBS Volumes
  * Ensure the snapshots are available in another region ( not in another AZ)
#### You have a requirement to host a web based application. You need to ensure high availability for the application, so you create an ELB and place the EC2 instances behind the ELB. You need to ensure that users only access the application via the DNS name of the load balancer. How would you design the network part of the application.
  * Create 2 public subnets for the ELB
  * Create 2 private subnets for the backend instances
    * You must create public subnets in the same AZ as the private subnets that are used by your private instances. Then asociate these public subnets to the internet-facing load balancer
#### You work as an architect for a company. An application is going to be deployed on a set of EC2 instances in a VPC. The Instances will be hosting a web application. You need to design a security group to ensure that users have the ability to connect from the Internet via HTTPS. 
  * Allow inbound access on port 443 for internet
    * Security group are stateful, you don't need to define the rule for outbound traffic. 
#### Create a bastion host in the public subnet and make IT admin staff use this as a jump server to backed instances to ensure secure administer of IT administrators for instances in the VPC
#### A customer needs corporate IT governance and cost oversight of all AWS resources consumed by its divisions. Each division has their own AWS account and there is a need to ensure that the security policies are kept in place at the Account Level. How can you achieve this?
  * Use AWS Organizations
  * Use Service control policies
    * SCPs allow you to define which AWS service APIs can and cannot be executed by AWS IAM enties.
#### A company is planning on migrating their infrastructure to AWS. For the data stores, the company does not want to manage the underlying infrastructure. Which of the following would be ideal for this scenario.
  * AWS S3
  * AWS DynamoDB
#### Your company has a set of resources defined in AWS. These resources consist of applications hosted on EC2 Instances. Data is stored on EBS Volumes and S3. The company mandates that all data should be encrypted at rest. How can you achieve this?
  * Enable EBS Encryption
  * Enable S3 server-side Encryption
#### Your company has a set of VPC's. There is now a requirement to establish communication across the instances in the VPC's. Your supervisor has asked you to implement the VPC peering connection. Which of the following considerations would you keep in mind for VPC Peering. 
  * Ensuring that the VPC's don't have overlapping CIDR blocks
  * Ensuring that no on-premise communication is required via transitive routing
#### You have been instructed to establish a successful site-to-site VPN connection from your on-premise network to the VPC. As an architect, which of the following pre-requisities should you ensure are in place for establishing the site-to-site VPN connection. 
  * A public IP address on the customer gateway for the on-premise network
  * A virtual private gateway attached to the VPC
#### Your company wants to enable encryption of services such as S3 and EBS volumes so that the data it maintains is encrypted at rest. They want to have complete control over the keys and the entire lifecycle around the keys. How can you accomplish this?
  * Use the HSM Module
    * AWS CloudHSM is a cloud-based hardware security module(HSM) that enables you to easily generate and use your own encryption.
#### A company has setup some EC2 Instances in a VPC with the default Security group and NACL settings. They want to ensure that IT admin staff can connect to the EC2 Instances via SSH. As an architect what would you ask the IT admin team to do to ensure that they can connect to the EC2 Instance from the Internet. 
  * Ensure that the Instances has a Public or Elastic IP
  * Ensure to modify the Security groups
    * We will not modify NACL because by default NACL rules will allow all traffic
#### Your company has a set of EBS volumes and a set of adjoining EBS snapshots. They want to minimize the costs for the underlying EBS snapshots. Which of the following approaches provides the lowest cost of Amazon ELastic Store snapshots while giving you the ability to fully restore data?
  * Maintain a single snapshot the latest snapshot is both incremental and complete.
#### A company is planning on setting up a web-based application. They need to ensure that users across the world have the ability to view the pages from the web site with the least amount of latency. How can you accomplish this?
  * Place cloudfront distribution in front of the web application. 
    * Place ElastiCache only in front of database layer.
#### A company is hosting their company website on a cluster of web servers that are behind the public facing ELB. The customer also uses Amazon Route 53 to manage their public DNS. How should Route 53 be configured to ensure the custom domain is made to point to the load balancer. 
  * Create an alias for CNAME record to the load balancer DNS name
  * Ensure that a hosted zone is in place
#### A customer is hosting their company website on a cluster of web servers that are behind a public-facing load balancer. The web application interfaces with a AWS RDS database. The management has specified that the database be available in case of a hardware failure on the primary database. The secondary needs to be made available in the least amount of time. Which of the following would you opt for?
  * Enabled Multi-AZ failover
    * Snapshot of database and read replica are not a suitable option here because it would take more time than just enabling Multi-AZ
#### You are an architect for your company. Your IT admin staff needs access to newly created EC2 Instances for administrative purposes. Which of the following needs to be done to ensure that the IT admin staff can successfully connect via port 22 on the EC2 instances
  * Adjust the instance's Security Group to permit ingress traffic over port 22 from your IP.
    * A security group acts as a virtual firewall that controls the traffic for one or more instances. When you launch an instances, you associate one or more security groups with the instances. You add rules to each security group that allow traffic to or from its associated instances. 
#### You work as an architect for a company. There is a requirement for an application to be deployed on a set of EC2 Instances. These would be part of a compute cluster that requires low inter-node latency. Which of the following would you use for this requirement?
  * Cluster Placement Groups
    * Cluster placement groups are recommended for applications that benefit from low network latency, high network throughput, or both, and if the majority of the network traffic is between the instances in the group. 
#### Your company stores a large set of files in Amazon S3. They need to ensure that if any new files are added to an S3 bucket, an event notification would be sent to the IT admin staff. Which of the following could be used to fulfill the requirement?
  * Create an SNS topic
  * Add an event notification to the S3 bucket ( not to S3 object)
#### Your company is planning on migrating some code form their on-premises infrastructure onto AWS. They want to ensure to limit the amount of maintenance that would be required for the underlying infrastructure. Which of the following would they choose for hosting the code base?
  * AWS Lambda
    * AWS Lambda is a compute service that lets you run code without provisioning or managing servers. 
#### A company has an AWS account that contains three VPCs (Dev, Test, and Prod) in the same region. There is a requirement to ensure that instances in the Development and Test VPC can access resources in the Production VPC for a limited amount of time. Which of the following would be the ideal way to get this in place?
  * Create a seperate VPC peering connection from Development to Production and from Test to the Production.
    * VPC peering can be between your own VPCs in same region, or within a VPC in another AWS account, or in different regions. 
#### You are designing a application architecture for a company. The architecture is going to consist of a web tier that will be hosted on EC2 instances placed behind an ELB. Which of the following would be considered important when considering what should the specification for the components of the application architecture?
  * Determine the required I/O operations
  * Determining the minimum memory requirements for an application 
    * You should decide on what are the requirements for the underlying EC2 Instances. You can then choose the Instance type for the underlying EC2 Instance.
#### Your company is planning on moving to the AWS Cloud. There is a strict compliance policy that mandates that data should be encrypted at rest. As an AWS Solution  architect, you have been tasked to put the organization data on the cloud and also ensure that all compliance requirements have been met. Which of the below needs to be part of the implementation plan to ensure compliance with the security requirements.
  * Ensure that all EBS Volumes are encrypted
  * Ensure that server-side encryption is enabled for S3 buckets. 
#### Your company currently has a set of virtual servers that need to be migrated to the AWS Cloud. These instances are normally 70%utilized and used throughout most of the year. As a solution architect which of the following instance pricing model would you suggest?
  * Reserved Instance
    * On-demand Instance- Pay, by the second, for the instances that you launch
    * Reserved Instances- Purchase, at a significant discount, instances that are always available, for a term from one to three years.
    * Scheduled Instances- Purchase instances that are always available on specified recurring schedule, for a one-year term.
    * Spot Instances- Request unused EC2 instances, which can lower your Amazon EC2 costs significantly.
    * Dedicated Host- Pay for the physical host that is fully dedicated to running your instances, and bring your existing per-socket, per-core, or per -VM software licenses to reduce costs. 
    * Dedicated Instances- Pay, by the hour, for instances that run on single-tenant hardware. 
#### You have a read intensive application hosted in AWS. The application is currently using the MySQL RDS feature in AWS. The cloudwatch metrics is showing high read throughput on the database and is causing performance issues on the database. Which of the following can be used to reduce the read throughput on the MySQL database?
  * Enable Read Replica's and offload the reads to the replica
    * asychronous replication for enhanced performance and durability of (DB) instances; ideal storage mechanism which require high read throughput.
#### Your company is planning on setting up a VPC with private and public subnets and then hosting EC2 Instances in the subnet. It has to be ensured that instances in the private subnet can download updates from the internet. Which of the following needs to be part of the architecture for this requirement?
  * NAT Gateway
    * You can use a Network Address Translation (NAT) gateway to enable instances in a private subnet to connect to the internet or other AWS services, but prevent the internet from initiating a connection with those instances. 
#### When to use NLB, Classic LB or ALB
  * NLB supports TCP, ALB supports HTTP and HTTPS. In, NLB source IP of the sender will be preserved and in case of ALB it gets modified.
  * Classic LB supports TCP, SSL, HTTP and HTTPs.
  * SSL offloading and path based routing or host based routing can only be done using application load balancer. 
  * Static IP address is only supported in NLB
#### Your company has an AWS account and a lot of resources defined in the Frankfurt region. They want to track the resources to monitor if any charges are made to the resources. Which of the following should be used for this purpose?
  * AWS Config 
    * is a service that enables you to assess, audit, and evaluate the configuration of your AWS resources. Config continuously monitors and records your AWS resource configuration and allows you to automate  the evaluation of recorded configuration against desired configuration. 
#### A company is planning on hosting an application with the below architecture: 1. A lambda function which reads metadata of objects from an S3 bucket, 2. The lambda function then stores the metadata in Dyanamo DB and AWS RDS- MySQL. Which of the following needs to be in place to high availability of all components in the system?
  * Enabling Multi-AZ for the MySQL database
    * Multi-AZ RDS automatically provisions and maintains a sychronous standby replica in different AZ.
#### A company has a set of EC2 instances hosting a revenue generating applications. Some of the data on the attached EBS volumes are critical to retain. Hence it has to be ensured that even after the instance are terminated, the EBS volumes will still remain inact. Which of the following needs to be done to ensure this requirement can be met?
  * Make the attribute of DeleteOnTermination for the EBS volume to false 
    * When an instance is terminated, EC2 uses the value of the DeleteOnTermination attribute for each attached EBS volume to determine whether to preserve or delete the volume when the instance is terminated. By default, the DeleteOnTermination attribute for root volume is set to true, but it is set to false for all other volume types. 
#### A company has an application that needs to be hosted on an EC2 Instances. The general amount of throughput data will be in the range of 400-500 MiB/s from the application. Which of the following should be used as the the storage type for the underlying EC2 Instace with Cost-effective manner?
  * Throughput Optimized HDD
    * When you want high throughput, you should choose using the Throughput Optimized EBS Volume. 
#### Your company is currently hosting an application on their On-premise environment. The company has developed this application inhouse. Consulting companies then use this application via API calls. You now need to consider moving this application to AWS. Which of the following services would best be suited in the architecture design, which would also help deliver a cost-effective solution. 
  * AWS Lambda
  * AWS API-Gateway
#### A company has an Amazon Aurora cluster setup. They have setup a Lambda function which needs to insert records into a DynamoDB table. The Amazon Aurora cluster needs to invoke the Lambda as a stored procedure. Which of the following need to be in place for this setup to work. 
  * Ensure that the Amazon Aurora cluster has an IAM Role which allows it to invoke Lambda functions
  * Allow the Amazon AUrora cluster to allow outbound communication to the lambda function
#### Your application consists of a set of EC2 instances which are spun up as part of an AutoScaling Group. These Instances need to access objects in an S3 bucket. Which of the following is the ideal approach to ensure this access is set in place?
  * Ensure that the AutoScaling Group attaches an IAM Role attached to the underlying EC2 Instances. 
#### You are an architect for a company that is going to be hosting an application in AWS. They want to load balance the traffic based on which route the user chooses. The 2 possible routes for the application are /customers and /orders. Which of the following would you include in the design?
  * Application Load Balancer instead of Classic load Balancer
#### Your company is planning on hosting an application that will be based on Docker containers. They need to setup an orchestration service that would automatically scale based on the load. As much as possible, the company does not want the burden of managing the underlying infrastructure. Which of the following can assist in this scenario?
  * AWS ECS with service autoscaling
    * Your ECS can optionally be configured to use Service Auto Scaling to adjust its desired count up or down in response to CloudWatch alarms. Service AutoScaling leverages the Application Auto Scaling service to provide this functionality. 
#### Your team is developing Lambda functions. These functions would need to interact with databases belonging to different environments. Which of the following is the ideal approach to ensuring that the Lambda function are designed in the right way to interact with Databases in multiple environments?
  * Make use of environment variables to store the database connecting strings. 
    * Environment variables for Lambda functions enables you to dynamically pass settings to your function code and libraries, without making changes to your code. 
#### A company is planning to store sensitive documents in an S3 bucket. They want to ensure that documents are encrypted at rest. They want to ensure that they managee the underlying keys which are used for encryption. Which of the following can be used for this purpose. 
  * Use S3 server-side encryption with Customer keys
  * Use S3 client-side encryption
    * Client-side encryption is the act of encrypting data before sending it to Amazon S3. To enable client side encryption, use an AWS KMS-managed customer master key and use a client-side master key.
#### A company has a requirement to monitor API activity for audit purposes for their AWS account. This audit would be conducted in the future as well and should be applicable to all regions. How would you design your solution to meet the present and future needs?
  * Ensure one Cloudtrial log is enabled for all regions. 
#### A Company is currently hosting an application which connects to a MySQL AWS RDS Instance. Off late there have been many performance issues being encountered. After careful analysis, it has been determined that the issue is occuring as a result of similar queries being fired against the database. Which of the following can be added to the architecture to alleviate the performance issue?
  * Use the ElastiCache Service
#### A company has a set of EC2 instances hosting a custom based application which is listening on port 3308. All of a sudden there seem to be a barrage of requests comming in from a source IP address of 52.0.9.10. Which of the following can be used to stop requests from entering the VPC from this IP address.
  * Network ACL's
    * NACL is a n optional layer of security for your VPC that acts as a firewall for controlling traffic in and out of one or more subnets. You might set up NACL with rules similar to your security group in order to add an additional layer of security.
    * Security group is not suitable option because it can only allow, but not deny traffic.
    * VPC flow logs is not suitable option because it is used for monitoring your network traffic into the VPC.
    * AWS CloudTrail is not suitable option because it is used for API Monitoring
#### Your company is planning to store sensitive documents in a bucket in the S3. They need to ensure that all objects are encrypted at rest in the bucket. Which of the following can help accomplish this?
  * Ensure that the default encrytion is enabled for the S3 buckets.
  * Ensure to change the configuration of the buckets to use a KMS key to encrypt the objects. 
    * You have three mutually exclusive options depending on how you choose to manage the encryption keys.
      * Use Server-Side Encryption with Amazon S3-Managed Keys(SSE-S3) - Each object is encrypted with a unique key employing strong multi-factor encryption. As an additional safeguard, it encrypts the key itself with a master key that it regularly rotates.
      * Use Server-Side Encryption with AWS KMS-Managed Keys (SSE-KMS) - similar to SSE-S3, but with some additional benefits along with some additional charges for using this service. 
      * Use Server-side Encryption with Customer-Provided Keys (SSE-C) - You manage the encryption keys and Amazon S3 manages the encryption, as it writes to disks, and decryption, when you access your objects. 
#### Your company has a series of web sites hosted in AWS. They need to ensure that users from the Europe region are directed to the website www.demo.com for regulatory purpose. Which of the following can help in this regard?
  * Using the Route 53 service
    * Geoloaction routing lets you choose the resources that serve your traffic based on the geographical loaction of your users, meaning the location that DNS queries originate from. for eg, you might want all queries from Europe to be routed to an ELB in another region.
#### A company is planning to host an active-active site. One site will be located in AWS and the other one on their On-premise data center. They need to ensure that traffic is distributed accordingly between both the sites. Which of the following routing policy would you use for this purpose?
  * Weighted Routing
    * Weighted Routing lets you associate multiple resources with a single domain name (example.com) or subdomain name (something.example.com) and choose how much traffic is routed to each resources. This can be useful for variety of purpose, including load balancing and testing new versions of software. 
#### A company needs to access a service provided by a consultant company. The service from the consultant company and the application of the primary company exist in AWS VPC. The VPC's are located in different region. How can you accomplish this connectivity ensuring that traffic does not pass via the Internet? 
  * Create a VPC peering between the VPC's in the primary company and consultant company's account
  * Create a AWS Direct Connect in the primary company's account. Create a private Virtual Interface to the VPC in the consultant company's account
    * A VPC Peering connection is a networking connection between two VPCs that enables you to route traffic between them privately.
    * Direct connect makes it easy to establish a dedicated network connection from your premise to AWS
 #### An application needs to setup on AWS. It consists of several components. Two primary components are required to run for 3 hours everyday. The other components are required everyday for more than 6-8 hours. Which of the following would you use to ensure COSTS are minimized for the underlying EC2 Instances?
   * On-demand instances for the primary components and for the remaining components, reserved instance.
     * reserved instances provide you with a significant discount compared to on-demand instance pricing. 
 #### You have currently contacted an AWS partner to carry out an audit for your AWS account. You need to ensure that the partner can carry out an audit on your resources. Which one of the following steps would you ideally carry out?
   * Create a cross account IAM Role
     * Cross-account IAM roles allow customers to securely grant access to AWS resources in their account to a third party, like an APN Partner, while retaining the ability to control and audit who is accessing their AWS accont. 
#### Your company is planning on setting up an application that will consist of a presentation layer and a datastore in DynamoDB. The data in DynamoDB will only used frequently within the week in which the data is inserted. After a week, the data would tend to become stale. But the stale data would need to be available on durable storage for future analysis on historical data. Which of the following would be ideal implementation steps for this sort of architecture?
  * Setup DynamoDB tables on a weekly basis. Ensure the most recent week table has a higher throughput setup
  * Use the AWS Data Pipeline service to transfer the older data to Amazon S3. 
    * Data pipeline is a web service that you can use to automate the movement and transformation of data. 
#### A company is going to setup an application that will be based on Docker based containers. The containers will be setup in the ECS. You need to also setup load balancing for the underlying services which are based on dynamic port values. Which of the following would be the ideal service to use for this purpose?
  * Application load balancer
    * Application load balancer offer several features that make them attractive for use with Amazon ECS service.
#### You currently have an architecture which consists of a set of Web servers in the public subnet. And database servers in the private subnet along with a NAT Instance. The NAT instance is now becoming a bottleneck and you are looking to replace it with a NAT gateway. Which of the following would ensure a high availibility setup for the NAT device?
  * Deploy the NAT gateway in 2 availability zones
    * Because if you have resources in multiple AZ and they share one NAT gateway, in the event that the NAT gateway's availability zone is down, resources in the other availability zones lose internet access. 
#### Your company is planning on setting up an application with the following architecture; a. a set of EC2 instances hosting a web application. b. the application will sit behind an ELB. c. The users will access the application from the internet via the ELB. d. The application will connect to a backend database server. d. A NAT Gateway is also implemented. Which of the following is the right architecture for the network, keeping high availability in mind?
  * 2 public subnets for the Elastic Load Balancer, 2 private subnets for the Web server EC2 Instances, 2 private subnet for database layer. 
    * You need to have public subnets for the ELB to ensure that traffic can flow via the Internet
    * The Web server can be in the private subnet since the communication between the instances and the ELB happens via the private IP
    * The database servers should be in the private subnet since it doesnot need to communicate with the Internet
