#### Create a RAID 0 configuration of multiple volumes
  * is used to increase the IOPS of clubbed volumes

#### Create a RAID 1 configuration of multiple volumes
  * is used for data mirroring

#### To ensure backups for available table in  DynamoDB
  * enable creation of on-demand backups for the tables.

#### To secure deletion of s3 bucket
  * In bucket policy, use condition key "aws:MultiFactorAuthPresent" to allow user to delete objects in S3 bucket post MFA authentication.

#### Deny access to any AWS Resources for root users
  * use SCP (service control policy) All SCP are applied from the master account which is account used to create AWS organization

#### To get list of the client's IP address for ec2 instances placed behind classic load balancer
  * Enable access logs for the ELB. ELB provides access logs that capture detailed information about requests sent to your load balancer.


## Monitoring

#### Basic: CloudWatch data is available automatically in 5-minute periods at no charge. This includes data for the root device volumes for EBS-backed instances.

#### Detailed: Provisioned IOPS SSD (io1) volumes automatically sends one-minute metrics in CloudWatch.


## load Balancing

#### Session cookie: aws elb create-lb-cookie-stickiness-policy.

#### Application Session cookie: aws elb create-app-cookie-stickiness-policy

#### In classic load balancer, configure connection draining to ensure that a classic load balancer stops sending requests to instances that are deregistered or unhealthy.
  * In CLB, the proxy protocol header helps you identify the IP address of a client when you have a load balancer that uses TCP for  back-end connections.

#### Sticky Sesson in CLB
  * By default, a Classic Load Balancer routes each request independently to the registered instance with the smallest load. However, you can use the sticky session feature (also known as session affinity), which enables the load balancer to bind a user's session to a specific instance. This ensures that all requests from the user during the session are sent to the same instances.

#### Permission required to ensure that ec2 instance will host an application that would access Dynamo DB table
  * A trust policy that allows the EC2 instance to assume a role
  * An IAM permission policy that allows the user to pass a role


#### Support plans
  * business and enterprise support plan facilitates:
    * Production system impared: < 4 hours
    * production system down: < 1 hour
  * enterprice additional support includes:
    * Business-critical system down: < 15 mins
    * Operational Support (Operation reviews, recommendation and reporting)

## Instance type
#### You may modify some attribute such as instance size for standard reserve instance, but if you are looking for probablity of having modifying instance type, switch to convertible reserve instance.

#### AWS Performance Insights
  * Performance Insights is on by default in the console for Aurora MySQL, Aurora PostgreSQL, and RDS PostgreSQL db engine, to help to monitor by vizualization of data load and analyze any issues that affect it.

#### AWS Organization
  * https://aws.amazon.com/organizations/faqs/
  * AWS Organizations allows you to manage multiple AWS accounts at once. With Organizations, you can create groups of accounts and then apply policies to those groups.

#### Other Important Concepts

```
AWS Organization helps to:
a.	Centrally Manage policies across multiple AWS Accounts
  i.	AWS Organizations allows you to manage multiple AWS accounts at once. You can create groups of accounts, and then attach policies to a group to ensure the correct policies are applied across the accounts. Organizations enables you to centrally manage policies across multiple accounts, without requiring custom scripts and manual processes.
b.	Control Access To AWS Services
  i.	With AWS Organizations, you can create Service Control Policies (SCPs) that centrally control AWS service use across multiple AWS accounts. You can specifically Allow or Deny individual AWS Services. For example you could deny the use of Kinesis or DynamoDB to your HR group within your AWS Organization. Even if IAM in that account allows it, SCP will overwrite it.
  ii.	Essentially you attach a policy to an organizational unit and every AWS accounts under that organizational unit will inherit that policy.
c.	Automate AWS Account Creation And Management
  i.	You can use the AWS Organizations APIs to automate the creation and management of new AWS accounts. The Organizations APIs enable you to create new accounts programmatically, and to add the new accounts to a group. The policies attached to the group are automatically applied to the new account.
d.	Consolidate Billing Across Multiple AWS Accounts
  i.	AWS Organizations enables you to set up a single payment method for all the AWS accounts in your organization through consolidated billing. With consolidated billing, you can see a combined view of charges incurred by all your accounts, as well as take advantage of pricing benefits from aggregated usage, such as volume discounts for Amazon EC2 and Amazon S3.

If organization has setup multiple IAM users and the organization wants that each IAM user accesses the IAM console only within the organization and not from outside.
Create an IAM policy with a condition which denies access when the IP address range is not from the organization.

What are Resource Groups?
Resource groups make it easy to group your resources using the tags that are assigned to them. You can group resources that share one or more tags.
Resource groups contain information such as;
a.	Region
b.	Name
c.	Health checks
Specific information
a.	For EC2- Public and Private IP addresses
b.	For ELB – Port Configurations
c.	For RDS – Database Engine, etc

COST EXPLORER cost explores helps to explore and forecast cost.
a.	Use tags to tag your resources
b.	Configure tags for cost centres (such as by department, employee id, etc)
c.	Activate cost allocation tags to track your costs by tags
d.	Generates cost report in csv format

AWS Config
AWS Config is a fully managed service that provides you with an AWS resource inventory, configuration history, and configuration change notifications to enable security and governance.
Enables:
a.	Compliance auditing
b.	Security analysis
c.	Resource tracking
Provides:
a.	Configuration snapshots and logs config changes of AWS resources
b.	Automated compliance checking
AWS Config stores everything inside S3 bucket. When any changes happen in the resources, it will send an event to AWS Config which will than send to AWS Config S3 Bucket.
As soon as something changes it could trigger a lambda function or you could schedule the lambda function to constantly look through AWS Config settings and tell you something is compliant. AWS Config will send notification to SNS notify to the system administrator.
Terminology
a.	Configuaration Items
 i.	Point-in-time attributes of resource
b.	Configuration Snapshots
 i.     Collection of Config Items
c.	Configuration Stream
 i.  Stream of changed Config Items
d.	Configuration History
 i.	Collection of config items for a resource over time
e.	Configuration Recorder
  i.	The configuration of Config that records and stores config items inside s3. Logs config for account in region

What we can see in AWS Config:
a.	Resource Type
b.	Resource ID
c.	Compliance
d.	Timeline
  i.	Configuration Details
  ii.	Relationships
	iii.	Changes
	iv.	CloudTrail Events
Note: config is regional

AWS CloudWatch vs CloudTrail vs Config
1.	CloudWatch monitors performance
2.	CloudTrail monitors API calls in the AWS platform
3.	AWS Config records the state of your AWS environment and can notify you of changes.

While sending data in CloudWatch, timestamp can be upto 2 weeks in past and upto 2 hours in future.
High-Resolution Metrics
Each metric is one of the following:
•	Standard resolution, with data having a one-minute granularity
•	High resolution, with data at a granularity of one second

Custom Metrics:
You can publish your own metrics to CloudWatch using the AWS CLI or an API. You can view statistical graphs of your published metrics with the AWS Management Console.

You can aggregate your data before you publish to CloudWatch. When you have multiple data points per minute, aggregating data minimizes the number of calls to put-metric-data.
aws cloudwatch put-metric-data --metric-name PageViewCount --namespace MyService --statistic-values Sum=11,Minimum=2,Maximum=5,SampleCount=3 --timestamp 2016-10-14T12:00:00.000Z

# Each PutMetricData request is limited to 40 KB in size for HTTP POST requests. You can send a payload compressed by gzip. Each request is also limited to no more than 20 different metrics.


# You can share a graph in Cloudwatch from the Share Graph URL.
# If a user would like to be notified if the CPU utilization of his EC2 instances exceed 90%, you can address this by using  AWS CloudWatch + AWS SNS
# Alarm set for 5 periods for 5 minutes each, means that there is no activity for 25 minutes then the state of alarm if set triggers.
# The aggregate data such as “sum of data”, “min value”, “max value” and “number of Data points”

HEALTH DASHBOARDS
1. Status.aws.amazon.com 1. Service health dashboards- shows the health of each AWS Service as a whole per region
2. Personal health dashboards – provides alerts and remediation guidance when AWS is experiencing events that may impact you
https://phd.aws.amazon.com/

Cloudwatch host level metrics consists of
1.	CPU
2.	Network
3.	Disk
4.	Status Check
Anything outside of that is a custom metrics
Custom metrics- minimum granularity is 1 minute
You can retrieve data from any terminated EC2 or ELB instance after its termination. CloudWatch Logs by default are stored indefinitely.
CloudWatch can be used on premise. Just need to download and install the SSM agent and Cloudwatch agent.

# User can supply file as an input to the CloudWatch command
Eg: aws cloudwatch put-metric-data - -namespace “Usage metrics” - -metric data file://metric.js     where namespace is mandatory

KEY IOPS METRICS – you can burst up to 3000 IOPS. If you need more than 3000 but less than 10000 just increase the volume size. Anything over 10,000 IOPS move to PIOPS
ELB MONITORING TYPES 4 Different Ways to Monitor Your Load Balancers;
1.	CloudWatch Metrics
2.	Access logs
3.	Request tracing
4.	CloudTrail logs

ELB connection draining
To ensure that the classical load balancer stops sending requests to instances that are de-registered or unhealthy while keeping the existing connection open, use connection draining. This enables the load balancer to complete inflight requests made to instance that are de-registering or unhealthy.
To enable connection draining using CLI, use aws elb modify-load-balancer-attributes command. You can set the connection draining timeout time from 1 sec to 3600sec(1hr)

# ELB supports the server order preference for negotiating connections between a client and a load balancer
ACCESS LOGS Access Logs can store data where the EC2 instance has been deleted. For example, say you have a fleet of EC2 instances behind an auto scaling group. For some reason your application has a load of 5XX errors which is only reported by your end customers a couple of days after the event. If you aren’t storing the web server logs anywhere persistent, it is still possible to trace these 5XX errors using Access Logs which would be stored in S3.
Access log sample bucket[/prefix]/AWSLogs/aws-account-id/elasticloadbalancing/region/yyyy/mm/dd/aws-account-id_elasticloadbalancing_region_load-balancer-id_end-time_ip-address_random-string.log.gz

Note the above sample doesn’t contain ec2-instance id

Loadbalancer
Spillovercount —> the total number of requests that were rejected because the surge queue is full.
ELASTICACHE
When it comes to monitoring our caching engines there are 4 important things to look at:
1.	CPU Utilization
2.	Swap Usage
3.	Evictions
4.	Concurrent Connections

# Use Elasticache offloading reads of DB for database query
CloudWatch – Dashboards are multi-region and can display any widget to any region. To add the widget, change to the region that you need and then add the widget to the dashboard.
Billing Alarms – You can create Billing Alarms to automatically alert you for when you go above a pre-defined cost that you set.
Create a billing alarm from within Cloudwatch: You can monitor your estimated AWS charges using Amazon CloudWatch. When you enable the monitoring of estimated charges for your AWS account, the estimated charges are calculated and sent several times daily to CloudWatch as metric data.
# CloudWatch will not truncate until it has an exponent larger than 126.
RESOURCE GROUPS resource groups are a way of grouping tags
You can use resource groups with AWS Systems manager to automate tags.

Placement Groups
Note:
1.	By default, AWS places instances across different physical hardware.
2.	This minimizes the impact of a hardware failure
3.	Great approach for building resilient, highly available systems
4.	Not so great for low latency, high network throughput applications.

Placement Group is the solution for this. There are three types of placement groups.
1.	Cluster Placement Group
Instances are all created in a single AZ. (low latency and high packet network performance)
2.	Partition
Instances are created in logical segments called partitions, each located in a separate rack(s), with independent network and power. Partition Placement Groups are described as large groups of instances where each group is placed on separate hardware.
3.	Spread
Each instance is created in separate rack, with independent network and power. Recommended for applications that have a small number of critical instances that should be kept separate from each other


STORAGE GATEWAY 
Storage Gateway consists of an on-premise software appliance which connects with AWS cloud-based storage to give you a seamless and secure integration between your on-premises IT environment and AWS.
Types of Storage Gateway
1	File Gateway- uses NFS/SMB
  i.	Files stored as objects in your S3 buckets
  ii.	Accessed using NFS or SMB mount point

2.	Volume Gateway – uses (iSCSI)
  a.	Stored Volumes
    i.	Store your all data locally and only backup to AWS
    ii.	Entire dataset stored on-site, backed-up to S3 as EBS Snapshots
  b.	Cached Volumes
    i. Use S3 as your primary storage and cache frequently accessed data in your Storage Gateway.
    ii. Entire dataset stored in S3, only frequently accessed data cached on-site.
3.	Tape Gateway – uses VTL(Virtual tape library)
  i.	Is a VTL which provides cost effective data archiving in the cloud using Glacier.


EXAM NOTES:    

1.	Configuration Recorder
AWS Config uses Configuration Recorder to detect and capture changes for resources. When a Configuration Recorder is stopped or deleted, the configuration change trigger does not run while periodic triggers continue to run at a specified period.

# Aggregator to collect data using AWS Config
For multi-account multi-region data aggregation. AWS Config uses aggregator to collect data from all account in various regions. Accounts which are not part of AWS Organization need to be individually added so that Aggregator can be authorized to collect data from these accounts.

CloudFront
Note: You might find it easier to use Amazon S3 bucket policies than object ACLs because you can add files to the bucket without updating permissions. However, ACLs give you more fine-grained control because you’re granting permissions on each individual file.
When an Amazon S3 bucket is not configured as website endpoint. Origin access identity can be used to restrict access directly to S3 bucket. OAI is a special CloudFront user which is associated with your distribution. S3 bucket policy is modified to allow OAI and deny all other access. Users accessing files use this OAI to access content from S3 bucket and cannot directly able to access S3 content bypassing CloudFront

CloudFront caches the 4xx and 5xx status codes returned by Amazon S3 or your custom origin server. If you have configured a custom error page for an HTTP status code, CloudFront caches the custom error page. If you are seeing error even after it, the possible reasons might be:
1. The user does not have access to the underlying bucket
2. The object which the user is requesting for is not present

Alias Record
An alias record can be created to redirect traffic to a specific AWS resources. Company can create an alias record for its domain name pointing to CloudFront Distribution. When a user access web application from any region, it would be redirect to nearest CoudFront edge location, and able to fetch web content with lowest latency.
Cost and Usage report
Cost and Usage report provides comprehensive cost details for all resources in AWS. Also, with Cost and Usage report, we can have customized reports. Cost and Usage reports can have multiple files which consists of data files for usage, separate file for discounts if any and a manifest file listing data files in a report. Columns in Cost and Usage Reports can be added or removed based upon customer requirement.
The Cost and Usage Reports is a .csv file or a collection of .csv files that is stored in an Amazon S3 bucket.

CloudWatch
1.	Single Graph for multiple Metrics
With Metric Math, you can create Amazon CloudWatch graphs querying multiple metric and display a new graph based upon math expression you required. This helps operational team to get a single graph for multiple metrics for AWS resources using math expressions.
2.	Metrics from multiple Regions
To create a custom dashboard with metrics data from different regions, detailed monitoring is required to be enabled. Also, any IAM users which has permission to use PutMetricData and PutDashboard can create such customized dashboard.

Consolidated Billing
In case of consolidated billing, estimated charges for all services in all accounts can be viewed by logging in as paying account. 
Cost Explorer
With Cost Explorer, 2 types of Reserved Instance are generated
1.	RI Utilization Report: This reports utilization of RI instance in terms of RI purchased and RI used. This RI is compared with On-demand cost for same amount of utilization and provides Net savings for using RI. RI utilization reports do not help you to identify under-purchased RI instances.
2.	RI Coverage Report: This report how much hours of instance utilization are covered by RI and hours spend on On-demand instance. This also displays how much savings would have been if RI are used instead of On-demand instance.
Both reports can be saves in CSV format

Health Check
For ELB health check following can be configure
1.	Ping protocol
2.	Ping port
3.	Ping path
4.	Response timeout
5.	Healthcheck interval
6.	Unhealthy Threshold
7.	Healthy threshold

HealthCheck interval is time period between health checks performed at EC2 instance while Unhealthy. Threshold is number of consecutive failed health checks before ELB considers EC2 as unhealthy. To determine unhealthy EC2 instance immediately, HealthCheck interval should be minimum as 5 sec (valid Range from 5 to 300 sec) and unhealthy threshold should also be least i.e. 2 (valid range from 2 to 10).
Amazon QuickSIght
Is a poweful BI tool to publish interactive dashboards report about the analysis.
It offers 2 editions, Standard and Enterprise.
Standard, you can invite an IAM user and allow to use their credentials to access amazon quicksight
Enterprise, you can select AD groups in directory services for access to amazon quicksight and supports encryption at rest

ELB error
504 Gateway Timeout error = check number of requests queued in SurgeQueueLength metric of Classic load balancer.

Configure sticky sessions for your Classic Load Balancer
By default, classic load balancer routes each request independently to the registered instance with the smallest load. However, you can use sticky session feature (also known as session affinity), which enables the load balancer to bind a user’s session to a specific instance. This insures all requests from the user during the session are sent to the same instance.
But if the instance fails or becomes unhealthly, the load balancer stops routing requests to that instance, and choses a new load balancer instance based on existing load balancer algorithm.

Have resource tagged during creation
You can use proactive approach for resource tagging to ensure all resources are tagged during creation. AWS CloudFormation, AWS Service Catalog, or IAM resource-level permissions are proactive method to have all resource tagged during creation.

Reactive approach for tagging== resource groups tagging api, aws config rules, and custom scripts


Protocol to retrieve metrics
1.	Collectd -> is a protocol used to retrieve metrics from Linux servers
2.	Statsd-> is protocol to retrieve metrics with Windows Servers
We can use Amazon Cloud Watch agent with StatsD and Collectd protocol.

Trusted advisor can be used to check usage details of AWS resources whether they are within the service limits for a resource.

Amazon GuardDuty: rules cannot be disabled or deleted but can be auto archived so any further findings from that rule will not be displayed on Amazon GuardDuty console or send to Amazon CloudWatch events for triggering further events.

Read Replica. If both Master and Read replica is part of the same region, encryption key used for encryption should be same. If master and read-replica are in different regions, encryption key should be used from the region in which read-replica is deployed.

AWS Inspector: for security assessment for applications deployed on EC2 instance.

Features associated with Master account:
1.	Create an organization and organizational unit
2.	Invite an external account to join your organization
3.	Pay all charges accrued by all the accounts in its organization.

Use AWS inspector to scan the instances for vulnerabilities. The following are the rules packages available in Amazon Inspector
1.	Common Vulnerabilities and Exposures
2.	Center for Internet Security (CIS) Benchmarks
3.	Security Best Practices
4.	Runtime Behavior Analysis


Note: Network Reachability package in amazon inspector helps to evaluate network configurations which can be used to identify potential risks in VPC. These package does not require and Amazon Inspector agent to be installed on EC2 instance. To automate these assessment checks, a CloudWatch event can be used which monitors changes to Security Group and Initiates Network Assessment using Network Reachability package.

When an object is uploaded to Amazon S3 bucket, a header “x-amz-server-side-encryption” requesting aws:kms encryption is added to that object. To deny any user to upload unencrypted objects to S3 bucket, a bucket policy can be created which will check header and deny user permission from uploading if header is not present.

# If the sysadmin has planned to encrypt server-side-key by supplying his own key(SSE-C). The valid parameters include:
1.	X-amz-server-side-encryption-customer-key
2.	X-amz-server-side-encryption-customer-algorithm
3.	X-amz-server-side-encryption-customer-key-MD5
4.	But doesn’t include X-amz-server-side-encryption-customer-key-AES-256


Iam: PassRole is the permission that controls which users can delegate IAM roles to an AWS resources. It ensures that users do not have additional permission to pass a role than a required minimum permission.

Note: for replication from one bucket to bucket onto another region:
1.	The source and destination buckets must have versioning enabled
2.	The source and destination buckets must be in different AWS Regions
Note: for storing server access logs,
1.	Source and target bucket should be separate bucket and should be created in the same AWS Region.

AWS Artifact
Provides on-demand downloads of AWS security and compliance documents, such as AWS ISO certifications, payment card industry(PCI), and Service Organization Control(SOC) reports.
Use case: an audit company is currenlty carrying out an audit of your infrastructure. They want to know what the types of security procedures are implemented at the data centers that host the AWS resources.

AWS CLoudFormation
If you are getting throttling, rate exceeded error in CloudFormation, the error is happening because the create stack API is creating too many resources at the same time. You can add some delayed between the request using a concept called “EXPONENTIAL BACKOFF”
# In CLoudFormation, you can use WaitCondition resource to hold the creation of other dependent resources.

When creating stacks in CLoudformation, and you want to manually correct the errors.
—> set the onFailure to DO_NOTHING when creating the stack

Mappings in CLoudformation:
The option mappings section matches a key to a corresponding set of named values. For example, if you want to set values based on a region, you can create a mapping that uses the region name as a key and contains the values you want to specify for each specific region. You use the Fn:FindInMap intrinsic function to retrieve values in a map.
To specify how AWS CloudFormation handles replacement updates for an AutoScaling group, use AutoScalingReplacingUpdate policy. This policy enables you to specify whether AWS Cloudformation replaces an Auto Scaling group with a new one or replaces only the instances in the Auto Scaling group.
Make changes to current stacks for updates:
When you need to make changes to a stack’s settings or change its resources, you update the stack instead of deleting it and creating a new stack. For example, if you have a stack with an EC2 instance, you can update the stack to change the instance’s AMI ID.
When you update a stack, you submit changes, such as new input parameter values or an updated template. AWS CloudFormation compares the changes you submit with the current state of your stack and updates only the changed resources.
# What is CORS Cross-Origin Resource Sharing (CORS) is a mechanism that uses additional HTTP headers to tell browsers to give a web application running at one origin, access to selected resources from a different origin

Temporarily Removing Instances from Your Auto Scaling Group
You can put an instance that is in the InService state into the Standby state, update or troubleshoot the instance, and then return the instance to service. Instances that are on standby are still part of the Auto Scaling group, but they do not actively handle application traffic.
https://docs.aws.amazon.com/autoscaling/ec2/userguide/as-enter-exit-standby.html



DynamoDB Tables
Table size:  there is no practical limit on a table size
Tables per account:  the initial limit is 256 tables per region, you can request a service limit increase.

Personal Health Dashboard.
AWS Personal Health Dashboard provides alerts and remediation guidance when AWS is experiencing events that may impact you. While the Service Health Dashboard displays the general status of AWS services, Personal Health Dashboard gives you a personalized view into the performance and availability of the AWS services underlying your AWS resources.

Aurora:
Supports up to 5 cross-region Read-replica for both encrypted and unencrypted DB cluster in any AWS region. Aurora automatically maintains 6 copies of data across 3 AZs.

Athena
While creating a Table in Amazon Athena, you can specify path of data to be read using LOCATION property. This path is specified as “s3://bucketname/prefix/”. Amazon Athena reads all data stored in this path.

RDS
Note: Amazon RDS started supporting Oracle from the version 12.1.0.2V10 and higher 12.1 versions, and for all 12.2 versions. So, there might be case where read replicas are not supported with the given version of Oracle.
Note: If the user didn’t specify the maintenance window during creation, AWS will select the default maintenance window. (30 mins)
Note: If the user has scheduled the maintenance of RDS DB, the DB instance may only go offline due to scale compute operations(which generally takes few minutes from start-to-finish) or required software patching. The DB instance never goes offline just by creating Read Replica, Making the DB Multi-AZ or changing the DB password.
# RDS Event Subscription
When you go to event dashboard in RDS, you can actually create event subscriptions based on security groups.
# For monitoring of MySQL RDS DB, you can direct the logs to the DB table, and then query the table.
# You can use Oracle GoldenGate with Amazon RDS for Active-Active database replication, zero-downtime migration and updates, disaster recovery, and in-region and cross-region replication.

Elasticache:
Memcached: If you exceed your chosen threshold, scale your cache cluster up by using a larger node type, and scale out by adding more nodes
Can handle load upto 90 percent, if it exceeds 90 percent, add more nodes to the cluster
It is multithreaded
Doesn’t support multiAZ
Redis: If you exceed your chosen threshold, choose a different node size with larger CPU and memory specification.
You only scale out(add more read replica)
It is not multithreaded
Supports multiAZ and master/slave replication
No swap-usage metric, instead use reserved memory

ElastiCache Redis (cluster mode disabled) cluster is under a heavy read load and needs to scale, Scale by adding read replicas to your cache cluster.



RDS
If you are using mysql RDS engine. Periodically, RDS performs below tasks in maintenance window:
1.	Update to the underlying Operating System
2.	Changes to the underlying DB version
3.	Patches applied to the server
# There is 35 days maximum retention period for automated backup. To have backup forever, consider using manual snapshot. Note that: if the you delete the DB instance, the automated backup can’t be recovered but if you take manual snapshot and delete the DB instance, it can be recovered.

Alias:
Alias records provide a Route-53 specific extension to DNS functionality. Instead of IP address or domain name, an alias record contains a pointer to an AWS resource such as a CloudFront distribution or an Amazon S3 bucket.

EFS:
EFS Mount Targets can be accessed only on following systems,
a.	Amazon EC2 Instance in local VPC
b.	EC2 Instance in VPC having VPC peering with other VPC
c.	On-Premise servers having AWS Direct Connect or AWS VPN to Amazon VPC.

Note: if the security team has received a list of black list IP address which are deemed as Spammers and want you to immediately block these IP address at the farthest point from cloud infrastructure.  In the Global level, create Web ACL, to block all IP address and apply it at edge level CloudFront.

Amazon DLM(Data lifecycle Manager)  helps to automate the creation, retention, and deletion of snapshots taken to back up your Amazon EBS volumes.

To get the object of S3 from only specific webpage, we can specify url in stringlike condition with aws:Referer, with action as S3:GetObject

Disaster Recovery

Backup and Restore - > Pilot light ->  Warm Standby -> Multi Site(most quickly recover against DR)

AWS Data Pipeline  is a web service that you can use to automate the movement and transformation of data. With AWS Data Pipeline, you can define data-driven workflows, so that tasks can  be dependent on the successful completion of previous tasks.
Eg: ec2- copy log files- dailys3- copy log files weekly Amazon EMR

If there is requirement to publish the metrics at an interval of 1 second from several devices onto Cloudwatch:
1.	Use the AWS CLI to publish custom metrics
2.	Publish metrics with high resolution

The following are required attributes which needs to be present in SAML Assertion send to AWS STS
1.	Role
2.	Audience
3.	RoleSessionName
4.	NameID
Saml maximum sessionduration is 12 hours.
You can ensure who has access to the keys in KMS services using Key Policies

Enabling log file integrity in Cloudtrail
•	To determine whether a log file was modified, deleted, or changed after CloudTrail delivered it, you can use CloudTrail log file integrity validataion.
Inline Policy
Inline policy are useful if you want to maintain a strict one-to-one relationship between a policy and the principal entity that it’s applied to. For eg: you have a vendor that needs access to an aws resource in your company’s account. You create an AWS user account. You want to restrict access to the resource using [inline policy] for a brief period of time.

For instance metrics, DiskReadOps, DiskWriteOps, DiskReadBytes, DiskWriteBytes are all associated with instance store volumes.
CLoudWatch Aggregation
Note: For aggregating, anything, for instance, cpu utilization of all of their EC2 instances across multiple regions.
1. Create a custom dashboard. Add widgets for each region. Aggregate the CPU utilization for all Instances in a region to each widget.
2. Ensure detailed monitoring is enabled for the instances.
CloudWatch widget types configuration for dashboard
1. Line —> Compare metrics over time
2. Stacked area —> Compare the total over time
3. Number —> Instantly see the latest value for a metric
4. Text —> Free text with markdown formatting
# VPC bounds main route table with private subnet and custom route table with public subnet.

Enable AutoScaling Instance Metrics
You can enable basic or detailed monitoring for your instances in AutoScaling group when you create launch configuration.
By default, basic monitoring is enabled when you create launch configuration using AWS console
But if you are using cli, by default, detailed monitoring is enabled. To set to basic monitoring you need to specify a flag with --instance-monitoring false
# Autoscaling terminates the instance first and then launches a new instance.
# If the user hasn’t selected security policy, by default, ELB will select the latest version of the policy.

NOTE: if you need to manage the global permission and billing for the various AWS Accounts, use AWS Organizations
Using AWS Organizations, you can create Service Control Policies(SCPs) that centrally control AWS service use across multiple AWS accounts. You can also use Organizations to help automate the creation of new accounts through APIs. Organizations helps simplify the billing for multiple accounts by enabling you to setup single payment method for all the accounts in your organization through consolidated billing.  AWS Organizations is available to all AWS customers at no additional charge.

Trusted Advisor —> for cost improvement suggestions.
Note: one of the major component of Trusted advisor is (COST OPTIMIZATION)

Reduce Latency of DynamoDb table
—> use DAX (DynamoDb accelerator)

For AWS S3 Default encryption
—> the objects are encrypted using server-side encryption with Amazon S3-managed keys (SSE-S3) or customer managed keys (CMKs) stored in AWS Key Management Service (AWS KMS).

AWS Shield
—> is managed Distributed Denial of Service(DDoS) protection
—> when you use AWS Shield Standard with Amazon CloudFront and Amazon Route 53, you receive comprehensive availability protection against all known infrastructure (Layer 3 and 4) attacks.
—> For higher levels of protection against attacks targeting your applications running on EC2, ELB, Cloudfront, Global accelerator and route 53 resource, you can subscribe to AWS Shield Advanced.

Note: AWS Global Accelerator is a service that improves the availability and performance of your applications with local or global users.

How MFA fit in with S3 Versioning
—> You can add another layer of protection by enabling MFA Delete on a versioned bucket. Once you do so, you must provide your AWS account’s access keys and a valid code from the account’s MFA device in order to permanently delete an object version or suspend or reactivate versioning on the bucket.
Note: MFA Delete only works for CLI or API interaction, not in the AWS Management console. Also, you cannot make version DELETE actions with MFA using IAM user credentials. You must use your root AWS account.

ALB —> scale automatically to adapt to changes in traffic. This makes planning for growth easy, but it has a side effect of changing the IP addresses that clients connect to. But the practice of resolving DNS are used along with ALB.
NLB —> enables static IP addresses for each AZ. These static address don’t change, so they are good for our firewalls’ whitelisting. However, NLB allows only TCP traffic, no HTTPS offloading, and they have none of the nice layer 7 features of ALB.

Direct Connect Gateways:
You can use an AWS Direct connect gateway to connect your AWS Direct Connect connection over a private virtual interface to one or more VPCs in your account that are located in the same or different regions.
Eg: us-west-1(VPC1) —> Direct connect gateway<— us-east-1(VPC2)

RDS Troubleshooting (If you are getting “Error connecting to database”): the possible case may be:
a. The application is using the wrong port number in the connection string
b. The database sever has the wrong ingress Security group rule for the web server.

Route 53
In case of complex routing policy for Route 53, a health check for all records alias and non-alias is necessary. For missing health check, Route 53 will assume it’s working and traffic is not diverted to healthy instance.

Reasons for not receiving a public DNS hostname for instances.
a. enableDnsHostNames is set to No
b. enableDnsSupport is set to No

Note: If you are planning to deploy a static website on Amazon S3 bucket. If you are using Route 53 and have registered domain and sub-domains name for a proposed website. While creating Amazon S3 bucket for this web content, which of the following is True with respect to name of s3 bucket
—> For both domains and sub-domains, name of Amazon s3 bucket should be same as name of record created in Amazon route 53.

Note: Amazon s3 does not support HTTPS access to the website. If you want to use HTTPS, you can use Amazon CloudFront to serve a static website hosted on Amazon S3.

Instance Warm-up
If you are creating step policy, you can specify the number of seconds that it takes for a newly launched instance to warm up. Until its specified warm-up time has expired, an instance is not counted toward the aggregated metrics of the Auto Scaling group.

Troubleshooting if you are getting “InsufficientInstanceCapacity”:
A. Wait a few minutes and then submit your request again
B. Try to launch an instance with different instance type.

Troubleshooting launch issues:
InstanceLimitExceeded —> error when you try to launch a new instance or restart a stopped instance, you have reached the limit on the number of instances that you can launch in a Region.
InsufficientInstanceCapacity —> error when you try to launch an instance or restart a stopped instance, AWS does not currently have enough available On-Demand capacity to service your request.

Maintenance of Underlying infrastructure that customer is responsible for:
a. Patch management of the underlying guest OS.
Note: AWS is responsible for patching and fixing flaws within the infrastructure, but customers are responsible for patching their guest OS and applications
b. Inventory management for the underlying databases.
Database Troubleshooting
If your db instance runs out of storage space, it might no longer be available. We highly recommend that you constantly monitor the FreeStorageSpace metric published in CloudWatch to ensure that your DB instance has enough free storage space. Also, the number of outstanding I/Os (read/write requests) waiting to access the disk.

Active Directory
—> Configure a SAML federation between AWS and the corporate Active Directory. Map Active Directory groups to IAM Roles to manage user permissions.

You can get public IP of an EC2 instance from the instance metadata.
Curl http://169.254.169.254/latest/meta-data/

Note: lambda functions can run only up to 15 minutes per execution.

Autoscaling
Note: if the instances run in autoscaling group across multiple AZs and is failing ELB health checks  that are not being replaced.
—> Configure the autoscaling group to determine health status using ELB health checks.
If you configure an Auto Scaling group to determine health status using EC2 status checks only (the default), the instance is unhealthy if it fails the EC2 status checks. However, if you have attached one or more load balancers or target groups to the autoscaling group and a load balancer reports that an instance is unhealthy, the instance is not considered unhealthy. Therefore, the instance is not replaced.

Run the command update-auto-scaling-group to configure one group to span across zones and delete the other group.

# Note: If health check returns status as impared to autoscaling group, terminate the instance and launch the new instance.
# If you suspend Launch, AZRebalance neither launches new instance nor terminates existing instances. This is because AZRebalance terminates instances only after launching the replacement instances. If you suspend Terminate, your Auto Scaling group can grow up to ten percent larger than maximum size.
Amazon Redshift.
—> logs information in the following log files:
1. Connection log -> logs authentication attempts, and connections and disconnections
2. User log -> logs information about changes to database user definitions
3. User activity log -> logs each query before it is run on the database.

# Multi-AZ supports MySQL, MariaDb, Oracle and PostgreSQL that utilizes synchronous physical replication to keep data on the standby up-to-date with primary. Note: With Microsoft SQL server, you need to use native mirroring to achieve High-Availability.
You can use scheduled scaling policy in AWS, both using console and CLI. But with CLI, you must specify the scheduled scaling period for less than a month whereas with Console there’s no such limitation.

AWS TAGS restriction
a.	Maximum number of tags per resource = 50
b.	Maximum key length = 128 Unicode characters in UTF-8
c.	Maximum value length = 256 Unicode characters in UTF-8

AWS reserved ip addresses
10.0.0.0 Network address
10.0.0.1 Reserved by AWS for the VPC router
10.0.0.2 Reserved by AWS for future use
10.0.0.255 Network broadcast address.

Multi AZ RDS Deployment
In Multi-AZ deployment, Amazon RDS automatically provisions and maintains a synchronous standby replica in different AZ. Please note that you may experience increase I/O latency (typically lasting few minutes) during backups for both Single-AZ and Multi-AZ deployments.
AWS Best practice for MultiAZ
In production based workload, we recommend you use Provisioned IOPS and DB instance classes (m1.large and larger) that are optimized for Provisioned IOPS for fast, consistent performance.

The example of SQS endpoint:
https://sqs.RegionName.amazonaws.com/AC-num/Queuename
Note: longer message retention provides greater flexibility to allow for longer intervals between message production and consumption. You can configure the Amazon SQS message retention period from 1 minute to 14 days. The default is 4 days.

# A user is using the AWS SQS to decouple the services. Operations supported by SQS
1.	SendMessageBatch
2.	DeleteMessageBatch
3.	CreateQueue
# Operation not supported by SQS is DeleteMessageQueue


Note: For EC2-Classic, If the user stops and starts the instance, the elastic IP disassociated form the instance when you stop it.

ASG options for suspended processes

Consolidated Billing
# If an AWS account wants to be a part of consolidated billing of his organization’s payer account.
 The payer account will send the request to the linked account to be a part of consolidated billing.

SSH Troubleshooting
If the user is getting error like “host key not found” the reason is:
1.	The user has provided the wrong user name for the OS login
2.	The access key to connect to the instance is wrong.

Copy AMI
1.	Copy AMI doesn’t copy the permission
2.	Copy AMI is used when you want the AMI to use in different region or with region to different AZ
3.	You can copy both Amazon-EBS backed AMIs and instance store-backed AMIs
4.	After the copy AMI is complete, you can apply launch permissions, user-defined tags, and Amazon s3 bucket permissions to the new AMI

Autoscaling Suspending link: https://docs.aws.amazon.com/autoscaling/ec2/userguide/as-suspend-resume-processes.html
Note: if the user suspended AutoScaling Alarm Notification which notifies Autoscaling for CloudWatch alarms process for a while  aws will receive the alarm but not execute the Auto Scaling policy. If you suspend Launch or Terminate, autoscaling would not be able to scale out and scale in respectively.

# For autoscaling to launch instance with new launch configuration,
 terminate-instance-in-auto-scaling-group<instance id> --no-should-decrement-desired-capacity

Reasons for instance to go from running state to terminated state
1.	The snapshot is corrupt
2.	The AMI is missing a required part
3.	The user account has reached the maximum volume limit

The following services provides the detailed monitoring in AWS CloudWatch without installing additional software.
1.	AWS RDS
2.	AWS ELB
3.	AWS Route53
4.	Autoscaling group
The service that don’t need detailed cloudwatch monitoring is AWS EMR, AWS SNS. CloudWatch metrics for EMR and SNS is 5 minutes.

VPC
Deleting the VPC will delete the objects associated with VPC in the region
1.	Subnets
2.	Security Group
3.	Network ACLs
4.	VPN attachments
5.	Internet Gateway
6.	Route table
7.	Network Interfaces
8.	VPC peering Connection
Note: not NAT gateway


Provisioned IOPS volume limit

General purpose
GP2 is designed to offer single-digit millisecond latencies, deliver a consistent baseline performance of 3 IOPS/GB (minimum 100 IOPS) to a maximum of 16,000 IOPS, and provide up to 250 MB/s of throughput per volume

EC2
# To know the EC2 instance reason behind termination
 The user can get the information from AWS Console, by checking the instance description under the Instance Termination reason level.

VPC
# How can user change the size of VPC
 You can expand the existing VPC by adding 4 secondary IPv4 ranges (CIDR) to your VPC

Security Policies
A security policy determines which ciphers and protocols are supported during SSL negotiations between a client and a load balancer. You can configure your Classic Load Balancers to use either predefined or custom security policies.
Note that a certificate provided by AWS Certificate Manager (ACM) contains an RSA public key. Therefore, you must include a cipher suite that uses RSA in your security policy if you use a certificate provided by ACM; otherwise, the TLS connection fails.
Predefined Security Policies
The names of the most recent predefined security policies includes version information based on the year and month that they were released. For example, the default predefined security policy is ELBSecurityPolicy-2016-08. Whenever a new predefined security policy is released, you can update your configuration to use it.
For information about the protocols and ciphers enabled for the predefined security policies, see Predefined SSL Security Policies.
Custom Security Policies
You can create a custom negotiation configuration with the ciphers and protocols that you need. For example, some security compliance standards (such as PCI and SOC) might require a specific set of protocols and ciphers to ensure that the security standards are met. In such cases, you can create a custom security policy to meet those standards.
# If the user gets Unprotected Private Key file error while ssh into instance, the private key file has wrong file permission. Try chmod for changing permission.
Encryption
Server-Side Encryption with Amazon S3-Managed Keys (SSE-S3)
When you use Server-Side Encryption with Amazon S3-Managed Keys (SSE-S3), each object is encrypted with a unique key. As an additional safeguard, it encrypts the key itself with a master key that it regularly rotates. Amazon S3 server-side encryption uses one of the strongest block ciphers available, 256-bit Advanced Encryption Standard (AES-256), to encrypt your data. For more information, see Protecting Data Using Server-Side Encryption with Amazon S3-Managed Encryption Keys (SSE-S3).
Server-Side Encryption with Customer Master Keys (CMKs) Stored in AWS Key Management Service (SSE-KMS)
Server-Side Encryption with Customer Master Keys (CMKs) Stored in AWS Key Management Service (SSE-KMS) is similar to SSE-S3, but with some additional benefits and charges for using this service. There are separate permissions for the use of a CMK that provides added protection against unauthorized access of your objects in Amazon S3. SSE-KMS also provides you with an audit trail that shows when your CMK was used and by whom. Additionally, you can create and manage customer managed CMKs or use AWS managed CMKs that are unique to you, your service, and your Region. For more information, see Protecting Data Using Server-Side Encryption with CMKs Stored in AWS Key Management Service (SSE-KMS).
Server-Side Encryption with Customer-Provided Keys (SSE-C)
With Server-Side Encryption with Customer-Provided Keys (SSE-C), you manage the encryption keys and Amazon S3 manages the encryption, as it writes to disks, and decryption, when you access your objects. For more information, see Protecting data using server-side encryption with customer-provided encryption keys (SSE-C).
# If the user is supplying his own key for SSE-C, it is possible to have different encryption keys for different versions of the same object.
# The server side encryption with the user supplied key works when versioning is enabled.
# Difference between instance-store and EBS-Backed volumes
Note: instance store volumes are ephemeral ( you will lose all data if the instance terminates) and is not under free tier limit. We cannot stop or start this instance-store volumes. Suitable for buffers, caches, scratch data, and other temporary content


# S3 buckets in all regions provide read-after-write consistency for PUTS of new objects and eventual consistency for overwrite PUTS and DELETE
# EC2, EMR and Elastic BeanStalk allows one to have complete access over the underlying architecture.
# For low latency between AWS and on-prep in authenticating using LDAP, you need to spin up secondary LDAP server that replicates from on-premise LDAP server. See below image

# If your webapplication behind ELB is disconnecting from session data. Follow below steps:
1.	Use Connection draining. This enables the load balancer to complete the in-flight requests made to the instances that are de-registering or unhealthy.
2.	Use ElastiCache to store session state. (in memory data store or cache in cloud)

Snapshot of Volumes
 Although you can take snapshot of a volume while a previous snapshot of that volume is in pending status, having multiple pending status may result in reduced volume performance until the snapshot is complete.
SurgeQueueLength and SpillOverCount
The Classic Load Balancer metric SurgeQueueLength measures the total number of requests queued by your Classic Load Balancer. An increased maximum statistic for SurgeQueueLength indicates that backend systems aren't able to process incoming requests as fast as the requests are received. Possible reasons for a high SurgeQueueLength metric include:
•	Overloaded Amazon Elastic Compute Cloud (Amazon EC2) instances behind the Classic Load Balancer that are unable to process all incoming requests
•	Application dependency issues due to external resource performance issues
•	Maximum allowable connection limits for instances
When requests exceed the maximum SurgeQueueLength, the SpilloverCount metric starts to measure rejected requests. The maximum SurgeQueueLength is 1024.
EBS

Elastic IP
 For EC2-classic, if you stop the instance, it’s elastic IP is disassociated, and you must reassociate the elastic IP when you restart the instance.
For regular EC2, The instance retains its associated Elastic IP addresses. You're charged for any Elastic IP addresses associated with a stopped instance


When you initiate the creation of a read replica, Amazon RDS takes a snapshot of your source DB instance and begins replication. As a result, you will experience a brief I/O suspension on your source DB instance as the snapshot occurs. The I/O suspension typically lasts on the order of one minute, and is avoided if the source DB instance is a Multi-AZ deployment (in the case of Multi-AZ deployments, snapshots are taken from the standby).

# more about volumes
https://aws.amazon.com/ebs/features/#:~:text=General%20purpose%20SSD%20(gp2)%20volumes&text=GP2%20is%20designed%20to%20offer,burst%20up%20to%203%2C000%20IOPS.


In an IAM policy, what action does IAM:PassRole relate to? [Select 2]
1.	Passing role to an AWS service to assign temporary permissions to the service
2.	Passing a role to another AWS account.


FAQs for glacier: Check Glacier Vault and data retrieving policy
```

### HAPPY LEARNING
