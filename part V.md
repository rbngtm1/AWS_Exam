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
