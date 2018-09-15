# EXAM NOTES
--by robin

#### Total Cost of Ownership
  * Invest in large capital expenditures to reduce TCO
  * Only pay for running servers (Consideration for migrating server)
    * The ability to pay as you go
    * No upfront cost
  * Pay-as-you-go model
  * Manage AWS Organizations
  * Cost Explorer
  * TCO Calculator
  * Manage Marketplace
    * Enables Customers to find, buy and immediately start software solution in their AWS Environment. 
  * Support Plans
    * Basic, Developer, Business, Enterprise

#### Trusted Advisor

Like your customized cloud expert, AWS Trusted advisor analyzes your AWS environment and provides best recommendation. It is a real time guidance to help you provision your resources following AWS best practices. Trusted Advisor is AWS service which can assist with:
* Cost Optimization
* Fault Tolerance
* Service Limits
* Performance
* Security

#### Database
* Database Migration Sytem
* Relational Database Service(RDS)
  * gives you option of mySQL, PostgreSQL, MicrosoftSQL Server, Oracle.
* Dynamo DB
  * noSQL non relational database, serverless and fully managed.
* Amazon RedShift
  * Data Warehouse

#### Security

* DDOS Prevention
  * AWS WAF(Web Application Firewall), AWS Shield, Cloudfront and Load Balancer
* Penetration Testing
  * Get permissions from AWS first. It can be done on your infrastructure only.

#### CloudTrial

* Records events within region in AWS
* Can identify the user that made the API call when Amazon EC2 was terminated.
* helps in governance, complicance, and risk auditing in AWS

#### Acceptabe Use Policy
* Describes Prohibited Actions
#### CloudFront
* Uses AWS Edge Location for content caching.
* Helps in streaming the content in an effecient manner across the globe (ex. deployment of video based application)
#### Edge Location
* Distributes content to users
* Cache Common Responses
* Used in conjunction with Cloudfront services
* ##### But doen't distribute load across multiple resources

## Key Points
##### Design for failure and nothing will fail
* Deployment of an application in multiple AZ
##### Benefit of running an application across 2 AZ's
* Increases the availability of an application 
##### Web-based user interface
* AWS Mgmt Console
##### Forcast AWS Spending
* AWS Cost Explorer
##### If 90-100% utilization of EC2 instance over a year (with least cost)
* Reserved Instance
##### Secure EC2 Instances
* Usage of Security Group
* Usage of Network Access Control List(NACL)
##### Import Data into Amazon 
* AWS Glacier API
* AWS Glacier SDK
* AWS S3 lifecycle policies
##### Access to Support Concierge
* Enterprise
##### Note
* AWS is a Cloud Service Provider(CSP) that doesn't direclty store, transmit or process any customer cardholder data(CHD). However, AWS customers may create their own card data environment(CDE) that can store, transmit or process cardholder data using AWS products.
* If database is going to be used for a minimum of a year, then it is better to get Reserved Instances. You can save on cost if you use a (partial upfront options), you can get better discount. 
##### Deploy an application that needs to be PCI Compliant
* Choose AWS Service which are PCI Compliant
* Ensure the right steps are taken during application development for PCI Compliant
##### Feature of RDS that allows for data redundancies across regions
* Creating Read Replicas 
  * Ensures data is replicated to another region
##### Host self-managed database in AWS
* Hosting a database in an EC2 Instance
  * which means you want complete control over the database engine and the underlying infrastructure. 
##### Compatibe MySQL database which has the ability to grow in storage size on its own
* Aurora 
  * is a fully managed, MySQL and PostgreSQl-compatible, relational database engine. 
##### Elasticity
* ability of an application to scale up and scale down
  * diverting traffic to instances based on the demand
  * diverting traffic to instances with the least load
##### Link Account
* Consolidated Billing
* AWS Organization
* Using AWS Organizations, you can create **Service Control Policies** (SCPs) that centrally control AWS service use across multiple AWS accounts.
##### DDOS Protection 
* AWS Shield
* CloudFront
##### SQS
* decouple resource hosted on cloud
  * offers a reliable, highly-scalable hosted queue for storing msg as they travel between applications.
##### Disaster Recovery
* Route 53
##### Manage Infrastructure a code
* AWS CLoudformation
##### Disaster Recovery
* Backup and Restore (highest downtime)
* Pilot light
  * Describe a DR scenario in which a minimal version of an environment is always running in the cloud
* Warm Standby
* Multi Site (least downtime)
##### For jobs that can be interrupted and resumed at any time
* Spot (for periodically processing large volumes of data)
  * Spot instances are a cost-effective choice if you can be flexible about when your application runs and if your application can be interrupted.
  * Well suited for data analysis, batch jobs, optional task, background processing. 
##### Elastic Beanstalk
* allows developers to easily deploy and manage application in the cloud
* easy-to-use service for deploying and scaling web application and services developed with 
  * Java, .Net, PHP, Node.js, Python, Ruby, Go and Docker with familiar Servers such as Apache, Nginx, Passenger and IIS.
##### CloudFront
* is a content deliverey service using global network of edge location.
##### AWS Direct Connect
* Easy to establish network connection from your premises to AWS
  * You can establish private connection between AWS and your datacenter
  * You can connect VPC to remote network by using VPN connection
##### EC2
* Secure, resizable compute capacity
* Equivalent to hosting virtual server on an on-premise location
* Allows customer to retain full administrative privilages of underlying virtual infrastructure.

##### Preventing DDoS attack from EC2
* Usage of NACL
* Usage of Security Groups
##### AMI
* You can launch as many Instances from AMI
* Virtual Server in a cloud
* Spin up EC2 Instances on AWS Cloud
##### AWS Console cannot be used to upload data onto Glacier. The console can only be used to create Glacier vault which can be used to upload the data. 
##### Option of lifecycle policies that can be used to move objects to archieve storage
* Amazon S3
##### Features of Amazon RDS for better availability of database
* Multi-AZ
* Read-Replica
##### Transfer petabytes of data from on-premise location to AWS Cloud
* AWS Snowball
##### Autoscaling
* Scaling up resources on Demand
* helps to base the number of resources on the demand of application or users
##### To prevent data loss, EBS Volume replicates in same availability zone
##### IAM Roles
* Secure communication between EC2 Instance and S3
* An application deployed on an EC2 Instance to write data to S3 in secure manner.
##### AWS Inspector
* Analyzes EC2 instances against predefined security templates to check for vulnerabilities 
##### EMR
* off-hand large number of data sets to be processed
##### Principle designing Cloud Based System
* Assume everything will fail
* Build loosely-coupled components
  * If one computer does fail, the entire system doesn't fail
##### Amount of Storage that can be stored in S3
* Virtually unlimited storage (unlimited amount of data)
* But max size of s3 objects = 5TB & maximum buckets = 100
##### AWS Config
* AWS Config is a service that enables you to assess, audit, and evaluate the configurations of your AWS resources. Config continuously monitors and records your AWS resource configurations and allows you to automate the evaluation of recorded configurations against desired configurations.
##### If Application is critical and must be globally availabe at all times
* Deployment to multiple Regions (prevention for disaster recovery)
##### AWS Shield Advance
* for higher level of protection (provides expanded DDoS attack protection)
##### Allows you to carve out a portion of AWS CLoud
* AWS VPC (network that you'd operate in your own data center, with the benefits of using the scalable)
##### Fast, easy and secure transfer from client to S3 bucket
* S3 Transfer Acceleration
##### Ec2 Costing determination
* Instance Type
* AMI Type
* Region 
##### Amazon Glacier
* Infrequently accessed data
* Data archives
##### - An AZ is an isolated location within an AWS region; an edge location will deliver cached content to the closest location to reduce latency.
##### - You might set up NACL with rules similar to your security groups in order to add an additional layer of security in you VPC
* NACL is a feature associated with a subnet in VPC to protect against incomming traffic requests.
##### document that provides a formal statement of (one or more permissions)
* Policy 
  * Policy contains ( Resource, Action, Effect and Principal)
  * JSON document that specifies what user can do on AWS
##### Security group
* Acts as a firewall that controls the traffic allowed to reach one or more instances
* When you launch a VPC, you can assign the instance upto 5 security groups
* ##### Users can only SSH into EC2 instances that are attached to security group
##### - When you think of cost effectiveness, you can either have to choose Spot or Reserved Instances. Now When you have Regular Processing job, the best is to use spot instance
##### Amazon Elasticache (improves response time)
* Web service that makes it easy to deploy, operate and scale an in-memory data store or cache in cloud.
##### 2 tier architecture
* interface runs on a client
* data layer or data structure gets stored in server
##### To run secondary RDS if primary fails
* AWS Multi-AZ

##### - In case of an infrastructure failure, Amazon RDS performs an automatic failover to the standby (or to a read replica in the case of Amazon Aurora), so you can resume database operations as soon as the failover is complete.

##### CloudWatch Logs
* Aggregate Logs from EC2 instance

##### S3 Costs
* The total size of GB of all objects stored
* Total storage class used for objects stored --(cost doesn't depend on number of buckets)

##### To provide connection from on-premise infrastructure to resources hosted in AWS Cloud
* AWS Direct Connect
* AWS VPN

##### Snapshot
* is equivalent to AMI. You can launch as many instance from the AMI as you need. 
##### Secure way of using AWS API to call AWS services from EC2 instances
* IAM Roles
##### Host self managed database in AWS
* Using database on an EC2 Instance
##### Responsibility of customers when ensuring that data on EBS volume is left safe
* Creating EBS Snapshots
##### CloudWatch
* is a monitoring service. It helps to collect and track metrics, collect and monitor log files, set alarms, and automatically react to changes in your AWS resources.
##### Application that must be globally available all the times
* Deployment to multiple regions (geographic locations)
