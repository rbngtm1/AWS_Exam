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
