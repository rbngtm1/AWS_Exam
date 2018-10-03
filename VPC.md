#### You are working as an architect in your organization. You have peered VPC A as requester and VPC B as accepter and both VPCs can communicate with each other. Now you want resources in both your VPCs to reach out to internet but anyone on internet should not be able to reach resources within VPC. 
  * Create a NAT Gateways on both VPCs and configure routes in respective route with NAT Gateway.
#### Your organization already had a VPC(10.10.0.0/16)setup with one public(10.10.0.0/24) and two private subnets- private subnet 1(10.10.2.0/24) and private subnet 2 (10.10.3.0/24). Public subnet is having main route and two private subnets having two different route tables respectively. AWS sysops team reports a problem stating the EC2 instance in private subnet 1 cannot communicate to RDS MySQL database which is on private 2. What are possible reasons.
  * RDS security group inbound rule is incorrectly configured with 10.10.1.0/24 instead of 10.10.2.0/24
  * 10.10.3.0/24 subnet's NACL is modified and it does not have an inbound ALLOW rule set for ALL Traffic.
#### A new VPC with CIDR range 10.10.0.0/16 has been setup. Internet Gateway and new route table has been created and a new route has been added with internet gateway as target and 0.0.0.0/0 as destination. Two subnets have been created, one for public and one for private. A new linux EC2 instance has been launched on public subnet with Auto-assign Public IP option enabled. But when trying to SSH to the new machine, connection is getting failed. What could be the reason?
  * Both the subnets are associated with Main route table, no subnet is explicitly associated with new route table which has internet gateway route. 
#### You are an architect in your organization. Your organization would want to upload files to AWS S3 bucket privately through AWS VPC. In an existing VPC, you already have a subnet and route table which contains a route to NAT Gateway. You have created VPC Endpoint for S3 and added same route table. But in AWS S3 server logs you noticed that the request to S3 bucket from an EC2 instance within the subnet associated with above route table are going to internet through NAT Gateway. What could be causing this situation?
  * AWS S3 bucket is in different region than the VPC
    * because endpoints are supported within the same region only. You cannot create an endpoint between a VPC and a service in a different region. 
    * Note: VPC Endpoint always takes precedence over NAT Gateway or Internet Gateway. In the absence of VPC endpoint, requests to S3 are routed to NAT Gateway or Internet Gateway based on their existence in route tables. 
#### Your organization has an existing VPC with an AWS S3 VPC endpoint created and serving certain S3 buckets. You were asked to create a new S3 bucket and reuse existing VPC endpoint to route requests to new S3 bucket. However, after creating a new S3 bucket and sending requests from an EC2 instance via VPC endpoint, you found the request are failing with "Access Denied" error. What could be the issue?
  * VPC endpoint contains a policy, currently restricted to certain S3 buckets and does not contain new S3 bucket.
  * AWS IAM role/user does not have access to new S3 bucket. 
    * VPC endpoint has a policy which by default allows all actions on all S3 buckets. We can restrict access to certain S3 buckets and certain actions on this policy. In such cases, for accessing any new buckets or for any new instances, VPC endpoint policy needs to be modified accordingly.
#### If instances in private subnet cannot access internet
  * Check that you've configured your route tables correctly. 
    * The NAT gateway must be in public subnet with a route table that routes internet traffic to an internet gateway.
    * Your instances must be in a private subnet with a route table that routes internet traffic to the NAT gateway.
    * Check that there are no other route table entries that route all or part of the internet traffic to another device instead of the NAT gateway.
  * Ensure that your security group rules for your private instances allow outbound internet traffic
    * The NAT gateway itself allows all outbound traffic and traffic received in response to an outbound request ( it is therefore stateful)
