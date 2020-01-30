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

#### Basic: data is available automatically in 5-minute periods at no charge. This includes data for the root device volumes for EBS-backed instances.

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
