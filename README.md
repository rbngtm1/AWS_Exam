# solution_architect_associate
#### You are hosting an web application in EC2, where number of users is expected to increase in comming months. Best methods to add elasticity is:
  * Set up web application on more EC2 instances and set them behind an ELastic Load Balancer.
  * Set up your web application on more EC2 and use Route 53 to route request accordingly.
#### Maximum ratio of IOPS to Volume size is 50:1
  * If the volume size is 8 GiB, the maximum IOPS of the volume can be 400.
#### In different subnet in same VPC, you have 2 Ubuntu instances located. These instances should be able to communicate with each other, but when you try to ping from one instance to another, you get a timeout. The route table seem to be valid and has the entry for the target "local" for your VPC CIDR. The valid reason for this issue is:
  * The Security Group has not been modified to allow the requested traffic.
 
