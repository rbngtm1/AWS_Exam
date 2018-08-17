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
  * 512 MB
#### Requirement to create a subnet in an AWS VPC which will host around 20 hosts. This subnet will be used to host web servers.
  * 10.0.1.0/27
  * The availabe IP addresses for this CIDR block is 32 addresses. However, the first four IP addresses and the last IP addresses in each subnet CIDR blocks are reserved and cannot be assigned to an instance. This is the reason why in the explanation part, it has been written as 27 IP addresses are available for location. 
  **Note:**
  * 10.0.1.0 : Network address
  * 10.0.1.1 : Reserved by AWS
  * 10.0.1.2 : Reserved by AWS
  * 10.0.1.3 : Reserved by AWS
  * 10.0.1.31 : Network Broadcast Address
