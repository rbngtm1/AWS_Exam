# solution_architect_associate
#### You are hosting an web application in EC2, where number of users is expected to increase in comming months. Best methods to add elasticity is:
  * Set up web application on more EC2 instances and set them behind an ELastic Load Balancer.
  * Set up your web application on more EC2 and use Route 53 to route request accordingly.
#### Maximum ratio of IOPS to Volume size is 50:1
  * If the volume size is 8 GiB, the maximum IOPS of the volume can be 400.
#### In different subnet in same VPC, you have 2 Ubuntu instances located. These instances should be able to communicate with each other, but when you try to ping from one instance to another, you get a timeout. The route table seem to be valid and has the entry for the target "local" for your VPC CIDR. The valid reason for this issue is:
  * The Security Group has not been modified to allow the requested traffic.
 #### For more EBS volume curently attached to EC2 instance from one AZ to other.
  * Create a snapshot of the volume and then crate a volume from the snapshot in other AZ.
 #### Retrieve the Pulbic IP addresses assigned to a running instance via the Instance metadata.
  * http://169.254.169.254/latest/meta-data/public-ipv4
 #### Ensure that you are available to recover from a database crash to use the MySQL RDS in AWS.
  * Ensure that you use MyISAM storage engine for MYSQL (**Recommended practice**)
    * Ensure that automated backup are enabled for RDS. (**Not Recommended practice**)
    * Ensure that tables in RDS donot get too large. (**Not Recommended practice**)
    * Ensure that file size for RDS is well under 16TB. (**Not Recommended practice**)
 #### Route 53 features
   * Registration of Domain Names.
   * Routing of internet traffic to domain resources.
   * Health check of resources
   * (**not a feature**)- Offloading content to cache locations.
 #### Type of endpoints exposed when working with API gateways.
   * HTTPS
 #### Verbs supported with API Gateway
   * Get, Post, Put, Patch, Delete, Head, Options
 #### Container technologies supported by AWS
   * Docker
 #### Provide a single sign-on experience for existing users when used alongside with AWS Token Service using on-premise application
   * SAML 2.0 (Security Assertion Markup Language)
 #### OpenID Connect and OAuth
   * used when you want users to sign in using well-known third party identity provider such as login with Amazon,Fb,Google
 #### Volume check has a status of 'Insufficient data'
   * The check on the volume is still in progress (If check fails, the status of volume is impared)
 #### Constitue the term of 'Golden Image'
   * Refers to an AMI which has been constructed from a customized image
 #### When designing a health check for your web application which is hosted behind an ELB, which of the following health check is ideal to implement
   * HTTP health check
 #### Exammple of synchronous replication in AWS
   * AWS Multi-AZ RDS
   * Amazon RDS automatically creates a primary DB Instance and synchronously replicates the data to standby instance in a different AZ.
 #### To get reason for your EC2 instance termination from CLI
   * aws ec2 describe-instances
 #### Which AWS service should be implemented in multiple AZ for high availability solutions
   * Amazon EC2
   * Amazon ELB
 #### If application is processing once in a week and not all messages are picked by application where application is currently configured on EC2 instance to process msg in SQS. The issue is:
   * Some of message have surpassed the retention period defined for the queue.
   * When you create SQS with default options, the message retention period is 4 days, which means message send at start of week will get deleted before it can be picked by application
   **Queue Attributes**
     * Default Visibility Timeout = 30 sec.
     * Message Retention Period = 4 days.
     * Maximum Message Size = 256KB.
 #### You created your own VPC and subnet. You have launched instance in that subnet. You noticed that the instance is not receiving DNS name. Probable reason is:
   * The VPC configuration needs to be changed.
   * Go to actions and edit DNS Hostnames.
 #### You wanted to have VPC created in AWS which will host an application. The application will just consist of web and database servers to accessed from the internet by internet users. The VPC configuration you use is:
   * VPC with public and private subnets
   * This practice is recommended if you wnat to run a public-facing web application, while maintaining back-end servers that aren't publicly accessible
 #### Which of the following are true with regards to EBS Volumes
   * EBS Volumes are automatically replicated within that zone to prevent data loss due to failure of any single hardware components.
   * After you attach a volume, it appears as a native block device similar to a hard drive or other physical device.
   * An EBS Volume can be attached to only one instance at a time. 
   **Not True** - EBS volumes can be attached to any EC2 instance in an AZ.
 #### Your VPC has 3 subnets- 1 private , 2 public. An EC2 instance are in same Security Group. You created an application which connects to mobile device using custom port. This application has been rolled out to production and you need to open this port globally to the Internet. 
   * Open the port on the existing security group. Your EC2 instances will be able to communicate over this port immediately. 
#### You are creating a number of EBS volumes for your EC2 instances. You are concerned on the backups of the EBS volumes. Which of the below is a way to backup the EBS volumes.
  * Write a cronjob that uses the AWS CLI to take a snapshot of production EBS volumes 
  * You cacn create a snapshot vial CLI command -create-snapshot
  * Even though snapshot are saved incrementally, the snapshot deletion process is designed so that you only need to retain most recent snapshot in order to restore the entire volume. 
#### Planning to host static website on EC3 for highly available environment. (Use below aspects)
  * An autoscaling group to recover from EC2 instance failure
  * Elastic Load Balancer
  * Multiple Availability Zone
#### What amount of temp space is allocated to you when using lambda function per invocation
  * 512 MB (Ephemeral disk capacity/ temp space)
#### Requirement to create a subnet in an AWS VPC which will host around 20 hosts. This subnet will be used to host web servers.
  * 10.0.1.0/27
  * The availabe IP addresses for this CIDR block is 32 addresses. However, the first four IP addresses and the last IP addresses in each subnet CIDR blocks are reserved and cannot be assigned to an instance. This is the reason why in the explanation part, it has been written as 27 IP addresses are available for location. 
  **Note:**
  * 10.0.1.0 : Network address
  * 10.0.1.1 : Reserved by AWS
  * 10.0.1.2 : Reserved by AWS
  * 10.0.1.3 : Reserved by AWS
  * 10.0.1.31 : Network Broadcast Address
#### You run a website which hosts videos and you have 2 types of members premium fee paying members and free members. All videos uploaded by both your premium members and free members are processed by a fleet of EC2 instances which will poll as videos are uploaded. However, you need that your premium fee paying memebers videos have a higher priority than your free members. How you design SQS?
  * Create 2 SQS queue, one for premium and one for free members. Program your EC2 fleet to poll the premium queue first and if empty, to then poll your free members SQS queue
#### True about SSE
  * SSE encrypts message as soon as Amazon SQS receives them
#### In VPC, you have launched 2 web servers and attached to an internet facing ELB. Both web servers and ELB are located in public subnets. Yet, you are still not able to access your web application via ELB.
  * You should attatch an Internet gateway to the VPC and route it to the subnet.
#### You want to ensure that you keep a check on the Active volumes, Active snapshots and Elastic IP Addresses you use, so that, you don't go beyond the service limit. Which of the below services can help in this regard?
  * AWS Trusted Advisor
    * It is online resourse to help you reduce cost, increase performancr and improve security by optimizing AWS environment.
#### If you don't know what storage capacity requirements are, text and audio files can be stored in s3 for storage until its retrieved.
  
#### To create a script which could create duplicate resources in another region in case of disaster.
  * Cloud formation
    * helps you model and set up your Amazon Web Service resources, so that, you can spend less time managing those resources and more time foucusing on your application that runs in AWS. 
#### Bastion hosts ar instances in the public subnets which are used as a jump servers to resources within other subnets.
#### For reserved instancs which we need to shutdown now but data is still required for future
  * Take a snapshot of EBS volumes and terminate the instance
  * Sell the instance on the AWS Reserved Instance Marketplace.
#### Disaster Recovery Best Solution
  * Creates an AMI of the EC2 instances and copy it to another region. 
#### You need to add the security rule so that you can access HTTP traffic to the server. Add rule to the security group as desired.
  * Type HTTP--Protocol TCP--Port Range 80--Source 0.0.0.0/0
  * Type HTTP--Protocol TCP--Port Range 80--Source ::/0
  * Type SSH--Protocol TCP--Port Range 22--SOurce 0.0.0.0/0
#### Amazon Redshift uses block size for its columnar storage
  * 1024KB
#### Don't save your API credentials. Instead create a role in IAM and assign this role to an EC2 instance when you first create it. 
#### Which of the following metrics do you need to design a custom cloud watch metric for, when monitoring the health of your EC2 instances.
  * Memory Usage
#### In order for EC2 Instance to be accessed to Internet. Required is:
  * An internet gateway attached to the VPC.
  * A public IP address attached to the instance.
  * A route entry to the Internet gateway in the Route table.
#### Kinesis Stream Data records are oly accessible for a default of 24 hours from the time they are added to a stream. It stores 25 hours by default, upto 168 hours.
#### A customer wants to track access to their Amazon S3 buckets and also use this information for their internal security and access audits. Which of the following will meet customers requirements.
  * Enable server access logging for all required Amazon S3 buckets. 
#### To define Network ACL for your subnet, as soon as the rule matches traffic, it's applied regardless of any higher-nubered rule that may contraidict it.
#### Which procedure for backing up a relational database on EC2 that is using a set of RAIDed EBS Volumes for storage minimizes the time during which the database cannot be written to and results in a consistent backups?
  * Supend disk I/0
  * Start EBS snapshot of volumes
  * Wait for snapshots to complete
  * Resume disk
 #### Serices that can be used to store sesson data for session management
  * RDS, DynamoDB and Elasticache.
#### 24/7 access to support 
  * Access to the full set of Trusted Advisor Checks (**Both Business and Enterprise**)-- But Business ensures the cost is minimum.
#### Private IP addresses
  * In Amazon EC2 classic, the private IP addresses are only returned to Amazon EC2 when the instance is stoppe or terminated.
  * In Amazon VPC, an instance retains its private IP addrsses when the instance is stopped.
  * In Amazon EC2 classic, the private IP address is associated exclusively with instance for its lifetime
  * **Not true about Private IP Addresses**
  * In Amazon VPC, an instance doesn't retain its private IP addresses when the instance is stopped.
#### Best practices for monitoring EC2 instances
  * Create and implement a monitoring plan that collects monitoring data from all of the parts on your AWS Solution.
  * Automate monitoring tasks as much as possible.
  * Check the log files on your EC2 instances.
#### SWF
  * makes easier to develop asynchronous and distributed applications by providing programming model and infrastructure for coordinating distributed components.
#### SWF and Amazon EC2 are appropriate solution for:
  * Managing a multi-step and multi-decision checkout process of an e-commerce website
  * Orchestrating the execution of distributed and auditable business processes.
#### In case of sudden increase in traffic to keep minimum storage cost where it doesn't matter if some objects are lost:
  * Use S3 Reduce Redundancy Storage(RRS)
#### EC2 Instance
  * There is no charge for public data sets.
  * Instance state can be pening, rebooting, running, stopping, stopped, sutting down an terminated.
  * EBS Backed Instance can be start, stop and terminated.
#### Database Servers
  * Shoulnot be exposed to the internet and should reside in private subnets.
#### Which of the following can be use as origin server in CloudFront?
  * A webserver running on EC2
  * A webserver running in your own datacenter.
  * An Amazon S3 bucket.
#### You have written a Cloud Formation template that creates 1 ELB fronting 2 EC2 instances. Which sector of template should you edit, so that DNS of the load balancer is rturned upon creation of the stack. 
  * Outputs
#### Is it true that EBS can always tolerate AZ failure?
  * No, all EBS volumes is stored in single AZ.
  * EBS volume has multiple copies but within same AZ.
#### Configured and Peered 2 VPC-VPC1 in Private Subnet and VPC2 in Public Subnet. AWS uses Direct Connect to connect to VPC1. Which methods increases fault tolerance:
  * Having a VPN Connection is considered as a backup to a Direct Connect Connection.
  * Establish a hardware VPN over the internet between VPC-1 an the on-premise network.
  * Establish a new AWS Direct Connect Connection and Private virtual interface in the same AWS region as VPC.
#### Which of the following benefits does adding Multi-AZ deployment in RDS provide?
  * MultiAZ deployed database can tolerate an AZ failure.
  * Make database more availabe during maintenace taskes.
#### By default, what happens to data when EC2 instance is terminated.
  * For EBS backed AMI, any volume attached apart from OS volume is preserved.
  * All the snapshots of the EBS volume with operating system is preserved.
  * For S3 backed AMI, all the data in the local( ephemeral) hard drive is deleted.
#### An instance must either have a public or Elastic IP in order to be accessible from the Internet. 
  * Elastic IP must be assigned to access Internet
  * A public IP address is reachable from the Internet. You can use public IP address for communication between your Instances and the internet.
  * An Elastic IP address is a static IP address designed for dynamic cloud computing. 


  

  
