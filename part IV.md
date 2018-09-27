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
#### 
