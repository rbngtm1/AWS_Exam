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
