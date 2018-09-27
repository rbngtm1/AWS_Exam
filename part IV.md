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
